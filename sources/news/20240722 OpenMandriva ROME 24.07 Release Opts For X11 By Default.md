[#]: subject: "OpenMandriva ROME 24.07 Release Opts For X11 By Default"
[#]: via: "https://news.itsfoss.com/openmandriva-rome-24-07-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

OpenMandriva ROME 24.07 Release Opts For X11 By Default
======
The newest upgrade to the independent Linux distro sounds good for users
annoyed by Wayland.
[![][1]][2]

Born from the ashes of [Mandriva Linux][3], OpenMandriva Lx is an increasingly popular Linux distribution that many users like for the simplicity it has to offer, with many usually committing to using it long-term.

It's offered in **two distinct editions** , one is “ **Rock** ” which is a stable release distro that receives major upgrades periodically, and the other is “ **ROME** ”, which was introduced back [in 2023][4], that follows a [rolling release][5] approach.

In a recent announcement, its developers have announced the new **OpenMandriva ROME 24.07** release, which comes bearing many gifts for both its loyal users, and prospective new users.

So, let's take a closer look at it.

## 🆕 OpenMandriva ROME 24.07: What's New?

![][6]

Powered by a customized version of [Linux kernel 6.10][7], OpenMandriva ROME 24.07 ships with [KDE Plasma 6.1.3][8] as the default desktop environment for its flagship variant.

Even though many distros have been making [the jump][9] to Wayland by default, **OpenMandriva's developers deem Wayland to be not mature enough** to warrant a complete switch for most users.

They are sticking with the dependable [X11][10] session, and have also noted that booting the standalone Wayland ISOs on [VirtualBox][11] will most likely cause a black screen. It does, however, work well on [QEMU][12] with KVM.

![][13]

In a bid to make the user on-boarding process simpler, the developers have merged the modules from “ _oma-welcome_ ” and “ _om-control-center_ ” into one “ **OM Welcome** ” application that allows users to configure the system and add new software.

They have also worked on bringing support for [AMD ROCm][14], an AI graphics generation plugin for Krita, re-enabled support for JPEG-XL, and have included the “ _proton_ ” and “ _proton-experimental_ ” variants of [Wine][15] for making [Proton][16] available outside Steam.

![][17]

To further complement this release, **the developers have included many updated applications** , such as LibreOffice 24.2.5, a de-Googled Chromium 126.0.6478.182, Falkon 24.05.2, and more.

There are many other updated packages too, such as:

  * **glibc 2.39**
  * **GCC 14.1.0**
  * **Mesa 24.1.4**
  * **Systemd 255.7**
  * **LLVM/Clang 18.1.8**



Outlining their plans, the devs have mentioned that **they are working on a RISC-V port for OpenMandriva** , which they intend to introduce with the upcoming release, and that builds for _aarch64_ devices are arriving soon.

You can learn more about the ROME 24.07 release in the [announcement blog][18].

## 📥 Download OpenMandriva ROME 24.07

Alongside the flagship KDE Plasma flavor, there are two other flavors, one is equipped with [LXQt 2.0.0][19], and the other is equipped with [GNOME 46.3][20].

You can get any of those variants from the [SourceForge][21] page for OpenMandriva ROME, where you will also find separate Wayland and AMD-only _znver1_ ISO images.

The latter of which is tailored to take advantage of processors such as Ryzen, Threadripper, and EPYC.

[OpenMandriva ROME 24.07 (SourceForge)][21]

**For existing users** , you can run the following command to upgrade:

```

    $ sudo dnf clean all ; dnf clean all ; dnf repolist
    $ sudo dnf --allowerasing distro-sync

```

Though, a fresh installation is recommended by the developers for running Plasma 6 smoothly. If you run into any issues with this release, the [official wiki][22] is the place to be.

_💬 Do let me know in the comments below if you try out this release._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/openmandriva-rome-24-07-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Mandriva_Linux
[4]: https://www.openmandriva.org/en/news/article/openmandriva-rome-the-rolling-release
[5]: https://itsfoss.com/rolling-release/
[6]: https://news.itsfoss.com/content/images/2024/07/OpenMandriva_24.07_a.png
[7]: https://news.itsfoss.com/linux-kernel-6-10-release/
[8]: https://kde.org/announcements/plasma/6/6.1.3/
[9]: https://news.itsfoss.com/ubuntu-24-10-nvidia-wayland/
[10]: https://www.x.org/wiki/
[11]: https://itsfoss.com/install-virtualbox-ubuntu/
[12]: https://www.qemu.org/
[13]: https://news.itsfoss.com/content/images/2024/07/OpenMandriva_24.07_b.png
[14]: https://www.amd.com/en/products/software/rocm.html
[15]: https://www.winehq.org/
[16]: https://github.com/ValveSoftware/Proton
[17]: https://news.itsfoss.com/content/images/2024/07/OpenMandriva_24.07_c.png
[18]: https://www.openmandriva.org/en/news/article/openmandriva-rome-24-07-released
[19]: https://lxqt-project.org/release/2024/04/15/release-lxqt-2-0-0/
[20]: https://discourse.gnome.org/t/gnome-46-3-released/22113
[21]: https://sourceforge.net/projects/openmandriva/files/release/ROME/24.07/
[22]: https://wiki.openmandriva.org/en/distribution/releases/rome/errata
