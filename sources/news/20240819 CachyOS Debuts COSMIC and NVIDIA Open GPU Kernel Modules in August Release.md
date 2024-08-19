[#]: subject: "CachyOS Debuts COSMIC and NVIDIA Open GPU Kernel Modules in August Release"
[#]: via: "https://news.itsfoss.com/cachyos-cosmic-debut/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

CachyOS Debuts COSMIC and NVIDIA Open GPU Kernel Modules in August Release
======
CachyOS catches up with the cosmic trend.
[![][1]][2]

CachyOS is a popular [rolling release][3] Arch Linux-based distro which is a good fit for both newbies and experienced Arch users alike.

Months after the [June 2024][4] release, the project's developers have introduced a new **CachyOS August 2024** release, with many useful tweaks, and some good news for users of [NVIDIA][5] GPUs.

Let's check it out. 😃

## 🆕 CachyOS August 2024: What's New?

![][6]

This release comes with **Linux kernel 6.10.5-cachyos** powering it, alongside [KDE Plasma 6.14][7] as the desktop environment for the flagship desktop edition, and [Mesa 24.2.0][8] handling the graphics side of things.

Some **key highlights** of this release include:

  * **NVIDIA Open GPU Kernel Modules**
  * **Inclusion of COSMIC Alpha**
  * **Infrastructure Upgrades**



### NVIDIA Open GPU Kernel Modules

Beginning with this release, CachyOS's hardware detection will automatically use the [recently introduced][9] open-source GPU kernel modules by NVIDIA. Do note that this support is only for GPUs of 20xx series and newer.

To make things even better, the developers **have made the beta version of the NVIDIA 560 driver the default on CachyOS** after a lot of testing. The kernel manager has also been updated to support building of the NVIDIA-open modules.

### Inclusion of COSMIC Alpha

![][10]

The next upgrade is the **adoption of the alpha release of the COSMIC desktop environment** in CachyOS, with the developers following the upstream release for packaging.

I checked out COSMIC in the installer when running a [virtual machine][11], and it seemed to install. But, it didn't play nice post installation, and showed me a black screen on reboot. Bare metal should be a better fit for this.

**Existing users can get COSMIC** by running the following command:

```

    sudo pacman -S cosmic-session

```

This will install the base packages required to run COSMIC, with additional packages to get the Rust-based COSMIC apps such as _cosmic-store_ , _cosmic-text_ , and _cosmic-terminal_.

I highly suggest you go through my [earlier coverage][12] of the COSMIC release on Pop!_OS 24.04 Alpha to learn more about this under-development desktop environment:

![][13]

### Infrastructure Upgrades

The CachyOS team has shared that they now have a new infrastructure sponsor, [CDN77][14], who has equipped them with a global cache [CDN][15], which is set to improve connection speeds for users located around the world.

Now, they are providing **a Cache CDN mirror alongside an Arch Linux mirror** during installation. Mirror ranking has also been tweaked to select up-to-date mirrors, making way for quicker package installations.

There are fallback mirrors hosted by CachyOS and a [Tier 1][16] mirror from Arch Linux in case the primary ones fail for some reason.

### 🛠️ Other Changes and Improvements

To wrap this up, there are some other notable changes you should know about:

  * [libextest][17] was replaced in favor of [libei][18].
  * cachy-chroot now has support for LUKS encryption.
  * The Handheld edition now supports the [ROG Ally X][19].
  * Secure Boot support was improved with the inclusion of a new script and a detailed Wiki [page][20].
  * Hardware detection has been improved thanks to the fixes in PRIME/Hybrid Profile detection.



To dive deeper into this release, you will want to go through the [release blog][21].

## 📥 Download CachyOS

You can download CachyOS from the [official website][22], [mirror][23], or the project's [SourceForge][24] page. There are **two editions on offer,** the Desktop Edition, and the Handheld Edition.

[CachyOS][22]

If you are an **existing user** , then running the following command will get you the CachyOS August 2024 release:

```

    sudo pacman -Syu

```

For more info, the official [upgrade guide][25] is a handy source of information. If interested in the source code, then you can visit the project's [GitHub][26] repo.

_💬 Are you going to try out this release? If you do, please let me know in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/cachyos-cosmic-debut/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/rolling-release/
[4]: https://news.itsfoss.com/cachyos-june-2024-release/
[5]: https://www.nvidia.com/
[6]: https://news.itsfoss.com/content/images/2024/08/CachyOS_August_2024_a.jpg
[7]: https://kde.org/announcements/plasma/6/6.1.4/
[8]: https://docs.mesa3d.org/relnotes/24.2.0.html
[9]: https://developer.nvidia.com/blog/nvidia-transitions-fully-towards-open-source-gpu-kernel-modules/
[10]: https://news.itsfoss.com/content/images/2024/08/CachyOS_August_2024_b.jpg
[11]: https://itsfoss.com/virtual-machine/
[12]: https://news.itsfoss.com/pop-os-24-04-cosmic-alpha/
[13]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[14]: https://www.cdn77.com/
[15]: https://en.wikipedia.org/wiki/Content_delivery_network
[16]: https://archlinux.org/mirrors/status/tier/1/
[17]: https://github.com/Supreeeme/extest
[18]: https://gitlab.freedesktop.org/libinput/libei
[19]: https://rog.asus.com/gaming-handhelds/rog-ally/rog-ally-x-2024/
[20]: https://wiki.cachyos.org/configuration/secure_boot_setup/
[21]: https://cachyos.org/blog/2408-august-release/
[22]: https://cachyos.org/download/
[23]: https://mirror.cachyos.org/ISO/
[24]: https://sourceforge.net/projects/cachyos-arch/files/gui-installer/
[25]: https://wiki.cachyos.org/installation/updating_cachyos/
[26]: https://github.com/cachyos
