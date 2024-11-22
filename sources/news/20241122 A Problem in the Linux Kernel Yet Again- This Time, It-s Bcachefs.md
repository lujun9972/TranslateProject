[#]: subject: "A Problem in the Linux Kernel Yet Again: This Time, It's Bcachefs!"
[#]: via: "https://news.itsfoss.com/linux-kernel-bcachefs/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A Problem in the Linux Kernel Yet Again: This Time, It's Bcachefs!
======
Some issues with the developer of bcachefs in the Linux Kernel
community. Maybe, it's just being overblown? What do you think?
[![][1]][2]

2024's been an interesting year for the Linux kernel, more so in the final months when we saw the [expulsion of Russian maintainers][3] over compliance requirements, and then a subsequent move by Russia to [build its own Linux community][4].

Linux kernel development is no stranger to a few controversies here and there, but geopolitics affecting their work was a surprise indeed.

Unfortunately, something else has happened now that involves [Bcachefs][5], the copy-on-write (COW) filesystem for Linux that focuses on reliability and being a robust alternative to ZFS and Btrfs.

### What's Going On With Bcachefs?

![Source: Kent Overstreet][6]

Kent Overstreet, the creator of Bcachefs, has put out [a blog][7] detailing **how the future of Bcachefs in the Linux kernel looks uncertain** , as Linus Torvalds has rejected a pull from him for the upcoming Linux 6.13, citing “ _an open issue with the CoC board_ ”.

If you didn't know, the Linux kernel CoC committee ( _mentioned as “board” above_ ) is tasked with enforcing the [Code of Conduct][8] ( _CoC_ ) that applies to the project, both in project spaces and in the public. The latter is applicable when an individual is publicly representing the project or the community as a whole, including on social media or online/offline events.

The consensus is that a recent [offensive reply][9] ( _back in September_ ) by Kent to Linux [memory management][10] (MM) developer, [Michal Hocko][11] is behind the suspension. As you can see below, Kent was not happy with how Michal was handling things related to _PF_MEMALLOC_NORECLAIM_.

![The offending reply by Kent Overstreet and a following post by Shuah Khan.][12]

In subsequent replies, Kent was asked by [Shuah Khan][13] of the Linux kernel CoC committee to not use such language, and to adhere to the Code of Conduct. To that, Kent responded that he had [worked this out][14] with Michal privately, with the CoC committee receiving the copies of the interactions.

However, Shuah [didn't let it go][15], asserting that he had to apologize. Consequently, there has been plenty of discussion over this, with Kent refusing to apologize publicly.

### What Happens Now?

![][16]

All of this seems to have been taken up a notch by the [formalized CoC enforcement policy][17] that was published on November 14, 2024. It expands on what kind of actions might be taken in cases of unacceptable behavior.

There are **provisions on it that can be used against offenders**. With a public apology by the offender being the first one. If an offender doesn't do that, then a ban from participating in kernel development, either for a short period or a full kernel development cycle, could be handed out.

In such a case, the offender may be required to publicly apologize to get back in, but that is not a mandatory requirement. The CoC committee has the final say in that.

Kent's blog appeared a few days after the publishing of the policy, so it looks like this is likely to be a drawn-out dispute. In the blog, he goes on to share that **his reply was not meant to be malicious or personal** , and things like this happen when developers get into technical arguments.

As for the CoC's handling of the situation ( _via Shuah_ ), many Linux kernel maintainers, including Kent, are unhappy with how heavy-handed the interactions have been, with CoC enforcement also being brought into question.

If you are interested in reading the ongoing conversation surrounding this, then you can go through the [original thread][18] that is at the core of it all.

In the end, some questions remain: _What will happen to the Bcachefs implementation in the mainline Linux kernel? Will it stay or go away? Is this a temporary suspension for Kent Overstreet, or a more permanent one?_

For answers to all that, we have to wait and see what happens.

_💬 Tell me what you think of this situation in the comments below!_

**Suggested Read** 📖

![][19]

* * *

[Get It's FOSS Plus Membership][20]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-kernel-bcachefs/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/russian-linux-maintainers-geopolitics/
[4]: https://news.itsfoss.com/russia-linux-community/
[5]: https://bcachefs.org/
[6]: https://news.itsfoss.com/content/images/2024/11/Bcachefs_Linux_Kernel_-fiasco_a.png
[7]: https://www.patreon.com/posts/116412665
[8]: https://docs.kernel.org/process/code-of-conduct.html
[9]: https://lore.kernel.org/all/citv2v6f33hoidq75xd2spaqxf7nl5wbmmzma4wgmrwpoqidhj@k453tmq7vdrk/#:~:text=Michal%2C%20if%20you,with%20this%20shit.
[10]: https://www.kernel.org/doc/html/v5.1/admin-guide/mm/index.html
[11]: https://lwn.net/Articles/684487/
[12]: https://news.itsfoss.com/content/images/2024/11/Bcachefs_Linux_Kernel_-fiasco_b.png
[13]: https://www.linkedin.com/in/shuah-khan/
[14]: https://lore.kernel.org/all/vvulqfvftctokjzy3ookgmx2ja73uuekvby3xcc2quvptudw7e@7qj4gyaw2zfo/t/#u:~:text=I%20believe%20Michal%20and%20I%20have%20more%20or%20less%20worked%20this%20out%20privately%20(and%0Ayou%20guys%20have%20been%20copied%20on%20that%20as%20well).
[15]: https://lore.kernel.org/all/vvulqfvftctokjzy3ookgmx2ja73uuekvby3xcc2quvptudw7e@7qj4gyaw2zfo/t/#u:~:text=Thank%20you%20for%20updating%20us%20on%20the%20behind%20the%20scenes%20work,discussions.%0A%0Athanks%2C%0A%2D%2D%20Shuah%20(On%20behalf%20of%20the%20Code%20of%20Conduct%20Committee)
[16]: https://news.itsfoss.com/content/images/2024/11/Bcachefs_Linux_Kernel_-fiasco_d.png
[17]: https://lore.kernel.org/lkml/20241114205649.44179-1-skhan@linuxfoundation.org/
[18]: https://lore.kernel.org/all/vvulqfvftctokjzy3ookgmx2ja73uuekvby3xcc2quvptudw7e@7qj4gyaw2zfo/t/
[19]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[20]: https://itsfoss.com/#/portal/signup
