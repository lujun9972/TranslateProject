[#]: subject: "Google Just Extended Linux Kernel Support for Android: This is Good!"
[#]: via: "https://news.itsfoss.com/google-linux-kernel-support/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Google Just Extended Linux Kernel Support for Android: This is Good!
======
Google's move to support the Linux Kernel longer should give Android
users better security.
[![][1]][2]

The Linux kernel is a wonderful thing that powers many things in this tech-driven world that many people often overlook.

You are most likely looking at a rectangular slab of tech in your hand right now, which is probably running [Android][3]. It uses Google's version of a Linux LTS ([long-term support][4]) release as a rock-solid foundation to provide you with a great smartphone experience.

Back in 2023, the maintainers of the Linux kernel decided to [cut short][5] the support period for their LTS kernel releases. They **went from the earlier six-year period, to a shorter two-year period** , after which they would stop pushing bug fixes for it, with an additional year for providing security patches.

The two key reasons behind that move were to handle the crucial issue of maintainer burnout, with the other being that **not many people use older versions of the Linux kernel**.

Back then, we expected systems relying on older Linux kernels to be affected adversely due to that move. Now, it looks like Google is not waiting around to be caught out by a shorter kernel support cycle and has stepped up their game.

### Google Steps Up Support For Android: What to Expect?

![][6]

In a very hush-hush manner, Google has **extended the support period for their stable kernel to four years** , starting with [Linux kernel 6.6][7].

The above table shared by them in their [documentation][8] for ACKs reflects the various EOLs (end-of-life) dates for the many kernels that they support right now, which goes all the way back to 4.19, released back in 2018.

They also mention that:

> ACKs might be supported for longer than the corresponding upstream stable kernel at [kernel.org][9]. In this case, Google provides extended support until the end-of-life (EOL) date shown in this section. When kernels are EOLed, they are no longer supported by Google and devices running them are considered to be vulnerable.

If you were wondering what ACKs are, they stand for “Android common kernels”, which are downstream of Linux kernels, and include dedicated patches for Android that are not seen on mainline Linux maintained by Linus Torvalds.

A longer support time should help Google address bugs, and more importantly, security vulnerabilities, that are a dime a dozen these days, with new ones [popping up][10] every other day.

**Wondering what you as a user should do?** 🤔

It's quite simple really. If you have a device that is still receiving important security updates and major operating system updates, then I highly suggest you keep your devices updated with those.

In addition to that, being aware of what applications you or anyone else using your device installs helps as well. You can never be too careful with things like this.

**Suggested Read** 📖

![][11]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-linux-kernel-support/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.android.com/
[4]: https://itsfoss.com/long-term-support-lts/
[5]: https://news.itsfoss.com/linux-kernel-support/
[6]: https://news.itsfoss.com/content/images/2024/07/ACK_Support_Period.png
[7]: https://news.itsfoss.com/linux-kernel-6-6-release/
[8]: https://source.android.com/docs/core/architecture/kernel/android-common
[9]: https://www.kernel.org/
[10]: https://source.android.com/docs/security/bulletin
[11]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
