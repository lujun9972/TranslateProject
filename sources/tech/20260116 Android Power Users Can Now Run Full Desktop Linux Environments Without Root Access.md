[#]: subject: "Android Power Users Can Now Run Full Desktop Linux Environments Without Root Access"
[#]: via: "https://itsfoss.com/local-desktop/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Android Power Users Can Now Run Full Desktop Linux Environments Without Root Access
======

[![Warp Terminal][1]][2]

Running Linux-based operating systems on smartphones has come a long way. We now have [several Linux-powered smartphones][3] on the market that cater to different use cases. Some pack in flagship-level performance, while others try to be a value-for-money proposition.

Sadly, these devices are out of reach for most people around the world due to excessive taxation from their countries and shipping charges. Of course, many do have an older spare Android smartphone laying around.

Why not make good use of it? In this article, we will be taking a look at a very cool project that turns an Android smartphone into a Linux machine with a simple APK file and no root access.

### Local Desktop: Easily Run Linux Desktop

![][4]

[Local Desktop][5] is an open source app that brings **a complete Linux ARM64 environment to your Android device**. The project is being led by [Mister Teddy][6], who has **built it on Rust** and has been pushing out updates regularly.

As for what it offers, well, for starters, you can install [different desktop environments][7] on this, with the app currently shipping with [LXQt][8] as the default. But you should be able to set up KDE Plasma, GNOME, or any other desktop environment that works on Arch Linux.

By default, **Local Desktop logs you in as the root user** for a simpler setup process. However, you can [create non-root users][9] if you need to. This is particularly important for certain applications.

The documentation for the app reads that Chrome and Electron-based apps like VS Code run better or are more securely without root access, and AUR helpers like [Paru][10] or [Yay][11] actually require a non-root user and will refuse to work as root.

Moreover, if you want to install new software, then it's easy since **Local Desktop is based on Arch Linux**. _I forgot to mention that earlier._ 😅

You can install applications from the official Arch repositories [using pacman][12], and should you need, you can also install new ones from the [Arch User Repository][13] (AUR). Though, **keep in mind that not every app might run** , and the developer's testing is limited to a few popular ones.

### Few Things to Keep in Mind

When I had tested it, **the installation progress was stuck at 33% for a few hours** , with new components being downloaded and installed during that. This could either be due to my device being slow, my ISP's routing being bad, or the download mirrors having a slow day.

Once it was done, I understood why [the documentation][14] for Local Desktop recommended using a physical keyboard. There's an on-screen keyboard that can be enabled via the _Applications_ menu, but having a real one at your fingertips should be much more convenient.

Also, **I recommend you install Local Desktop on a tablet or a smartphone with a big screen** , as the interface has many things to show. You will end up touching the wrong pixels for certain options if your screen size is too small.

Desktop Linux is mostly neglected by the industry but loved by the community. For the past 13 years, It's FOSS has been helping people use Linux on their personal computers. And we are now facing the existential threat from AI models stealing our content.

If you like what we do and would love to support our work, please become It's FOSS Plus member. It costs $49 a year (less than the cost of a McDonald's burger a month), and you get 5 ebooks, an ad-free reading experience and the satisfaction of helping the desktop Linux community.

[Join It's FOSS Plus][15]

* * *

**Suggested Read 📖:** [_Looking for Linux Phones? Here are Your Options_][3]

![][16]

--------------------------------------------------------------------------------

via: https://itsfoss.com/local-desktop/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/linux-phones/
[4]: https://itsfoss.com/content/images/2026/01/local-desktop-lxqt-1.jpg
[5]: https://localdesktop.github.io/
[6]: https://github.com/mister-teddy
[7]: https://localdesktop.github.io/docs/user/custom-de/
[8]: https://lxqt-project.org/
[9]: https://localdesktop.github.io/docs/user/creating-a-non-root-user/
[10]: https://itsfoss.com/paru-aur-helper/
[11]: https://itsfoss.com/install-yay-arch-linux/
[12]: https://itsfoss.com/pacman-command/
[13]: https://itsfoss.com/aur-arch-linux/
[14]: https://localdesktop.github.io/docs/user/getting-started/
[15]: https://itsfoss.com/membership/
[16]: https://itsfoss.com/content/images/icon/android-chrome-512x512-225.png
