[#]: subject: "Deleting Linux Entry from Boot Menu from Windows After Removing Linux"
[#]: via: "https://itsfoss.com/delete-linux-entry-boot-dual/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Deleting Linux Entry from Boot Menu from Windows After Removing Linux
======

[![Warp Terminal][1]][2]

Recently, I bought an Asus Zenbook and dual booted it with Ubuntu. But Ubuntu 24.04 didn't perform well on the new hardware and thus [I removed Ubuntu from dual boot][3].

This is typically done by moving the Windows boot manager up the boot order and deleting the Linux partition from within Windows.

The annoyance is that Linux will still show up in the UEFI boot settings.

![][4]

Although it doesn't hurt to leave it there, it triggers some sort of OCD in me to get a pristine system without unnecessary stuff.

And hence, I went out to 'fix this non-issue' and I am going to share how you can do the same if you like.

The process is composed of these two steps:

  * Mount the [EFI system partition][5] (ESP) in Windows (has to be command line)
  * Delete the Ubuntu/Linux entry from the EFI folder using either command line or GUI



📋

Again, the Linux entry in the UEFI boot menu is not a blocking issue and you can leave it as it is to use only Windows on the system.

### Step 1: "Mount" the EFI partition in Windows

Press the Windows start button and look for CMD. Right click on it and select "Run as administrator".

![][6]

Once the command prompt is open, start the disk partition utility by entering:

```

    diskpart

```

Type "list disk" to list all the disks present on your system and get the name of the disk where the EFI partition is located.

```

    list disk

```

If you have only one disk, it should show only one entry.

![][7]

Enter the disk to see all the partitions on this disk:

```

    select disk 0

```

You should see 'Disk 0 is now the selected disk' in the ouput.

Now, list all the partitions on this disk with:

```

    list partition

```

Usually, it is the system partition that is EFI partiton and as you can see in the screenshot below, it is the partition number 1.

![][8]

🚧

Since my ESP (EFI System Partition) has assigned number 1, I'll select this partition. Yours could be different, so pay attention.

```

    select partition 1

```

Now, assign it a drive letter. Since C, D, E etc are usually taken, let's go to the end of the alphabet and use the letter x here.

```

    assign letter x

```

![][9]

With the EFI partition getting a driver letter, you can now see it in the file explorer like C or D drives.

![][10]

Basically, all this hassle for mounting the ESP partition. Anyway, exit the disk partition tool:

```

    exit

```

### Step 2: Delete Linux folder from EFI

Till here, we were not doing anything risky. But now, we have to delete the Ubuntu Linux folder from the EFI partition.

This can be done via graphically as well as via command line. You used the command line above but for 'deleting' something, I would recommend using the graphical method.

#### Method 1: Use GUI

Open the task manager in Windows (Ctrl+Alt+Del) and here, click the 'Run new task':

![][11]

This will give you the option to create new task. What you have to do here is to click on the "browse" button:

![][12]

You can now browse the partitions and the files inside them. Using this, you can add or delete files and folders.

Browse to drive X and the EFI folder. You should see ubuntu (or whichever distro you used) listed here. Select it first and then right click to see the option to delete it.

![][13]

I could not take a screenshot of it as Window's built-in tool didn't allow taking screenshots of the right-click context menu. Once you hit the delete option, a conformation dialogue box will pop up.

![][14]

Select yes and close the browser and then close task manager as well.

Congratulations! Now if you [access the UEFI settings from Windows][15], you won't see the Linux entry anymore.

Command line warrior? Let's see the other method for you.

#### Method 2: Use command line

📋

You need to perform all this in command prompt running as administrator.

Use this command to enter the drive you had mounted earlier. **Mind the colon after the drive letter**.

```

    x:

```

See the content of the directory with:

```

    dir

```

It should show a folder named EFI. Enter this directory:

```

    cd EFI

```

And now look at the content of this folder:

```

    dir

```

You should see some folder belonging to Linux. It could be named Ubuntu, Fedora etc.

![][16]

The next step is to use the rd command (remove directory) with the Linux folder's name to delete it:

```

    rd ubuntu /s

```

Once done, exit the command prompt by typing exit.

### Conclusion

The ESP partition mounted as drive X won't be there anymore when you restart the system. And neither will be the Linux boot entry.

In a [YouTube video, I discussed uninstalling Ubuntu from the dual boot system][17], I mentioned the fact that a leftover Ubuntu entry in the boot doesn't hurt. Still, a few comments indicated that they would like everything cleaned up. Hence, this tutorial.

💬 Is it worth the hassle to clean up the Linux boot entry after removing it from dual boot? Share it in the comments, please.

--------------------------------------------------------------------------------

via: https://itsfoss.com/delete-linux-entry-boot-dual/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/uninstall-ubuntu-linux-windows-dual-boot/
[4]: https://itsfoss.com/content/images/2025/02/boot-menu-ubuntu-windows.webp
[5]: https://en.wikipedia.org/wiki/EFI_system_partition
[6]: https://itsfoss.com/content/images/2025/02/image.png
[7]: https://itsfoss.com/content/images/2025/02/image-1.png
[8]: https://itsfoss.com/content/images/2025/02/image-2.png
[9]: https://itsfoss.com/content/images/2025/02/image-3.png
[10]: https://itsfoss.com/content/images/2025/02/image-4.png
[11]: https://itsfoss.com/content/images/2025/02/image-5-1.png
[12]: https://itsfoss.com/content/images/2025/02/image-6-1.png
[13]: https://itsfoss.com/content/images/2025/02/image-7.png
[14]: https://itsfoss.com/content/images/2025/02/image-9.png
[15]: https://itsfoss.com/access-uefi-settings-windows-10/
[16]: https://itsfoss.com/content/images/2025/02/image-8.png
[17]: https://www.youtube.com/watch?v=Kskjujf2TYc
