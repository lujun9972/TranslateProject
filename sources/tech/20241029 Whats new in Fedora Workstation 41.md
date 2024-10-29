[#]: subject: "Whats new in Fedora Workstation 41"
[#]: via: "https://fedoramagazine.org/whats-new-fedora-workstation-41/"
[#]: author: "Aoife Moloney https://fedoramagazine.org/author/amoloney/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Whats new in Fedora Workstation 41
======

![][1]

Background image by Yotam Guttman

Fedora Workstation 41 is the latest release of one of the leading providers of free, open source software, The Fedora Project. This article describes some of the user-facing changes in the newest version of Fedora Workstation. Upgrade today from [the official website][2], or upgrade your existing install using GNOME Software or through the terminal with [_dnf system-upgrade_][3].

### GNOME 47

In Fedora 41 workstation, you can enjoy the latest features the GNOME software release has to offer, plus benefit from an array of system enhancements! Check out the GNOME 47 release notes for more details.

#### Accent Colors

One of the biggest features to land in GNOME 47, and Fedora Workstation 41, is the option to customize the standard blue accent color of GNOME interfaces. You can now choose from an array of vibrant colors, and customizing couldn’t be simpler – just select a color from the Appearance setting, and enjoy a uniquely-your desktop!

#### Enhanced Small Screen Support

This added support means user who have lower resolution screens will have a better experience as icons will be optimized and scaled for easier interaction and better visibility on smaller screens.

![][4]

#### New Style Dialogue Windows

In GNOME 47, the dialogue windows have a new style. This is intended to enhance usability across many screen sizes. This benefits everyone, but especially users who work on compact laptops and mobiles, and this upgrade means the dialogues work more effectively and they can adapt seamlessly to different environments. For added fun, try it out with custom accent colors!

![][5]

### IPU6 Camera support

In Fedora Workstation 41, we have added integrated support into Fedora Linux for Intel IPU6 attached MIPI cameras using the IPU6 CSI-receiver together with libcamwera’s 0.3 software ISP support in Firefox through PipeWire. This means a much better experience for users with newer camera models, and users will be able to see the camera icon in the top bar in GNOME if and when your camera is on.

### IBus Chewing for Traditional Chinese (Taiwan) Desktop enabled by Default

The default input method for Traditional Chinese has changed to ibus-chewing in Fedora Workstation 41. This change makes Fedora Linux more friendly to users as ibus-chewing is maintained by native speakers and the upstream is active. Much less reliance on Google Translate when reporting issues! It even has multi dictionary so users can load domain specific dictionaries.

### Nvidia Driver Install Support

Returning to Fedora Workstation in Fedora Linux 41 is support for installing Nvidia drivers with secureboot. By using mokutil, users can install the drivers, create a key with mokutil to self-sign the drivers, and provide a password for the key. On the next reboot the user is presented with the mokutil interface to enroll the key. For a how-to on using mokutil, please refer to the [docs page][6]. With this support now added, installation of Nvidia drivers on Fedora Linux 41 is now more accessible than ever!

### Ptyxis as the new Terminal App

Ptyxis is a terminal for GNOME with first-class support for containers, and works really well for Flatpaks as this is the intended distribution mechanism. This is now the default terminal app in GNOME 47 and Fedora Workstation 41 and brings features such as terminal inspector to help you debug issues when writing applications for the terminal, native support for light/dark mode and user-customizable keyboard shortcuts.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-fedora-workstation-41/

作者：[Aoife Moloney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/amoloney/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/10/f41-whats-new-background-816x345.jpg
[2]: https://fedoraproject.org/workstation/download
[3]: https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/
[4]: https://release.gnome.org/47/dash-after.webp
[5]: https://release.gnome.org/47/dialog-light-screenshot.webp
[6]: https://docs.fedoraproject.org/en-US/quick-docs/mok-enrollment/
