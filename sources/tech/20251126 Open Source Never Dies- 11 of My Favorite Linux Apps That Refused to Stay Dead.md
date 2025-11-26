[#]: subject: "Open Source Never Dies: 11 of My Favorite Linux Apps That Refused to Stay Dead"
[#]: via: "https://itsfoss.com/new-gen-linux-apps/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Open Source Never Dies: 11 of My Favorite Linux Apps That Refused to Stay Dead
======

[![Warp Terminal][1]][2]

One of the greatest things about open-source software is that anyone can pick up where a project left off and bring it back to life, whether it's to continue a legacy, or a spiritual successor that builds on a new foundation.

In this article, I'll share some of the popular Linux apps that got new lives as "New/Next Generation" (-ng) versions of their former selves.

### 1\. iotop-c

![iotop-c gives iotop a refreshed look][3]

You've heard of top and [htop][4], but did you know there's also a tool specifically for monitoring disk I/O? That's what iotop was created to do, but, but it's not seen development activity for some time, and being written in Python, it can get a bit slow (sorry Python lovers).

That's where iotop-c comes in. It's a rewrite of the original iotop in C, of course, and it's not only much faster, but richer in features, and actively maintained.

#### Installation

Iotop-c is packaged as `iotop-c` in most distros. You can also check out [the GitHub page][5] to grab the source code, star the project, or report bugs.

For Debian/Ubuntu you can run:

```

    sudo apt install iotop-c

```

💡

Want to learn how to make the most of iotop? Check out [this guide to iotop and ntopng][6] on Linux Handbook.

### 2\. vokoscreenNG

![vokoscreen NG makes screenrecording a breeze][7]

[vokoscreen NG][8] (vovokscreen Next Generation) is the [modernized rewrite][9] of vokoscreen, a popular [open-source screen recording app][10] from the previous decade. Where the original version used FFmpeg and was limited to X11 (not because of its backend, to be clear), vokoscreenNG uses Gstreamer and has a fresh Qt interface.

It's also got support for Wayland, which the previous generation lacked.

#### Installation

You can grab vokoscreenNG [from Flathub][11], or install it most distros directly from your package manager. On Debian/Ubuntu, you can install vokoscreen NG with:

```

    sudo apt install vokoscreen-ng

```

### 3\. WoeUSB-ng

![WoeUSB-ng makes it easy to create bootable Windows USB drives][12]

[WoeUSB-ng][13] is a total rewrite of WoeUSB, an open-source Linux app for creating bootable Windows USB flash drives. It was created by the same developers, but rewritten in Python and given a GUI to make it easier to set Windows installers from Linux.

Ironically, despite an active community, WoeUSB-ng seems abandoned again, as it hasn't been updated in at least two years. For instance, there's an [open pull request][14] to add AppImage packaging, and pave the way for others, but the main repository appears stalled. Maybe some day WoeUSB-ng will rise again.

🚧

WoeUSB was popular in 2010s. Then it was abandoned and WoeUSB-ng took its place. From what I see, WoeUSB-ng's development has stagnated as well. Until we see a WoeUSB-ng++ or WoeUSB-GenZ, we have [Ventoy to make bootable Windows USB on Linux][15].

#### Installation

If you're on Arch (or, if you use Arch on your distro of choice [via Distrobox][16]), you can install WoeUSB-ng with:

```

    yay -S woeusb-ng

```

### 4\. eSpeak NG

![The Screen Reader in GNOME uses eSpeak NG at the backend][17]

[eSpeak NG][18] is speech synthesizer with support for over a hundred languages. Its a true fork that builds on the preexisting [eSpeak][19] engine, adding more languages and new features while possessing a cleaner codebase and remaining fully compatible with the original.

This means eSpeak NG serves as a drop-in replacement for the original.

#### Installation

eSpeak NG is included with most distros as their text-to-speech engine. You can also install `espeak-ng` from your package manager of choice, for example:

```

    sudo apt install espeak-ng

```

Will install it on Debian/Ubuntu (if you don't already have it).

### 5\. stress-ng

![The safest move with stress-ng \(unless you know what you're doing\)][20]

[stress-ng][21] (stress next generation) is an app designed to do exactly what its name suggests, but for a good cause. It generates system load to stress-test both hardware and software subsystems to uncover bugs and limitations. Let me stress, no pun intended, it is _**not**_ meant for casual use.

As you might guess, stress-ng is the remake of stress, the original app. After stress was abandoned, stress-ng became the standard, adding new features and methods for a broader range of systems.

#### Installation

You can install stress-ng from your distro's package manager. For Debian/Ubuntu, the command would be:

```

    sudo apt install stress-ng

```

⚠️

****Warning:**** stress-ng is not a toy and can genuinely cause your system to overheat or become unresponsive. It should ****only**** be used by professionals, in controlled conditions.

### 6\. aircrack-ng

![aircrack-ng is a great pen-test tool][22]

[aircrack-ng][23] is a total remake and expansion of aircrack, an [app used for professional security auditing of WiFi networks][24] by attempting to "crack" their passwords (hence the name). The original aircrack was a WEP/WPA recovery tool from the early 2000s.

Designed when WPA2 was new, it lacked the coverage and hardware support needed for the modern era. By contrast, aircrack-ng is a full suite, with broader hardware support, various attack types, automation features, and more.

#### Installation

You can get aircrack-ng on most distros through the package manager. It's included with many security focused distros, like Kali, Parrot, and BlackArch.

To install aircrack-ng on Debian/Ubuntu, you can run:

```

    sudo apt install aircrack-ng

```

### 7\. tomboy-ng:

![Tomboy-ng keeps the note nostalgia alive][25]

[Tomboy-ng][26] is a total rewrite of Tomboy, which was once the standard notes tool on the GNOME desktop, and shipped with several distros, including Ubuntu. Tomboy was written in C#, and required [Mono][27], which was too heavy in the days of CD and DVDs.

For this reason, Tomboy was dropped from Ubuntu, and its C# dependency raised issues for some. Later, the legacy Tomboy codebase was abandoned, and Tomboy-ng, written in Pascal, took its place.

#### Installation

You can install Tomboy-ng on most distros by from the default repositories. On Debian/Ubuntu, you can run:

```

    sudo apt install tomboy-ng

```

### 8\. radiotray-ng:

![Radiotray-ng lets you listen to online radios easily][28]

[﻿Radiotray-ng][29] is a complete rewrite of Radiotray, a minimalist Python/GTK2 app for playing online radio stations right from the system tray. This rewrite use C++ and Glib/Gtkmm, and is not only more stable, but less prone to breakage from GTK updates.

Radiotray-ng brings better codec handling, lower resource usage, more stable stream reconnection and uses JSON for saving its configuration (as opposed to XML).

#### Installation

Radiotray-ng is packaged for Fedora and can be installed directly with:

```

    sudo dnf install radiotray-ng

```

For Ubuntu users, .deb packages are typically provided [with each release][30].

### 9\. GoldenDict-ng

![GoldenDict-ng is way more than a basic dictionary app][31]

[GoldenDict-ng][32] is a true fork of GoldenDict, an popular open-source dictionary and translation app. GoldenDict-ng maintains the original's support for multiple dictionary formats (StarDict, Babylon, Webster, and more), audio pronunciations, web lookups, and scan-to-translate functionality.

On top of these, it brings an updated interface based on Qt 6, various bug fixes, better multimedia support, and improved dictionary rendering. It also adds other niceties like dark mode, better scanning behavior, and more robust indexing, making it suitable for dictionary power users.

#### Installation

Goldendict-ng is available on Flathub, for those who'd prefer to use a Flatpak. You can also install it from most distro repos. Debian/Ubuntu users can run:

```

    sudo apt install goldendict-ng

```

### 10\. ntopng

![ntopng gives a bird's eye view of your network activity][33]

[ntop-ng][34] is the next-generation rewrite of ntop, a powerful real-time network traffic analyzer. The original ntop was already groundbreaking, and ntopng brings a new architecture, modern web UI, deep packet inspection, powerful metrics and flow analysis, and real-time bandwidth monitoring.

It also adds Lua scripting, network flow export, and integration with PF_RING for high-performance environments.

#### Installation

ntop-ng is packaged for most distros. On Debian/Ubuntu systems you can run:

```

    # Install ntop-ng
    sudo apt install ntop-ng

```

💡

****Note:**** You can learn how to put ntop-ng to good use by following [this tutorial][6].

### 11\. Shutter: revived, not replaced

![Shutter's back like it never left][35]

[Shutter][36] is popular Linux screenshot app with a slew of useful features that served countless users for many years. It was abandoned for some time, not working on modern distros, nor supporting Wayland. Despite apps like Flameshot and Gradia arising in its absence, Shutter still held a special place for many.

Fortunately, Shutter has been revived and even has initial support for Wayland. It's actively maintained by a community of enthusiastic users and contributors.

#### Where to get it:

Shutter is packaged for most popular distros, so you can grab it right from your package manager. On Debian/Ubuntu, you can run the following to install it:

```

    sudo apt install shutter

```

### Conclusion

Open-source projects are rarely ever _truly_ dead: the right person or community can bring them back to life. From humble desktop apps, to critical system utilities, open-source finds new ways to preserve old ideas.

If you rely on any of these apps, consider contributing or making a donation. After all, it's we, the community, who keep open-source alive.

--------------------------------------------------------------------------------

via: https://itsfoss.com/new-gen-linux-apps/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/11/image-12-1.png
[4]: https://itsfoss.com/use-htop/
[5]: https://github.com/Tomas-M/iotop
[6]: https://linuxhandbook.com/iotop-ntopng/
[7]: https://itsfoss.com/content/images/2025/11/image-9.png
[8]: https://linuxecke.volkoh.de/vokoscreen/vokoscreen.html
[9]: https://itsfoss.com/vokoscreenng/
[10]: https://itsfoss.com/best-linux-screen-recorders/
[11]: https://flathub.org/en/apps/com.github.vkohaupt.vokoscreenNG
[12]: https://itsfoss.com/content/images/2025/11/image-18.png
[13]: https://github.com/WoeUSB/WoeUSB-ng
[14]: https://github.com/WoeUSB/WoeUSB-ng/pull/145
[15]: https://itsfoss.com/bootable-windows-usb-linux/
[16]: https://itsfoss.com/distrobox/
[17]: https://itsfoss.com/content/images/2025/11/image-10.png
[18]: https://github.com/espeak-ng/espeak-ng
[19]: https://itsfoss.com/espeak-text-speech-linux/
[20]: https://itsfoss.com/content/images/2025/11/image-11-1.png
[21]: https://github.com/ColinIanKing/stress-ng
[22]: https://itsfoss.com/content/images/2025/11/image-13-1.png
[23]: https://www.aircrack-ng.org/
[24]: https://itsfoss.com/best-kali-linux-tools/
[25]: https://itsfoss.com/content/images/2025/11/image-14.png
[26]: https://github.com/tomboy-notes/tomboy-ng
[27]: https://www.mono-project.com/
[28]: https://itsfoss.com/content/images/2025/11/image-15-1.png
[29]: https://github.com/ebruck/radiotray-ng
[30]: https://github.com/ebruck/radiotray-ng/releases
[31]: https://itsfoss.com/content/images/2025/11/image-19.png
[32]: https://xiaoyifang.github.io/goldendict-ng/
[33]: https://itsfoss.com/content/images/2025/11/FireShot-Capture-054---ntopng---Interface-wlp49s0----localhost-.png
[34]: https://www.ntop.org/products/traffic-analysis/ntopng/
[35]: https://itsfoss.com/content/images/2025/11/image-20.png
[36]: https://shutter-project.org/
