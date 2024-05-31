[#]: subject: "A great journey towards Fedora CoreOS and bootc"
[#]: via: "https://fedoramagazine.org/a-great-journey-towards-fedora-coreos-and-bootc/"
[#]: author: "Daniel Mendizabal https://fedoramagazine.org/author/sigulete/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A great journey towards Fedora CoreOS and bootc
======

![][1]

Photo by [Matt Foxx][2] on [Unsplash][3]

Some time ago I wrote an article about Fedora Server. At the time, I didn’t know Fedora CoreOS, and my use case lead me to Fedora Server as a good alternative to run my workload which is mainly based on containers. Thanks to comments from the community, I learned about Fedora CoreOS as the natural next step, and they were not wrong.

Getting to know Fedora CoreOS has been a good experience. I use Fedora Silverblue on my laptop, so I wasn’t a stranger to atomic (image based) operating systems.

## **Provisioning with Ignition**

The documentation for this project is well organised and simple to follow. The first step was playing with Ignition to provision my node. Something I noticed from the beginning was that Ignition would be used to install Fedora CoreOS for the first time (first boot), but any future changes would have to be applied manually.

Despite the documentation advising that it would be possible to reinstall Fedora CoreOS while keeping the data persistent, I couldn’t get that result. It is due to the procedure I have to use on a cloud provider for reinstallations.

Nevertheless, to record post-installation changes, I keep my Ignition file up to date and matching my node. This policy helps me to remember what I have done and it makes it easy to replicate my server in the future.

As a rule of thumb, all system configuration in my node is handled by Ignition. It includes content in /etc and installed (layered) packages. Changes in my home directory would be created once the server is up and running and they would be backed up regularly.

## **Layering and Toolbx**

As suggested in the documentation, and similar to the criteria I follow on my laptop, I try to keep layering to a minimum, and use Toolbx to install utilities and troubleshooting tools.

Toolbx works in user space and it cannot access the root of the host filesystem, so there are a few limitations on what makes sense to install inside the container. Programs that need to access the host filesystem other than /home, /mnt and a few other specific locations wouldn’t be good candidates to run in Toolbx. The same rule applies for programs that need access to systemd services running on the host.

Ultimately, it depends on each individual case, but I opted to use the following criteria:

  * **Toolbx** : htop, ncdu, nmap, speedtest-cli, etc.
  * **Layered** : httpd, cockpit, tailscale, fail2ban, postfix, etc.



## **How bootc is rpm-ostree on steroids**

Following the announcement of container images at Red Hat summit, I started to look at this technology.

Using the existing techniques to build containers, bootc allows you to build your own OS. Container images use the OCI specification and container tools to build, and transport your containers. But, once the container is installed in a node, it becomes a regular OS.

Think of Fedora CoreOS as an opinionated final product, whereas bootc reference images are skeleton bootable containers to build on.

As of today, there are three official container images available:

  * quay.io/fedora/fedora-bootc
  * quay.io/centos-bootc/centos-bootc
  * registry.redhat.io/rhel9/rhel-bootc



Some of the issues I faced with rpm-ostree were resolved for my use case. Unlike Ignition applicable only at first boot, all changes are centralized in a container image and applied to my node in a continues integration approach orchestrated by Containerfile and bootc.

Furthermore, bootc includes the dnf package manager which has several benefits over the rpm-ostree package manager. For example, it is easier to query installed and available packages from existing and added repositories using dnf.

You may be tempted to execute dnf install. It appears to work, but it will error out. How the OS is configured is interesting. There is an overlay mount on **/** with no available space, so dnf install is tricked to believe that there is no space available.

Finally, with a simple command (bootc usr-overlay) bootc mounts an overlay on /usr making it possible to use dnf to install packages temporary. Once you are done testing, this overlay will be dropped at boot or it can be manually unmounted (umount -l /usr). I recommend removing all packages installed this way before unmounting /usr, so any configuration files installed in /etc will also be removed.

Personally, I feel more comfortable installing packages in my container image than I do when layering with rpm-ostree. However, I still follow the same criteria and put most system packages in the container image and the rest in Toolbx. Regarding my system configuration (/usr, /etc content), it is all implemented in the container image.

Unlike Fedora CoreOS which provides a default user (core), bootc images don’t have default user other than root. A default user can be created as part of the container build, or during the installation.

Similar to Fedora CoreOS, my system is completely reproducible at all times. There is however more control, fine tuning and available options building a container versus defining Ignition.

## **Filesystem structure**

The filesystem structure follows ostree specifications:

  * **/usr** directory is read-only, so all changes are solely managed by the container image.
  * **/etc** is editable, but any change applied in the container will be transferred to the node if the relevant configuration file wasn’t modified locally.



Anything requiring to be added to /var (including /var/home) will be done during first boot. Afterwards, /var is untouched.

## **Auto updates**

Fedora CoreOS uses _zincati_ as the agent handling transactional updates and reboots. There are a couple of parameters that control this process. One is wariness which indicates how eager the server is to receive updates. Another is the strategy to initiate a reboot. These parameters are used to control when rpm-ostree downloads image updates and when the system will be rebooted.

In a similar manner, bootc uses _bootc-fetch-apply-updates_ agent to accomplish the same outcome. This service checks the container repository for updates to the image, and triggers downloads as required to then reboot the system to apply the changes.

For convenience, it is simple to host a repo on GitHub, and use actions to generate images. In case you are not familiar with GitHub actions, the code below will do the trick:

The following example assumes your _Containerfile_ is located at: repo/mycontainer/Containerfile.
The action is implemented at: repo/.github/workflows/mycontainer-image.yml.

```

    name: build container -> mycontainer-image
    run-name: building container -> mycontainer-image
    on:
      workflow_dispatch:              #Allow triggering this action manually
      schedule:
      - cron: '30 0 * * 6'            #Schedule build at 12:30AM every Saturday
    jobs:
      mycontainer-image:
      runs-on: ubuntu-latest
      steps:
      - uses: actions/checkout@v4
      - name: run podman build
      run: podman build -t mycontainer-image mycontainer
      - name: push image to ghcr.io
      run: podman push --creds=${{ github.actor }}:${{ secrets.GITHUB_TOKEN }} mycontainer-image ghcr.io/<username>/mycontainer-image

```

## **Tweaks**

I encountered a few hurdles along the way that I would like to share here in hope that it will help others achieve a softer landing than I did.

When I created my container image, I configured _sshd_ to not allow password authentication, and I injected a public key as part of the container build. It took me sometime to understand why my connection was being rejected by the node.

Finally, I realized that for sshd to read authorized keys, it needs the _ssh-key-dir_ package. So, if you intend to use a SSH key to connect to your node, be sure to install that package as part of your container image. One could argue that it should be part of the base, but presumably there is some reason it is not.

Some packages rely on alternatives (explained here <https://www.redhat.com/sysadmin/alternatives-command>). As an example, when installing Postfix, it creates /usr/sbin/sendmail as a symlink implemented by /usr/sbin/sendmail.postfix, so any application relying on the _sendmail_ command will still work. A similar situation exists for the _man_ command. When installing the _man-db_ package, /usr/bin/man is created as a symlink and the target is /usr/bin/man.man-db.

Those symlinks are not created, so _sendmail_ and _man_ in these examples don’t work. As a temporary solution, I created symlinks to their respective handlers as part of the container image. I have submitted a bug report explaining this issue, and I can see that there is work being done to resolve it.

## **Final thoughts**

Below are the most common methods to install your custom container image:

  * **bootc install to-disk** is for installing the image on an available (not busy) disk. It doesn’t work if the disk has the root of the OS you booted from.
  * **bootc to-existing-root** can be used to install to the root of the OS you booted from (e.g. Fedora Server). This method won’t create the standard _bootc_ partitions. Instead, it will follow the existing disk configuration.
  * **bootc-image-builder** will create a raw image for _fedora-bootc_ and a raw/iso for _centos-bootc_ and _rhel-bootc_.



If this article has inspired your curiosity, then here are some links for further reading:

  * [Fedora/CentOS bootc][4]
  * [Fedora CoreOS][5]
  * [Bootc project][6]
  * [Bootc-image-builder][7]
  * [Curated documentation from Red Hat][8]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/a-great-journey-towards-fedora-coreos-and-bootc/

作者：[Daniel Mendizabal][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/sigulete/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/journey_toward_Fedora_CoreOS_bootc-816x346.jpg
[2]: https://unsplash.com/@foxxmd?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/asphalt-road-between-trees-IUY_3DvM__w?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://docs.fedoraproject.org/en-US/bootc
[5]: https://docs.fedoraproject.org/en-US/fedora-coreos
[6]: https://containers.github.io/bootc
[7]: https://github.com/osbuild/bootc-image-builder
[8]: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/using_image_mode_for_rhel_to_build_deploy_and_manage_operating_systems
