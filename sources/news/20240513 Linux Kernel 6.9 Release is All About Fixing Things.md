[#]: subject: "Linux Kernel 6.9 Release is All About Fixing Things"
[#]: via: "https://news.itsfoss.com/linux-kernel-6-9-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Kernel 6.9 Release is All About Fixing Things
======
A not-so-interesting, but useful upgrade.
Close on the heels of the [previous][1] kernel release, we now have the new **Linux kernel 6.9** release, which features all kinds of improvements across the board.

As usual, Linus Torvalds had a few things to add:

> Outside of drivers, it's some filesystem fixes (bcachefs still stands
>  out, but ksmbd shows up too), some late selftest fixes, and some core
>  networking fixes.
>
> And I now have a more powerful arm64 machine (thanks to Ampere), so
>  the last week I've been doing almost as many arm64 builds as I have
>  x86-64, and that should obviously continue during the upcoming merge
>  window too.

This is good news for users of the [_ARM64_][2] architecture; a better machine ought to improve how Linus optimizes the kernel for it. That being said, let's see what Linux kernel 6.9 has to offer.

## 🆕 Linux Kernel 6.9: What's New?

![][3]

As a non-LTS release, Linux kernel 6.9 is an important interim release that paves the way for Linux 6.10, for which, the merge window is currently open. Linus already has a few dozen requests in the queue.

Here are the **key highlights** of this release:

  * **AMD Upgrades**
  * **Intel Refinements**
  * **Better ARM Support**



### AMD Upgrades

We start with the newly added **support for AMD Preferred Core** , which will prioritize the use of higher-performing cores for tasks that require more performance.

Other than that, the **FRU Memory Poison Manager** is now included with this kernel release, which allows information on any bad/faulty memory to be carried over across boots, and there is now support for **AMD Secure Nested Paging** (SNP).

### Intel Refinements

On older platforms, there is now **support for Fastboot** , and the x86 CPU topology code was reworked to make way for **better hybrid CPU support**.

Intel's [FRED][4] ( _Flexible Return and Event Delivery_ ) architecture also makes a debut with Linux kernel 6.9, with many patches being made to improve the performance and efficiency of Intel Meteor Lake chips.

### Better ARM Support

We finally have **Rust support for ARM64** , which has paved the path for future Rust-based kernel code to be implemented in this architecture. To complement that, we also have [Rust 1.76.0][5] with this kernel release.

Additionally, there are numerous newly supported hardware, such as **MediaTek MT7981B “Filogic 820”** , **NXP i.MX8DXP** , **ten MediaTek MT8186-based Chromebooks** , **LG Optimus 4X HD** , and more.

### 🛠️ Other Changes & Improvements

Moving on to the other notable changes, we have:

  * Zoned block device and per-file compression support for F2FS.
  * Many improvements for the Intel Xe DRM driver and the various open-source graphics drivers.
  * Faster boots for systems featuring large amounts of RAM ( _read 1 TB or more_ ), specially those using HugeTLB pages.
  * AMD's FreeSync Video mode being retired, seeing that compositors have taken over handling variable refresh rate (VRR).



You can dive into the technical details by going through the [changelog][6]. For a shorter version, you can refer to the [shortlog][7].

## Installing Linux Kernel 6.9

If you are sporting a [rolling-release][8] distro like Arch or Fedora, then you can just wait until this release is made available on the repos.

In the case of other distros, you can either wait for a major release that includes Linux kernel 6.9, or you could follow [our guide][9] to upgrade to the latest mainline Linux kernel on Ubuntu:

![][10]

🚧

We don't recommend manual Linux kernel upgrades unless you really need to fix a specific issue.

You can get started with Linux kernel 6.9 by sourcing the tarball from the [official website][11].

[Linux Kernel 6.9][11]

_💬 What are your thoughts? Use the comment box below to tell us!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-kernel-6-9-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/linux-kernel-6-8-release/
[2]: https://en.wikipedia.org/wiki/AArch64
[3]: https://news.itsfoss.com/content/images/2024/05/linux-kernel-6-9-fixes-2.png
[4]: https://www.intel.com/content/www/us/en/content-details/779982/flexible-return-and-event-delivery-fred-specification.html
[5]: https://blog.rust-lang.org/2024/02/08/Rust-1.76.0.html
[6]: https://cdn.kernel.org/pub/linux/kernel/v6.x/ChangeLog-6.9
[7]: https://lore.kernel.org/lkml/CAHk-=whnKYL-WARzrZhVTZ8RP3WZc24C9_DT7JMJooONNT2udQ@mail.gmail.com/
[8]: https://itsfoss.com/rolling-release/
[9]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[10]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[11]: https://www.kernel.org/
