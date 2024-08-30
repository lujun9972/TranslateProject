[#]: subject: "How to Reset Raspberry Pi Password"
[#]: via: "https://itsfoss.com/reset-raspberry-pi-password/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Reset Raspberry Pi Password
======

[![Warp Terminal][1]][2]

Don't remember the password you set while installing Raspberry Pi OS? It happens.

Raspberry Pi OS is set to auto login and doesn't even need password while using sudo. Since you are hardly entering the password anywhere, it is only human that you'll forget it.

Resetting the Raspberry Pi OS password is not complicated. In this tutorial, I'll cover both cases where you can auto login and where you cannot login to your system.

Let's start with the first method.

### Method 1: If you can auto login

Here's the deal: By default, Raspberry Pi OS is set to automatically log in to the system without requiring a password.

If that's the case, you are in luck. Raspberry Pi OS is configured to not ask for a password with sudo. Since you can log in automatically, and no password is required for sudo, resetting the password will be super easy.

You just have to type this in the terminal:

```

    sudo passwd username

```

Here's an example where I changed the password for the main user named `ushika`:

![][3]

Alternatively, you can use the GUI tool provided by

![][4]

In here, under the System tab, you'll see the option to change the password.

![][5]

### Method 2: If you cannot auto login

This is slightly complicated and longer procedure. If you cannot log in to your Raspberry Pi OS, you can modify a few parameters to boot into the root shell and reset the password from there.

You need a separate computer, preferably running Linux here.

#### Step 1: Modify cmdline.txt file

Take out the micro SD card from the Pi and put it in your computer. On Linux, it should automatically mount. All you have to do is to edit the /boot/cmdline.txt file.

You can do it graphically or use the terminal; the choice is yours.

![][6]

There should be one or more lines and you have to add ` init=/bin/sh` at the end of this last line, **NOT on a new line**. There must be a **space before init=/bin/sh**.

Now, this last line should look like this.

```

    console=serial0,115200 console=tty1 root=PARTUUID=585e914d-02 rootfstype=ext4 fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles cfg80211.ieee80211_regdom=IN init=/bin/sh

```

**Save the file** and unmount the SD card.

#### Step 2: Boot Raspberry Pi into the root shell

Plug the modified SD card into the Pi again and power it on.

Now when you boot into the Pi, it will drop you into the root shell. In here, you can run commands as root and make changes to your system.

![][7]

But for that, you have to remount the system with read-write access ( **you must type the command exactly** ):

```

    mount -o remount, rw /

```

Now, change the password for the user:

```

    passwd username

```

If you do not remember the username, you can run `ls /home/` and it should show what users are there on your system.

Enter the new password twice and then use this command to make sure that the changes are saved to the disk:

```

    sync

```

![][8]

Everything seems to be set now. But you still have to revert the changes you made in cmdline.txt file otherwise you'll keep on booting into the root shell.

Use the command below to reboot into Raspberry Pi OS but temporarily bypassing the root shell:

```

    exec /sbin/init

```

Once you are in your regular Raspberry Pi system, modify the cmdline.txt file again using this command:

```

    sudo nano /boot/firmware/cmdline.txt

```

![Revert the cmdline.txt changes you made earlier][9]

Remove the `init=/bin/sh` and press Ctrl+X to save the changes.

Next time you boot, you'll normally boot into your system.

### Conclusion

There could be a few other methods for resetting the Raspberry Pi password. I came across them in various forum discussions. However, I find these two the most reliable options.

I hope this tutorial helps you reset the password on your Raspberry Pi OS. Let me know if you have questions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/reset-raspberry-pi-password/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/08/change-raspberry-pi-passwrd-terminal.png
[4]: https://itsfoss.com/content/images/2024/08/raspberry-pi-config.png
[5]: https://itsfoss.com/content/images/2024/08/change-raspberry-pi-password.png
[6]: https://itsfoss.com/content/images/2024/08/edit-cmdline-txt-file-raspberry-pi.png
[7]: https://itsfoss.com/content/images/2024/08/raspberry-pi-root-shell.jpg
[8]: https://itsfoss.com/content/images/2024/08/resetting-raspberry-pi-password.jpg
[9]: https://itsfoss.com/content/images/2024/08/reset-cmdline-txt-changes.png
