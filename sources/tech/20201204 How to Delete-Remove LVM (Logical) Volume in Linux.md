[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Delete/Remove LVM (Logical) Volume in Linux)
[#]: via: (https://www.2daygeek.com/how-to-delete-remove-lvm-logical-volume-in-linux/)
[#]: author: (Magesh Maruthamuthu https://www.2daygeek.com/author/magesh/)

How to Delete/Remove LVM (Logical) Volume in Linux
======

If the LVM volume (logical volume) is no longer required to use by LVM on the system.

You can remove/delete it with the lvremove command using the following steps.

But make sure the LVM volume does not contain any data.

If yes, please make sure to back up that data before proceeding with LVM removal.

To demonstrate this, we will remove **“lv001”** from the volume group **“vg01”**. The LV is mounted on the mount point **/lvmtest**.

  * **Part-1: [How to Create/Configure LVM (Logical Volume Management) in Linux][1]**
  * **Part-2: [How to Extend/Increase LVM’s (Logical Volume Resize) in Linux][2]**
  * **Part-3: [How to Reduce/Shrink LVM’s (Logical Volume Resize) in Linux][3]**
  * **Part-4: [How to Remove Physical Volume from a Volume Group in LVM][4]**



Use the **[df command][5]** to check if the LVM volume is containing any data. If yes, then backup the data.

```
# df -h /lvmtest

Filesystem Size Used Avail Use% Mounted on
/dev/mapper/vg01-lv001 15360M 34M 15326M 4% /lvmtest
```

Alternatively, you can verify this using the lvs or lvdisplay command as follows.

```
# lvs
or
# lvdisplay /dev/mapper/vg01-lv001
```

Firs delete the entry of the mount point from the **[/etc/fstab][6]** file.

```
# vi /etc/fstab
…
/dev/mapper/vg01-lv001 /lvmtest ext4 defaults 0 0
…
```

Unmount the mount point using the **[umount command][7]**.

```
# umount /lvmtest
```

Disable the **“lv001”** logical volume.

```
# lvchange -an /dev/vg01/lv001
or
# lvchange -an /dev/mapper/vg01-lv001
```

Finally delete the **“lv001”** logical volume.

```
# lvremove /dev/vg01/lv001
or
# lvremove /dev/mapper/vg01-lv001

Do you really want to remove active logical volume "lv001"? [y/n]: y
  Logical volume "lv001" successfully removed
```

If there is no logical volumes associated with volume group and no more required, then remove that as well.

Disable the **“vg01”** volume group.

```
# vgchange -an vg01
```

Delete the **“vg01”** volume group.

```
# vgremove vg01

Volume group "officevg" successfully removed
```

Delete physical volumes used for volume group **“vg01”**.

```
# pvremove /dev/sdb /dev/sdc

Labels on physical volume "/dev/sdb" successfully wiped.
Labels on physical volume "/dev/sdc" successfully wiped.
```

--------------------------------------------------------------------------------

via: https://www.2daygeek.com/how-to-delete-remove-lvm-logical-volume-in-linux/

作者：[Magesh Maruthamuthu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/magesh/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/create-lvm-storage-logical-volume-manager-in-linux/
[2]: https://www.2daygeek.com/extend-increase-resize-lvm-logical-volume-in-linux/
[3]: https://www.2daygeek.com/reduce-shrink-decrease-resize-lvm-logical-volume-in-linux/
[4]: https://www.2daygeek.com/linux-remove-delete-physical-volume-pv-from-volume-group-vg-in-lvm/
[5]: https://www.2daygeek.com/linux-check-disk-space-usage-df-command/
[6]: https://www.2daygeek.com/understanding-linux-etc-fstab-file/
[7]: https://www.2daygeek.com/mount-unmount-file-system-partition-in-linux/
