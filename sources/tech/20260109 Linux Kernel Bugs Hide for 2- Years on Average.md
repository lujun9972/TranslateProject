[#]: subject: "Linux Kernel Bugs Hide for 2+ Years on Average"
[#]: via: "https://itsfoss.com/news/linux-kernel-bugs-arent-found-for-years/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Kernel Bugs Hide for 2+ Years on Average
======

[![Warp Terminal][1]][2]

It was not too long ago we talked about [the first Rust CVE in the Linux kernel][3], which caused system crashes. That same day, 159 other CVEs were issued for C code. While that shows progress with Rust, it also highlights something more concerning; **the kernel has bugs that hide for years before anyone finds them**.

A research blog published on [Pebblebed][4] demonstrates how bugs often stay hidden for years before they are discovered and fixed.

🚧

Please note that this study talks about bugs of all kinds. Not all bugs are vulnerabilities.

### The Linux Kernel Isn't Perfect

![Source: Jenny Guanni Qu via Pebblebed][5]

[Jenny Guanni Qu][6], a researcher at Pebblebed, **analyzed 125,183 bugs from 20 years of Linux kernel development history** ( _on Git_ ). The findings show that the average bug takes 2.1 years to find. The longest-lived bug, a buffer overflow in networking code, **went unnoticed for 20.7 years**!

The research was carried out by relying on the `Fixes:` tag that is used in kernel development. Basically, when a commit fixes a bug, it includes a tag pointing to the commit that introduced the bug.

Jenny wrote a tool that extracted these tags from the kernel's git history going back to 2005. The tool finds all fixing commits, extracts the referenced commit hash, pulls dates from both commits, and calculates the time frame.

![Example of how the Fixes: tag is used on the left, the dataset parameters used by Jenny on the right.][7]

As for the dataset, it includes over 125k records from [Linux 6.19-rc3][8], covering bugs from April 2005 to January 2026. Out of these, 119,449 were unique fixing commits from **9,159 different authors** , and only 158 bugs had [CVE][9] IDs assigned.

Plus, she found out that **different parts of the kernel show significant variation in how long bugs remain hidden**. [CAN bus][10] drivers have the longest average at 4.2 years, followed by [SCTP][11] networking at 4.0 years. [GPU][12] bugs get caught fastest at 1.4 years, and [BPF][13] bugs are found within 1.1 years.

The research also found that incomplete fixes are common. Someone notices undefined behavior and ships a fix, but the fix does not fully address the problem. In one case, a 2024 fix for _netfilter set field validation_ was incomplete, and a security researcher found a bypass a year later.

Jenny's research goes much deeper than what I covered here. She has also developed an AI model called **VulnBERT** that predicts whether a commit introduces a vulnerability. The detailed blog post linked above includes elaborate technical explanations on that; it is a must-read!

* * *

**Suggested Read 📖:** [_The First Rust CVE in Linux Kernel_][3]

![][14]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/linux-kernel-bugs-arent-found-for-years/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/first-linux-kernel-rust-cve/
[4]: https://pebblebed.com/blog/kernel-bugs
[5]: https://itsfoss.com/content/images/2026/01/linux-kernel-bug-lifetime-distribution-chart.png
[6]: https://github.com/quguanni
[7]: https://itsfoss.com/content/images/2026/01/fixes-tag-usage-example.png
[8]: https://www.phoronix.com/news/Linux-6.19-rc3-Released
[9]: https://www.cve.org/
[10]: https://en.wikipedia.org/wiki/CAN_bus
[11]: https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol
[12]: https://itsfoss.com/news/arch-linux-old-nvidia-gpu-issue/
[13]: https://en.wikipedia.org/wiki/Berkeley_Packet_Filter
[14]: https://itsfoss.com/content/images/icon/android-chrome-512x512-200.png
