[#]: subject: "If You Have an Older NVIDIA GPU on Arch Linux, Your System Might Be Broken"
[#]: via: "https://itsfoss.com/news/arch-linux-old-nvidia-gpu-issue/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

If You Have an Older NVIDIA GPU on Arch Linux, Your System Might Be Broken
======

[![Warp Terminal][1]][2]

[Arch Linux][3] attracts people who want to stay on the bleeding edge of what Linux has to offer. Its adoption has been steadily increasing over the years. [Linux desktop market share][4] data shows Arch ( _and derivatives_ ) usage growing.

[Several derivatives][5] like **CachyOS** , **Manjaro Linux** , **EndeavourOS** , and **SteamOS** have become popular choices, with the latter being Valve's operating system that provides a console-like gaming experience on the Steam Deck handheld.

Arch's rolling release approach usually works well, but [the latest NVIDIA driver update][6] has left some users with broken systems.

### Arch Stops Shipping Drivers for Older NVIDIA GPUs

The distro recently switched to the [NVIDIA 590 driver][7], which dropped support for Pascal ( _GTX 10xx_ ) and older GPUs ( _GTX 900_ ) on Linux. Alongside this, they also transitioned users of NVIDIA 20xx and newer GPUs to [open kernel modules][8].

Explaining why they did this, [Peter Jung][9], one of the package maintainers for Arch Linux, explained that NVIDIA's closed-source modules are not tested as thoroughly as the open kernel modules, which are now recommended for use instead.

But **these new modules don't support older GPUs** released before the RTX 20xx series, and that is a problem for those on such hardware.

If you have a GTX 10xx, GTX 9xx, or older card, updating breaks your graphics, the new driver fails to load, and you get plopped into the [command-line interface][10] (CLI) with no GUI in sight.

To fix this, the Arch Linux developers recommend that you first uninstall the existing NVIDIA packages: `nvidia`, `nvidia-lts`, or `nvidia-dkms`. Then, install `nvidia-580xx-dkms`, which is a community-maintained package from the [Arch User Repository][11] (AUR) that contains the old proprietary driver that works on these GPUs.

If that doesn't suit you, then you could always switch to [nouveau][12], the open source driver for NVIDIA hardware. But expect weaker performance than what you usually get...

**For users of Turing ( _RTX 20xx, GTX 16xx_ ) and newer GPUs**, they will be automatically transitioned to the new open module driver without any manual intervention required on their part.

If you ask me, this situation could have been handled better by allowing more time for people to switch to this new driver handling behavior. But it is what it is.

* * *

**Suggested Read 📖:** [How to Install Arch Linux [Step by Step Guide]][13]

![][14]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/arch-linux-old-nvidia-gpu-issue/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://archlinux.org/
[4]: https://itsfoss.com/linux-market-share/
[5]: https://itsfoss.com/arch-based-linux-distros/
[6]: https://archlinux.org/news/nvidia-590-driver-drops-pascal-support-main-packages-switch-to-open-kernel-modules/
[7]: https://www.nvidia.com/en-us/drivers/details/259267/
[8]: https://github.com/NVIDIA/open-gpu-kernel-modules
[9]: https://gitlab.archlinux.org/archlinux/packaging/packages/nvidia-utils/-/commit/cc7ae772aec0b147f75c0aa4e148f1d97f2c1848
[10]: https://itsfoss.com/rust-alternative-cli-tools/
[11]: https://aur.archlinux.org/packages/nvidia-580xx-dkms
[12]: https://nouveau.freedesktop.org/
[13]: https://itsfoss.com/install-arch-linux/
[14]: https://itsfoss.com/content/images/icon/android-chrome-512x512-167.png
