[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Mount and Unmount File System/Partition in Linux)
[#]: via: (https://www.2daygeek.com/mount-unmount-file-system-partition-in-linux/)
[#]: author: (Magesh Maruthamuthu https://www.2daygeek.com/author/magesh/)

How to Mount and Unmount File System/Partition in Linux
======

Generally, a file system must be mounted on a Linux system to access the contents.

When adding a new hard disk to your system, you may need to use the fdisk command or the parted command to create partitions.

Once you have created partitions, you must create a file system using the mkfs command on disk space.

You will be not able to use any disk on Linux system without a filesystem because the file system contains information about files and directories.

Once you have done the above steps, you can mount the partition (a directory) into a mount point using the mount command.

The mount and umount programs maintain a list of currently mounted filesystems in the “/etc/mtab” file.

### What’s mount Command?

The mount command is used to attach (mount) filesystems and removable devices such as CDRM, DVD, USB flash drives to a specific mount point in the directory tree.

All mentioned filesystems in the “/etc/fstab” file will be mounted automatically when a system boot.

**The general syntax for mounting a file system**

```
mount -[options] [device_name] [mount_directory]
mount [-t file_system_type] [-o mount_options] [device_name] [mount_point]
```

Below are some options you can use when mounting the filesystem.

  * **defaults :** You may have seen that most of the mounted file systems have default options in the “/etc/fstab” file. This default option uses the following options such as rw, suid, dev, exec, auto, nouser, async, and relaime in the mounted file system.
  * **ro :** Mount the filesystem read-only.
  * **rw :** Mount the filesystem read-write.
  * **async :** All I/O to the filesystem should be done asynchronously (It’s used default).
  * **noauto :** File systems set with the option noauto in the file /etc/fstab are not mounted automatically when the system boots.
  * **noexec :** Ban execution of any binaries on the loaded file system.
  * **nosuid :** To ignore set-user-identifier (SUID) or set-group-identifier (SGID) bits in the file system.
  * **nodev :** Do not interpret character or block special devices on the file system.
  * **_netdev :** This allows the system to mount the file system only after the network is enabled.
  * **remount :** This remount an already-mounted filesystem. This is commonly used to incorporate the changes that you made on a filesystem.



### What’s umount Command?

The umount command is used to manually unmount (detaches) filesystems on Linux and other Unix-like operating systems.

All mounted filesystems are unmounted automatically when a system shuts down.

Unmounting the file system is not always successful. The most common problem is that the file system is busy, which is currently used by some processes.

If so, you should kill the process to unmount the filesystem.

### How to List Mounted File Systems

When you run the mount command without any argument that display mounted file systems, including the virtual file systems such as cgroup, tmpfs, devpts, debugfs, etc.

It displays a device name, filesystem type, mount point name and mount options with a single line.

```
# mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime,seclabel)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,seclabel,size=1928468k,nr_inodes=482117,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,noexec,seclabel)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,seclabel,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,seclabel,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,seclabel,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,cpuacct,cpu)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,net_prio,net_cls)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,seclabel,freezer)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/mapper/vg_root-lv_root on / type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
selinuxfs on /sys/fs/selinux type selinuxfs (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12557)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,seclabel)
mqueue on /dev/mqueue type mqueue (rw,relatime,seclabel)
/dev/sda1 on /boot type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_var on /var type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_apps on /apps type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_repo on /var/www/html type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_home on /home type xfs (rw,nosuid,nodev,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_tmp on /tmp type xfs (rw,nosuid,nodev,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_tmp on /var/tmp type xfs (rw,nosuid,nodev,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_var_log on /var/log type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_var_log_audit on /var/log/audit type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_opt on /opt type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/0 type tmpfs (rw,nosuid,nodev,relatime,seclabel,size=388060k,mode=700)
```

Use the `-t` option with the mount command to display only the specified file system type.

For instance, to print only the **“xfs”** partition, use the following one.

```
# mount -t xfs
/dev/mapper/vg_root-lv_root on / type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/sda1 on /boot type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_var on /var type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_apps on /apps type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_repo on /var/www/html type xfs (rw,relatime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_home on /home type xfs (rw,nosuid,nodev,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_tmp on /tmp type xfs (rw,nosuid,nodev,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_tmp on /var/tmp type xfs (rw,nosuid,nodev,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_var_log on /var/log type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_var_log_audit on /var/log/audit type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
/dev/mapper/vg_root-lv_opt on /opt type xfs (rw,noatime,nodiratime,seclabel,attr2,inode64,noquota)
```

### How to Mount a File System

The mount command is already available on most Linux operating systems. Once you have determined your mount point, go ahead and mount the file system. To to so use the following format.

```
mount -[options] [device_name] [mount_directory]
```

For instance, to mount the **“/dev/sdb1”** file system to the **“/backup”** directory, use the following command.

```
# mount /dev/sdb1 /backup
```

**Make a note**, you do not need to specify the file system type when you mount a device with a common file system such as ext4 or xfs because the mount command automatically detects the file system type.

**For example**, when you run the mount command on RHEL 7/8 based systems, it mounts the file system with xfs. At the same time it mounts the file system with ext4 on Ubuntu-based systems.

When you want to mount a device with a specific file system, you can specify the file system type with the **“-t”** option with the mount command.

Also, if you want to mount the file system with multiple mount options, use the **“-o”** option with the mount command.

### How to Remount a File System

This is commonly used to incorporate the changes that you made on a filesystem without interrupting the current run-time processes.

For instance, you can use the following command to enable **“acl”** option on the **“/app”** file system.

Refer the following article to **[enable acl on Linux][1]**.

```
# mount -o remount,acl /app
```

### How to Mount a File Systems on System Boot

If you want to mount any file system on the system boot, you must add a specific file system information to the “/etc/fstab” file.

See the following article to **[understand the /etc/fstab file][2]**.

The Linux system automatically mounts the file systems included in the “/etc/fstab” file at boot time.

### How to Mount USB Drive

Most of the modern Linux distribution automatically mounts the USB drive, and you can get the details using the df command as shown below. But sometimes if your system doesn’t recognize the USB drive, you may need to manually mount them by following the procedure below.

```
df -h
Filesystem Size Used Avail Use% Mounted on
dev 7.8G 0 7.8G 0% /dev
run 7.8G 1.7M 7.8G 1% /run
/dev/nvme0n1p1 217G 83G 124G 41% /
tmpfs 7.8G 674M 7.1G 9% /dev/shm
tmpfs 7.8G 0 7.8G 0% /sys/fs/cgroup
tmpfs 7.8G 38M 7.8G 1% /tmp
tmpfs 1.6G 12K 1.6G 1% /run/user/120
tmpfs 1.6G 32K 1.6G 1% /run/user/1000
/dev/sda2 932G 546G 387G 59% /run/media/daygeek/DATA
/dev/sdb 7.5G 1.5G 6.1G 20% /mnt/usb
```

To do so, you need to **[identify the filesystem type][3]**. This can be found with help of the **[fdisk command][4]**.

```
# fdisk -l
```

Create a directory to mount the USB drive and I recommend you to create the following directory.

```
# mkdir /media/usb
```

Assuming that the USB drive uses the /dev/sdb2 device, you can use the bleow command to mount it.

```
# mount /dev/sdb2 /media/usb
```

### How to Mount a CD/DVD-ROM

Once you insert the DVD, run the blkid command to find a correct CD/DVD block device.

```
# blkid
```

Create a directory to mount the CD/DVD drive and I recommend you to create the following directory.

```
# mkdir /media/dvdrom
```

Finally mount the CD/DVD-ROM as shown below.

```
# mount /dev/sr0 /media/dvdrom
OR
# mount /dev/cdrom /media/dvdrom
mount: /media/dvdrom: WARNING: device write-protected, mounted read-only.
```

### How to Mount ISO Image in Linux

You can mount an ISO file using the loop device. A loop device is a pseudo-device that makes a file accessible as a block device.

Create a mount point.

```
# mkdir /media/iso
```

Finally mount the ISO file using the following command. Make sure to replace **“/path/to/image.iso”** with the path to your ISO file.

```
# mount /path/to/image.iso /media/iso -o loop
```

### How to Mount NFS Share

Make sure you already have installed NFS client package on your computer. I assume you have already installed NFS and started the necessary services.

Run the following command to check the available share for you.

```
# showmount -e 192.168.1.101

Export list for 192.168.0.100:
/test_nfsshare 192.168.0.101
```

Create a mount point to mount nfs share.

```
# mkdir /mnt/nfs
```

You can run the following command to mount nfs share temporarly on system.

```
# mount -t nfs 192.168.1.101:/test_nfsshare /mnt/nfs
```

Generally, you will not use the NFS share as a temporary mount, so add the following line to the “/etc/fstab” file to load the nfs share at boot time (for permanent mount).

```
# vi /etc/fstab

192.168.1.101:/test_nfsshare /mnt/nfs nfs defaults 0 0
```

  * **Remote_Server_IP –** 192.168.1.101
  * **NFS Share Name –** /test_nfsshare
  * **Local Mount Point –** /mnt/nfs



### How to Unmount a File System

You don’t need to use any arguments to unmount (remove) the file system. To remove the file system, use the mount point name or device name following the umount command.

```
# umount /backup
umount: /backup: target is busy.
(In some cases useful info about processes that use
the device is found by lsof(8) or fuser(1))
```

If the filesystem being used by any process, you will be not able to unmount (detach) filesystem. This is most common cause when you unmount the file system. You can use the fuser command or the lsof command to find out which processes being accessing the file system.

```
# fuser -cu /backup
or
# lsof | grep /backup
```

If any process uses the file system, you can kill all processes in the mount point using the fuser command.

```
# fuser -ck /backup
```

Finally you can unmount the file system.

```
# umount /backup
```

### Force Unmount a File System

I would not recommend using this option as it may corrupt data in the file system. If you have no other options, use this.

### How to Unmount a stale NFS mount

You can unmount a stale NFS mount that fails to unmount with ‘device is busy’ after network disconnectivity using the below steps.

Run the below commands one by one, i can damn sure one of the commands can unmount the stale nfs share.

```
# mount -t nfs -o remount /nfs-share
# umount /nfs-share
# umount -f /nfs-share
# umount -l /nfs-share
# umount -lf /nfs-share
```

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/mount-unmount-file-system-partition-in-linux/

作者：[Magesh Maruthamuthu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/magesh/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/how-to-configure-access-control-lists-acls-setfacl-getfacl-linux/
[2]: https://www.2daygeek.com/understanding-linux-etc-fstab-file/
[3]: https://www.2daygeek.com/find-identify-check-determine-linux-file-system-type/
[4]: https://www.2daygeek.com/linux-fdisk-command-to-manage-disk-partitions/
