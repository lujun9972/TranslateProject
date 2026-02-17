[#]: subject: "Someone Just Made an Immutable Gentoo-Based Distro Tailored for Gaming"
[#]: via: "https://itsfoss.com/matrixos/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Someone Just Made an Immutable Gentoo-Based Distro Tailored for Gaming
======

[![Warp Terminal][1]][2]

[Sabayon Linux][3] was a Gentoo-based distribution that existed from the mid-2000s until 2019. It aimed to make Gentoo accessible to regular users without the usual compilation headaches.

Created by [Fabio Erculiani][4], Sabayon offered pre-built binaries through its Entropy package manager. This let users skip the hours of compiling while still getting the Gentoo experience.

Now Fabio [has shared][5] that he's working on a new immutable, atomic Linux distro called **matrixOS**. Like Sabayon, it's also based on Gentoo.

🚧

__The developer warns that this is__ _****a hobby project****_ __specifically created for__ [__homelab__][6] __setups, not for production machines.__

### matrixOS: Overview ⭐

The project's motto is " _emerge once, deploy everywhere_." In Gentoo, [emerge][7] compiles packages from source on practically every machine you set up. matrixOS remedies this by building once and distributing binaries, so you skip the compilation wait entirely.

Plus, it uses [OSTree][8] for atomic upgrades. Your system either updates completely or not at all. **The base is read-only** , which prevents accidental breakage.

Gaming is also one of its priorities, with the latest [Mesa][9] and [NVIDIA][10] drivers handling AMD and NVIDIA GPUs, so graphics work right away without you needing to go looking for drivers.

Cooling management is handled by [coolercontrold][11] and [liquidctl][12], and the filesystem runs btrfs on both `/boot` and `root` with zstd compression. The root partition auto-resizes on first boot and NTFS drives work using the [NTFSPlus][13] driver.

**SecureBoot support is built in** with certificates you can enroll directly in UEFI BIOS or through Shim MOK enrollment at first boot.

Looking ahead, the project aims to implement proper CI/CD pipelines and testing workflows, rewrite the core tooling in Go ( _replacing the current bash scripts_ ), and migrate to [bootc][14] or build a wrapper on top of OSTree with [Unified Kernel Image][15] (UKI) support.

### A Quick Look 😶‍🌫️

![matrixOS' GNOME implementation looks slick.][16]

Seeing that matrixOS is an experimental distro, I ran it as a virtual machine using [Virtual Machine Manager][17]. Right away, I found the GNOME interface familiar, but with a Windows-like taskbar at the bottom.

I could access pinned apps, notifications, and the quick-settings menu from here, with a handy button on the far-right letting me focus on the desktop when multiple app windows were open.

![][18]

**Speaking of apps** , there are plenty of useful ones included, like [Steam][19] for gaming, [Btop][20] for system monitoring, [Google Chrome][21] for browsing, and [gedit][22] for text editing. Classic games like Mahjong and Chess are also pre-installed.

Likewise, the distro ships with [Google Antigravity][23] for AI-assisted coding, and there's built-in support for [GNOME Shell extensions][24] if you want to further customize the desktop to your liking.

![matrixOS gives you many ways to install new apps!][25]

_Flatpak_ , _Snap_ , and _Docker_ **are all pre-configured and ready to use** , so you have multiple options for installing apps. GNOME Software ties it all together with a simple interface for browsing and fetching applications without [you needing to touch the terminal][26].

### Grab an Image 📥

matrixOS comes in [three variants][27]: _Bedrock_ , _GNOME_ , and _Server_. Each is available in `raw` for flashing to drives and `qcow2` for running on [virtual machines][28].

The distro **requires UEFI to boot** , so legacy BIOS systems won't work. For logging in, the default password is " _matrix_ ," and the source code lives on [GitHub][29] for people interested in contributing or building from source.

[matrixOS][27]

* * *

**Suggested Read 📖:** [_7 Best Gentoo-Based Linux Distributions_][30]

![][31]

--------------------------------------------------------------------------------

via: https://itsfoss.com/matrixos/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://en.wikipedia.org/wiki/Sabayon_Linux
[4]: https://www.linkedin.com/in/fabio-erculiani-b154b74/
[5]: https://www.phoronix.com/news/Sabayon-Linux-To-matrixOS
[6]: https://itsfoss.com/tag/homelab/
[7]: https://wiki.gentoo.org/wiki/Emerge
[8]: https://ostreedev.github.io/ostree/
[9]: https://mesa3d.org/
[10]: https://www.nvidia.com/en-us/drivers/
[11]: https://docs.coolercontrol.org/
[12]: https://github.com/liquidctl/liquidctl
[13]: https://itsfoss.com/ntfsplus/
[14]: https://bootc-dev.github.io/bootc/
[15]: https://uapi-group.org/specifications/specs/unified_kernel_image/
[16]: https://itsfoss.com/content/images/2026/02/matrixos-desktop-view.jpeg
[17]: https://virt-manager.org/
[18]: https://itsfoss.com/content/images/2026/02/matrixos-pre-installed-apps.jpeg
[19]: https://store.steampowered.com/
[20]: https://www.youtube.com/watch?v=ZXClWDkOH3Q
[21]: https://www.google.com/chrome/
[22]: https://itsfoss.com/gedit-tweaks/
[23]: https://antigravity.google/
[24]: https://itsfoss.com/gnome-shell-extensions/
[25]: https://itsfoss.com/content/images/2026/02/matrixos-snap-flatpak-docker-1.png
[26]: https://itsfoss.com/no-longer-need-terminal/
[27]: https://images.matrixos.org/index.html
[28]: https://itsfoss.com/virtual-machine/
[29]: https://github.com/lxnay/matrixos
[30]: https://itsfoss.com/gentoo-based-distros/
[31]: https://itsfoss.com/content/images/icon/android-chrome-512x512-282.png
