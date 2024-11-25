[#]: subject: "Automounting External Drives in Linux"
[#]: via: "https://itsfoss.com/automount-drives-linux/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Automounting External Drives in Linux
======

[![Warp Terminal][1]][2]

Imagine this situation. You have attached an external USB or SSD to your system and using it as an additional storage media. This is a common use case specially if you have set up a [_media server on Raspberry Pi_][3] or any Linux system.

On Linux, you normally have to click on the mount option in the file explorer or use the mount command to start using the external drive.

This is an incontinence and it could also be problematic in situation where you require the disk to be mounted like internal disks when the system starts. Imagine the media server not showing any media because the media was stored on external disk and it was not mounted.

The good thing is that you can solve this problem by ensuring that the external disk automounts.

In this guide, we’ll explore two popular methods for automatically mounting drives on Linux:

  * Configuring the `fstab` file for startup mounting
  * Using `udev` and `autofs` for more dynamic setups



Let's see them one by one.

### Method 1: Automount with `fstab` at Startup

If you want the external drive to automatically mount whenever your system starts, you can configure it using `fstab` (File Systems Table).

This method is reliable for drives that remain connected during system boot and I mostly use this method for my homelab.

![I have a 1.5TB HDD connected to my server and I need to automount the /sdb2][4]

##### Steps to Automount via `fstab`:

  1. First, connect your USB drive and run the following command to identify the device name and UUID:



```

    sudo blkid

```

Look for the line that corresponds to your external drive. For instance:

```

    /dev/sdb2: UUID="12ab345cd-1234-4166-8539-ff4ff3ff2ff1" TYPE="ntfs"

```

![][5]

  2. Edit the `/etc/fstab` file with your preferred text editor (you’ll need super-user rights):



```

    sudo nano /etc/fstab

```

Add the following line at the end of the file:

```

    UUID=12ab345cd-1234-4166-8539-ff4ff3ff2ff1 /media/hdd auto defaults,nofail,x-systemd.automount 0 2

```

Replace the UUID with the one from your drive, and adjust the mount point (`/media/hdd`) as per your requirement.

![][6]

  3. Reload systemd to apply the changes:



```

    sudo systemctl daemon-reload

```

Then reboot your system, and the drive should automatically mount at the specified location.

![HDD is automounted in the right directory][7]

💡

The same method can also be utilized when you are using a dual boot system and you want to automount the Windows partition(s).

### Method 2: Automount Using Udev Rules and `autofs`

If you want the external drive to mount only when it’s plugged in, `udev` rules and `autofs` provide a dynamic approach.

This method is more suitable if you frequently swap USB drives or prefer not to have them mounted at startup.

##### Steps to Automount Using `udev` and `autofs`:

  1. Create a new rule file in the `/etc/udev/rules.d/` directory:



```

    sudo nano /etc/udev/rules.d/usb_auto_mount.rules

```

Add the following content:

```

    ACTION=="add", KERNEL=="sd*", ENV{DEVTYPE}=="partition", ENV{ID_BUS}=="usb", \
        SYMLINK+="usbdisks/%k", MODE:="0660", \
        RUN+="/bin/ln -sf /media/hdd/%k /media/usb-sticks/%k"
    ACTION=="remove", KERNEL=="sd*", ENV{DEVTYPE}=="partition", ENV{ID_BUS}=="usb", \
        RUN+="/bin/rm /media/usb-sticks/%k"

```

**Breakdown:**

  * **`ACTION=="add"`** : This rule triggers when a new device (like a USB) is added.
  * **`KERNEL=="sd*"`** : Matches devices whose kernel name starts with "sd" (typical for drives).
  * **`ENV{DEVTYPE}=="partition"`** : Ensures that only partitioned devices are targeted.
  * **`ENV{ID_BUS}=="usb"`** : Limits this rule to USB devices.
  * `SYMLINK+="usbdisks/%k"`: Creates a symbolic link in `/dev/usbdisks/` for the device. `%k` is a placeholder for the device name assigned by the kernel.
  * **`MODE:="0660"`** : Sets read and write permissions for the user and group (but not others).
  * `RUN+="/bin/ln -sf /media/hdd/%k /media/usb-sticks/%k"`: Creates a symbolic link in `/media/usb-sticks/` pointing to `/media/hdd/%k`, where the drive will be mounted.
  * **`ACTION=="remove"`** : This rule is triggered when the USB drive is unplugged.
  * **`RUN+="/bin/rm /media/usb-sticks/%k"`** : Removes the symbolic link when the drive is disconnected.



![][8]

  2. After saving the file, reload the udev rules to apply the changes:



```

    sudo udevadm control --reload-rules

```

  3. Edit the `auto.master` file to instruct `autofs` to mount the USB drive:



```

    sudo nano /etc/auto.master

```

Add the following line:

```

    /media/hdd /etc/auto_mount.usb --timeout=60

```

![][9]

Then, create the corresponding automount map file:

```

    sudo nano /etc/auto_mount.usb

```

Add this content:

```

    #!/bin/bash
    fstype=$(/sbin/blkid -o value -s TYPE /dev/usbdisks/${1})
    if [ "${fstype}" = "vfat" ] ; then
      echo "-fstype=ntfs,sync,uid=0,gid=plugdev,umask=007 :/dev/usbdisks/${key}"
      exit 0
    fi
    exit 1

```

**Breakdown:**

  * `fstype=$(/sbin/blkid -o value -s TYPE /dev/usbdisks/${1})`: This command fetches the file system type (e.g., FAT32, NTFS) of the USB drive using the `blkid` command.
  * `if [ "${fstype}" = "ntfs" ]`: Checks if the file system is `ntfs` a common file system type used by Windows.
  * **`echo "-fstype=ntfs,sync,uid=0,gid=plugdev,umask=007 :/dev/usbdisks/${key}"`** : Mounts the drive with specific options:`fstype=vfat`: Mount it as a `vfat` file system. **`sync`** : Ensures that data is written to the drive immediately rather than being cached.`uid=0,gid=plugdev`: Sets the owner to `root` (uid 0) and the group to `plugdev` (a common group for USB devices). **`umask=007`** : Sets the permissions for files and directories so that only the owner and group can access them.



![][10]

Save and exit the file.

The drive will now automatically mount in `/media/hdd/` when connected and unmount after 60 seconds of inactivity.

#### Tips for Automounting External Drives

  * **Use UUIDs:** When using `fstab`, always prefer UUIDs over `/dev/sdX` identifiers as they remain consistent across reboots.
  * **Check Filesystem Support:** Ensure that your system supports the filesystem of your USB drive (e.g., install `ntfs-3g` for NTFS drives).
  * **Test Changes:** Always test your configuration changes after setting them up to ensure the drive mounts properly. Using `journalctl` can help diagnose any issues.



### Conclusion

Automounting the drives can significantly streamline your workflow. This I realized with my personal experience.

A few days ago, while setting up an external drive as part of my DIY NAS (Network Attached Storage) on a Raspberry Pi, I encountered a frustrating issue.

I was backing up crucial files and using the drive for remote access. Everything was going smoothly until a reboot occurred.

To my dismay, the system booted back up, but the external drive didn't automatically mount. The backup process was disrupted, and I had to manually intervene every time the system restarted.

It was frustrating because the whole point was to make the system run seamlessly without constant supervision. I experimented with automounting the drives and decided to share my experience with you.

The approach you choose between fstab and udev depends on your specific needs whether you prefer the drive to be ready at boot or only when plugged in.

With these steps, you can ensure that your external storage is always accessible without manual intervention.

💬 Do let me know if you have questions or face issues while automounting the external disks in Linux.

--------------------------------------------------------------------------------

via: https://itsfoss.com/automount-drives-linux/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/jellyfin-raspberry-pi/
[4]: https://itsfoss.com/content/images/2024/10/lsblk-command-to-list-drives.png
[5]: https://itsfoss.com/content/images/2024/10/blkid-to-know-uuid.png
[6]: https://itsfoss.com/content/images/2024/10/editing-the-fstab-1.png
[7]: https://itsfoss.com/content/images/2024/10/automount-at-boot.png
[8]: https://itsfoss.com/content/images/2024/10/udev-rule-file-1.png
[9]: https://itsfoss.com/content/images/2024/10/mount-timeout-settings-1.png
[10]: https://itsfoss.com/content/images/2024/10/automount-final-script-for-udev-1.png
