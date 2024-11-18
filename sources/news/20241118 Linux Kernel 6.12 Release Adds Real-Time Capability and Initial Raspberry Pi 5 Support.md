[#]: subject: "Linux Kernel 6.12 Release Adds Real-Time Capability and Initial Raspberry Pi 5 Support"
[#]: via: "https://news.itsfoss.com/linux-kernel-6-12/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Kernel 6.12 Release Adds Real-Time Capability and Initial Raspberry Pi 5 Support
======
Linux Kernel 6.12 finally brings in real-time computing capabilities to
the mainline.
[![][1]][2]

Every two or three months, we get a new kernel release with numerous improvements and Linus's thoughts on it.

Now is the time for a brand-new release, i.e., **Linux kernel 6.12**.

It brings in plenty of interesting changes, and other refinements. And, I am sure, you will find some new feature changes very cool!

As usual, Linus Torvalds had something to [add][3]:

> No strange surprises this last week, so we're sticking to the regular
>  release schedule, and that obviously means that the merge window opens
>  tomorrow. I already have two dozen+ pull requests in my mailbox, kudos
>  to all the early birds.

### Linux Kernel 6.12: What's New?

For starters, this is expected to be a [Long-Term Support][4] (LTS) release that will remain supported for two years, until 2026. The various distribution maintainers can choose to extend support for the kernel by backporting patches or adding new ones.

Let me dive in to the **key highlights** of this release:

  * **Real-time PREEMPT_RT**
  * **Intel Improvements**
  * **Better Laptop Support**
  * **AMD & RISC-V Upgrades**



#### Real-Time PREEMPT_RT

![][5]

The support for PREEMPT_RT in the mainline kernel has been in the making for more than a decade now, and it finally saw the light with the Linux kernel 6.12 release.

In simpler terms, it is a technical improvement that should give you a better response time for the tasks you run, and boost the performance overall.

Of course, it is tough for an end-user to notice the difference; however, this makes the Linux kernel's real-time computing capabilities complete, and more enterprise-grade for factories, healthcare, telco, and automotive industries.

And, this improvement is ready for ARM64, RISC-V, and X86/X86_64 as well.

In case you did not know, Canonical managed to bring this a little early with its [Real-time Ubuntu][6] offering. You can go through the official blog posts on it to learn more about real-time Linux:

![][7]

#### Intel Improvements

![][8]

Introduced as part of this release is support for Intel [uncore][9] and power events for Arrow Lake and Lunar Lake, with additional improvements for hybrid P/E-core handling for some Lunar Lake processors.

There are also some updates for the [perf][10] subsystem, such as per-PMU context rescheduling for improved single-[PMU][11] performance, a fix for a long-standing bug, and implementation of [RCU][12]-protected hot path optimizations for improved performance.

Furthermore, Intel has started **initial enablement work for the upcoming Panther Lake and Diamond Rapids Xeon processors** , adding the model numbers to the kernel, and introducing HDMI support for Panther Lake.

On the graphics side, Linux 6.12 enables [Xe2][13] and Battlemage GPUs by default, with the Intel graphics driver now reporting the fan speed of GPUs via HWMON.

#### Better Laptop Support

![][14]

Similarly, there are many updates for laptops in this kernel release. There is now the ASUS WMI driver for supporting fan profiles on [Vivobook][15] laptops, the ThinkPad ACPI driver for fan control on the [ThinkPad Edge E531][16], and extended battery configuration support for recent Dell laptops.

I am particularly looking forward to the Dell upgrade, as I don't have to go into the BIOS to change between the various battery modes on my laptop anymore.

There's also better support for LG and Panasonic laptops. You can learn more about these laptop upgrades in the [GIT pull][17].

#### AMD & RISC-V Upgrades

AMD's engineers have been busy working on RDNA 4 hardware support, alongside new things like OverDrive overclocking for SMU 14.x hardware, better support for AMD Instinct accelerators, and various graphics command processor padding optimizations.

For RISC-V, there is now support for reporting generic CPU vulnerabilities to userspace, IP-triggered CPU backtracing, Svvptc extension, and the removal of the size limit on the XIP kernel.

#### Miscellaneous Changes

Some other notable changes include:

  * Initial support for the [Raspberry Pi 5][18].
  * Further enablement work for Intel's [CXL][19].
  * Improved driver for Wacom drawing tablets.
  * Enhanced KVM virtualization for LoongArch CPUs.
  * Minor performance optimizations and fixes for Btrfs.
  * Optional support for displaying a QR code ( _Rust-based_ ) during kernel panic.



### Installing Linux Kernel 6.12

Users of [rolling release][20] distributions will be among the first ones to receive this kernel release on their systems. Others, including the ones running LTS versions of a distribution, will have to wait before their distro offers it as part of a point release.

If you can't wait, then we have a [detailed guide][21] on migrating to the latest mainline Linux kernel on Ubuntu. Back up your data before proceeding.

The tarball for Linux kernel 6.12 can be sourced from the [official website][22].

[Linux Kernel 6.12][22]

**Suggested Read** 📖

![][23]

* * *

[Get It's FOSS Plus Membership][24]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-kernel-6-12/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://lore.kernel.org/lkml/CAHk-=wgtGkHshfvaAe_O2ntnFBH3EprNk1juieLmjcF2HBwBgQ@mail.gmail.com/T/#u
[4]: https://itsfoss.com/long-term-support-lts/
[5]: https://news.itsfoss.com/content/images/2024/11/linux-6-12-rt.png
[6]: https://ubuntu.com/real-time
[7]: https://assets.ubuntu.com/v1/f38b9c7e-COF%20apple-touch-icon.png
[8]: https://news.itsfoss.com/content/images/2024/11/linux-6-12-intel.png
[9]: https://en.wikipedia.org/wiki/Uncore
[10]: https://perfwiki.github.io/main/
[11]: https://cloud.google.com/compute/docs/pmu-overview
[12]: https://en.wikipedia.org/wiki/Read-copy-update
[13]: https://www.intel.com/content/www/us/en/content-details/824434/2024-intel-tech-tour-xe2-and-lunar-lake-s-gpu.html
[14]: https://news.itsfoss.com/content/images/2024/11/linux-6-12-laptop.png
[15]: https://www.asus.com/laptops/for-home/vivobook/
[16]: https://psref.lenovo.com/syspool/Sys/PDF/withdrawnbook/ThinkPad_E531_WE.pdf
[17]: https://lore.kernel.org/lkml/dede57b5-3ef2-4451-a496-537f3c05a1d6@redhat.com/
[18]: https://news.itsfoss.com/raspberry-pi-5/
[19]: https://en.wikipedia.org/wiki/Compute_Express_Link
[20]: https://itsfoss.com/rolling-release/
[21]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[22]: https://www.kernel.org/
[23]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[24]: https://itsfoss.com/#/portal/signup
