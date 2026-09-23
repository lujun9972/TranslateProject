[#]: subject: "Installing Fedora 45 on Stratis storage"
[#]: via: "https://fedoramagazine.org/installing-fedora-45-on-stratis-storage/"
[#]: author: "Vojtěch Trefný https://fedoramagazine.org/author/vtrefny/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing Fedora 45 on Stratis storage
======

![][1]

Photo by [Bernd 📷 Dittrich][2] on [Unsplash][3] [Modified]

The Anaconda installer in Fedora 45 will introduce a new option for storage configuration: Stratis, a modern solution for local storage management.

Stratis isn’t a completely new technology, it uses existing tools and technologies like device mapper, LUKS, and XFS and integrates them into an easy to use package. The idea is to provide modern storage features while hiding the often complex logic behind them. Adding support to the installer brings these features even closer to Fedora users.

There are only two basic structures or layers you need to know when working with Stratis: pools and filesystems. Pools represent an abstract layer on top of existing block devices (disks, partitions, RAID arrays etc.). A pool can consist of one or more devices (for systems with multiple disks, for example). Features like encryption or over-provisioning are also configured on the pool level. Multiple filesystems can be created on the pool. These are devices that will serve as your root or home volumes. Some additional features supported by Stratis include snapshots, caching, and for encrypted pools, multiple unlocking methods like TPM or Clevis/Tang. Caching and encryption without a passphrase are not currently supported by Anaconda, but these can be easily enabled after the installation.

Management of Stratis devices can be done using the _stratis_ command. For more information, check our older, but still valid, article [Getting started with Stratis][4] or the [Stratis project how-to][5].

### Installation using Web UI

The new web-based user interface for the Anaconda installer currently doesn’t allow selecting which type of storage technology will be used for the automated and guided partitioning options. The storage layout you will get depends on the Fedora variant you choose to install. But if you want to use Stratis, you still have an option in the graphical installation. Any storage layout can be created manually using the [Cockpit][6] storage module, which is integrated into the installer. To enter it, simply select the _If none of the options above apply…_ option on the _Installation Destination_ step.

![][7]

The Cockpit storage module supports a wide variety of storage configurations and Stratis is one of the supported technologies. Do not forget that with manual partitioning, you need to create all required partitions so first create partitions required for booting ( _/boot_ and _/boot/efi_ or _biosboot_ , based on your system configuration). After that, simply create a new Stratis pool from the menu.

![][8]

#### Creating stratis pool

After selecting a name for the pool and the disk (or disks) it will be placed on, you can decide whether to enable encryption and over-provisioning for the pool. Over-provisioning allows allocation of more space for the filesystems created on the pool. Similarly to how LVM thin provisioning and Btrfs work. With over-provisioning enabled, there is no need to worry about running out of space in root with still plenty of free space in _/home_. It also allows greater flexibility when using snapshots. On the other hand, you actually need to be aware that you don’t really have terabytes of space and you need to make sure you won’t actually run out of space on your disk. Both encryption and over-provisioning can also be enabled or disabled after the installation.

![][9]

#### Creating stratis filesystems

With the new pool created, you now need to add some filesystems to it. You’ll most likely want the standard two separate filesystems for your _/_ and _/home_. But you can also create a separate filesystem for your _/var_ , for example.

![][10]

If you enable over-provisioning on your pool, you can also decide to not specify sizes for the filesystems and use the 1 TiB default size with over-provisioning or set a size limit for the filesystem to prevent it from automatically growing if you ever run out of space.

![][11]

#### Using the configured layout

With all the filesystems created, you can _Return to installation_. Anaconda will check the created devices to make sure all requirements are met and return you to the _Installation destination_ page where a new _Use configured storage_ option will be preselected with the devices that were just created.

![][12]

![][13]

That is the storage part of the installation done. You can double-check on the _Review and install_ page that everything is correctly set and start the installation.

![][14]

### Installation using kickstart

For advanced users who wish to use automated installations, full kickstart support for Stratis is also available. Both automatic and manual partitioning are available via kickstart.

Automatic partitioning is simple: the existing _autopart_ command can be used with _–type=stratis_ to create the default Stratis storage layout fully automatically. A storage section in kickstart, for setting up an encrypted Stratis layout, could look like this:

```

    zerombr
    clearpart --all --initlabel
    autopart --type=stratis --encrypted --passphrase="passphrase"

```

Manual partitioning requires building the entire storage layout manually from bottom up. Two new Stratis kickstart commands were added: _stratispool_ for creating and managing Stratis pools and _stratisfs_ for creating and managing Stratis filesystems. Usage of these commands and most of the options are similar to how kickstart partitioning works with LVM. An example of a more advanced Stratis layout can be found below.

```

    reqpart
    part /boot --fstype=ext4 --size=500
    part stratis.01 --size=1 --grow --ondisk=vda
    part stratis.02 --size=1 --grow --ondisk=vdb
    stratispool fedora stratis.01 stratis.02
    stratisfs / --name=root --poolname=fedora --size=5000 --grow
    stratisfs /home --name=home --poolname=fedora --size=1 --grow

```

Here we are creating a pool called fedora on top of two disks, _vda_ and _vdb_ , with two filesystems. One called _root_ for _/_ and a second called _home_ for _/home_. The _–grow_ tells the installer to use all available free space when creating the devices. For more details about the commands see the [kickstart documentation][15].

### Conlusion

The newly introduced Stratis support in Anaconda offers an easy way to take advantage of the modern storage features offered by Stratis. With the Web UI support available through Cockpit storage, you can now easily use Stratis on your system. We plan to simplify the process even more in future releases and enable even more advanced Stratis features.

If you run into any issues or have feedback, both the Anaconda and Stratis teams would love to hear from you.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/installing-fedora-45-on-stratis-storage/

作者：[Vojtěch Trefný][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/vtrefny/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/09/fedora_45_on_stratis-816x345.jpg
[2]: https://unsplash.com/@hdbernd?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/rows-of-vintage-punched-cards-with-data-pmav25ETLiM?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://fedoramagazine.org/getting-started-with-stratis-up-and-running/
[5]: https://stratis-storage.github.io/howto/
[6]: https://cockpit-project.org/
[7]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-1-1024x640.png
[8]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-2-1024x640.png
[9]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-3-1024x640.png
[10]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-4-1024x640.png
[11]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-5-1024x640.png
[12]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-8-1024x640.png
[13]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-9-1-1024x640.png
[14]: https://fedoramagazine.org/wp-content/uploads/2026/09/installation-10-1024x640.png
[15]: https://pykickstart.readthedocs.io/en/latest/kickstart-docs.html
