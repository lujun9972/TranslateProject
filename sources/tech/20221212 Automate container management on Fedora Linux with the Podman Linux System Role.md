[#]: subject: "Automate container management on Fedora Linux with the Podman Linux System Role"
[#]: via: "https://fedoramagazine.org/automate-container-management-on-fedora-linux-with-the-podman-linux-system-role/"
[#]: author: "Brian Smith https://fedoramagazine.org/author/briansmith/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Automate container management on Fedora Linux with the Podman Linux System Role
======

![][1]

Photo by [Wesley Tingey][2] on [Unsplash][3]

Containers are a popular way to distribute and run software on Linux. One of the tools included in Fedora Linux to work with containers is the Pod Manager tool, also known as [Podman][4]. This article describes the use of the Ansible Podman Linux System Roles to automate container management.

With Podman, you can quickly and easily download container images and run containers. For more information on Podman, check out the [Getting Started section][5] on the [podman.io][4] site.

While Podman is very easy to use, many people are interested in automating Podman for a variety of reasons. For example, maybe you have multiple Fedora Linux systems that you would like to deploy a container workload across, or perhaps you’re a developer and would like to setup an automated process to deploy containers on your local workstation for testing purposes. Whether you are working with containers on a single system, or need to manage containers across a number of systems, automation can be critical to being efficient and saving time.

### Overview of Linux System Roles

[Linux System Roles][6] are a set of Ansible roles/collections that can help automate the configuration and management of several aspects of Fedora Linux, CentOS Stream, RHEL, and RHEL derivatives. Linux System Roles is packaged in Fedora as an RPM (_linux-system-roles_) and is also available on Ansible Galaxy. For more information on Linux System Roles, and to see a list of included roles, refer to the [Linux System Roles project page][6].

Linux System Roles recently added a new [podman][7] role for automating the management of Podman containers. One of Podman’s unique features is that it is daemonless, so the _podman_ role directly sets the desired configuration on each host, and is capable of configuring the _containers.conf_, _containers-registries.conf_, _containers-storage.conf_, and _containers-policy.json_ settings.

### Podman systemd integration and Kubernetes YAML support

The _podman_ system role utilizes the [systemd integration with Kubernetes YAML][8] introduced in Podman version 4.2. Podman supports the ability to run containers based on Kubernetes YAML, which can make it easier to transition between Podman and Kubernetes. Podman 4.2 introduced a new _[podman-kube@.service][9]_ which uses systemd to manage containers defined in Kubernetes YAML. You’ll see an example of how the _podman_ system role utilizes this functionality below.

### Demo environment overview

In my environment I have four systems running Fedora Linux. The _fedora-controlnode.example.com_ system will be the Ansible control node — this is where I’ll install Ansible and Linux System Roles. The other three systems, _fedora-node1.example.com_, _fedora-node2.example.com_, and _fedora3-node3.example.com_ are the systems that I would like to deploy container workloads on to.

On these three systems, I would like to deploy a [Nextcloud][10] container. I would also like to deploy a web server container on these systems and run this as a non-privileged user (also referred to as a rootless container). I’ll use the [httpd-24 container image][11] that is a Red Hat [Universal Base Image][12] (UBI).

### Setting up the control node system

Starting on the _fedora-controlnode.example.com_ system, I’ll need to install the _linux-system-roles_ and _ansible_ packages:

```

    [ansible@fedora-controlnode ~]$ sudo dnf install linux-system-roles ansible

```

I’ll also need to configure SSH keys and the sudo configuration so that a user on the _fedora-controlnode.example.com_ host can authenticate and escalate to root privileges on each of the three managed nodes. In this example, I am using an account named _ansible_.

### Defining the Kubernetes YAML for the Nextcloud container

I’ll create a Kubernetes YAML file named _nextcloud.yml_ with the following content that defines how I want the [Nextcloud container][13] configured:

```

    apiVersion: v1
    kind: Pod
    metadata:
      name: nextcloud
    spec:
      containers:
        - name: nextcloud
          image: docker.io/library/nextcloud
          ports:
            - containerPort: 80
              hostPort: 8000
          volumeMounts:
            - mountPath: /var/www/html:Z
              name: nextcloud-html
      volumes:
        - name: nextcloud-html
          hostPath:
            path: /nextcloud-html

```

The key parts of this YAML specify:

  * the name of the container,
  * the URL for the container image,
  * that the container’s port 80 will be published on the host as port 8000,
  * that the _/var/www/html_ directory should use a volume mount using the _/nextcloud-html_ directory on the host.



### Defining the Kubernetes YAML for the web server

I’d also like to deploy a container running a web server, so I’ll define the following Kubernetes YAML file for it, named _ubi8-httpd.yml_:

```

    apiVersion: v1
    kind: Pod
    metadata:
      name: ubi8-httpd
    spec:
      containers:
        - name: ubi8-httpd
          image: registry.access.redhat.com/ubi8/httpd-24
          ports:
            - containerPort: 8080
              hostPort: 8080
          volumeMounts:
            - mountPath: /var/www/html:Z
              name: ubi8-html
      volumes:
        - name: ubi8-html
          hostPath:
            path: ubi8-html

```

This is similar to the _nextcloud.yml_ file:

  * specifying the name of the container,
  * the URL for the container image,
  * that the container’s port 8080 should be published on the host as port 8080,
  * that the _/var/www/html_ directory should use a volume mount using the _ubi8-html_ directory on the host.



Note that later on we’ll configure this container to run as a non-privileged user, so this path will be relative to the user’s home directory.

### Defining the Ansible inventory file

I need to define a Ansible inventory file that lists the host names of the systems I would like to deploy the containers on. I’ll create a simple inventory file, named _inventory_, with the list of my three managed nodes:

```

    fedora-node1.example.com
    fedora-node2.example.com
    fedora-node3.example.com

```

### Defining the Ansible playbook

The final file I need to create is the actual Ansible playbook file, which I’ll name _podman.yml_ with the following content:

```

    - name: Run the podman system role
      hosts: all
      vars:
        podman_firewall:
          - port: 8080/tcp
            state: enabled
          - port: 8000/tcp
            state: enabled
        podman_create_host_directories: true
        podman_host_directories:
          "ubi8-html":
            owner: ansible
            group: ansible
            mode: "0755"
        podman_kube_specs:
          - state: started
            run_as_user: ansible
            run_as_group: ansible
            kube_file_src: ubi8-httpd.yml
          - state: started
            kube_file_src: nextcloud.yml
      roles:
        - fedora.linux_system_roles.podman

    - name: Create index.html file
      hosts: all
      tasks:
        - ansible.builtin.copy:
            content: "Hello from {{ ansible_hostname }}"
            dest: /home/ansible/ubi8-html/index.html
            owner: ansible
            group: ansible
            mode: 0644
            serole: object_r
            setype: container_file_t
            seuser: system_u

```

This playbook contains two plays, the first is named _Run the podman system role_. This play defines variables that control the _podman_ system role, which is called as part of this play. The variables defined are:

  * _podman_firewall_: specifies that port 8080/tcp and 8000/tcp should be enabled. These ports are used by the _ubi8-httpd_ and _nextcloud_ containers, respectively.
  * _podman_create_host_directories_: specifies that host directories defined in the Kubernetes files will be created if they don’t exist
  * _podman_host_directories_: Within the _ubi8-httpd.html_ Kubernetes YAML file, I defined a _ubi8-html_ volume. This variable specifies that this _ubi8-html_ directory on the hosts will be created with the _ansible_ owner and group, and with a _0755_ mode. Note that the _nextcloud-html_ volume, defined in the _nextcloud.yml_ file, is not listed here so the default ownership and permissions will be used when the directory is created on the hosts.
  * _podman_kube_specs_: This lists the Kubernetes YAML files that the _podman_ system role should manage. It refers to the two files that were previously explained, _ubi8-httpd.yml_, and _nextcloud.yml_ . Note that for the _ubi8-httpd.yml_ container, it is also specified that this should be run as the _ansible_ user and group.



The second play, _Create index.html file_, uses the _ansible.builtin.copy_ module to deploy a _index.html_ file to the _/home/ansible/ubi8-html/_ directory. This will provide the web server running from the _ubi8-html_ containers content to serve.

### Running the playbook

The next step is to run the playbook from the _fedora-controlnode.example.com_ host with the following command:

```

    [ansible@fedora-controlnode ~]$ ansible-playbook -i inventory -b podman.yml

```

I’ll verify that the playbook completes successfully with no failed tasks:

![][14]

At this point, the _nextcloud_ and _ubi8-html_ containers should be deployed on each of the three managed nodes.

### Validating the Nextcloud containers

Now, I’ll validate the successful deployment of the _nextcloud_ containers on the three managed nodes. I can validate that Nextcloud is accessible by connecting to each host on port 8000 using a web browser, which shows the Nextcloud configuration screen on each host:

![][15]

I’ll further investigate the _fedora-node1.example.com_ host by connecting to it over SSH and using sudo to access a root shell:

```

    [ansible@fedora-controlnode ~]$ ssh fedora-node1.example.com
    [ansible@fedora-node1 ~]$ sudo su -
    [root@fedora-node1 ~]#

```

Run _podman ps_ to validate that the _nextcloud_ container is running:

```

    [root@fedora-node1 ~]# podman ps
    CONTAINER ID  IMAGE                                    COMMAND               CREATED        STATUS            PORTS                 NAMES
    7b6b131a652d  localhost/podman-pause:4.2.1-1662580699                        4 minutes ago  Up 4 minutes ago                        0aa0edcf4b08-service
    71a2a1a48232  localhost/podman-pause:4.2.1-1662580699                        4 minutes ago  Up 4 minutes ago  0.0.0.0:8000->80/tcp  8b226e4ad5c1-infra
    c307a07c7cae  docker.io/library/nextcloud:latest       apache2-foregroun...  4 minutes ago  Up 4 minutes ago  0.0.0.0:8000->80/tcp  nextcloud-nextcloud

```

Validate that the _/nextcloud-html_ directory on the host has been populated with content from the container:

```

    [root@fedora-node1 ~]# ls -al /nextcloud-html/
    total 112
    drwxr-xr-x. 1   33 tape   420 Nov  7 13:16 .
    dr-xr-xr-x. 1 root root   186 Nov  7 13:12 ..
    drwxr-xr-x. 1   33 tape   880 Nov  7 13:16 3rdparty
    drwxr-xr-x. 1   33 tape  1182 Nov  7 13:16 apps
    -rw-r--r--. 1   33 tape 19327 Nov  7 13:16 AUTHORS
    drwxr-xr-x. 1   33 tape   408 Nov  7 13:17 config
    -rw-r--r--. 1   33 tape  4095 Nov  7 13:16 console.php
    -rw-r--r--. 1   33 tape 34520 Nov  7 13:16 COPYING
    drwxr-xr-x. 1   33 tape   440 Nov  7 13:16 core
    ...
    ...

```

I can also see that a systemd unit has created for this container:

```

    [root@fedora-node1 ~]# systemctl list-units | grep nextcloud
      podman-kube@-etc-containers-ansible\x2dkubernetes.d-nextcloud.yml.service                                                            loaded active running   A template for running K8s workloads via podman-play-kube

    [root@fedora-node1 ~]# systemctl status podman-kube@-etc-containers-ansible\\x2dkubernetes.d-nextcloud.yml.service
    ● podman-kube@-etc-containers-ansible\x2dkubernetes.d-nextcloud.yml.service - A template for running K8s workloads via podman-play-kube
         Loaded: loaded (/usr/lib/systemd/system/podman-kube@.service; enabled; vendor preset: disabled)
         Active: active (running) since Mon 2022-11-07 13:16:52 MST; 7min ago
           Docs: man:podman-play-kube(1)
       Main PID: 7601 (conmon)
          Tasks: 3 (limit: 4655)
         Memory: 31.1M
            CPU: 2.562s
    ...
    ...

```

Note that the name of the service is quite long because it refers to the name of the Kubernetes YAML file, _/etc/containers/ansible-kubernetes.d/nextcloud.yml_. This file was deployed by the _podman_ system role. If I display the contents of the file, it matches the contents of the _nextcloud.yml_ Kubernetes YAML file I created on the control node host.

```

    [root@fedora-node1 ~]# cat /etc/containers/ansible-kubernetes.d/nextcloud.yml
    apiVersion: v1
    kind: Pod
    metadata:
        name: nextcloud
    spec:
        containers:
        -   image: docker.io/library/nextcloud
            name: nextcloud
            ports:
            -   containerPort: 80
                hostPort: 8000
            volumeMounts:
            -   mountPath: /var/www/html:Z
                name: nextcloud-html
        volumes:
        -   hostPath:
                path: /nextcloud-html
            name: nextcloud-html

```

### Validating the ubi8-httpd containers

I’ll also validate that the _ub8-httpd_ container, which was deployed to run as the _ansible_ user and group, is working properly. Back on the _fedora-controlnode.example.com_ host, I’ll validate that I can access the web server on port 8080 on each of the three managed nodes:

```

    [ansible@fedora-controlnode ~]$ for server in fedora-node1.example.com fedora-node2.example.com fedora-node3.example.com; do curl ${server}:8080; echo; done
    Hello from fedora-node1
    Hello from fedora-node2
    Hello from fedora-node3

```

I’ll also connect to one of the managed nodes as the _ansible_ user to further investigate:

```

    [ansible@fedora-controlnode ~]$ ssh fedora-node1.example.com
    [ansible@fedora-node1 ~]$ whoami
    ansible

```

I’ll run _podman ps_ and validate that the ubi8-httpd container is running:

```

    [ansible@fedora-node1 ~]$ podman ps
    CONTAINER ID  IMAGE                                            COMMAND               CREATED         STATUS             PORTS                   NAMES
    7b42efd7c9c0  localhost/podman-pause:4.2.1-1662580699                                20 minutes ago  Up 20 minutes ago                          1b46d9874ed0-service
    f62b9a2ef9b8  localhost/podman-pause:4.2.1-1662580699                                20 minutes ago  Up 20 minutes ago  0.0.0.0:8080->8080/tcp  0938dc63acfd-infra
    4b3a64783aeb  registry.access.redhat.com/ubi8/httpd-24:latest  /usr/bin/run-http...  20 minutes ago  Up 20 minutes ago  0.0.0.0:8080->8080/tcp  ubi8-httpd-ubi8-httpd

```

This container was deployed as a non-privileged user (the _ansible_ user) so there is a systemd user instance running as the _ansible_ user. I’ll need to specify the _–user_ option on the _systemctl_ command when validating that the systemd unit was created and is running:

```

    [ansible@fedora-node1 ~]$ systemctl --user list-units | grep ubi8
      podman-kube@-home-ansible-.config-containers-ansible\x2dkubernetes.d-ubi8\x2dhttpd.yml.service                                       loaded active running   A template for running K8s workloads via podman-play-kube

    [ansible@fedora-node1 ~]$ systemctl --user status podman-kube@-home-ansible-.config-containers-ansible\\x2dkubernetes.d-ubi8\\x2dhttpd.yml.service
    ● podman-kube@-home-ansible-.config-containers-ansible\x2dkubernetes.d-ubi8\x2dhttpd.yml.service - A template for running K8s workloads via podman-play-kube
         Loaded: loaded (/usr/lib/systemd/user/podman-kube@.service; enabled; vendor preset: disabled)
         Active: active (running) since Mon 2022-11-07 13:12:31 MST; 24min ago
           Docs: man:podman-play-kube(1)
       Main PID: 5260 (conmon)
          Tasks: 17 (limit: 4655)
         Memory: 9.3M
            CPU: 1.245s
    ...
    ...

```

As previously mentioned, the systemd unit name is so long because it contains the path to the Kubernetes YAML file, which in this case is _/home/ansible/.config/containers/ansible-kubernetes.d/ubi8-httpd.yml_. This file was deployed by the _podman_ system role and contains the contents of the _ubi8-httpd.yml_ file previously configured on the _fedora-controlnode.example.com_ host.

### Validating containers automatically start at boot

I’ll reboot the three managed nodes to validate that the containers automatically start up at boot.

After the reboot, the _nextcloud_ containers are still accessible on each host on port 8000, and the _ubi8-httpd_ containers are accessible on each host at port 8080.

The systemd units for the _nextcloud_ containers and _ubi8-httpd_ containers are both enabled to start at boot. However, note that the _ubi8-httpd_ container is running as a non-privileged user (the _ansible_ user) , so the _podman_ system role has automatically enabled user lingering for the _ansible_ user. This setting enables a systemd user instance to be started at boot, and to keep running when the user logs out, so that the container will automatically start at boot.

### Conclusion

The _podman_ Linux System Role can help automate the deployment of Podman containers across your Fedora Linux environment. You can also combine the _podman_ system role with the other Linux System Roles in the Fedora _linux-system-roles_ package to automate even more. For example, you could write a playbook that utilizes the _storage_ Linux System Role to configure filesystems across your environment, and then use the _podman_ system role to deploy containers that utilize those filesystems.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/automate-container-management-on-fedora-linux-with-the-podman-linux-system-role/

作者：[Brian Smith][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/briansmith/
[b]: https://github.com/lujun9972
[1]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/11/Podman_Linux_Sys_Role-816x345.jpg
[2]: https://unsplash.com/@wesleyphotography?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/backgrounds?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://podman.io/
[5]: https://podman.io/getting-started/
[6]: https://linux-system-roles.github.io/
[7]: https://github.com/linux-system-roles/podman/
[8]: https://www.redhat.com/sysadmin/kubernetes-workloads-podman-systemd
[9]: mailto:podman-kube@.service
[10]: https://nextcloud.com/
[11]: https://catalog.redhat.com/software/containers/ubi8/httpd-24/6065b844aee24f523c207943
[12]: https://developers.redhat.com/products/rhel/ubi
[13]: https://hub.docker.com/_/nextcloud
[14]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/11/Screenshot-from-2022-11-07-13-17-06-copy.png
[15]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/11/Screenshot-from-2022-11-07-13-17-35-copy.png
