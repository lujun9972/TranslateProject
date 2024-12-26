[#]: subject: "Serpent OS Gets an Alpha Release Right Before 2024 Ends"
[#]: via: "https://news.itsfoss.com/serpent-os-alpha-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Serpent OS Gets an Alpha Release Right Before 2024 Ends
======
Serpent OS is an interesting release to look forward to in 2025.
[![][1]][2]

The Linux ecosystem is a genuinely innovative space, where we have countless distributions. We have the popular ones like Ubuntu, Debian, Fedora, Arch Linux, and their derivatives.

On the other hand, we have [independent options][3] like NixOS, Gentoo Linux, and Slackware.

A few months ago, we took a look at the [pre-alpha release][4] of a new independent distro called Serpent OS that performed quite well for an early build. It is a distro that focuses on being modern, minimal, and developer-friendly with its unique tooling.

As 2024 comes to an end, its developers have introduced an alpha release with a [recent announcement][5] that offers many notable refinements.

Let's dive in. 😃

### Serpent OS Alpha: What to Expect?

![Serpent OS Alpha running a pre-release version of COSMIC.][6]

Powered by **Linux kernel 6.12.6** , Serpent OS Alpha comes loaded with many updated packages like Firefox 133.0.3, LLVM 18.1.8, GNOME 47.2, and COSMIC 1.0.0_alpha4.

Similarly, key components of the distro were replaced with **Rust-based alternatives** such as [uutils coreutils][7], [Sudo-rs][8], [ntpd-rs][9], and curl being built with [Rustls][10] support. Users can now easily download [Steam][11] from the Serpent OS repository, too.

The alpha release also debuts some **new hardware support** , with patches being included for ASUS and Microsoft Surface devices and the arrival of NVIDIA drivers ([ _open GPU kernel modules_][12]) in the repositories.

In the tooling department, [lichen][13] installer now features a revamped UI with the ability to pick _XFS_ , _ext4_ , or _F2FS_ as the root filesystem. The [moss][14] package manager receives major updates, such as the _/usr_ directory being replaced during system upgrades to ensure a more reliable upgrade process.

And, finally, the [blsforme][15] boot management tool now supports drop-in command-line snippets for kernel parameters, allowing easy boot entry changes by the user.

The developers mention that **they are very eager to grow Serpent OS's community and contributor base** as they enter an important phase in development. Following this, they want to focus on improving/creating documentation and continue their work on improving tooling.

### 📥 Get Serpent OS Alpha

You can take Serpent OS Alpha for a run on a [virtual machine][16] by downloading either the GNOME Edition or the COSMIC Edition from the [official website][17]. Just ensure that you have enabled EFI and 3D acceleration before proceeding.

If you run into any issues or just want to provide feedback, then you can visit the project's [GitHub][18] repo.

[Serpent OS Alpha][17]

**Suggested Read** 📖

![][19]

* * *

[Get It's FOSS Plus Membership][20]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/serpent-os-alpha-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/independent-linux-distros/
[4]: https://news.itsfoss.com/serpent-os-alpha/
[5]: https://serpentos.com/blog/2024/12/23/serpent-os-enters-alpha/
[6]: https://news.itsfoss.com/content/images/2024/12/Serpent_OS_Alpha_COSMIC.jpg
[7]: https://github.com/uutils/coreutils
[8]: https://github.com/trifectatechfoundation/sudo-rs
[9]: https://github.com/pendulum-project/ntpd-rs
[10]: https://github.com/rustls/rustls
[11]: https://store.steampowered.com/
[12]: https://github.com/NVIDIA/open-gpu-kernel-modules
[13]: https://github.com/serpent-os/lichen
[14]: https://github.com/serpent-os/tools
[15]: https://github.com/serpent-os/blsforme
[16]: https://itsfoss.com/virtual-machine/
[17]: https://serpentos.com/download/
[18]: https://github.com/serpent-os/recipes/issues
[19]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[20]: https://itsfoss.com/#/portal/signup
