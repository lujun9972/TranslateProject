[#]: subject: "36 Years in Making, GNU's Very Own Kernel Project Hurd is Anything But Dead"
[#]: via: "https://itsfoss.com/news/gnu-hurd-progress-report/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

36 Years in Making, GNU's Very Own Kernel Project Hurd is Anything But Dead
======

[![Warp Terminal][1]][2]

At this point, you might think that [GNU Hurd][3] is a mythical beast lost to time, but fret not, it's still around. Speaking at [FOSDEM 2026][4], Samuel Thibault has provided a much-needed progress update.

To the uninitiated, GNU Hurd is a replacement for the [Unix kernel][5], which has been in development since 1990. Unlike Linux's approach, where there's a monolithic kernel, Hurd breaks down components into small, independent servers.

This way, **any changes or major redesigns can be carried out without having to rewrite the whole thing**. You can draw a parallel with how tricky [Linux's rustification][6] has been.

### Still Going Strong

It is now said to be rather stable, with [Debian][7] builds being able to compile about 80% of the archive, and GNOME, KDE, and Xfce all working on it. Guix has also shipped [a Hurd release][8], with some work coming to [Arch Linux][9] and [Alpine Linux][10] as well.

On the software side, _**gcc**_ , _**glibc**_ , _**LLVM**_ , and _**Rust**_ have all added Hurd support upstream, with **64-bit support now working** and a Debian amd64 version bootstrapped.

Similarly, on the hardware side, it supports **SMP ( _multi-core_ )**, with SATA handled by an AHCI driver and USB drives and CDs supported through a [userland][11] translator.

Network drivers have also been ported to userland, replacing the old Linux 2.6.32-based layer. ACPI and PCI access both run in userland too, with PAE support on 32-bit added for memory-hungry builds.

There's KVM/Xen support too, but the performance for it is said to be " _not satisfactory,_ " and initial ARM64 support is in the works.

The **included console is a modular one** , with a server running virtual ttys and gettys and a client handling keyboard, mouse, and VGA. The VGA driver allows it to print kanji and emojis in text mode, with up to 512 dynamic glyphs and double-width character support.

Samuel also shared that:

> The x86_64 port is essentially complete, which mostly required fixing the MIG RPC layer, and telling various software that it exists. To bootstrap the Debian GNU/Hurd x86_64 distribution, many of the crossbuilding, rebootstrapping and build profiles tools were used to make it relatively smooth.
>
> Additionally, the Guix/Hurd distribution is also on its way, as well as an Alpine/Hurd distribution. And more to discover during the talk!

Via: [Phoronix][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/gnu-hurd-progress-report/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.gnu.org/software/hurd/
[4]: https://fosdem.org/2026/schedule/event/7FZXHF-updates_on_gnuhurd_progress_rump_drivers_64bit_smp_software_bootstrapping/
[5]: https://en.wikipedia.org/wiki/Unix
[6]: https://itsfoss.com/news/first-linux-kernel-rust-cve/
[7]: https://www.debian.org/
[8]: https://guix.gnu.org/en/download/latest/#:~:text=GNU%20Guix%20System%20on%20GNU%20Hurd
[9]: https://archlinux.org/
[10]: https://www.alpinelinux.org/
[11]: https://en.wikipedia.org/wiki/User_space_and_kernel_space#:~:text=The%20term%20user,software%2C%20etc.
[12]: https://www.phoronix.com/news/GNU-Hurd-In-2026
