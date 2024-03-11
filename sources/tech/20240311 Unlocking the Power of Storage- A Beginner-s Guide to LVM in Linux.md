[#]: subject: "Unlocking the Power of Storage: A Beginner's Guide to LVM in Linux"
[#]: via: "https://itsfoss.com/lvm-guide/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Unlocking the Power of Storage: A Beginner's Guide to LVM in Linux
======

[![Warp Terminal][1]][2]

The **LVM (Logical Volume Manager)** is a storage management system used by Linux operating systems. It allows for the creation of logical volumes, which can be viewed as containers that hold data.

The single biggest advantage of LVM is the ease of changing the size of logical volumes (consider it to as disk partitions).

In this tutorial, you'll learn what LVM is, how it works, and some of its other uses in Linux.

Before diving in, let's take a moment to learn a bit about LVM, ensuring you're equipped with the knowledge to make the most out of this storage management gem.

### What is LVM in Linux?

Linux's Logical Volume Manager, or LVM for short, was [introduced by Red Hat][3] in 2001, and has since become a standard feature in many Linux distributions. It provides a way to map physical storage as virtual disks, which can be created, modified and destroyed as per your needs.

Instead of dealing directly with individual hard drives or storage devices, LVM creates a layer of abstraction, making storage management a breeze. This allows for more efficient use of your computer's storage capacity.

You can think of volume management on Linux using LVM as something very close or even a replacement to RAID, where you "pool" multiple physical disks together to create a one or more virtual storage devices.

#### Components of LVM:

Logical Volume Manager in Linux comprises several key components that work together to provide flexible storage management.

Here are the main components of LVM:

  1. **Physical Volume (PV):** Actual storage devices like hard drives.
  2. **Volume Group (VG):** Combine multiple PVs into a flexible pool of storage.
  3. **Logical Volume (LV):** Virtual partitions within a VG that users can interact with (think of them as disk partitions).
  4. **Physical Extent (PE):** Smallest units of storage in a PV.
  5. **Logical Extent (LE):** Similar to PEs, but within LVs.
  6. **Metadata:** Information describing the configuration of PVs, VGs, and LVs.



Enough reading about LVM! Let's dive in and get hands-on experience by creating partitions or logical volumes ourselves.

🚧

This is also a hands-on tutorial and you may follow it. However, I highly recommend doing so in a virtual machine, as playing with disks partitions will likely result in data loss on your bare metal system.

### Installing LVM

Assuming you've already updated your system, let's proceed with installing LVM.

Actually, most Linux distributions come with lvm support pre-installed.

However, if, for some reason, they are not, you can easily install them by typing the **following command in the terminal on Ubuntu or Debian-based systems** :

```

    sudo apt update
    sudo apt install lvm2

```

### Creating Partitions

📋

While creating my virtual machine, I assigned it an extra 'disk' of 16 GB.

First things first – you're going to create partitions on your hard drive. This makes it easier for the next step, where you'll set up the physical volume.

You can either create these partitions on a plain, untouched storage space, or you can use existing partitions.

Our example disk is called `/dev/sdb`. It's a 16 GB hard drive without any partitions right now.

To check out the details of our `/dev/sdb` disk, including its current state, use this command.

```

    lsblk

```

![][4]

I am using the `parted` command which is a CLI based partitioning tool but you can also use the GUI based tools like [GParted][5] or GNOME Disks.

🚧

Creating partitions wipes all data on the selected disk. Double-check before proceeding to avoid unintended data loss.

I'll partition this 16 GB drive into two equal partitions and for that, I will use this command:

```

    sudo parted /dev/sdb

```

![][6]

Once you are inside `parted` wizard, create a partition table with:

```

    mklabel gpt

```

Set up the units to Gigabytes:

```

    unit GB

```

Now, create your first partition of 8 GB:

```

    mkpart primary 0 8GB

```

For the other partition:

```

    mkpart primary 8GB 16GB

```

Just to verify that your partitions has successfully created, check it using `print` command.

The output will look something like this:

![][7]

To exit out of `parted` just type `quit`.

### Creating Physical Volumes (PV)

It acts as the fundamental component for storage management like as a raw disk, or a disk partition, allowing administrators to pool and manage diverse storage resources within a logical volume group.

To create Physical Volumes, you'll be using the `pvcreate` command:

```

    sudo pvcreate /dev/sdb1

```

and for our second partition also:

```

    sudo pvcreate /dev/sdb2

```

![][8]

To list all the PVs, you can use this command:

```

    sudo pvs

```

![][9]

You can also remove the physical volume using the `pvremove` command:

```

    sudo pvremove /dev/sdb1

```

### Creating a Volume Group (VG)

VG is a collection of one or more physical volumes (disks or partitions) that are grouped together to create a pool of storage resources. This volume grouping allows administrators to manage and allocate logical volumes (LVs) more flexibly.

In this section, you'll be creating a VG with the name of `foss_vg` for both `/sdb1` and `sdb2`:

```

    sudo vgcreate foss_vg /dev/sdb1 /dev/sdb2

```

![][10]

To list the Volume groups, we need to use `vgs` command. Just like:

```

    sudo vgs

```

and the output would be like this:

![][11]

#### Extending a Volume Group

Suppose you have a new drive added with the name of `/dev/sdb3` and you want to add it to your existing Volume Group to extend the size of it. You can simply add it with the `vgextend` command.

```

    sudo vgextend foss_vg /dev/sdb3

```

### Creating Logical Volumes (LV)

These are the virtual partitions created within a Logical Volume Group (VG), forming a layer of abstraction over the underlying physical storage.

You will be creating a LV named as `foss_lv` with the size of 2084 MB:

```

    sudo lvcreate -L 2048 -n foss_lv_01 foss_vg

```

and another one, with the size of 4096 MB:

```

    sudo lvcreate -L 4096 -n foss_lv_02 foss_vg

```

![][12]

Viewing the Logical volumes that we just created using the `lvdisplay` command:

```

    sudo lvdisplay

```

and the output will be :

![][13]

### Creating a Filesystem on Logical Volumes

After creating a LV, the next step is often to initialize it with a file system to make it usable. The `mkfs` command is employed for this purpose.

Specifically, to create an ext4 file system on the newly formed logical volume, you would use the `mkfs.ext4` command.

```

    sudo mkfs.ext4 -m 0 /dev/foss_vg/foss_lv_01

```

![][14]

You can now mount this newly created filesystem to somewhere in your directory like:

```

    sudo mount /dev/foss_vg/foss_lv_01 /mnt

```

![][15]

#### Extend a Logical Volume

Unlike traditional partitions, LVs offer dynamic resizing capabilities, allowing administrators to easily adjust their size without the need to re-partition the entire disk.

This flexibility enables efficient storage management, facilitating tasks such as extending or shrinking volumes to accommodate changing storage requirements.

✋

This command only extends the size of logical volume but not the filesystem you have on it.

```

    sudo lvextend -L +1200 /dev/foss_vg/foss_lv_01

```

![][16]

To resize the filesystem and add back the new space we just created, type this command:

```

    sudo resize2fs /dev/foss_vg/foss_lv_01

```

💡

The ****resize2fs**** command is only used for extending ext2/ext3/ext4 file-systems. If you formatted the logical volume using a different file-system other than ext4 (as demonstrated in this tutorial), please refer to the ****apropos**** for your file-system.

![][17]

#### Remove Logical Volume

The `lvremove` command is utilized for the deletion of logical volumes. It is essential to ensure that the logical volume contains no important data before initiating the removal process.

Additionally, it is crucial to confirm that the **volume is not currently mounted**.

```

    sudo lvremove /dev/foss_vg/foss_lv_01

```

### Bonus: Automatically mount partition on boot using `fstab`:

It is simple, you just have to add one line at the bottom of the `fstab` file.

To edit the file, type:

```

    sudo nano /etc/fstab

```

Move to the bottom and then add this line:

```

    /dev/foss_vg/foss_lv_01    /mnt    ext4    defaults    0    2

```

The output would be something like this:

![][18]

Once done, [you can save and exit nano][19] using `CTRL+X` then pressing `y` .

You also need to reload `systemctl` for the changes to take effect:

```

    sudo systemctl daemon-reload

```

### Conclusion:

The Logical Volume Manager is a powerful tool that provides many benefits for managing storage on your computer. It allows for efficient use of storage space, flexibility in file system support, and supports various backup and recovery options.

LVM might seem like a puzzle at first, but once you understand how its pieces fit together, it becomes surprisingly fun to use. So, take your time, explore, and feel free to reach out if you have questions. Happy LVM-ing!

--------------------------------------------------------------------------------

via: https://itsfoss.com/lvm-guide/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/logical_volume_manager_administration/lvm_overview
[4]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-lsblk-command-16gb-block-device.png
[5]: https://itsfoss.com/gparted/
[6]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-using-parted-command.png
[7]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-using-parted-to-create-partitions-2.png
[8]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-using-pvcreate-to-create-physical-volumes.png
[9]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-pvs-command-to-display-all-physical-volumes.png
[10]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-uisng-vgcreate-command-to-create-virtual-groups.png
[11]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-uisng-vgs-command-to-show-the-existing-volume-group.png
[12]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-using-lvcreate-command-to-create-logical-volumes.png
[13]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-using-lvdisplay-command-to-show-all-the-logical-volumes.png
[14]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-creating-ext4-filesystem-using-mkfs-command.png
[15]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-successfully-mounting-the-logical-volumes-using-mount-command.png
[16]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-extending-the-logical-volumes-using-lvextend-command.png
[17]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-reszing-filesystem-match-the-extended-logical-volume.png
[18]: https://itsfoss.com/content/images/2024/02/lvm-ubuntu-guide-editing-the-fstab-to-automount-the-logical-volume.png
[19]: https://itsfoss.com/nano-save-exit/
