[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (10 Ansible modules for Linux system automation)
[#]: via: (https://opensource.com/article/20/10/ansible-modules-linux)
[#]: author: (Ricardo Gerardi https://opensource.com/users/rgerardi)

10 Ansible modules for Linux system automation
======
These handy modules save time and hassle by automating many of your
daily tasks, and they're easy to implement with a few commands.
![gears and lightbulb to represent innovation][1]

[Ansible][2] is a complete automation solution for your IT environment. You can use Ansible to automate Linux and Windows server configuration, orchestrate service provisioning, deploy cloud environments, and even configure your network devices.

Ansible [modules][3] abstract actions on your system so you don't need to worry about implementation details. You simply describe the desired state, and Ansible ensures the target system matches it.

This module availability is one of Ansible's main benefits, and it is often referred to as Ansible having "batteries included." Indeed, you can find modules for a great number of tasks, and while this is great, I frequently hear from beginners that they don't know where to start.

Although your choice of modules will depend exclusively on your requirements and what you're trying to automate with Ansible, here are the top ten modules you need to get started with Ansible for Linux system automation.

### 1\. copy

The [copy][4] module allows you to copy a file from the Ansible control node to the target hosts. In addition to copying the file, it allows you to set ownership, permissions, and SELinux labels to the destination file. Here's an example of using the copy module to copy a "message of the day" configuration file to the target hosts:


```
\- name: Ensure MOTD file is in place
  copy:
    src: files/motd
    dest: /etc/motd
    owner: root
    group: root
    mode: 0644
```

For less complex content, you can copy the content directly to the destination file without having a local file, like this:


```
\- name: Ensure MOTD file is in place
  copy:
    content: "Welcome to this system."
    dest: /etc/motd
    owner: root
    group: root
    mode: 0644
```

This module works [idempotently][5], which means it will only copy the file if the same file is not already in place with the same content and permissions.

The copy module is a great option to copy a small number of files with static content. If you need to copy a large number of files, take a look at the [synchronize][6] module. To copy files with dynamic content, take a look at the `template` module next.

### 2\. template

The [template][7] module works similarly to the `copy` module, but it processes content dynamically using the [Jinja2 templating language][8] before copying it to the target hosts.

For example, define a "message of the day" template that displays the target system name, like this:


```
$ vi templates/motd.j2
Welcome to {{ inventory_hostname }}.
```

Then, instantiate this template using the `template` module, like this:


```
\- name: Ensure MOTD file is in place
  template:
    src: templates/motd.j2
    dest: /etc/motd
    owner: root
    group: root
    mode: 0644
```

Before copying the file, Ansible processes the template and interpolates the variable, replacing it with the target host system name. For example, if the target system name is `rh8-vm03`, the result file is:


```
Welcome to rh8-vm03.
```

While the `copy` module can also interpolate variables when using the `content` parameter, the `template` module allows additional flexibility by creating template files, which enable you to define more complex content, including `for` loops, `if` conditions, and more. For a complete reference, check [Jinja2 documentation][9].

This module is also idempotent, and it will not copy the file if the content on the target system already matches the template's content.

### 3\. user

The [user][10] module allows you to create and manage Linux users in your target system. This module has many different parameters, but in its most basic form, you can use it to create a new user.

For example, to create the user `ricardo` with UID 2001, part of the groups `users` and `wheel`, and password `mypassword`, apply the `user` module with these parameters:


```
\- name: Ensure user ricardo exists
  user:
    name: ricardo
    group: users
    groups: wheel
    uid: 2001
    password: "{{ 'mypassword' | password_hash('sha512') }}"
    state: present
```

Notice that this module tries to be idempotent, but it cannot guarantee that for all its options. For instance, if you execute the previous module example again, it will reset the password to the defined value, changing the user in the system for every execution. To make this example idempotent, use the parameter `update_password: on_create`, ensuring Ansible only sets the password when creating the user and not on subsequent runs.

You can also use this module to delete a user by setting the parameter `state: absent`.

The `user` module has many options for you to manage multiple user aspects. Make sure you take a look at the module documentation for more information.

### 4\. package

The [package][11] module allows you to install, update, or remove software packages from your target system using the operating system standard package manager.

For example, to install the Apache web server on a Red Hat Linux machine, apply the module like this:


```
\- name: Ensure Apache package is installed
  package:
    name: httpd
    state: present
```

This module is distribution agnostic, and it works by using the underlying package manager, such as `yum/dnf` for Red Hat-based distributions and `apt` for Debian. Because of that, it only does basic tasks like install and remove packages. If you need more control over the package manager options, use the specific module for the target distribution.

Also, keep in mind that, even though the module itself works on different distributions, the package name for each can be different. For instance, in Red Hat-based distribution, the Apache web server package name is `httpd`, while in Debian, it is `apache2`. Ensure your playbooks deal with that.

This module is idempotent, and it will not act if the current system state matches the desired state.

### 5\. service

Use the [service][12] module to manage the target system services using the required init system; for example, [systemd][13].

In its most basic form, all you have to do is provide the service name and the desired state. For instance, to start the `sshd` service, use the module like this:


```
\- name: Ensure SSHD is started
  service:
    name: sshd
    state: started
```

You can also ensure the service starts automatically when the target system boots up by providing the parameter `enabled: yes`.

As with the `package` module, the `service` module is flexible and works across different distributions. If you need fine-tuning over the specific target init system, use the corresponding module; for example, the module `systemd`.

Similar to the other modules you've seen so far, the `service` module is also idempotent.

### 6\. firewalld

Use the [firewalld][14] module to control the system firewall with the `firewalld` daemon on systems that support it, such as Red Hat-based distributions.

For example, to open the HTTP service on port 80, use it like this:


```
\- name: Ensure port 80 (http) is open
  firewalld:
    service: http
    state: enabled
    permanent: yes
    immediate: yes
```

You can also specify custom ports instead of service names with the `port` parameter. In this case, make sure to specify the protocol as well. For example, to open TCP port 3000, use this:


```
\- name: Ensure port 3000/TCP is open
  firewalld:
    port: 3000/tcp
    state: enabled
    permanent: yes
    immediate: yes
```

You can also use this module to control other `firewalld` aspects like zones or complex rules. Make sure to check the module's documentation for a comprehensive list of options.

### 7\. file

The [file][15] module allows you to control the state of files and directories—setting permissions, ownership, and SELinux labels.

For instance, use the `file` module to create a directory `/app` owned by the user `ricardo`, with read, write, and execute permissions for the owner and the group `users`:


```
\- name: Ensure directory /app exists
  file:
    path: /app
    state: directory
    owner: ricardo
    group: users
    mode: 0770
```

You can also use this module to set file properties on directories recursively by using the parameter `recurse: yes` or delete files and directories with the parameter `state: absent`.

This module works with idempotency for most of its parameters, but some of them may make it change the target path every time. Check the documentation for more details.

### 8\. lineinfile

The [lineinfile][16] module allows you to manage single lines on existing files. It's useful to update targeted configuration on existing files without changing the rest of the file or copying the entire configuration file.

For example, add a new entry to your hosts file like this:


```
\- name: Ensure host rh8-vm03 in hosts file
  lineinfile:
    path: /etc/hosts
    line: 192.168.122.236 rh8-vm03
    state: present
```

You can also use this module to change an existing line by applying the parameter `regexp` to look for an existing line to replace. For example, update the `sshd_config` file to prevent root login by modifying the line `PermitRootLogin yes` to `PermitRootLogin no`:


```
\- name: Ensure root cannot login via ssh
  lineinfile:
    path: /etc/ssh/sshd_config
    regexp: '^PermitRootLogin'
    line: PermitRootLogin no
    state: present
```

Note: Use the service module to restart the SSHD service to enable this change.

This module is also idempotent, but, in case of line modification, ensure the regular expression matches both the original and updated states to avoid unnecessary changes.

### 9\. unarchive

Use the [unarchive][17] module to extract the contents of archive files such as `tar` or `zip` files. By default, it copies the archive file from the control node to the target machine before extracting it. Change this behavior by providing the parameter `remote_src: yes`.

For example, extract the contents of a `.tar.gz` file that has already been downloaded to the target host with this syntax:


```
\- name: Extract contents of app.tar.gz
  unarchive:
    src: /tmp/app.tar.gz
    dest: /app
    remote_src: yes
```

Some archive technologies require additional packages to be available on the target system; for example, the package `unzip` to extract `.zip` files.

Depending on the archive format used, this module may or may not work idempotently. To prevent unnecessary changes, you can use the parameter `creates` to specify a file or directory that this module would create when extracting the archive contents. If this file or directory already exists, the module does not extract the contents again.

### 10\. command

The [command][18] module is a flexible one that allows you to execute arbitrary commands on the target system. Using this module, you can do almost anything on the target system as long as there's a command for it.

Even though the `command` module is flexible and powerful, it should be used with caution. Avoid using the command module to execute a task if there's another appropriate module available for that. For example, you _could_ create users by using the `command` module to execute the `useradd` command, but you _should_ use the `user` module instead, as it abstracts many details away from you, taking care of corner cases and ensuring the configuration only changes when necessary.

For cases where no modules are available, or to run custom scripts or programs, the `command` module is still a great resource. For instance, use this module to run a script that is already present in the target machine:


```
\- name: Run the app installer
  command: "/app/install.sh"
```

By default, this module is not idempotent, as Ansible executes the command every single time. To make the `command` module idempotent, you can use `when` conditions to only execute the command if the appropriate condition exists, or the `creates` argument, similarly to the unarchive module example.

### What's next?

Using these modules, you can configure entire Linux systems by copying, templating, or modifying configuration files, creating users, installing packages, starting system services, updating the firewall, and more.

If you are new to Ansible, make sure you check the documentation on how to create [playbooks][19] to combine these modules to automate your system. Some of these tasks require running with elevated privileges to work. For more details, check the [privilege escalation][20] documentation.

As of Ansible 2.10, modules are organized in collections. Most of the modules in this list are part of the `ansible.builtin` collection and are available by default with Ansible, but some of them are part of other collections. For a list of collections, check the Ansible [documentation][3].

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/ansible-modules-linux

作者：[Ricardo Gerardi][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/rgerardi
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/innovation_lightbulb_gears_devops_ansible.png?itok=TSbmp3_M (gears and lightbulb to represent innovation)
[2]: https://www.ansible.com/products/engine
[3]: https://docs.ansible.com/ansible/latest/collections/index.html#list-of-collections
[4]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html#ansible-collections-ansible-builtin-copy-module
[5]: https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html#desired-state-and-idempotency
[6]: https://docs.ansible.com/ansible/latest/collections/ansible/posix/synchronize_module.html#ansible-collections-ansible-posix-synchronize-module
[7]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html#ansible-collections-ansible-builtin-template-module
[8]: http://jinja.pocoo.org/docs/
[9]: https://jinja.palletsprojects.com/en/2.11.x/templates/
[10]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html
[11]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/package_module.html
[12]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/service_module.html
[13]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/systemd_module.html
[14]: https://docs.ansible.com/ansible/latest/collections/ansible/posix/firewalld_module.html
[15]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html
[16]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/lineinfile_module.html
[17]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/unarchive_module.html
[18]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html
[19]: https://docs.ansible.com/ansible/latest/user_guide/index.html#writing-tasks-plays-and-playbooks
[20]: https://docs.ansible.com/ansible/latest/user_guide/become.html
