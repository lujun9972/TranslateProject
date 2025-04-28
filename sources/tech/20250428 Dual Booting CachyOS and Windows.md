[#]: subject: "Dual Booting CachyOS and Windows"
[#]: via: "https://itsfoss.com/dual-boot-cachyos-windows/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Dual Booting CachyOS and Windows
======

[![Warp Terminal][1]][2]

There is something about CachyOS. It feels fast. The performance is excellently smooth, specially if you have newer hardware.

I don't have data to prove it but my new Asus Zenbook that I bought in November last year is rocking CachyOS superbly.

The new laptop came with Windows, which is not surprising. I didn't replace Windows with Linux. Instead, I installed CachyOS in dual boot mode alongside Windows.

The thing is that it was straightforward to do so. Anything simple in the Arch domain is amusing in itself.

So, I share my amusing experience in this video.

[Subscribe to It's FOSS YouTube Channel][3]

I understand that video may not be everyone's favorite format so I created this tutorial in the text format too.

There are a few things to note here:

  * An active internet connection is mandatory. Offline installation is not possible.
  * An 8 GB USB is needed to create the installation medium.
  * At least 40 GB free disk space (it could be 20 GB as well but that would be way too less).
  * Time and patience is of essence.



🚧

You should back up your important data on an external disk or cloud. It is rare that anything will go wrong, but if you are not familiar to dealing with disk partitions, a backup will save your day.

SPONSORED

****Use Swiss-based pCloud storage****

Back up important folders from your computer to pCloud, securely. Keep and recover old versions in up to 1 year.

[Learn more about pCloud backup][4]

### Creating live USB of CachyOS and booting from it

First, download the desktop edition of CachyOS from its website:

[Download CachyOS][5]

You can create the live USB on any computer with the help of Ventoy. I used [my TUXEDO notebook][6] for this purpose.

[Download Ventoy][7] from the official Website. When you extract it, there will be a few executables in it to run it either in a browser or in a GUI. Use whatever you want.

Making sure that USB is plugged in, install Ventoy on it.

![][8]

Once done, all you need to do is to drag the CachyOS ISO to the Ventoy disk. The example below shows it for Mint but it's the same for any Linux ISO.

![][9]

If you need [detailed steps for using Ventoy][10], please follow this tutorial.

![][11]

Once I had the CachyOS live USB, I put it in the Asus Zenbook and restarted it. When the computer was starting up, pressing F2/F10 button took me to the BIOS Settings.

I did that to ensure that the system boots from the USB instead of the hard disk by changing the boot order.

![Change boot priority][12]

When the system booted next, Ventoy screen was visible and I could see the option to load the CachyOS live session.

![Select CachyOS][13]

I selected to boot in normal mode.

![Normal Mode][14]

There was an option to boot into CachyOS with NVIDIA. I went with the default option.

![Open-source or closed-source drivers][15]

While booting into CachyOS, I ran into an issue. **There was a "Start Job is running...** " message for more than a minute or two. I force restarted the system and the live USB worked fine the next time.

![Start job duration notification][16]

If this error persists for you, try to change the USB port or create live USB again.

**Another issue I discovered by trial and error was relating to the password**. CachyOS showed a login screen that seemed to be asking for username and password. As per the official docs, there are no password required in live session.

What I did was to change the display server to Wayland and then click the next button, and I was logged into the system without any password.

![Select Wayland][17]

### Installing CachyOS

Again, active internet is mandatory to download the desktop environment and other packages.

Select the "Launch installer" option.

![Click on "Launch Installer"][18]

My system was not plugged into a power source but it had almost 98% battery and I knew that it could handle the quick installation easily.

![System not connected to power source warning][19]

Quite straight forward settings in the beginning. Like selecting time zone

![Set Location][20]

and keyboard layout.

![Set keyboard layout][21]

The most important step is the disk partition and I was pleasantly surprised to see that the Calamares installer detected Windows presence and gave option to install CachyOS alongside.

I have a single disk with Windows partition as well as EFI system partition.

All I had to do was to drag the slider and shrink the storage appropriately.

![Storage settings][22]

I gave more space to Linux because it was going to be my main operating system.

The next screen gave the options to install a desktop environment or window manager. I opted for GNOME. You can see why it is important to have active internet connection. The desktop environment is not on the ISO file. It needs to be downloaded first.

![Select Desktop Environment][23]

And a few additional packages are added to the list automatically.

![Installing additional packages][24]

And as the last interactive step of install, I created the user account.

![Enter user credentials][25]

A quick overview of what is going to be done at this point. Things looked fine so I hit the Install button.

![Click on Install][26]

And then just wait for a few minutes for the installation to complete.

![Installation progress][27]

When the installation completes, restart the system and take out the live USB. In my case, I forgot to take the USB out, but still booted from the hard disk.

### Fixing the missing Windows from grub

When the system booted next, I could see the usual [Grub bootloader][28] screen but there was no Windows option in it.

![Windows Boot Manager is absent][29]

Fixing it was simple. I opened the grub config file for [editing in Nano][30].

```

    sudo nano /etc/default/grub

```

OS_PROBER was disabled, so I uncommented that line, saved the file and exited.

![Uncomment OS Prober][31]

The next step was to update grub to make it aware of the config changes.

```

    sudo grub-mkconfig -o /boot/grub/grub.cfg

```

And on the next reboot, the Windows boot manager option there to let me use Windows.

![Windows Boot Manager in the boot screen][32]

This is what I did to install CachyOS Linux alongside Windows. For an Arch-based distro, the procedure was pretty standard, and that's a good thing. Installing Linux should not be super complicated.

💬 If you tried dual booting CachyOS, do let me know how it went in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/dual-boot-cachyos-windows/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.youtube.com/@itsfoss
[4]: https://partner.pcloud.com/r/141499
[5]: https://cachyos.org/download/
[6]: https://news.itsfoss.com/tuxedo-infinitybook-pro-16-review/
[7]: https://www.ventoy.net/en/download.html
[8]: https://itsfoss.com/content/images/2025/04/image-1.png
[9]: https://itsfoss.com/content/images/2025/04/image-2.png
[10]: https://itsfoss.com/use-ventoy/
[11]: https://itsfoss.com/content/images/icon/android-chrome-192x192-416.png
[12]: https://itsfoss.com/content/images/2025/04/boot-priority-usb.png
[13]: https://itsfoss.com/content/images/2025/04/select-cachyos-from-ventoy-screen.png
[14]: https://itsfoss.com/content/images/2025/04/boot-in-normal-mode.png
[15]: https://itsfoss.com/content/images/2025/04/cachy-boot-oss-noss.jpg
[16]: https://itsfoss.com/content/images/2025/04/start-job-duration.png
[17]: https://itsfoss.com/content/images/2025/04/select-wayland.png
[18]: https://itsfoss.com/content/images/2025/04/launch-installer.jpg
[19]: https://itsfoss.com/content/images/2025/04/no-power-source-warning.jpg
[20]: https://itsfoss.com/content/images/2025/04/select-loaction-1.jpg
[21]: https://itsfoss.com/content/images/2025/04/select-keyboard-layout.jpg
[22]: https://itsfoss.com/content/images/2025/04/partition-settings.jpg
[23]: https://itsfoss.com/content/images/2025/04/select-desktop.jpg
[24]: https://itsfoss.com/content/images/2025/04/additional-packages.jpg
[25]: https://itsfoss.com/content/images/2025/04/enter-user-credentials.jpg
[26]: https://itsfoss.com/content/images/2025/04/click-install-1.jpg
[27]: https://itsfoss.com/content/images/2025/04/install-progress.jpg
[28]: https://itsfoss.com/what-is-grub/
[29]: https://itsfoss.com/content/images/2025/04/no-windows-boot-manager.png
[30]: https://itsfoss.com/nano-editor-guide/
[31]: https://itsfoss.com/content/images/2025/04/uncomment-os-prober.png
[32]: https://itsfoss.com/content/images/2025/04/windows-boot-manager.png
