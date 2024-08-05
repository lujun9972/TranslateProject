[#]: subject: "How I Installed Armbian Desktop"
[#]: via: "https://itsfoss.com/install-armbian/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I Installed Armbian Desktop
======

[![Warp Terminal][1]][2]

Armbian is an awesome project. While there are [numerous operating systems for Raspberry Pi][3], Armbian is the operating system for [numerous Raspberry Pi like single board computer][4] (SBC) devices.

If you have a non-Raspberry Pi device, you should surely give it a try.

Recently, I installed Armbian on my [ArmSoM Sige7 board][5] and I thought of sharing the process I followed.

The installation procedure is quite simple:

  * Download the appropriate Armbian image for your SBC
  * Flash the Armbian image on the micro SD card
  * Boot the device from the micro SD card and do the initial setup



Let's see it in detail.

📋

As the title already indicates, it is for the Armbian desktop, and hence, the installation procedure is not headless here.

### Choosing the correct image (it's important)

Despite the name that suggests that Amrbian is Debian for ARM devices, Armbian is more than that.

**Armbian offers both Ubuntu and Debian builds**. There are various builds available for servers (without desktop environment) and desktop (with GNOME or Xfce). A few special builds are available for setting up Home Assistant and Open Hab.

Now this is really up to you to decide which version you want to go with. If you are more comfortable with Debian, go with Debian version, otherwise stick with Ubutnu version.

If you don't have much experience with either, you may stick with Ubuntu as it seems to be more popular, especially among beginners.

It doesn't end here. Armbian has three categories of images:

  * Platinum supported SBCs
  * Standard supported SBCs
  * Community Supported SBCs
  * Generic images



![][6]

There are numerous SBCs and Armbian aims to provide support for most of them, if not all. This is why they have different images for different SBCs. You should look for your SBC and see if Aermbian has a dedicated image for your board.

Some SBC vendors, like Banana Pi etc, have partnership with Armbian and thus they are in the 'Platinum' support category. Expect better hardware support for these boards.

[Download Armbian][7]

If you do not find your board under the Platinum, Standard or Community category, you can download the generic Armbian image from the homepage. It may or may not work completely.

📋

I am using an ArmSoM Sige7 device, which is the same as the Banana Pi M7. But I used a custom Armbian build provided by ArmSoM here. The installation process should be the same for other Armbian desktop versions.

### Preparing the micro SD card

I used [Etcher on Linux][8] to create the Armbian Micro SD card. Etcher is a cross platform tool and you can easily use it on Windows and other platforms, too.

[Download Etcher][9]

It comes in AppImage format for Linux. Please read our [guide on using AppImage][10] if you are not familiar with it.

Using Etcher is simple. Plug in your micro SD card into your computer and run Etcher. It will recognize the SD card immediately. Browse the downloaded .img file for Armbian and click on Flash.

![][11]

Wait for a few minutes for the process to complete. If you have a slow SD card, it make take time.

![][12]

Once the process is complete, take out the micro SD card and prepare your SBC.

📋

If you try to eject the newly created Armbian SD card named `armbi_root` in Ubuntu, it may show an error like 'no object for D-Bus interface'. That's okay. Just take out the micro SD card.

### Installing Armbian on your ARM board

✋

It is possible to encounter boot and other issues with the latest images. In such cases, you should download a bit older image for your device from the archive and see if it works. It would be good if you could notify the devs in the official forum about it.

Plug the micro SD card on your ARM board. Connect the board to a monitor, keyboard and mouse and a power source. It would be good if you can connect to an Ethernet port although that's not necessary.

Once you power on the device, in a few seconds, you should see the Armbian logo. After that, you'll be on a black screen with an option to set up the root password.

![][13]

💡

If you encounter the screen where it asks you to log in and provide password, please note that default user is root and the default password is 1234. As soon as you enter it, you'll be asked to create root password.

Once you have created the root password, you'll be asked to choose the default shell between bash and zsh. If you don't know what zsh is, stick with bash.

Afterwards, you'll be asked to create a new user and set up its password. This user will be a sudoer and you can use it to run commands with sudo.

![][14]

Since I was connected to Ethernet and hence it knew my geographical location and suggests locales based on that. If you are not connected to internet yet, you should provide the appropriate options.

![][15]

Once the locales are set, it should boot into the desktop environment.

✋

When I connected the newly created Armbian SD card to my 4K monitor, it didn't show the initial setup screen. Connecting it to a normal Full HD monitor worked. 4K monitor worked fine after the initial setup though.

### Enjoy Armbian

Armbian falls in the familiar terrain of APT package manager and if you ever used a Debian/Ubuntu based distro, it should not feel unfamiliar to you.

I shared the installation process I followed for my [Rockchip-based ArmSom Sige7 SBC][16]. I am hoping that the procedure remains the same for other single board computers, too. Please let me know if you face any issues.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-armbian/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/raspberry-pi-os/
[4]: https://itsfoss.com/raspberry-pi-alternatives/
[5]: https://www.armsom.org/sige7
[6]: https://itsfoss.com/content/images/2024/08/armbian-platinum-support-download.webp
[7]: https://www.armbian.com/download/
[8]: https://itsfoss.com/install-etcher-linux/
[9]: https://etcher.balena.io/
[10]: https://itsfoss.com/use-appimage-linux/
[11]: https://itsfoss.com/content/images/2024/08/burn-armbian-to-sd-card.png
[12]: https://itsfoss.com/content/images/2024/08/burning-armbian-to-sd-card.png
[13]: https://itsfoss.com/content/images/2024/08/armbian-set-root-password.webp
[14]: https://itsfoss.com/content/images/2024/08/armbian-create-user-setup-shell.webp
[15]: https://itsfoss.com/content/images/2024/08/armbian-set-locale.webp
[16]: https://itsfoss.com/arosom-sige7-review/
