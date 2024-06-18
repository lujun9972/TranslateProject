[#]: subject: "Reset Forgotten Root Password in Ubuntu"
[#]: via: "https://itsfoss.com/ubuntu-reset-lost-root-password/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Reset Forgotten Root Password in Ubuntu
======

[![Warp Terminal][1]][2]

It's only human to forget passwords, especially if you are not using it frequently.

It happens with Ubuntu, Linux, or any other operating system you use. If you don't use it frequently, you are likely to forget the password.

I have written about [resetting forgotten Ubuntu passwords in the past][3]. It works flawlessly unless you have a root password set.

In this tutorial, I'll show you how to set a new root password if you forget the original one.

### Resetting the forgotten root password

✋

This scenario only works when you have root password set up (do not confuse it with the default admin account with sudo access) and you have physical access to the system.

First thing first, I am talking about the case where you have explicitly set a root password.

Let me recall [things around the root user in Ubuntu][4].

[When you install Ubuntu][5], you create a user account. This user account has admin access to install and remove software and do all the other administrative tasks with elevated access thanks to the sudo mechanism.

By default, the root account doesn't have a password. You use sudo with your main/admin account to do things as root. However, some people explicitly set a root password.

And this creates a problem when you try to [reset forgotten password using the recovery shell as described in this tutorial][3]. You'll see this error:

> Give root password for maintenance

Let me show you how to bypass this error and reset the root password.

#### Step 1: Go to the recovery mode from Grub screen

When you power on the system, it shows up the grub screen that gives you different options to enter Ubuntu, recovery mode or [access UEFI settings][6].

In here, you use the arrow key to select the **Advanced options for Ubuntu** :

![][7]

💡

If you don't see the grub screen, press and hold the Shift key as your system boots.

On the next screen, you should see the available kernel options with their respective recovery mode. You can choose the first entry that has **recovery mode** in it:

![][8]

#### Step 2: Use dpkg package repair option

The recovery mode gives you various choices. What you need to do here is to go to **dpkg Repair broken packages** option.

![][9]

Press tab key to go to OK and then press enter to confirm your choice.

Press Yes when you see this next screen:

![][10]

⚠️ Important step now

It will update the package cache and ask you if you want to upgrade. **You have to enter d here** for details.

![Enter d for details][11]

While it gives you package details, you get access to write something on the screen here. You have to write:

```

    !/bin/bash

```

![Access root shell in Ubuntu][12]

Press enter and you'll be in the root shell. That's a good thing 😄

#### Step 3: Reset root password from the root shell

Now, you are using the shell as root user. You don't know the password, so the next step is to [use the passwd command][13] and reset its password:

```

    passwd

```

You'll be asked to enter the password and then repeat the same password.

📋

Nothing is displayed on the screen when you type the password. That's normal. Just type the password and press enter.

![][14]

If you see the ' **you** ', you have fulfilled your mission.

Now to exit this screen, enter the reboot command:

```

    reboot

```

### Conclusion

And that's it. You have successfully used local privilege escalation to reset the forgotten root password in [Ubuntu][15]. Enjoy 😄

Sorry for the poor screenshots. I took it from an actual bare metal system while testing this scenario. As long as you can follow the steps, it should be fine, right?

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-reset-lost-root-password/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/how-to-hack-ubuntu-password/
[4]: https://itsfoss.com/root-user-ubuntu/
[5]: https://itsfoss.com/install-ubuntu/
[6]: https://itsfoss.com/access-uefi-from-linux/
[7]: https://itsfoss.com/content/images/2024/06/access-advanced-options-for-ubuntu-from-grub-screen.png
[8]: https://itsfoss.com/content/images/2024/06/accessing-recovery-mode-ubuntu.webp
[9]: https://itsfoss.com/content/images/2024/06/ubuntu-recovery-dpkg-broken-package.webp
[10]: https://itsfoss.com/content/images/2024/06/using-dpkg-package-repair-option.webp
[11]: https://itsfoss.com/content/images/2024/06/get-dpkg-package-details.webp
[12]: https://itsfoss.com/content/images/2024/06/access-root-shell-ubuntu.jpg
[13]: https://linuxhandbook.com/passwd-command/
[14]: https://itsfoss.com/content/images/2024/06/reset-ubuntu-root-password-in-recovery.webp
[15]: https://ubuntu.com/
