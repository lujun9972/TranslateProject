[#]: subject: "Raspberry Pi OS Is Now Wayland By Default For All Models!"
[#]: via: "https://news.itsfoss.com/raspberry-pi-os-wayland/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Raspberry Pi OS Is Now Wayland By Default For All Models!
======
Raspberry Pi OS now uses Wayland out of the box!
[![][1]][2]

If you are into hardware tinkering, then you have most likely used a [Raspberry Pi][3] to give your DIY projects the appropriate firepower. Heck, you can even run [Linux distributions][4] or [Windows][5] on it if it suits you.

However, for many, the OS of choice is the Raspberry Pi OS, which is based on Debian and has been tailored by Raspberry Pi engineers to run well on their hardware.

In a recent announcement, they introduced a major change when it comes to how they handle the windowing system of their operating system.

Let's check it out. 😃

### Raspberry Pi OS Switches To Wayland

![Source: Raspberry Pi][6]

Marking a departure from [X11][7], Raspberry Pi OS is now [Wayland][8] by default from the latest Bookworm release. The developers have included [Xwayland][9] so that users don't face any issues when running native X11 applications.

This move was something that the Raspberry Pi developers **first considered 10 years ago** , but at the time, Wayland had not matured enough for them to justify a complete switch.

Over the years, they started to experiment with it. They began in 2021 with the [Bullseye release][10], switching to [Mutter][11] and using it as an X11 window manager with an optional Wayland mode.

Then, in 2023, with the [Bookworm release][12], they replaced Mutter with [Wayfire][13], and made the Wayland session the default one on the Raspberry Pi [4][14] and [5][15], continuing to use the X11 session on weaker Raspberry Pi models.

After many extensive bouts of experimenting and testing, they found out that **they were doing more harm than good** and had to look for new solutions. That is when they found [labwc][16], where, within hours of work, they were able to implement it into the Raspberry Pi OS.

They then collaborated with the developers of labwc and [wlroots][17] ( _a crucial component of labwc_ ) to further refine the Wayland experience for Raspberry Pi devices. They have now reached a stage where **Raspberry Pi OS runs efficiently on both older and newer devices** when using the Wayland session.

During the announcement, [Simon Long][18], UX Lead at Raspberry Pi, added that:

> For most of this year, we have been working on porting labwc to the Raspberry Pi Desktop. This has very much been a collaborative process with the developers of both labwc and wlroots: both have helped us immensely with their support as we contribute features and optimisations needed for our desktop.

Other than the Wayland stuff, there is now **a vastly improved touch-screen experience** , **better Raspberry Pi Connect integration** , and various other user experience tweaks with the new release.

You can go through the [announcement blog][19] to learn more.

### Get Raspberry Pi OS

Existing Raspberry Pi OS Bookworm users can upgrade to this new Wayland-by-default release by running the following commands:

```

    sudo apt update && sudo apt full-upgrade

```

After reboot, you will be asked to switch to labwc. If you would rather not switch, then you can select “ _Keep Wayfire_ ”. Keep in mind that the Wayfire implementation won't be receiving any updates going forward.

For fresh installations, you can visit the [official website][20], where you will find images for the various Raspberry Pi models.

[Raspberry Pi OS][20]

**Suggested Read** 📖

![][21]

* * *

[Get It's FOSS Plus Membership][22]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/raspberry-pi-os-wayland/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.raspberrypi.org/
[4]: https://itsfoss.com/raspberry-pi-os/
[5]: https://itsfoss.com/windows-raspberry-pi/
[6]: https://news.itsfoss.com/content/images/2024/10/Raspberry_Pi_OS_Wayland.jpg
[7]: https://www.x.org/wiki/
[8]: https://wayland.freedesktop.org/
[9]: https://wayland.freedesktop.org/docs/html/ch05.html
[10]: https://www.raspberrypi.com/news/raspberry-pi-os-debian-bullseye/
[11]: https://mutter.gnome.org/
[12]: https://www.raspberrypi.com/news/bookworm-the-new-version-of-raspberry-pi-os/
[13]: https://github.com/WayfireWM/wayfire
[14]: https://itsfoss.com/raspberry-pi-4/
[15]: https://news.itsfoss.com/raspberry-pi-5/
[16]: https://github.com/labwc/labwc
[17]: https://gitlab.freedesktop.org/wlroots/wlroots
[18]: https://www.linkedin.com/in/simon-long-27127827/
[19]: https://www.raspberrypi.com/news/a-new-release-of-raspberry-pi-os/
[20]: https://www.raspberrypi.com/software/operating-systems/
[21]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[22]: https://itsfoss.com/#/portal/signup
