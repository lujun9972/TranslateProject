[#]: subject: "AMD and Intel improvements take the cake in the Linux kernel 6.11 release"
[#]: via: "https://news.itsfoss.com/linux-kernel-6-11-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

AMD and Intel improvements take the cake in the Linux kernel 6.11 release
======
Linux kernel 6.11 has arrived with plenty of technical changes. Learn
more here.
[![][1]][2]

If you are familiar with the Linux kernel's [release schedule][3], you know that there's usually a new one every two to three months, with long-term support kernels being announced around the end of the year.

So far this year, things have been consistent, with many kernel releases already being made available. The [6.10][4] series was the most recent one. But, now we have yet another Linux kernel release, with Linus Torvalds sharing some of his [thoughts][5] on it:

> The last week was actually pretty quiet and calm, which is nice to
>  see. The shortlog is below for anybody who wants to look at the
>  details, but it really isn't very many patches, and the patches are
>  all pretty small. Nothing in particular stands out - the biggest patch
>  in here is for Hyper-V Confidential Computing documentation.

### Linux Kernel 6.11: What's New?

Seeing that this is **a non-LTS release** , Linux 6.11 is an incremental update that has arrived with many significant improvements.

Let's dive into the **key highlights** of this release:

  * **AMD Improvements**
  * **Intel Upgrades**
  * **Misc Changes**



#### AMD Improvements

![][6]

We start things off with the inclusion of **enablement patches for AMD's upcoming RDNA4 series of GPUs** , which are rumored for a late 2024 or early 2025 launch. The drivers have already been enabled by default, making it a positive sign for those considering using RDNA4 GPUs on Linux.

On the CPU side, there are patches that introduce support for [Core Performance Boost][7] in the AMD P-State CPU frequency scaling driver and [Fast CPPC][8]; enabling users to make the most out of their Ryzen processors.

#### Intel Upgrades

![][9]

Similarly, on the Intel side, there has been work on **preparing initial support for the upcoming Battlemage GPU series** , with the Intel Xe graphics driver receiving a host of fixes.

Some of those include things like simplified _HWMon_ code, improved _forcewake_ behavior, a fix for an out-of-bounds array access issue, and [more][10]. They have also put out something called “ _Hardware Replay_ ”, which is supposed to help with GPU debugging.

For CPUs, Intel has worked on offering “ _Performance Limit Reason_ ” (PLR), which will show helpful information in cases where the CPU was downclocked or was running at a lower performance level than normal.

Last but not least, there's the introduction of **initial audio support for the Panther Lake series of CPUs** and [perf][11] support for Arrow Lake and Lunar Lake processors.

#### Miscellaneous Changes

There are a few other notable changes that you should know about:

  * Better support for the LoongArch CPU architecture.
  * The DRM Panic handler can now show a monochrome logo.
  * Faster [AES-GCM][12] performance on both Intel and AMD chips.
  * RISC-V gets better on Linux, with support for [NUMA][13] on ACPI-based systems and new [ISA][14] extensions.



### Installing Linux Kernel 6.11

As usual, if you are running a [rolling-release][15] distribution, you should be receiving this kernel release earlier than users of other distros.

To be on the safe side, wait for your distribution to make it available via an update. If you have an LTS version of the distro, you will not receive this kernel update.

For users on Ubuntu who can't wait, they can follow [our guide][16] for upgrading to the latest mainline Linux kernel. Do keep in mind that **upgrading to a newer Linux kernel is risky** ; always back up your data before proceeding.

The Linux kernel 6.11 tarball can be downloaded from the [official website][17].

[Linux Kernel 6.11][17]

**Suggested Read** 📖

![][18]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-kernel-6-11-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/linux-kernel-release-support/
[4]: https://news.itsfoss.com/linux-kernel-6-10-release/
[5]: https://lore.kernel.org/lkml/CAHk-=whVpSHw9+4ov=oLevfv8sPYbh59T_9VKif-6Vqkr41jQA@mail.gmail.com/
[6]: https://news.itsfoss.com/content/images/2024/09/linux-6-11-amd.png
[7]: https://en.wikipedia.org/wiki/AMD_Turbo_Core
[8]: https://lore.kernel.org/linux-pm/d8de3761-6fa1-477e-8ed8-71abf115eb60@amd.com/
[9]: https://news.itsfoss.com/content/images/2024/09/linux-6-11-intel.png
[10]: https://lore.kernel.org/dri-devel/ZoROvquFrTFhk3Pb@intel.com/
[11]: https://perf.wiki.kernel.org/index.php/Tutorial
[12]: https://cryptosys.net/pki/manpki/pki_aesgcmauthencryption.html
[13]: https://en.wikipedia.org/wiki/Non-uniform_memory_access
[14]: https://en.wikipedia.org/wiki/Instruction_set_architecture
[15]: https://itsfoss.com/rolling-release/
[16]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[17]: https://www.kernel.org/
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
