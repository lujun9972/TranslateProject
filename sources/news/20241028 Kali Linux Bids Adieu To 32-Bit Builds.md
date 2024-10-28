[#]: subject: "Kali Linux Bids Adieu To 32-Bit Builds"
[#]: via: "https://news.itsfoss.com/kali-linux-32-bit-builds-end/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Kali Linux Bids Adieu To 32-Bit Builds
======
It's time for 32-bit Kali Linux to go.
[![][1]][2]

i386, or [IA-32][3], is the 32-bit version of the [x86][4] instruction set architecture (ISA), which has been around since 1985 when Intel introduced the [80386 microprocessor][5]. It was at the forefront of personal computing for many decades, before [64-bit computing][6] became mainstream.

Over the years, many Linux distributions have moved away from i386/32-bit builds owing to its outdated state considering everyone has 64-bit hardware now, and it appears [Kali Linux][7] has joined that club as well.

📋

I have used the terms i386 and 32-bit interchangeably, it denotes the ISA, not the microprocessor.

### 32-Bit Builds Are No More: What Happened?

![Image: Kali Linux][8]

Recently [announced][9] by the developers, 32-bit builds of the Kali Linux kernel and images have been discontinued, with no new i386 installer images, live images, or pre-built VM images to be released in the future.

The transition has already begun, as today's [weekly builds][10] don't include any 32-bit images, and the forthcoming 2024.4 release is expected to follow suit.

This move was a long time coming, seeing that the last 32-bit CPU models came out back in 2007, and Kali Linux's upstream, Debian, [decided to drop][11] i386 kernel packages late last year.

In the announcement, they added that:

> Kali Linux is based on Debian, so it follows that Kali Linux also drops i386 kernel and images. This is going to be effective for weekly images starting 2024-W44, to be published on Monday 28th of October. It’s already effective for Kali rolling users.

However, they have ensured that **i386 packages will remain in the repositories** , allowing people to run i386 programs on 64-bit ( _amd64_ ) systems without any issues. They are also providing i386 [Docker images][12] for those interested.

_💬 Will you miss 32-bit builds of Kali Linux? Looking to switch due to this? Let me know!_

**Suggested Read** 📖

![][13]

* * *

[Get It's FOSS Plus Membership][14]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/kali-linux-32-bit-builds-end/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/IA-32
[4]: https://en.wikipedia.org/wiki/X86
[5]: https://en.wikipedia.org/wiki/I386
[6]: https://en.wikipedia.org/wiki/64-bit_computing
[7]: https://www.kali.org/
[8]: https://news.itsfoss.com/content/images/2024/10/Kali_Linux_i386_EOL.jpg
[9]: https://www.kali.org/blog/end-of-i386-kernel-and-images/
[10]: https://www.kali.org/get-kali/
[11]: https://lists.debian.org/debian-release/2024/09/msg00220.html
[12]: https://hub.docker.com/r/kalilinux/kali-rolling/tags
[13]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[14]: https://itsfoss.com/#/portal/signup
