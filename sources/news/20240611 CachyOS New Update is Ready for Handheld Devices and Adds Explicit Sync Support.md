[#]: subject: "CachyOS New Update is Ready for Handheld Devices and Adds Explicit Sync Support"
[#]: via: "https://news.itsfoss.com/cachyos-june-2024-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

CachyOS New Update is Ready for Handheld Devices and Adds Explicit Sync Support
======
CachyOS June update is a solid one!
[![][1]][2]

CachyOS is an Arch Linux-based distribution that appeals to all kinds of users. Be it the casual user who just wants to run a basic set of apps and tools, or pros who love to flaunt their Arch guru status everywhere by saying “ _I use Arch, btw_ ”.

As a [rolling release][3] distro, it is constantly going through changes which aim to improve the overall experience, while also adding some new bits along the way.

Coming just a few months after the [March 2024][4] release, we are now taking a look at the **CachyOS June 2024** release.

## 🆕 CachyOS June 2024: What's New?

![][5]

We start with _Linux kernel 6.9.3-3-cachyos_ which is powering it all, with [_Mesa 24.1.1_][6] being implemented for better graphics handling, _XWayland 24.1_ which comes with many improvements, and [_KDE Plasma 6.0.5_][7] as the desktop environment.

Some key highlights of this release include:

  * **Storage Improvements**
  * **Better NVIDIA Support**
  * **Handheld Edition Refinements**



### Storage Improvements

Starting with this release, the ISO now comes equipped with a script called “ _cachy-chroot_ ”, which is meant to guide users during the chroot process, while also ensuring that partitions are mounted correctly.

The **default file system is now BTRFS** instead of XFS, with the option to choose other file systems, and the script mentioned above can also detect subvolumes for BTRFS.

Furthermore, the ISO will now be copied over to the RAM if there's enough space available, speeding up the user experience when booting into the ISO. This was made possible due to the implementation of _mkinitcpio_ microcode hook and _copytoram_.

### Better NVIDIA Support

Equipped with the 555 NVIDIA driver, CachyOS is **among the first distros to feature support for explicit sync** , which is [the answer to NVIDIA Linux problems][8]. No more flickers when using NVIDIA GPUs, and the multi-monitor experience should be better too.

The developers have also enabled various services to fix the graphical corruption issue when sleep was used on Wayland sessions.

![][9]

### Handheld Edition Refinements

The Handheld Edition of CachyOS has been **promoted to the stable status** , with many improvements like SDDM now using Wayland, the default kernel being _linux-cachyos-deckify_ , hardware detection automatically configuring/installing the relevant packages according to the device, and more.

Currently, only the [Steam Deck][10], [Legion Go][11], and [ROG Ally][12] are officially supported.

### 🛠️ Other Changes and Improvements

There are a few other interesting changes that you should know of:

  * Various Netinstall improvements.
  * Newly introduced support for [Apple T2][13] MacBooks.
  * Improved official wiki, equipped with an updated structure.
  * It is now necessary to use the [latest][14] Ventoy version during installation.



For more details, you can go through the official [release blog][15].

## 📥 Download CachyOS

If you are going for a new desktop installation, go for the KDE image of the “ _Desktop Edition_ ”, as the **GNOME image is not maintained anymore**. Go for the “ _Handheld Edition_ ” if you are looking to run CachyOS on a supported handheld gaming device.

Head on over to the [official website][16] to get the latest release. If that's not working, then you can either get it from the [official mirror][17] or the project's [SourceForge][18] page.

[CachyOS (SourceForge)][18]

**For existing users** , they can just run the following command to get the latest CachyOS release:

```

    sudo pacman -Syu

```

You can refer to the [official wiki][19] if you run into problems.

_💬 What are your thoughts on this release? Let me know below!_

**Suggested Read** 📖

![][20]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/cachyos-june-2024-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/rolling-release/
[4]: https://news.itsfoss.com/cachyos-march-2024-release/
[5]: https://news.itsfoss.com/content/images/2024/06/CachyOS_June_2024.jpg
[6]: https://docs.mesa3d.org/relnotes/24.1.1.html
[7]: https://kde.org/announcements/changelogs/plasma/6/6.0.4-6.0.5/
[8]: https://news.itsfoss.com/explicit-sync-wayland/
[9]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[10]: https://store.steampowered.com/steamdeck
[11]: https://www.lenovo.com/us/en/p/handheld/legion-go/len106g0001
[12]: https://rog.asus.com/gaming-handhelds/rog-ally/rog-ally-2023/
[13]: https://en.wikipedia.org/wiki/Apple_T2
[14]: https://github.com/ventoy/Ventoy/releases
[15]: https://cachyos.org/blog/2406-june-release/
[16]: https://cachyos.org/download/
[17]: https://mirror.cachyos.org/ISO/
[18]: https://sourceforge.net/projects/cachyos-arch/files/gui-installer/
[19]: https://wiki.cachyos.org/installation/updating_cachyos/
[20]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
