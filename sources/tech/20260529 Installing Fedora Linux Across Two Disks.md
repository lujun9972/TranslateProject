[#]: subject: "Installing Fedora Linux Across Two Disks"
[#]: via: "https://fedoramagazine.org/installing-fedora-linux-across-two-disks/"
[#]: author: "Jim Hall https://fedoramagazine.org/author/jhall/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing Fedora Linux Across Two Disks
======

![][1]

Photo by [Heliberto Arias][2] on [Unsplash][3]

A year ago, a family member gave me a 2019 laptop that wouldn’t run Windows anymore. And of course, I immediately installed Fedora Linux on it. While my day-to-day Fedora Linux system is a desktop PC, it’s nice to have a laptop to take with me when I do workshops or conference demos.

However, the laptop has a physical “spinning heads” hard disk, so it is really slow to boot. I timed it; the laptop takes almost two minutes to go from “power on” to “login prompt.” And that’s a very long time when you’re at the front of the room, waiting to start a demo.

I thought about replacing the hard disk with a solid state drive, but when I opened the laptop to make sure the drive was replaceable, I saw that the laptop also supports an NVMe solid state drive in addition to the hard disk.

![][4]

This presented an interesting opportunity: I could put in an NVMe drive and install Fedora Linux across two disks. Specifically, I wanted to boot Fedora Linux from the NVME drive, and keep extra apps and other data on the hard disk. I use several big third-party apps for my demos, which I install in both _/opt_ and _/usr/local_ , and it’s a huge pain to download and install those extra applications whenever I upgrade Fedora Linux. (I prefer to wipe and reinstall when I upgrade Fedora Linux, so I always have a clean starting point.) If I could keep _/opt_ and _/usr/local_ on the hard disk, I could preserve those when I install the next version of Fedora Linux.

### Installing Fedora Linux to the NVMe

After installing a new NVMe drive in the laptop, I needed to reinstall Fedora Linux. I prefer the Xfce desktop, so I downloaded the [Fedora Xfce spin][5] and booted the installer. When the installer reached the “Destination” step, it prompted me for the target disk. I clicked “Choose destination” and selected the NVMe disk:

![][6]

The rest of the installation ran normally. The Fedora Linux installer set up the partitions automatically on the new NVMe drive, encrypted my data, and installed the operating system.

![][7]

With Fedora Linux on the NVMe drive, booting took seconds instead of minutes. Again, I timed it: about 20 seconds to go from “power on” to “login prompt.” That’s a huge improvement!

### Setting up partitions on the hard disk

The disk partition app in the Fedora Xfce is GParted, which makes it easy to set up the hard disk with new partitions. However, GParted’s main limitation is that it [can’t set up encrypted volumes][8] for you. If you want to use encryption, you’ll need to use the command line and run _cryptsetup_ on your own.

However, I’m not very concerned about encrypting my _/opt_ and _/usr/local_ partitions. These are just third-party apps, not private data. My personal data will be saved to my home directory, which is safely encrypted on the NVMe drive. So I decided to set up regular partitions, formatted as ext4 filesystems.

I used GParted to delete the old partitions on the hard disk, and define three partitions that were each about 300 GB: _/opt_ (which I labeled as _opt_ ), _/usr/local_ (labeled _usrlocal_ ) and _/backup_ (labeled _backup_ ). GParted created the partitions and wrote an ext4 filesystem on each.

![][9]

However, the _/usr/local_ filesystem has a directory tree in it already, such as _/usr/local/bin_ and _/usr/local/lib_ , although these directories will be empty after installing Fedora Linux. I wanted to copy the original directories to the new filesystem. The easiest way to do that is to add the new _usrlocal_ partition somewhere else and then copy the old _/usr/local_ to the new partition. Adding a partition to a directory is called mounting, and the directory itself is called a mount point.

First, I needed to create a new mount point for the _usrlocal_ partition, which can be located anywhere on the filesystem. Since this was temporary, I created it under _/tmp_ then mounted the new partition using the _mount_ command:

```

    $ sudo mkdir /tmp/usrlocal
    $ sudo mount LABEL=usrlocal /tmp/usrlocal

```

Then I copied the contents of the old _/usr/local_ to the new /tmp/usrlocal mount point. The **-a** or **–archive** option copies everything:

```

    $ cd /usr/local
    $ sudo cp --archive * /tmp/usrlocal

```

After the process is complete, I unmounted the new partition:

```

    $ sudo umount /tmp/usrlocal

```

### Adding the partitions to the system

To make sure the new partitions are automatically mounted every time my laptop reboots, I needed to add them to my _/etc/fstab_ file. This is a special file that contains the filesystem table, which is a list of partitions that the system can find on the disk and where to mount them. For example, my default _/etc/fstab_ file looks like this:

```

    #
    # /etc/fstab
    # Created by anaconda on Sat May 23 20:15:13 2026
    #
    # Accessible filesystems, by reference, are maintained under '/dev/disk/'.
    # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
    #
    # After editing this file, run 'systemctl daemon-reload' to update systemd
    # units generated from this file.
    #
    UUID=c10ec138-be4b-4513-89b7-749ef4a0605e / btrfs subvol=root,compress=zstd:1,x-systemd.device-timeout=0 0 0
    UUID=a87b1ed4-4951-4da1-a4a4-a5c48f1f3b28 /boot ext4 defaults 1 2
    UUID=9AD9-2C52 /boot/efi vfat umask=0077,shortname=winnt 0 2
    UUID=c10ec138-be4b-4513-89b7-749ef4a0605e /home btrfs subvol=home,compress=zstd:1,x-systemd.device-timeout=0 0 0

```

Each line in the _/etc/fstab_ file is divided into several fields: the identifier for the filesystem (to learn more about these, see [Persistent Identifiers for Storage Devices][10] in the Fedora online documentation), the mount point, the filesystem type, a list of mount options, and two optional fields that control if backup software should “dump” the filesystem to backup media (use 0 for _never_ ) and what order the _fsck_ command should check filesystems when needed (usually 1 for the root filesystem, or 2 for other filesystems). I added these lines to my _/etc/fstab_ file, which defined the mount points for each of my new filesystems:

```

    LABEL=backup /backup ext4 defaults,noatime 0 2
    LABEL=opt /opt ext4 defaults,noatime 0 2
    LABEL=usrlocal /usr/local ext4 defaults,noatime 0 2

```

This is an internal drive, so it should be there every time the laptop boots up. If you add removable storage to the _/etc/fstab_ file, such as a USB drive, you should add the **nofail** option to this list of mount options. Otherwise, if the partition is not available when Linux starts up, the system will hang.

With these lines in the _/etc/fstab_ file, I ran these commands to reload the _/etc/fstab_ file, create the _/backup_ mount point, and mount each of the filesystems:

```

    $ sudo systemctl daemon-reload
    $ sudo mkdir /backup

    $ sudo mount /backup
    $ sudo mount /opt
    $ sudo mount /usr/local

```

This generated an SELinux alert right away, complaining that the new _/usr/local_ filesystem lacked the correct security context. The security information wasn’t “carried over” when copying the old _/usr/local_ directory tree. Fortunately, the SELinux error provides the solution:

![][11]

To restore the default SELinux security contexts to the new _/usr/local_ directory tree, I ran the _restorecon_ command. The **-v** option will print what it does to fix the system:

```

    $ sudo restorecon -v /usr/local
    Relabeled /usr/local from system_u:object_r:unlabeled_t:s0 to system_u:object_r:usr_t:s0
    Relabeled /usr/local/lost+found from system_u:object_r:unlabeled_t:s0 to system_u:object_r:usr_t:s0

```

### Filesystem flexibility

With just a few extra steps, I was able to use two disks with Fedora Linux, which lets me take full advantage of the storage on my laptop. The operating system now runs from the very fast NVMe drive, while my big third-party applications in _/usr/local_ and _/opt_ run from the hard disk.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/installing-fedora-linux-across-two-disks/

作者：[Jim Hall][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jhall/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/05/fedora-2-disks-816x345.jpg
[2]: https://unsplash.com/@helibertoarias?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/green-and-silver-hard-disk-drive-raNIrcd39jY?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://fedoramagazine.org/wp-content/uploads/2026/05/nvme-laptop.jpg
[5]: https://fedoraproject.org/spins/xfce/
[6]: https://fedoramagazine.org/wp-content/uploads/2026/05/nvme-install2-full.png
[7]: https://fedoramagazine.org/wp-content/uploads/2026/05/nvme-install4-full.png
[8]: https://gparted.org/features.php
[9]: https://fedoramagazine.org/wp-content/uploads/2026/05/nvme-gparted3.png
[10]: https://docs.fedoraproject.org/en-US/quick-docs/persistent-identifiers-for-storage-devices/#_filesystem_identifiers
[11]: https://fedoramagazine.org/wp-content/uploads/2026/05/nvme-selinux-full.png
