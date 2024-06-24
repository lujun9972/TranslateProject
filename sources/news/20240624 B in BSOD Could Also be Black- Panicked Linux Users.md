[#]: subject: "B in BSOD Could Also be Black: Panicked Linux Users!"
[#]: via: "https://news.itsfoss.com/black-screen-of-death-linux/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

B in BSOD Could Also be Black: Panicked Linux Users!
======
Linux users, from blue to black screen of death, yes, it is possible!
[![][1]][2]

We are all too familiar with the prospect of [systemd bringing the blue screen of death to Linux][3], with it focusing on boot failures, and other related problems.

Similarly, there's another approach that's [been undertaken][4] with the upcoming Linux kernel 6.10 release, which sees a new DRM panic handler that will promptly show a helpful message when a [kernel panic][5] occurs.

As expected, the general opinion around such implementations appears to be mixed. Some really liked them, while some not so much.

This debate has been reignited thanks to a chain of posts by Red Hat engineer, [Javier Martinez C][6]. who earlier this month showcased a working BSOD implementation using the newly introduced DRM panic handler.

### A Blue Screen of Death: Too Similar to Windows?

![Source: Javier Martinez C.][7]

So, the [original thread][8] on Mastodon showcased an example of how the new DRM panic message could look like, with a familiar blue screen, an error code, and of course, the loveable Tux in ASCII at the top-left. This was being tested on a [BeaglePlay][9].

However, as you can see in the [comment section][10] of Phoronix's initial coverage of it, many people were not happy with the blue nature of it. Someone said that:

> Why does it have to be blue? Don't copy Windows! I'd rather prefer black, with white text.

Naturally, there were also those who said that Windows is not the only one who is entitled to use the color blue for an error screen, with someone else suggesting a more macabre red background and a “ _Penguin skull_ ” to be shown.

In response to all the commotion, Javier [shared][11] another photo a few days later that showcased a black screen of death for Linux on a _SSD1306_ OLED dot matrix display saying “ _KERNEL PANIC! Please reboot yo_ ”, with the rest not fitting into this tiny screen space. _(it would be cool to have this short one though_ 😆).

![Source: Javier Martinez C.][12]

He wrote that:

> It seems that a blue #Linux DRM panic triggered some people, so here is a “Black Screen Of Death” on a #SSD1306 display!

This was expected, if you ask me. As are most things with Linux, you also have the freedom to tweak the DRM panic message screen any way you like. There do happen to be pros who build [Linux from Scratch][13], configuring it to their liking, fine-tuning every fine bit.

Of course, if the majority of the users and developers would rather have a black screen for such error messages, then maybe systemd and Linux kernel could choose to follow suite, offering up black screens of death during critical errors.

Until that happens, those who **want to try this BSOD functionality** , they can do so on Linux kernel 6.10 or later by running the following command:

```

    echo c > /proc/sysrq-trigger

```

**Suggested Read** 📖

![][14]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/black-screen-of-death-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/bsod-linux/
[4]: https://lore.kernel.org/dri-devel/2dc1b7c6-1743-4ddd-ad42-36f700234fbe@linux.intel.com/T/#u
[5]: https://en.wikipedia.org/wiki/Kernel_panic
[6]: https://www.linkedin.com/in/javiermartinezcanillas/
[7]: https://news.itsfoss.com/content/images/2024/06/BSOD_Linux_a.jpg
[8]: https://fosstodon.org/@javierm/112619967725108081
[9]: https://www.beagleboard.org/boards/beagleplay
[10]: https://www.phoronix.com/forums/forum/phoronix/general-discussion/1471143-linux-s-new-drm-panic-blue-screen-of-death-in-action
[11]: https://fosstodon.org/@javierm/112650880236436431
[12]: https://news.itsfoss.com/content/images/2024/06/BSOD_Linux_b.jpg
[13]: https://www.linuxfromscratch.org/
[14]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
