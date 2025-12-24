[#]: subject: "5 New Linux Distributions We Discovered in 2025"
[#]: via: "https://itsfoss.com/new-distros-2025/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

5 New Linux Distributions We Discovered in 2025
======

[![Warp Terminal][1]][2]

One of the most exciting elements of Linux being open source is that anyone can take the kernel and make a distribution of their own with whatever modifications and specializations they need. Making a distro for your own needs is how this whole movement started in the first place, after all.

At It's FOSS, we actively cover various Linux related topics. And in that process, we often come across new distros that we try to share with you. I am listing five of such new distros that we covered here in 2025.

📋

This is not the 'best distros of 2025' kind of list. It's about the distros that we came across this years and covered it here on It's FOSS. Mostly these distros saw their first release in the year 2025.

### 1\. Omarchy

![][3]

[Omarchy][4] comes from [David Heinemeier Hansson][5] ( _DHH_ ), who is also the creator of [Ruby on Rails][6] and [Basecamp][7]. The 'distribution', if I can call it that, is based on Arch, and has the tiling window manager [Hyprland][8]. The idea is that instead of having to spend hours on customizing your Arch installation with Hyprland to make it look beautiful, and installing every important package one-by-one, you can directly install a distribution that comes with all of that.

Omarchy comes with a bunch of programs preinstalled, such as Neovim, Spotify, Chromium, fzf, Typora, Ghostty, Obsidian, Kdenlive, mpv, LibreOffice, etc. There is a heavy focus on easy [keyboard shortcuts][9] that make [navigation][10] and window management much easier at your fingertips. It comes with [14 gorgeous themes][11], which each have a specific aesthetic focus, ranging from cyberpunk to warm designs, and everything in between. There are more custom themes on the community pages and users can design their own themes as well.

This distribution has been designed for proper productivity, gorgeous looks with a straight-to-work attitude, with everything a power user might need already in the package. You can even install it as a configuration setting on plain Arch Linux. Read more about it here on [our article here][4]. And the manual is extremely helpful at exposing new users to its features [here][12].

[Omarchy][13]

📋

You can install Omarchy on a vanilla Arch install as well.

### 2\. ArchRiot

![][14]

ArchRiot is another Arch-based distribution that features the [Hyprland][8] Tiling window manager. Actually, it is a fork of Omarchy itself.

It has a Go Installer, that gives way to atomic operations, instant rollbacks, and prevents dependency issues to a very large extent. It comes with development enhancements with alternative applications such as Ghostty, Zed, Neovim, Fish as the default shell, Telegram, Proton Mail and so on. ArchRiot also has many privacy improvements, claiming zero telemetry, tracking or corporate data harvesting. For quick usage, it has custom keyboard shortcuts that will speed up your navigation around the system significantly.

In terms of appearance, it has specifically crafted dark themes, with optional intelligent theming that can extract colors from the wallpaper. It also has a unique status bar with system metrics, network management, audio, a blue-light filter, controls, Mullvad VPN status as well as a Pomodoro timer (obviously indicating that this OS is aimed at being productive). These can all be configured from the ArchRiot Control Panel.

Same as Omarchy, this can be installed either directly as an ISO or as a configuration setting on plain Arch Linux. It has many more features which can be checked out on their website.

[ArchRiot][15]

We also [have a video on ArchRiot][16], in case you prefer watching videos.

[Subscribe to It's FOSS YouTube Channel][17]

### 3\. NebiOS

![][18]

[NebiOS][19] isn't just a new Ubuntu-based distribution, but it comes also with a brand new desktop environment designed specifically for it called NebiDE, which was built for [Wayland][20]. It has been developed by [Sarp Mateson][21] under the umbrella of [NebiSoft][22] in Turkey, and has been in development since 2023.

The interface elements are Windows 7 Aero-like, coming with pre-configured widgets like a music player, clock, RSS reader, sticky notes, etc. There's a dock for quick launches, a top panel, an app launcher among other DE elements. The pre-installed applications are sufficient for daily driving the distribution.

All in all, it is a little buggy and clunky, but works well within the larger framework of daily-driving modern Linux distributions on a secondary, spare system.

[NebiOS][23]

### 4\. Helwan Linux

![][24]

Helwan Linux is a distribution out of Cairo, from Helwan University. Aimed at making a distribution for developers, power users and gamers, it is built on top of Arch Linux with the Cinnamon DE, striking a great balance between powerful features and user-friendliness. Focusing on the geographically local aspects of the distribution, its primary language is Arabic, but worry not as it also comes with other languages among which are English, French, etc.

It comes with development tools and editors preinstalled, such as Geany, Rust and VS Code. It even comes with gaming programs such as Steam and Lutris. It has some applications designed specifically for itself, like the _hel-terminal_ , _hel-builder_ , _hel-text-editor_ and _hel-tutorial_. Not limited to only that, Helwan Linux also comes with a package manager _hpm_ , which aims at modifying packages easier with just one-letter flags.

It looks simple, works great, and has everything you might need as a power user. Development, gaming, editing is all made easy on Helwan Linux. It is also a great testament to the tech coming out of Egypt, which is great to see. Read more about it on our article [here][25].

[Helwan Linux][26]

### 5\. ObsidianOS

![][27]

[ObsidianOS][28] is another Arch-based distribution in this list. Why do all these new distros use Arch?

Anyway, its main feature is an A/B partitioning system on ext4 instead of the usual btrfs that Arch Linux uses. Arch is known for its rapid, rolling updates, but also for the instability and system breaks that come with it. To resolve it, there are two root partitions that store the system files. When an update is installed, it is done so on one partition, and the other remains untouched. In case the update goes wrong or there's some other issue, the system can switch back to the other partition and everything can remain hunky-dory. This completely redefines the working of updates, rollbacks and system recovery on Linux.

Other than that, it offers a base not only of Arch, but also of Gentoo or Void Linux. It can come with either a plain TUI installer, with KDE, or with COSMIC. The packages are light and uncluttered, without much bloat. It comes _obsidianctl_ (and its GUI counterpart) to configure the A/B partitioning, giving you the choice to switch between the partitions, and the logs of the versions on each partition.

ObsidianOS also provides user-mode overlays, using which existing packages can be modified, and new packages can be installed without altering the existing package configuration. It has its own _opm_ (Obsidian package manager), which downloads packages from _pacman_ and installs them on overlays. There are even custom plugins for power management, connection/disconnection events, hardware triggers and so on.

ObsidianOS is quite experimental, but the features work quite well together, making this probably the most innovative and promising distribution released this year. You can read more [about it in this article][28].

[ObsidianOS][29]

### Wrapping Up

The year 2025 has brought about some interesting Linux distributions. Not that we need more distros but more because there is no harm in having variety. As Roland argued in his opinion piece, [fragmentation is also a strong point of the desktop Linux community][30].

It would be interesting to see how many of these distros stay active by the end of the next year.

--------------------------------------------------------------------------------

via: https://itsfoss.com/new-distros-2025/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/12/omarchy.jpg
[4]: https://itsfoss.com/news/omarchy/
[5]: https://dhh.dk/
[6]: https://rubyonrails.org/
[7]: https://basecamp.com/
[8]: https://hypr.land/
[9]: https://learn.omacom.io/2/the-omarchy-manual/53/hotkeys
[10]: https://learn.omacom.io/2/the-omarchy-manual/51/navigation
[11]: https://learn.omacom.io/2/the-omarchy-manual/52/themes
[12]: https://learn.omacom.io/2/the-omarchy-manual
[13]: https://omarchy.org/
[14]: https://itsfoss.com/content/images/2025/12/image-42.png
[15]: https://archriot.org/
[16]: https://www.youtube.com/watch?v=qrraIOvAcdg&vl=en
[17]: https://www.youtube.com/@itsfoss
[18]: https://itsfoss.com/content/images/2025/12/nebi-os-desktop-view.jpg
[19]: https://itsfoss.com/news/nebios/
[20]: https://wayland.freedesktop.org/
[21]: https://mateson.site/
[22]: https://nebisoftware.com/
[23]: https://nebios.org/index.html
[24]: https://itsfoss.com/content/images/2025/12/image-43.png
[25]: https://itsfoss.com/news/helwan-linux/
[26]: https://helwan-linux.github.io/helwanlinux/index.html
[27]: https://itsfoss.com/content/images/2025/12/obsidianos.png
[28]: https://itsfoss.com/obsidianos-review/
[29]: https://wiki.obsidianos.xyz/#/home
[30]: https://itsfoss.com/linux-fragmentation-as-positive/
