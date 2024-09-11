[#]: subject: "Change Between sysvinit and systemd in MX Linux"
[#]: via: "https://itsfoss.com/mxlinux-sysvinit-systemd/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Change Between sysvinit and systemd in MX Linux
======

[![Warp Terminal][1]][2]

If you happen to be an MX Linux user and really want to change their init system from SysVinit to Systemd and vice versa, then this guide is for you. Although, you should not try something like this.

I wrote it for an It's FOSS reader and performed the steps in a virtual machine.

This guide will walk you through the following:

  * Switch from SysVinit to Systemd
  * Switch from Systemd to SysVinit



🚧

Changing the init system is NOT RECOMMENDED unless you have a very strong reason to do so. I'd recommend using a distro that ships with your preferred init system rather than changing the init system afterward. I suggest making system settings backup with Timeshift first.

### Switch from SysVinit to Systemd MX Linux

[MX Linux][3] uses the SysVinit, making it [one of the best systemd-free Linux distros][4] but there are times when you would want to switch to Systemd, the most popular init system out there.

There are two ways you can change your init system to the Systemd in MX Linux:

  * Booting directly into the system with Systemd through GRUB
  * Installing Systemd and removing SysVinit (easy for permanent effect)



#### Using bootloader (GUI method)

This is the easiest way you can switch to Systemd where all you have to do is select the Systemd option from the GRUB bootloader and it will boot into system using the Systemd.

First, reboot your system and choose the `Advanced options for MX Linux` and then you will find the option to boot with the Systemd:

![][5]

Yep, that's all it takes to use the Systemd.

But wait ✋.

This is a temporary solution. Want a permanent solution? Here you have it.

##### Boot into Systemd-enabled system by default

To use the Systemd by default, open the utility called `MX boot options` and choose the Systemd boot option in the `Boot to` menu:

![][6]

Finally hit the `Apply` button and from now on, you'll boot into the Systemd-enabled environment.

#### Using the command line (permanent)

🚧

The Systemd-only setup will lead to the unavailability of MX Live system (USB) functionalities like persistence. Avoid it please.

If you want to switch to the Systemd permanently, then this is the perfect solution where you install the Systemd which will remove the SysVnit as it conflicts with the other init system.

So you are left with the system that purely uses Systemd.

To install Systemd, use the following command:

```

    sudo apt install systemd-sysv

```

Once done, reboot your system and you'll boot to a Systemd-enabled MX Linux environment.

### Switch from Systemd to SysVnit in MX Linux

If you used the previous section to switch to Systemd and want to switch back to SysVnit then here I will be sharing two ways to do so:

  * Using MX boot options
  * Removing Systemd (will install SysVnit automatically)



#### Using the MX boot options

If you previously used the MX boot options to configure Systemd as a default init system to boot into that it can easily be reverted.

All you have to do is open the MX boot options and choose the default boot option (the first one):

![][7]

Finally, hit the `Apply` button and you get access to the default init system (SysVnit).

#### By removing Systemd

Previously, I explained that installing Systemd will remove the SysVnit and you will access to the Systemd-enabled MX Linux,

In that case, all you need to do is remove the Systemd, and MX Linux will automatically install SysVnit.

To remove Systemd, execute the following command:

```

    sudo apt remove systemd-sysv

```

Once done, reboot your system and you will boot into a SysVnit-powered environment.

### My take on changing the init system

If you want to use a different init system then use a distro that comes pre-configured with your desired init system but I don't recommend changing the init system.

Why? Because there might be some parts of the system that'd only work with its default init system such as in MX Linux, changing to Systemd won't let you use the persistence features of the MX live USB.

But if you want to experiment, then use a VM and test things thoroughly before making changes to the main system.

Feel free to ask such questions (I love solving your queries and feels refreshing too).

--------------------------------------------------------------------------------

via: https://itsfoss.com/mxlinux-sysvinit-systemd/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://mxlinux.org/
[4]: https://itsfoss.com/systemd-free-distros/
[5]: https://itsfoss.com/content/images/2024/02/Choose-Systemd-in-GRUB.png
[6]: https://itsfoss.com/content/images/2024/02/Boot-into-systemd-enabled-environment-by-default-in-MX-Linux.png
[7]: https://itsfoss.com/content/images/2024/02/Switch-back-to-SysVnit-in-MX-Linux.png
