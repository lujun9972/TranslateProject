[#]: subject: "EndeavourOS Gemini drops ARM: Ships with Proprietary NVIDIA Drivers"
[#]: via: "https://news.itsfoss.com/endeavouros-gemini/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

EndeavourOS Gemini drops ARM: Ships with Proprietary NVIDIA Drivers
======
EndeavourOS Gemini release ditches open-source NVIDIA drivers for the
proprietary ones.
Being one of the [top Arch-based user-friendly Linux distributions][1] around, [EndeavourOS][2] is a lightweight offering that focuses on giving users a no-nonsense experience, with minimal amount of preinstalled apps.

In a recent announcement, the developers have just released a new release in the form of **EndeavourOS Gemini** , which takes its codename from NASA's [Gemini program][3].

During the launch, the devs added that:

> The road to Gemini, named after the NASA program that was a bridge between the Mercury and the Apollo missions, was a real journey for our developing team but they got the release in top shape with an endless perseverence in a relatively short time.

So, let's get started with this release!

## 🆕 EndeavourOS Gemini: What's New?

![][4]

Like many recent distro releases, this release benefits from the stability of [Linux kernel 6.8][5], and comes equipped with [Calamares 3.3.5][6] and [Mesa 24.0][7]. Sadly, owing to [maintenance issues][8], **the ARM installation option has been removed from EndeavourOS**.

On the desktop environment side of things, EndeavourOS now features [KDE Plasma 6][9], which makes use of the X11 session for the live environment but **defaults to Wayland** after installation is complete.

However, users can switch to the X11 session if they don't prefer Wayland by using the SDDM login manager.

[GParted][10] has made a comeback after many users reported that the KDE partition manager lacks a few features that GParted has. The devs have also addressed an issue with the EFI partition not being created correctly when the “ _replace partition_ ” option was chosen.

Interestingly, **this release uses the proprietary NVIDIA graphics driver** instead of the _NVIDIA-dkms_ driver, as the latter was causing freezing issues in the Live environment.

You can dive deeper into this release by referring to the official [announcement blog][11].

## 📥 Get EndeavourOS Gemini

For new installations, you can head to the [official website][2] to download the latest EndeavourOS release. For existing users, there's no need to do anything if you keep your systems updated.

[EndeavourOS Gemini][2]

_💬 Already running this release? Going to get it? Let me know below!_

**Suggested Read** 📖

![][12]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/endeavouros-gemini/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/arch-based-linux-distros/
[2]: https://endeavouros.com/
[3]: https://www.nasa.gov/gemini/
[4]: https://news.itsfoss.com/content/images/2024/04/EndeavourOS_Gemini.jpg
[5]: https://news.itsfoss.com/linux-kernel-6-8-release/
[6]: https://calamares.io/calamares-3.3.5-is-out/
[7]: https://docs.mesa3d.org/relnotes/24.0.0.html
[8]: https://endeavouros.com/news/goodbye-endeavouros-arm/
[9]: https://news.itsfoss.com/kde-plasma-6/
[10]: https://itsfoss.com/gparted/
[11]: https://endeavouros.com/news/plasma-6-with-wayland-or-x11-option-and-qt-6-ported-calamares-meet-gemini/
[12]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
