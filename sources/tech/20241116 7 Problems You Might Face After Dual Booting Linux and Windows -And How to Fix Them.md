[#]: subject: "7 Problems You Might Face After Dual Booting Linux and Windows [And How to Fix Them]"
[#]: via: "https://itsfoss.com/dual-boot-issues/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

7 Problems You Might Face After Dual Booting Linux and Windows [And How to Fix Them]
======

[![Warp Terminal][1]][2]

Dual booting enables you to enjoy the best of both worlds by having both Windows and Linux on the same computer.

However, as our years of experience goes with dual booting, you are likely to face some of the common issues that I list here.

Let me share what they are along with suggestions on fixing them.

### 1\. Wrong time displayed when you switch OS

One of the most persistent issues with dual booting is that whenever you make a switch to the second operating system (or come back to the first one), you will find your time messed up.

Sure, you can correct the time every time you boot up. But, that will be annoying.

The most effective way to fix this issue is to type in a command in Ubuntu (or other Linux distros **which sets the hardware clock to use local time** :

```

    sudo timedatectl set-local-rtc 1

```

Another easy way to resolve this issue is to **enable automatic date & time via the internet.**

![][3]

Every Linux distro will have a similar setting, and the same applies for Windows too. With this option enabled, the OS will check the time from the internet even if it is messed up to start with, and should be updated automatically as soon as it connects to the internet.

If it still does not work, you can refer to our [tutorial on fixing the wrong time displayed][4] to know more.

![][5]

### 2\. Windows being lower in the boot order

Considering, you installed Linux as the second option for dual booting, it is possible you are worried about the order of boot displayed in the grub screen.

By default, you might end up loading the Linux distribution instead of Windows and see Windows listed in the second option in the grub screen.

![][6]

So, how do we change this? We use **Grub Customizer**.

You can customize grub to your liking, not just the order, but its design too (if you want to go beyond what I say here).

First, you need to **install the Grub Customizer**. You can find it in the software center or install it via the terminal with the following command (for Ubuntu-based distros):

```

    sudo apt install grub-customizer

```

Once you get it installed, open the program. It should prompt you to enter your password again. And, then access the list configuration as shown below.

![][7]

All you have to do is to [**move Windows over the first Ubuntu**][8]. You can use the **arrow option** from the top menu for this task.

Make sure to hit " **Save** " once you change the order for it to take effect.

If you need detailed steps, you can watch this video (a little old but still works):

[Subscribe to It's FOSS YouTube Channel][9]

Or refer to this tutorial:

![][10]

You can learn more about [using grub customizer][11] (and how to change the background of the grub screen) in our tutorial here:

![][12]

### 3\. No bootable device found error

Whether you installed Ubuntu as a secondary OS or decided to eliminate Windows completely, it is possible to mess up the bootloader (or UEFI settings).

You may not see a grub screen or fail to boot into the OS you installed entirely 😱

Fret not, do not panic, not all is lost.

In such cases, you need to fiddle around with the boot settings, trying a couple of options like turning secure boot on to fix the situation.

Here is what you could do:

**Step 1:** Head to the boot options before the OS loads up by pressing F12/F2/F10/DEL key.

**Step 2** : Navigate your way to the security settings, making sure the **Secure Boot is enabled.**

![][13]

**Step 3** : Next, you must look for “ _Select an UEFI file as trusted for executing_ ” and click enter.

📋

With this option, we are adding UEFI settings file (it was generated during Ubuntu installation) among the trusted UEFI boots in your device. If you remember, UEFI boot’s main aim is to provide security and since Secure Boot was not disabled (perhaps) the device did not intend to boot from the newly installed OS. We fix the secure boot issue, and hopefully, that solves our issue here.

In that option, you have to select the HDD/SDD you installed Ubuntu on, and navigate through:

```

     HDD → <EFI> → <ubuntu> → <shimx64.efi>

```

![][14]

Select **shimx64.efi** file as the UEFI file and save the boot configuration. Now, when you reboot the system, grub should appear.

If you have already tried this, you might want to re-install Ubuntu, and ensure that you select the correct bootloader device for the grub screen to show up.

You can find more details on these steps on our tutorial for [fixing no bootable device found][15]:

![][16]

### 4\. No grub Screen & no option to boot into Linux/Windows

Occasionally, there is no error to be found, but instead, the entire grub screen disappears.

In such cases, you are directly booted in to Windows/Linux by default, with no option to head in to the second operating system.

The **immediate workaround** to this is to head into the boot menu (using F8, F12, or DEL key) and manually choose to boot into the second operating system.

However, if you want to fix this permanently, you need to fix the boot order for the grub screen to show up.

To achieve that, you can try to change the boot priority from your boot settings. It is the easiest method for most.

![Make sure that Ubuntu is above Windows in the boot order][17]

You should see the option to access the boot menu. Access it.

Here, identify the Linux boot option ( _here, it says - ubuntu_ ).

Select it and move it up the order using the **F5 key**. Thereafter, press **F10** to save and exit.

💡

Helpful keyboard shortcuts are always displayed in the boot menu.

If you do not have this option in your boot settings. You can try adding a new boot entr or set Linux boot from Windows EFI configuration.

To explore those two options, you can follow our tutorial on [fixing no grub screen][18]:

![][19]

If nothing mentioned works, you can try re-installing the Linux distro with the correct bootloader device selected or [update grub][20]. That tends to work in some cases.

### 5\. Windows does not appear at all in Grub screen

This was noticed with the release of Ubuntu 22.04 and you can still experience it at times.

The OS Prober feature in Grun probes for installed operating systems on the computer and adds them to Grub menu so that you can choose to boot into them.

But this OS_prober was disabled in Grub version 2.06 and thus when you install Ubuntu or some other Linux, the existing Windows would not show up in the Grub menu.

The fix, or should I say workaround, is to change the grub configuration by adding this line:

```

    GRUB_DISABLE_OS_PROBER=false

```

to the file `/etc/default/grub`. After making changes, save the file and [update grub][20] with:

```

    sudo update-grub

```

### 6\. The system keeps on booting into live version of Linux

This happens when you have the live Linux USB still plugged into the system.

Here's the scenario. You create a live Linux USB, you plug it in the system and then change the BIOS settings to boot from USB at the top of the boot order and boot from it. Once you installed Linux but you keep the live USB plugged in, it is likely going to boot into the live session again as USB is up the boot order.

That's the reason why Ubuntu and some other distributions explicitly display a message to remove the installation media (i.e. the live USB) and then reboot.

### 7\. Your distro might not use Grub

![Credits: Reddit][21]

You hear about the grub boot screen all the time. However, there are some distributions that do not use grub at all.

So, what then? I was clueless **when I first installed Pop!_OS and realized that it does not use grub**.

In such a case, you can **manually install rEFInd boot manager** to act as a replacement to grub.

You can follow the [official instructions][22] to install the rEFInd package on your Linux distro. For instance, if you are on Ubuntu, you can install it from its PPA:

```

    sudo apt-add-repository ppa:rodsmith/refind
    sudo apt update
    sudo apt install refind

```

Once done, all you need to do is run its installation script:

```

    refind-install

```

You can also take a look at the [ArchWiki][23] for more information on the same if you need to customize the experience.

The installation script should automatically set things up for you. The next time you reboot, you should see a screen like the one in the screenshot above.

_💬 What is the problem that you were facing? Did we manage to help you out? Is there something we missed? Let us know in the comments below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/dual-boot-issues/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/11/set-auto-time-date-timezone-ubuntu.png
[4]: https://itsfoss.com/wrong-time-dual-boot/
[5]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[6]: https://itsfoss.com/content/images/2024/11/grub_screen.png
[7]: https://itsfoss.com/content/images/2024/11/grub-customizer.png
[8]: https://itsfoss.com/grub-customizer-ubuntu/
[9]: https://www.youtube.com/@itsfoss
[10]: https://itsfoss.com/content/images/icon/android-chrome-192x192-111.png
[11]: https://itsfoss.com/customize-grub-linux/
[12]: https://itsfoss.com/content/images/icon/android-chrome-192x192-100.png
[13]: https://itsfoss.com/content/images/2024/11/No_Bootable_Device_Found_2.jpg
[14]: https://itsfoss.com/content/images/2024/11/No_Bootable_Device_Found_6.jpg
[15]: https://itsfoss.com/no-bootable-device-found-ubuntu/
[16]: https://itsfoss.com/content/images/icon/android-chrome-192x192-98.png
[17]: https://itsfoss.com/content/images/wordpress/2021/10/windows-ubuntu-boot-order-800x282.webp
[18]: https://itsfoss.com/no-grub-windows-linux/
[19]: https://itsfoss.com/content/images/icon/android-chrome-192x192-99.png
[20]: https://itsfoss.com/update-grub/
[21]: https://itsfoss.com/content/images/2024/11/refind.png
[22]: https://www.rodsbooks.com/refind/installing.html
[23]: https://wiki.archlinux.org/title/REFInd
