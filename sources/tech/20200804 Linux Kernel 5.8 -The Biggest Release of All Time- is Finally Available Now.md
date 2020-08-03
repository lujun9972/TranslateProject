[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Linux Kernel 5.8 “The Biggest Release of All Time” is Finally Available Now)
[#]: via: (https://itsfoss.com/kernel-5-8-release/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

Linux Kernel 5.8 “The Biggest Release of All Time” is Finally Available Now
======

Linux 5.8 is one of the biggest releases of all time as [pointed out by Linus Torvalds][1]. However, unlike other releases, you may not see a lot of eye candy changes for an average user to understand.

Overall, the Linux kernel 5.8 release introduces a bunch of driver support, security improvements, and optimizations.

Just to put it in perspective, Linus Torvalds did mention this with Linux 5.8 RC1 release:

> But again, 5.8 is up there with the best, despite not really having any single thing that stands out. Yes, there’s a couple of big driver changes (habanalabs and atomisp) that are certainly part of it, but it’s not nearly as one-sided as some of the other historical big releases have been.

In this article, let’s take a look at what’s new in Linux Kernel 5.8.

### Linux Kernel 5.8: Key Changes

![][2]

While considering it as one of the biggest releases, it’s obvious to see a lot of technical changes. Here, we will focus on the important highlights that mostly matter to the end-user.

#### Adreno 405 / 640 / 650 GPUs open source driver support

Linux 5.8 involves updates the to the open-source MSM drivers (Freedreno) which now brings support for [Qualcomm’s Adreno][3] 405, 640, and 650 GPUs.

This isn’t something significant for desktop Linux — but you can find these mobile GPUs on some of the latest [SoCs][4] like Snapdragon 855+ and Snapdragon 865 (which you can find on Galaxy S20 smartphone).

#### Improved Radeon Driver support

AMD has been hard at work to improve its GPU support on the latest Linux Kernel 5.8.

Along with some performance improvements, you will also find encrypted vRAMs enabled with the help of TMZ (Trusted Memory Zone) support on AMDGPU kernel driver on Linux 5.8.

Not to forget, the driver also has an improvement for dealing with critical thermal faults. In other words, if your AMD GPU goes above the safe temperature limit, the driver will shut down the GPU to prevent damage to your Graphics Card.

#### Spectre Mitigation Fixes

It’s evident that Intel can’t get enough of security vulnerabilities in its chipsets. However, it looks like there are some important changes made to Linux’s spectre mitigation handling.

I’m not an expert about this – but it looks like the mitigation handling that was implemented impacted AMD CPUs for no reason. Hence, it was necessary for a fix. This change is also being [back ported to stable series][5].

#### Support for POWER10 Processor

POWER10 is an upcoming IMB + OpenPOWER processor to arrive in 2021.

And, it’s going to be manufacturing using a 7 nm process (Intel, come on!) and aims to offer big improvements over POWER9 micro architecture.

#### New Arm SoCs support

While I already mentioned the support for open-source drivers on modern mobile SoCs. But, with Linux 5.8, it looks like there are some new boards (or SoCs) like Realtek RTD1195 supported in this release.

#### Introduces AMD Energy Driver

If you have a Zen/Zen2 AMD CPU, you will be happy to know that with Linux 5.8 release, the AMD Energy Driver is finally in!

This will enable you to get energy reports on per-socket/per-core on Zen/Zen2 CPUs, which you weren’t able to know before. In case you’re wondering, this is useful for the users curious about their CPU power consumption.

#### exFAT Driver Improvements

Even though Linux 5.7 involved the addition of exFAT file-system driver, Samsung has sent some optimization improvements and fixes for it on Linux 5.8.

#### Improved DAX support

If you’re fond of using Intel’s Optane memory to speed things up on your system, the improved DAX code will allow the persistent memory to directly access files without needing the page cache. So, Linux 5.8 will make the best of it.

If you’re curious to learn more about it, I’ll suggest you to go through one of the documentations about [Intel Optane DC persistent memory][6].

#### Improved Thunderbolt support

It looks like with Linux 5.8, we will also see [Thunderbolt][7] support for non-x86 systems as well (ARM support).

In addition to that, you will also notice Thunderbolt support for Intel Tiger Lake.

Of course, there are some other USB improvements as well such as USB Type-C driver updates among the others.

#### Other Changes in Linux Kernel 5.8

Linux Kernel 5.8 is indeed an important release with a lot of driver updates, security improvements, and performance optimizations.

As usual, Phoronix tracks all the detailed reports for every change involved in Linux 5.8. You may refer to their [Linux 5.8 Kernel feature article][8] to dive into more technical details for the changes involved.

### How to get Kernel 5.8?

As we have explained in the past, [most Linux distributions don’t provide the latest kernel][9]. Rolling release [distributions like Arch][10] might have it available soon but stability focused distributions like Debian or Ubuntu won’t make it available for all its users.

This doesn’t mean that you cannot get kernel 5.8 in Ubuntu or Debian. If you really want and if you have intermediate knowledge of the Linux command line, you can [upgrade to the latest mainline Linux kernel in Ubuntu manually][11]. But do that only if you need it and only if you are comfortable doing it. I don’t recommend it for everyone.

**Wrapping Up**

What do you think about Linux Kernel 5.8? Do you think it’s an exciting release given that it is the biggest release of all time?

Feel free to let me know your thoughts in the comments below.

--------------------------------------------------------------------------------

via: https://itsfoss.com/kernel-5-8-release/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://lore.kernel.org/lkml/CAHk-=whfuea587g8rh2DeLFFGYxiVuh-bzq22osJwz3q4SOfmA@mail.gmail.com/
[2]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/kernel-5-8-release.png?ssl=1
[3]: https://en.wikipedia.org/wiki/Adreno
[4]: https://en.wikipedia.org/wiki/System_on_a_chip
[5]: https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.8-x86-urgent-Round-1
[6]: https://software.intel.com/content/www/us/en/develop/articles/introduction-to-programming-with-persistent-memory-from-intel.html
[7]: https://en.wikipedia.org/wiki/Thunderbolt_(interface)
[8]: https://www.phoronix.com/scan.php?page=article&item=linux-58-features&num=1
[9]: https://itsfoss.com/why-distros-use-old-kernel/
[10]: https://itsfoss.com/arch-based-linux-distros/
[11]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
