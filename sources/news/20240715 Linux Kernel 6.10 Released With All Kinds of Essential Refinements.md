[#]: subject: "Linux Kernel 6.10 Released With All Kinds of Essential Refinements"
[#]: via: "https://news.itsfoss.com/linux-kernel-6-10-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Kernel 6.10 Released With All Kinds of Essential Refinements
======
Linux Kernel 6.10 has landed!
[![][1]][2]

Every new Linux kernel release features various improvements and feature additions that make it better than the previous release, while many users don't really run the latest kernel, it's a good indicator of how development is progressing.

Since the [last one][3], we now have a new **Linux kernel 6.10** release to check out, and, as usual, Linus Torvalds had [something to say][4]:

> So the final week was perhaps not quote as quiet as the preceding
>  ones, which I don't love - but it also wasn't noisy enough to warrant
>  an extra rc. And much of the noise this last week was bcachefs again
>  (with netfs a close second), so it was all pretty compartmentalized.

### Linux Kernel 6.10: What's New?

This goes without saying, but this is **a non-LTS release** , and it may be included on upcoming distro releases like Ubuntu 24.10 and Fedora 41, but, you don't need to think about it now.

Here are some **key highlights** that we will be diving into with this article:

  * **AMD Upgrades**
  * **Intel Refinements**
  * **Storage Improvements**
  * **Rust Support on RISC-V**



#### AMD Upgrades

![][5]

Thanks to [the patches][6] sent out back in May, there is now **support for newer AMD GPUs on the** [**RISC-V**][7] **platform**. Then there's the **initial perf tool event support for the upcoming AMD Zen 5 processors** , that allows for getting information like L1/L2 cache activity, branch prediction, and a few other metrics.

Developers also got in some refinements for the [AMDKFD][8] kernel compute driver that is used by their [ROCm][9] open-source software stack, enabling better handling of memory limitations on AMD APUs.

#### Intel Refinements

The Intel P-State driver has been [improved][10] to consistently update CPU frequency, when [Turbo Boost][11] is disabled, and work has been done to introduce support for Adaptive Sync SDP.

There are niceties for the [upcoming][12] Battlemage series of GPUs too, with there now being audio support via the HDMI interface, and various refinements being made to their version of the Sound Open Firmware ([SOF][13]) stack.

**On the networking side of things** , there's new support too. There is now support for the PFCP filter with Intel wired network drivers, Intel Blazarl and Filmore Peak2 in the Bluetooth driver, and BZ-W devices with the Intel IWLWIFI driver.

#### Storage Improvements

Building on the already existing Bcachefs support, Linux kernel 6.10 features many safety-focused fixes and improvements for it, with initial preparatory work for online fsck functionality.

For EROFS, its **LZ4 code was improved for working more reliably on large server deployments** with many CPU cores. Similarly, support for Zone Write Plugging ([ZWP][14]) was introduced to substantially increase the performance of zoned storage devices.

#### Rust Support on RISC-V

![][15]

The push for improving Linux kernel's compatibility with the RISC-V platform has been at an all-time high, with this release featuring support for Rust on the popular RISC-V architecture.

Moreover, there's now support for changing the boot image compression with options ranging from LZ4, BZ2, LZO, LZMA, LZ4, and Zstd. We also get initial support for the [Milk-V Mars][16].

**To wrap this up** , there are a few other changes, like the inclusion of the open-source Panthor DRM driver for **providing support for newer ARM Mali GPUs** , and the Qualcomm MSM driver now supporting the upcoming Snapdragon X Elite platform.

### Installing Linux Kernel 6.10

Users of [rolling-release][17] distros like Arch Linux will get this kernel sooner than others. For other distros, you will have to wait for a major release that may or may not include this release.

If you can't wait, then [our guide][18] for upgrading to the latest mainline Linux kernel on Ubuntu is a must-read:

![][19]

🚧

Don't perform a manual Linux kernel upgrade, unless you are absolutely certain that you want one. Back up your data before you start.

You can source the Linux kernel 6.10 tarball from the [official website][20].

[Linux Kernel 6.10][20]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-kernel-6-10-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/linux-kernel-6-9-release/
[4]: https://lore.kernel.org/lkml/CAHk-=wjV_O2g_K19McjGKrxFxMFDqex+fyGcKc3uac1ft_O2gg@mail.gmail.com/T/#u
[5]: https://news.itsfoss.com/content/images/2024/07/linux-6-10-gpu.png
[6]: https://lore.kernel.org/lkml/20240522173553.4653fabdd1f4d9825f38e0ae@linux-foundation.org/
[7]: https://riscv.org/
[8]: https://github.com/ROCm/ROCK-Kernel-Driver
[9]: https://www.amd.com/en/products/software/rocm.html
[10]: https://lore.kernel.org/lkml/CAJZ5v0hDjPb8n5wQODb==QMvp7ipEVpRoSqJ6pTii=_6XvRwEw@mail.gmail.com/
[11]: https://www.intel.com/content/www/us/en/gaming/resources/turbo-boost.html
[12]: https://www.tomshardware.com/pc-components/gpus/intel-next-gen-arc-battlemage-gpu-lineup
[13]: https://www.sofproject.org/
[14]: https://patchwork.kernel.org/project/linux-block/cover/20240202073104.2418230-1-dlemoal@kernel.org/#25695123
[15]: https://news.itsfoss.com/content/images/2024/07/linux-6-10-rust.png
[16]: https://milkv.io/mars
[17]: https://itsfoss.com/rolling-release/
[18]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[19]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[20]: https://www.kernel.org/
