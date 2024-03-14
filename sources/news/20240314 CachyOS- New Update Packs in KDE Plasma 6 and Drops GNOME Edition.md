[#]: subject: "CachyOS' New Update Packs in KDE Plasma 6 and Drops GNOME Edition"
[#]: via: "https://news.itsfoss.com/cachyos-march-2024-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

CachyOS' New Update Packs in KDE Plasma 6 and Drops GNOME Edition
======
CachyOS features the latest from KDE Plasma and other goodies!
[CachyOS][1] is one of those Linux distros that is [easier to install and use][2] than Arch Linux itself. If you were to get started with it, you wouldn't even know that it is based on Arch; it is that straightforward to get started with.

Tailored for most use cases, it follows a monthly release schedule, with regular fixes and improvements on offer.

For the month of March 2024, we have a new CachyOS release that packs in some exciting upgrades we have been waiting for.

Let's take a look and see what it has to offer.

**Suggested Read** 📖

![][3]

## 🆕 CachyOS March 2024: What's new?

![][4]

Powered by a customized version of [Linux kernel 6.7][5], CachyOS March 2024 is the third release of this year for the distro that drops the GNOME image owing to lack of maintenance from the community.

The developers wanted to avoid double testing for every new CachyOS release (KDE+GNOME), so they decided to ditch GNOME. They also mention that doing so will make it simpler for users when setting up a new CachyOS system.

As for the key highlights of this release, let's start off with the installer.

### Installer Improvements

![][6]

Since the last time we [took a look][7] at CachyOS, there is now an updated installer in the form of **a** [**QT6**][8] **installer** thanks to the [Calamares 3.3.5][9] release. These changes were made to accommodate Plasma 6.

### Inclusion of KDE Plasma 6

![][10]

Yes, CachyOS now features the latest and greatest from KDE's stable. With the addition of [Plasma 6][11], CachyOS now **defaults to a Wayland session** , with the option to switch back to X11 if you face any issues. Plasma 6 is also the default desktop environment for the live session.

According to the developers, they are quite convinced with the way Plasma 6 handles Wayland, and users with NVIDIA GPUs can still switch to the X11 session if the need arises.

Furthermore, they are confident that when the [_explicit sync protocol_][12] from [NVIDIA][13] and [_wayland-protocols_][14] ** is here, users will be able to more comfortably use the Wayland session with NVIDIA GPUs.

**Suggested Read** 📖

![][15]

### 🛠️ Other Changes and Improvements

To wrap this up, there are a few other notable improvements that you should know of:

  * Microcode is not booted alongside the bootloader anymore.
  * Updated packages such as _linux-cachyos 6.7.9_ , _mesa 24.0.2_ , _zfs-utils 2.2.3._
  * [_pacstrap_][16] no longer installs config packages for a more clean installation process.
  * When the [_refind_][17] bootloader is selected, F2FS and ZFS are now available to choose.



If you are interested in learning more about this release, head over to the [announcement blog][18].

## 📥 Download CachyOS

The developers have made this release of CachyOS available via official mirrors on their [website][19] and [SourceForge][20]. Just remember to get the KDE build, as the GNOME images won't be updated going forward.

[CachyOS March 2024 (KDE) (SourceForge)][21]

You do get to pick from a long list of desktop environments when you run the installer (including GNOME), so you don't need to worry about that.

_💬 Will you be installing this release of CachyOS? Or are you content with Arch Linux?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/cachyos-march-2024-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://cachyos.org/
[2]: https://itsfoss.com/arch-based-linux-distros/
[3]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[4]: https://news.itsfoss.com/content/images/2024/03/CachyOS_March_2024_a.jpg
[5]: https://news.itsfoss.com/linux-kernel-6-7-release/
[6]: https://news.itsfoss.com/content/images/2024/03/CachyOS_March_2024_b.jpg
[7]: https://news.itsfoss.com/cachyos/
[8]: https://www.qt.io/product/qt6
[9]: https://calamares.io/calamares-3.3.5-is-out/
[10]: https://news.itsfoss.com/content/images/2024/03/CachyOS_March_2024_c.jpg
[11]: https://news.itsfoss.com/kde-plasma-6/
[12]: https://gitlab.freedesktop.org/wayland/wayland-protocols/-/merge_requests/90
[13]: https://www.nvidia.com/
[14]: https://gitlab.freedesktop.org/wayland/wayland-protocols
[15]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[16]: https://wiki.archlinux.org/title/Pacstrap
[17]: https://www.rodsbooks.com/refind/index.html
[18]: https://cachyos.org/blog/2403-march-release/
[19]: https://mirror.cachyos.org/ISO/
[20]: https://sourceforge.net/projects/cachyos-arch/files/gui-installer/
[21]: https://sourceforge.net/projects/cachyos-arch/files/gui-installer/kde/240313/
