[#]: subject: "This Project Lets You Run Linux as an App on Android"
[#]: via: "https://news.itsfoss.com/lindroid/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Project Lets You Run Linux as an App on Android
======
Linux can run in all forms and sizes. And, that's true.
[![][1]][2]

There's no denying that [Android][3] is the most popular open-source operating system in the world, ( _sorry Arch Linux users_ ) that uses a highly customized version of the Linux kernel to provide users with a powerful smartphone experience.

Of course, not everyone likes the “ _Google_ ” aspect of Android, and usually opt for [De-Googled alternatives][4] like LineageOS, CalyxOS, etc.

However, in a recent announcement, two developers, [Erfan Abdi][5] and [Luka Panio][6] introduced a very interesting project called “ **Lindroid** ”, which aims to let users run Linux in “ **a new way on Android devices** ”.

### Project Lindroid: What to Expect?

![][7]

With this, users can run various Linux distributions on native hardware, on their Android installation, with the lead developer, Erfan, calling it “ _a reverse Waydroid_ ”.

As you can see above, that's [Debian 12][8] running on a Xiaomi Pad 6 equipped with LineageOS, showing off how Lindroid makes it effortless to run Linux distros on native hardware.

The default/recommended compositor for Lindroid is [KWin][9], with **Wayland enabled by default** , and experimental support for X11.

During the launch, Erfan added that:

> My personal goal is to make Linux using convenient for everyone and hope to see more love, contribution and devs in Linux mobile community in future🙏🙏

He also shared many impressive features of Lindroid. We start with **the multi input and multi display support** , which Erfan showed off:

![][10]

The video shows how effortless the switch is, with little to no lag visible during the transition. He also [added][11] that it's also **compatible with Android's desktop mode** , which, by the way, is [set to receive a revamp][12] in the upcoming Android 15 release.

You are maybe wondering; **What about running apps using Lindroid?**

Well, the developers have ensured that it doesn't fall short in that department by **implementing hardware acceleration**. It was made possible using “[ _libhybris_][13] _to call host_ [_EGL_][14] _Libraries and display_ [_HAL_][15]”.

When [asked][16] whether Wine ran on this, Erfan added that he has not tested it yet, but intends to do it soon, and that he [will try][17] to set up GL soon to check for Wine+Proton compatibility.

He also [showed off][18] Lindroid running on distros like Ubuntu Touch ([Lomiri][19]), [Droidian][20] ([Phosh][21]), and [Plasma Mobile][22].

If you are eager to learn more about this cool project, you can refer to the [X thread][23], and [Luka's presentation][24] at Volla Community Days ( _4:01:00 timestamp_ ), where he answered many interesting questions from the audience.

### Want to Check it Out?

Before you do that, you need to know that you **will require a rooted Android device** alongside some AOSP patches to be able to run Lindroid. It is not possible to run it without root access because the underlying architecture uses [LXC][25] with access to host drivers.

Sadly, there's one more catch, currently, **there's no straightforward way to run Lindroid** , Erfan has [mentioned][26] that this is not easy to set up, but, he's working on sharing instructions soon.

In addition, he also announced that Lindroid will be officially made available via [LibreMobileOS][27] under the **Ulumo** name, where it will feature an Ubuntu base.

I expect that as an " _install it and forget it"_ Lindroid solution, but there's no ETA on that.

You can refer to the project's [GitHub][28] page if you are interested in helping with the development, or want to see how it progresses.

[Lindroid (GitHub)][28]

_💬 Did Lindroid pique your interest? Have some other project in mind? Share your thoughts below!_

**Suggested Read** 📖

![][29]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/lindroid/

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
[4]: https://itsfoss.com/android-distributions-roms/
[5]: https://x.com/Khode_Erfan
[6]: https://x.com/lukapanio
[7]: https://news.itsfoss.com/content/images/2024/06/Lindroid_a.jpeg
[8]: https://news.itsfoss.com/debian-12-release/
[9]: https://en.wikipedia.org/wiki/KWin
[10]: https://news.itsfoss.com/content/images/2024/06/Lindroid_b.gif
[11]: https://x.com/Khode_Erfan/status/1802332143579742336
[12]: https://www.androidauthority.com/android-15-desktop-mode-demo-3430991/
[13]: https://github.com/libhybris/libhybris
[14]: https://en.wikipedia.org/wiki/EGL_(API)
[15]: https://source.android.com/docs/core/graphics/hwc
[16]: https://x.com/stashyymane/status/1802419147961254322
[17]: https://x.com/4k_isn/status/1802364478803296729
[18]: https://x.com/Khode_Erfan/status/1802331901933334839
[19]: https://lomiri.com/
[20]: https://droidian.org/
[21]: https://github.com/droidian/phosh
[22]: https://plasma-mobile.org/
[23]: https://x.com/Khode_Erfan/status/1802331845633212554
[24]: https://www.youtube.com/live/7vF5647gNbo?si=q5mxoLeEhhlTC5ew&t=14460
[25]: https://linuxcontainers.org/
[26]: https://x.com/basujindal/status/1802425576436744680
[27]: https://lmo.framer.website/
[28]: https://github.com/linux-on-droid/
[29]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
