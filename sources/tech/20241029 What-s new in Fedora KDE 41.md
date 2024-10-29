[#]: subject: "What’s new in Fedora KDE 41"
[#]: via: "https://fedoramagazine.org/whats-new-in-fedora-kde-41/"
[#]: author: "John Kizer https://fedoramagazine.org/author/johnandmegh/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new in Fedora KDE 41
======

![][1]

Fedora Linux provides a wide variety of users with leading edge open source technology in a community developed and maintained operating system. The Fedora KDE Spin combines the reliable and trusted Fedora Linux base with the KDE Plasma desktop environment and a selection of KDE applications – simple by default, yet powerful when needed.

Back in April 2024, [Fedora Linux 40 included the KDE “MegaRelease 6”][2] – the Plasma desktop environment, Frameworks application libraries (with the underlying Qt platform), and Gear application suite were all upgraded to new versions in one fell swoop to deliver improved performance and reliability. Since then, continuous upstream updates by the KDE teams to fix bugs and deploy new features were quickly deployed to Fedora 40 users, including breakthroughs such as Explicit Sync in Wayland (which addressed the most prevalent graphical glitches on Nvidia devices)!

Now, as part of the Fedora Linux 41 release, the KDE Spin again includes the very latest with the recently released KDE Plasma 6.2, up-to-date KDE applications and core system packages, and new ways of using Plasma on different devices:

### KDE Plasma 6.2

[Plasma 6.2][3] features numerous bug fixes and additional features to continue building on the modern foundation of Plasma 6:

  * Drawing tablet configuration, calibration and pen button binding that are built-in to the System Settings app – no extra software needed
  * Color management upgrades all over – Wayland protocol improvements, better brightness handling for HDR and ICC profiles, tone mapping built-in to the KWin compositor, and faster HDR performance add up to a better desktop experience for graphic design, gaming, and multimedia
  * Accessibility improvements, by adding the complete “Sticky Keys” feature on Wayland (enabling users with limited dexterity and/or mobility to use keyboard shortcuts more easily), and by providing color blindness correction filters directly in the revamped System Settings Accessibility page



### Fedora KDE across devices

#### ARM-Based devices (AArch64)

The Fedora Project and KDE have both worked to support ARM-based devices like Raspberry Pi and Apple Silicon with high-quality experiences. Beginning with Fedora Linux 41, the KDE Spin for AArch64 will now be “release-blocking”. This means that showstopper bugs impacting the KDE experience on these devices can now qualify as blockers for the overall release, helping ensure that projects such as Fedora Asahi Remix (for Apple Silicon) get the best possible support.

_Please note that live ISOs for KDE on AArch64 are not yet release-blocking, and will be coming in a future release_

#### KDE Plasma Mobile Spin & Kinoite Mobile

Built on the foundations of the Plasma Desktop, KDE Plasma Mobile brings its flexibility to devices with a mobile form factor. Although it was originally geared towards phones, the touch-friendly interface works very well on tablets and 2-in-1 laptops, and enables users with an even broader range of devices to join the Fedora community!

This experience will be available in both the traditional distribution format, as the Fedora KDE Plasma Mobile Spin, and in an Atomic Desktop bootable container image, as Kinoite Mobile.

_Please note that installation ISOs have not yet been published for Kinoite Mobile on this cycle, but are coming soon!_

### Fedora Linux 41 general updates

Some of the key updates occurring in the core components of Fedora 41, which specifically impact the KDE Spin, include:

  * New power profiles daemon: _tuned_ replaces the old _power-profiles-daemon_ , providing advanced users with more options to fine-tune the power consumption of their system. This change also provides API compatibility for developers, and reduces the number of different approaches for which software maintainers need to account
  * Broader laptop camera support: Many recently released laptops include new IPU6 webcams that use a unique bus (instead of USB) and rely on much more software support to function. Fedora Linux 41 includes out-of-the-box support for cameras using the ov2740, ov01a10 and hi556 sensors in applications such as Firefox that can access cameras via Pipewire



### Wrap-up

The Fedora Project and the KDE Community hope that you’ll find Fedora KDE 41 to be an easy-to-use, reliable and powerful desktop operating system. When you’re ready to check it out, [click here for download links and verification instructions][4].

If you use and enjoy Fedora KDE, consider getting involved in the [Fedora Project][5], the [KDE Community][6], the [Fedora KDE Special Interest Group][7], or all of the above!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-in-fedora-kde-41/

作者：[John Kizer][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/johnandmegh/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/10/Whats-new-in-Fedora-KDE-41-2-816x431.jpg
[2]: https://fedoramagazine.org/whats-new-in-fedora-kde-40/
[3]: https://kde.org/announcements/plasma/6/6.2.0/
[4]: https://fedoraproject.org/spins/kde/download
[5]: https://docs.fedoraproject.org/en-US/project/join/
[6]: https://community.kde.org/Get_Involved
[7]: https://fedoraproject.org/wiki/SIGs/KDE
