[#]: subject: "Christmas Comes Early With elementary OS 8.1 Release"
[#]: via: "https://itsfoss.com/news/elementary-os-8-1-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Christmas Comes Early With elementary OS 8.1 Release
======

[![Warp Terminal][1]][2]

[elementary OS][3] is a Linux distribution that focuses on user experience and design. It offers a clean, macOS-like interface built on Ubuntu's foundation. The project prioritizes simplicity and ease of use for everyday computing tasks.

It's [previous release][4] introduced some major upgrades like a Secure Session, a new Dock, Flathub support, and more.

Now, [elementary OS 8.1][5] is available for download. The release focuses on refining the experience based on user feedback, with **over 1,100 issues being addressed** since the earlier release.

### elementary OS 8.1: What's New?

![][6]

Powered by [Linux kernel 6.14][7], which brings improved hardware support and gaming performance, the release is based on [Ubuntu 24.04 LTS][8], which acts as a stable, secure base with many refinements.

Here are the **key highlights** of elementary OS 8.1:

  * User Interface Upgrades
  * Improved AppCenter
  * Privacy/Security Buffs
  * Easier System Updates
  * New ARM64 Builds



### User Interface Upgrades

![][9]

The **workspace switcher has moved directly into the dock**. A plus button lets you create new workspaces, while existing ones can be rearranged by drag and drop. Clicking on your current workspace brings up the _Multitasking View_.

Background apps now show up in the dock through the _Background Portal_. You can see what's running without needing to check the window and why it's running. Force-quitting apps is also straightforward with this.

Dark Mode gets **schedule snoozing** in this release. When you manually toggle Dark Mode while using a schedule, it resumes on the next scheduled change instead of stopping.

**Accessibility has received a lot of attention too**. elementary OS can now be installed and set up completely by blind users. The installer features more accessible labels throughout, and the password quality review is read aloud by screen readers during installation and initial setup.

The _Reduce Motion_ setting now handles more animations across the desktop and apps. Keyboard focus indicators appear while navigating with a keyboard but disappear when using a mouse or touch navigation.

Fractional display scaling is now available in the _Secure Session_. Previously, only integer scaling was supported, making interfaces either too large or too small on these displays.

### Improved AppCenter

![elementary OS 8.1's AppCenter user ratings on the left, package updates on the right.][10]

[AppCenter][11] **now shows percentage-based app ratings** from [ODRS][12]. This is the same ratings server used by [GNOME Software][13]. Additionally, when developers provide screenshots for multiple platforms, AppCenter prioritizes the elementary OS versions. The interface also indicates when a game supports controller input.

The action button for free apps says " _Install_ " instead of " _Free_ ". Apps with in-app purchases get a small label next to the action button. This makes it easier to spot free-to-play games or storefront apps like [Steam][14] and [Heroic Games Launcher][15].

App Updates handling got improved too. Installed apps are now sorted by release date instead of alphabetically.

### Privacy/Security Buffs

The **Secure Session is now the default**. [Danielle Foré][16], the Founder of elementary OS, says that this provides a better experience for most users and supports more modern hardware features. The Classic Session remains available for those who need it.

Password authentication dialogs have a new security feature. When opened in _Secure Sessions_ , the screen dims and other windows cannot steal focus. This prevents accidentally typing passwords into the wrong app window.

### Easier System Updates

![][17]

System Updates now show the download size before you start. A progress bar appears while downloading. The system skips held-back packages like `phased` or `staged` updates for more reliable installation.

The updates check has been rewritten. It no longer runs in Demo Mode ( _the live session_ ), only happens once daily, and does not slow down the initial login flow. Plus, **system updates do not automatically download on metered connections** and send a notification instead.

### New ARM64 Builds

elementary OS **offers ARM64 builds for the first time**. These work on devices that boot with UEFI. You can run the OS on M-series Apple Silicon and devices with UEFI-supporting firmware like the Raspberry Pi.

The included kernel also supports certain Qualcomm and Rockchip processors.

### **Miscellaneous** Changes

Apart from the major changes, elementary OS 8.1 includes several other improvements worth noting:

  * [Maps][18] and [Monitor][19] apps are now offered as default applications.
  * Inclusion of [GNOME Web 48.3][20] that delivers performance improvements.
  * The [Music][21] app gets queue management with save/restore and search functionality.
  * You can now deny notification bubble access for apps directly via System Settings.
  * Bluetooth settings have been redesigned with better device separation and keyboard navigation in mind.



### Install elementary OS 8.1

elementary OS 8.1 is available as a _**pay-what-you-can**_ offering on the [official website][3]. Localized direct downloads and a torrent magnet link are provided for an easy installation experience.

**The release will receive monthly feature and bug fix updates**. You can also get it pre-installed on computers from [Star Labs][22], [Slimbook][23], and [Laptop with Linux][24].

[elementary OS 8.1][3]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/elementary-os-8-1-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://elementary.io/
[4]: https://itsfoss.com/news/elementary-os-8-release/
[5]: https://blog.elementary.io/os-8-1-available-now/
[6]: https://itsfoss.com/content/images/2025/12/elementary-os-8-1-desktop-view.jpeg
[7]: https://itsfoss.com/news/linux-kernel-6-14/
[8]: https://itsfoss.com/news/ubuntu-24-04-lts/
[9]: https://itsfoss.com/content/images/2025/12/elementary-os-8-1-multitasking.jpeg
[10]: https://itsfoss.com/content/images/2025/12/elementary-os-8-1-app-center-ratings.png
[11]: https://appcenter.elementary.io/
[12]: https://odrs.gnome.org/
[13]: https://apps.gnome.org/Software/
[14]: https://store.steampowered.com/
[15]: https://heroicgameslauncher.com/
[16]: https://mastodon.online/@danirabbit
[17]: https://itsfoss.com/content/images/2025/12/elementary-os-8-1-system-updates.png
[18]: https://blog.elementary.io/updates-for-october-2025/#:~:text=elementary%20OS%208.1!-,Maps,-The%20first%20stable
[19]: https://blog.elementary.io/updates-for-november-2025/#:~:text=%23updates-,Monitor,-The%20first%20release
[20]: https://gitlab.gnome.org/GNOME/epiphany/-/releases/48.3
[21]: https://appcenter.elementary.io/io.elementary.music/
[22]: https://starlabs.systems/
[23]: https://slimbook.com/en/
[24]: https://laptopwithlinux.com/
