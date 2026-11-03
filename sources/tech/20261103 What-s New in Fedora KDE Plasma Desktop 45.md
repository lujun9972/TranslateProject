[#]: subject: "What’s New in Fedora KDE Plasma Desktop 45"
[#]: via: "https://fedoramagazine.org/whats-new-in-fedora-kde-plasma-desktop-45/"
[#]: author: "Troy Dawson https://fedoramagazine.org/author/tdawson/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s New in Fedora KDE Plasma Desktop 45
======

![][1]

KDE Plasma 6.8 was released on KDE’s 30 year anniversary and we are proud to have it be the star of Fedora KDE Plasma Desktop Edition 45.

The Fedora KDE Plasma Desktop Edition is well suited for many needs. It combines the reliable and trusted Fedora Linux base with the KDE Plasma Desktop environment. It provides a selection of KDE applications that are simple by default, but powerful when needed.

### KDE Plasma 6.8

KDE developers continue to release new features, fix bugs and fine-tune the desktop experience to improve on the now well-established foundation of Plasma 6. There have been two KDE Plasma releases since our last Fedora KDE Plasma Desktop Edition shipped. Some of the new features and updates include:

#### New Features

  * **Per-screen virtual desktops:** After 21 years per-screen virtual desktops have finally arrived!
  * **Test your microphone volume:** Stop wondering if it’s your microphone or an app that’s misbehaving.
  * **Press-and-hold for special characters:** With Plasma’s virtual keyboard enabled, press and hold a key to type special characters related to it.
  * **Light/dark mode toggle:** A quick toggle in the system tray to switch between light and dark Global Themes immediately.
  * **“Background Apps” in the System Tray:** The system tray now shows apps using the newer “Background Apps” system, which is more common for apps using the Flatpak package format.



#### Updated Features

  * **Better Accessibility:** a new “dwell clicker” feature can send a mouse click when the pointer stops moving. Designed especially for users with mobility issues.
  * **Remote Desktop:** Much better performance and quality, bi-directional clipboard synchronization, exclusive mode and overall polish to the experience.
  * **Printing:** Now the System Tray icon for printers shows the number of active jobs in a little badge.
  * **Faster virtual desktop switching in the Overview:** When you press “Meta + W” to open the Overview screen, Plasma now lets you switch virtual desktops simply by scrolling or pressing the “Page Up” or “Page Down” keys.
  * **Easier to compare different time zones:** The Digital Clock widget lets you add multiple time zones and quickly compare them.



#### Theming

  * **Oxygen:** For KDE’s 30th anniversary the Oxygen theme is back and brought up to par.
  * **Breeze:** The default Breeze theme also continues to evolve, now featuring rounded list and grid view highlights for many applications, and visible click effects for menu items.
  * **Union:** Plasma’s all-new Union theming system streamlines theming by making it possible to style Plasma, QtQuick apps, and QtWidgets apps all with a single set of easy-to-write CSS.



#### And More …

There is so much new stuff since our last Fedora KDE Plasma Desktop Edition was released. Check out the full release announcements for [Plasma 6.7][2] and [Plasma 6.8][3].

### Fedora Linux 45 general updates

Some broader changes in Fedora Linux also directly impact Fedora KDE Plasma Desktop Edition, notably:

  * **Updated Podman:** Podman 6 includes new features, but also significant API and CLI breaking changes. Depending on how you use Podman, this change may significantly affect you. The [Podman 6 change proposal][4] has information on what is affected.
  * **NetworkManager VPN:** NetworkManager-vpnc and NetworkManager-fortisslvpn are not in Fedora 45. If you already have them installed and are updating to Fedora 45, NetworkManager will obsolete and remove them. Users still using them should migrate their connection profiles to openconnect or libreswan.
  * **Lazarus with multiple widget sets:** The lazarus-ide now comes with a Qt6 option in lazarus-ide-qt6.
  * **Updated IBus:** IBus now supports the ISO latch and shift states of XKB key-maps in Wayland desktop environments like KDE, Sway, Hyprland, COSMIC.
  * **DRM Panic Frontend:** The DRM Panic Frontend provides users with a user-friendly interface for understanding kernel panic information and facilitates bug reports.



### Wrap-up

The Fedora KDE SIG hopes that you’ll find Fedora KDE Plasma Desktop 45 to be a wonderful experience. When you’re ready to try it, [click here for download links and verification instructions][5]. If you would like to learn more, check out the [Fedora KDE Plasma Desktop website][6].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-in-fedora-kde-plasma-desktop-45/

作者：[Troy Dawson][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/tdawson/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/10/new_in_KDE_plasma_desktop_45-816x345.jpg
[2]: https://kde.org/announcements/plasma/6/6.7.0/
[3]: https://kde.org/announcements/plasma/6/6.8.0/
[4]: https://fedoraproject.org/wiki/Changes/Podman6
[5]: https://fedoraproject.org/kde/download
[6]: https://fedoraproject.org/kde/
