[#]: subject: "Ultramarine Linux 40 is a Refreshing Distro Upgrade"
[#]: via: "https://news.itsfoss.com/ultramarine-linux-40-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ultramarine Linux 40 is a Refreshing Distro Upgrade
======
A new edition, and more improvements to Ultramarine Linux 40.
[![][1]][2]

Ultramarine Linux is one of the [best Fedora-based distributions][3] around, which has been built keeping ease of use in mind.

Liked by both beginners and veterans, most people find it to be a very reliable daily-driver Linux distro that doesn't get in the way.

It has been brought forward by [Fyra Labs][4] and a dedicated community, who have been proactively pushing new improvements to Ultramarine regularly.

In a recent announcement, the developers introduced the Ultramarine Linux 40 release, which is based on the recent [Fedora 40][5] release.

So, let's take a brief look at it! 😀

### Ultramarine Linux 40: What's New?

![][6]

For starters, this release of Ultramarine Linux is powered by [Linux kernel 6.8][7], which has brought about improved hardware support for Intel, AMD, Raspberry Pi, and even Qualcomm's Snapdragon.

Some **key highlights** of this release include:

  * **Desktop Environment Upgrades**
  * **Better Raspberry Pi Support**
  * **New Edition**



#### Desktop Environment Upgrades

![][8]

The flagship edition of Ultramarine Linux comes equipped with the latest [Budgie 10.9.1][9] desktop environment. This release comes with many bug fixes that focus on improving the user experience.

![A Screenshot of GNOME 46 for Reference][10]

For the GNOME edition, we now have [GNOME 46][11], which offers niceties such as an improved file manager, revamped online accounts, better remote sessions, updated core apps, and more.

![][12]

![][13]

Similarly, for the KDE Plasma edition, there is now the [Plasma 6][14] release, which comes with improvements like a better Discover app, Wayland by default, a new wallpaper, various tweaks for the System Settings, and more.

![][12]

#### Better Raspberry Pi Support

Starting with this release, **the Raspberry Pi images now come equipped with desktop environments**. For now, you can download the Raw images, but Ultramarine will also be made available in the Raspberry Pi Imager in the near future.

The developers have also shared that they are working on bringing support for [Raspberry Pi 5][15] and [Zero 2][16].

#### New XFCE Edition

![][17]

Ultramarine Linux 40 also debuts a new “Xfce” edition that comes equipped with [Xfce 4.18][18]. This was voted into place [earlier this year][19], with other contenders being Sway, Cinnamon, Server, and Wayfire.

The devs have **kept the experience pretty close to the vanilla Xfce experience** , with one key change. They have gone for a traditional dock and panel setup with a modern menu that features search functionality instead of Xfce's split layout.

Unfortunately, **the Pantheon edition had to be sunset** due to a growing maintenance burden and a shrinking user base.

To wrap this up, the developers have shared that they are **working on bringing Ultramarine Linux to Chromebooks** , and they intend to ditch [Anaconda][20] in favor of their in-house project called "[Readymade][21]".

For more details, head over to the [release blog][22] to learn more.

### Get Ultramarine Linux 40

You can get the four variants, Budgie, GNOME, Xfce, and KDE Plasma from the [official website][23], where you will also find alternative ways to download them, ARM images, and Raw images.

[Ultramarine Linux 40][23]

#### ⚙️How to Upgrade from Older Releases?

Before you begin, ensure that you have backed up your system. Then, head over to the app store on the respective Ultramarine Linux editions ( _except Pantheon_ ) to get the upgrade started.

You can also run the following commands to upgrade to the latest release:

```

    sudo dnf upgrade
    sudo dnf install dnf-plugin-system-upgrade
    sudo dnf system-upgrade download --releasever=40
    sudo dnf system-upgrade reboot

```

If you have further questions, then you can refer to the [upgrade guide][24].

💬 Are you hyped for this release? Let me know below!

**Suggested Read** 📖

![][25]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ultramarine-linux-40-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/best-fedora-linux-distributions/
[4]: https://fyralabs.com/
[5]: https://news.itsfoss.com/fedora-40-release/
[6]: https://news.itsfoss.com/content/images/2024/05/Ultramarine_Linux_40_a.jpg
[7]: https://news.itsfoss.com/linux-kernel-6-8-release/
[8]: https://news.itsfoss.com/content/images/2024/05/Ultramarine_Linux_40_b.jpg
[9]: https://buddiesofbudgie.org/blog/budgie-10-9-1-released
[10]: https://news.itsfoss.com/content/images/2024/05/Ultramarine_Linux_40_c.jpg
[11]: https://news.itsfoss.com/gnome-46-release/
[12]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[13]: https://news.itsfoss.com/content/images/2024/05/Ultramarine_Linux_40_d.jpg
[14]: https://news.itsfoss.com/kde-plasma-6/
[15]: https://www.raspberrypi.com/products/raspberry-pi-5/
[16]: https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/
[17]: https://news.itsfoss.com/content/images/2024/05/Ultramarine_Linux_40_e.jpg
[18]: https://news.itsfoss.com/xfce-4-18-release/
[19]: https://blog.fyralabs.com/um40-new-edition-vote/
[20]: https://github.com/rhinstaller/anaconda
[21]: https://github.com/FyraLabs/readymade
[22]: https://blog.fyralabs.com/ultramarine-40-release/
[23]: https://ultramarine-linux.org/download/
[24]: https://wiki.ultramarine-linux.org/en/release/upgrade-to-ultramarine-40/
[25]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
