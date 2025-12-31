[#]: subject: "Debian Embraces Chinese LoongArch Processors with Official Loong64 Support"
[#]: via: "https://itsfoss.com/news/debian-embraces-loongarch-processors/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Debian Embraces Chinese LoongArch Processors with Official Loong64 Support
======

[![Warp Terminal][1]][2]

[Debian][3] has officially promoted loong64 to a supported architecture, making it eligible for inclusion in the upcoming Debian 14 release codenamed " _Forky_ ". The announcement came via the [debian-devel-announce][4] mailing list just over a week ago ( _this Penguin reporter missed it_ ).

With this promotion, **loong64 will receive the same build, release, and security processes as Debian's other primary architectures**. This means users can expect the usual coverage and, eventually, installer support, inclusion in release milestones, and long-term maintenance throughout Debian 14's lifecycle.

For those unfamiliar, `loong64` is the 64-bit architecture associated with [LoongArch][5], an instruction set developed by [Loongson][6], a Chinese processor manufacturer. **The architecture represents an alternative to the dominant x86 and ARM ecosystems.**

The path to official status has been over two years in the making. Back in [August 2023][7], John Paul Adrian Glaubitz announced the initial addition of LoongArch to [Debian Ports][8]. At that time, the team manually bootstrapped roughly 200 packages and set up two build daemons using `qemu-user` emulation.

The original plan involved replacing those emulated [buildds][9] with real Loongson hardware once the port became self-hosting. That transition appears to have been successful, as the architecture has now been moved from the experimental Debian Ports to mainline support.

**While the integration of loong64 is ongoing** , the developers have already manually imported 112 packages from Debian Ports to kickstart the official archive. This was enough to set up a working [chroot][10] and get the first build [daemon][11] running.

The progress has been pretty quick. The first buildd built 300 packages in just the first night. The team expected the full bootstrap to take about a week, so it should be complete by now.

When the bootstrap wraps up and there are enough packages, loong64 will get the same treatment as Debian's other architectures. Same testing process, same quality checks, everything.

* * *

**Suggested Read 📖:** [13 Interesting Distributions Based on Debian Linux][12]

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/debian-embraces-loongarch-processors/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.debian.org/
[4]: https://lists.debian.org/debian-devel-announce/2025/12/msg00004.html
[5]: https://www.loongson.cn/EN/application/list?id=39
[6]: https://www.loongson.cn/EN
[7]: https://lists.debian.org/debian-devel-announce/2023/08/msg00000.html
[8]: https://wiki.debian.org/Ports/loong64
[9]: https://wiki.debian.org/buildd
[10]: https://wiki.debian.org/chroot
[11]: https://en.wikipedia.org/wiki/Daemon_(computing)
[12]: https://itsfoss.com/debian-based-distros/
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-168.png
