[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Troubleshooting “No Bootable Medium Found” Error in VirtualBox)
[#]: via: (https://itsfoss.com/virtualbox-no-bootable-medium-found/)
[#]: author: (Dimitrios Savvopoulos https://itsfoss.com/author/dimitrios/)

Troubleshooting “No Bootable Medium Found” Error in VirtualBox
======

Many [VirtualBox][1] users have experienced at least once the message **‘FATAL: Could not read from the boot medium! System halted.**‘ Sometimes it is also shown ‘**No Bootable Medium Found**! **System halted**‘.

This error is more common when trying to start a new virtual machine, but it is not impossible to happen at an existing virtual machine if the virtual hard drive is missing.

**Note**: This problem has to do purely with VirtualBox, and can be experienced on any host operating system be it Windows, Mac OS or Linux.

![][2]

### What causes this “Could not read from the boot medium” error?

There are two main reasons behind this issue:

  * **VirtualBox doesn’t point to an operating system, either a mounted iso or a virtual hard disk with a bootable OS.** When you create a virtual machine for a first time, you need to mount a bootable iso like [Ubuntu][3]. If you mount a bootable iso before you start your virtual machine, you will be successful booting up the system.
  * **The CD/ DVD** **storage device controller is configured as SATA**. Another issue can be appeared, if you mount accidentally the bootable iso to a SATA storage device controller instead of IDE. VirtualBox works without any problems when a SATA storage device points to a virtual hard drive, but this is not the case for a bootable iso.



### How to solve it?

If you are not sure which of the 2 reasons apply to you, I can show you a solution that covers both, and finally stop receiving the error message.

**Step 1**: Right click on the virtual machine that isn’t a bootable state and click on settings.

![][4]

**Step 2**: Once the settings menu is open, follow the steps access storage &gt; Controller:IDE &gt; Choose the bootable iso and click ok.

![][5]

**Step 3**: Start your virtual machine and you should be able to boot normally from the mounted iso.

![][6]

#### Conclusion

VirtualBox boot issue is very common, and easy to fix but can be frustrating if you don’t know what to do. If you are a regular reader of It’s FOSS, you know already that virtualization technology is among my interests. If you discovered us recently and you are curious to start exploring the features of VirtualBox, I suggest to start experimenting with [this guide that covers Fedora installation on VirtualBox][7], as you can go beyond a simple installation.

--------------------------------------------------------------------------------

via: https://itsfoss.com/virtualbox-no-bootable-medium-found/

作者：[Dimitrios Savvopoulos][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/dimitrios/
[b]: https://github.com/lujun9972
[1]: https://www.virtualbox.org
[2]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/12/1.No-Bootable-Medium-Found-VirtualBox.png?resize=800%2C500&ssl=1
[3]: https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-desktop-amd64.iso
[4]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/12/2-VirtualBox-settings.png?resize=800%2C600&ssl=1
[5]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/12/3-VirtualBox-IDE-controller.png?resize=800%2C578&ssl=1
[6]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/12/4-VirtualBox-Gentoo-boot.png?resize=800%2C600&ssl=1
[7]: https://itsfoss.com/install-fedora-in-virtualbox/
