[#]: subject: "Introducing the new bootc kickstart command in Anaconda"
[#]: via: "https://fedoramagazine.org/introducing-the-new-bootc-kickstart-command-in-anaconda/"
[#]: author: "Jiri Kortus https://fedoramagazine.org/author/jikortus/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introducing the new bootc kickstart command in Anaconda
======

![][1]

Anaconda installer now supports installation of bootc based bootable container images using the new bootc command. It has supported several types of payload to populate the root file system during installation. These include _RPM packages_ (likely the most widely used option), _tarball images_ you may know from Fedora Workstation, _ostree_ , and _rpm-ostree containers_. The [newest addition][2] to the family, from a couple of weeks ago, is _bootc-based bootable containers_.

### The difference is under the hood

We have added a new [bootc][3] kickstart command to Anaconda to support the new feature. This is very similar to the [ostreecontainer][4] command that has been present for some time. From the user’s perspective the two are very similar. The main difference, however, is under the hood.

One of the most important setup steps for a deployment is to create a requested partitioning in both cases. When the partitioning is ready, the ostreecontainer command makes Anaconda deploy the image onto the root filesystem using the ostree tool. It also executes the bootupctl tool to install and set up the bootloader. By contrast, with bootc containers installed using the bootc kickstart command, both the filesystem population and bootloader configuration is performed via the bootc tool. This makes the deployment process even more integrated.

The content of the container images used for installation is another difference. The bootc-enabled images are somewhat more versatile. Apart from installation using Anaconda, they provide a self-installing option via the bootc command executed from within a running container.

On the other hand, both options provide you with a way to install an immutable system based on a container image. This option may be useful for particular use cases where regular installation from RPM packages is not desired. This might be due to potentially lower deployment speed or inherent mutability of the resulting system.

### A simple how-to

In practice, you’d likely use a custom container with pre-configured services, user accounts and other configuration bits and pieces. However, if you want to quickly try out how the new Anaconda’s feature works, you just need to follow a few simple steps. Starting with a [Fedora Rawhide ISO][5]:

First, take an existing container from a registry and create a minimal [kickstart file][6] instructing Anaconda to install the bootable container image:

```

    # Beware that this kickstart file will wipe out the existing disk partitions.
    # Use it only in an experimental/isolated environment or edit it accordingly!
    zerombr
    clearpart --all --initlabel
    autopart

    lang en_US.UTF-8
    keyboard us

    timezone America/New_York --utc
    rootpw changeme

    bootc --source-imgref=registry:quay.io/fedora/fedora-bootc:rawhide

```

As a next step, place the kickstart file in some reachable location (e. g. HTTP server), point Anaconda to it by appending the following on the kernel command line:

```

    inst.ks=http://url/to/kickstart

```

Now start the installation.

Alternatively, you may use the mkksiso tool provided by the lorax package to embed the kickstart file into the installation ISO.

When installation and reboot is complete, you are presented with an immutable Fedora Rawhide system. It will be running on your hardware (or VM) installed from a bootable container image.

### Is there anything more about bootc in Anaconda?

You may ask if this option is limited to Fedora Rawhide container images. Technically speaking, you can use the Fedora Rawhide installation ISO to install, for instance, a CentOS Stream container image:

```

    bootc --source-imgref=registry:quay.io/centos-bootc/centos-bootc:stream10

```

Nevertheless, keep in mind that for now Anaconda will handle it as Fedora installation in such a case. This is because it runs from a Fedora Rawhide boot ISO. This may result in unforeseen problems, such as getting a btrfs-based partitioning that CentOS Stream won’t be able to boot from. This particular issue is easily overcome by explicitly telling Anaconda to use some different partitioning type, e. g. autopart –fstype=xfs. We would like to address the lack of container images handling based on the contained operating system or flavour in the future. For now, one just needs to take the current behavior into consideration when using the bootc command.

There are a couple more known limitations in Anaconda or bootc at this point in time. These include lack of support for partitioning setups spanning multiple disks, support for arbitrary mount points, or for installation from authenticated registries. But we hope it won’t take long to solve those shortcomings. There are also plans to make the new bootc command available even on the RHEL-10 platform.

We invite you to try out this new feature and share your experience, ideas or comments with the Installer team. We are looking forward to hearing from you in a thread on [discussion.fedoraproject.org][7]!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/introducing-the-new-bootc-kickstart-command-in-anaconda/

作者：[Jiri Kortus][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jikortus/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/12/anaconda-1890x800-1-816x345.jpg
[2]: https://github.com/rhinstaller/anaconda/pull/6298
[3]: https://pykickstart.readthedocs.io/en/latest/kickstart-docs.html#bootc
[4]: https://pykickstart.readthedocs.io/en/latest/kickstart-docs.html#ostreecontainer
[5]: https://dl.fedoraproject.org/pub/fedora/linux/development/rawhide/Server/x86_64/iso/
[6]: https://pykickstart.readthedocs.io/en/latest/kickstart-docs.html
[7]: http://discussion.fedoraproject.org
