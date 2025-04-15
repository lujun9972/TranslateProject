[#]: subject: "What’s new in Fedora KDE Plasma Desktop 42"
[#]: via: "https://fedoramagazine.org/whats-new-for-fedora-kde-plasma-desktop-42/"
[#]: author: "John Kizer https://fedoramagazine.org/author/johnandmegh/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new in Fedora KDE Plasma Desktop 42
======

![What's new in Fedora KDE Plasma Desktop 42][1]

Fedora Linux provides a wide variety of users with leading edge open source technology in a community developed and maintained operating system. Fedora KDE releases combine the reliable and trusted Fedora Linux base with the KDE Plasma desktop environment. It provides a selection of KDE applications – simple by default, yet powerful when needed.

New with this release cycle, the KDE Plasma Desktop is now a full-fledged Edition. It is maintained by the KDE Special Interest Group through the Personal Systems Working Group. As an Edition, it is now one of the flagship experiences for Fedora Linux. This recognizes the mutual successes and commitments of the Fedora and KDE communities.

The Fedora KDE Plasma Desktop Edition is well-suited for many needs, including those of creators, scientists, developers and gamers. Check out the [brand new website][2] to learn more!

### KDE Plasma 6.3

KDE developers continue to release new features, fix bugs and fine-tune the desktop experience to improve on the now well-established foundation of Plasma 6. Fedora KDE 42 ships with Plasma 6.3.4 featuring:

  * Robust drawing tablet configuration, including better screen area mapping, calibration, pressure curve and range setting, and button mapping
  * Display improvements. This includes overhauled fractional scaling that produces sharper images even at high zoom levels. More accurate color management is provided – even with Night Light enabled
  * Easier monitoring of your device, including accuracy and efficiency improvements to _System Monitor_ , greater GPU and battery detail in _Info Center_ , and direct access to individual print queues from the widget



### Fedora KDE across devices

#### Power (ppc64le) systems

Fedora KDE now supports Power Systems (ppc64le architecture). Thanks to Dan Horák, we now have the full KDE stack – including PIM tools like KMail and Kontact – available on Power. Installable live images are also available for OpenPOWER-based systems, like the Talos Workstation from [Raptor Systems][3].

Note that Fedora KDE for ppc64le is available on a best-effort basis, and is not “release-blocking”. This means Fedora Linux releases will not be stopped by bugs impacting that architecture). Community assistance to support this new platform is welcome!

#### x86_64 emulation on ARM-based devices (AArch64)

Fedora KDE now has significantly expanded usability on ARM-based (AArch64) devices. This is the result of contributors Alyssa Rosenzweig, Davide Cavalca, and Neal Gompa integrating support for x86 emulation powered by FEX. This allows x86_64 applications to work on ARM using a Fedora FEX rootfs image, and is particularly optimized for running Windows or Steam applications.

Read more about this new feature here: [New in Fedora: Running x86 programs on ARM systems][4]

### Fedora Linux 42 general updates

Some of the key updates occurring in the core components of Fedora Linux 42, which directly impact the KDE Plasma Desktop Edition, include:

  * Fedora default wallpapers are now delivered in the JXL format instead of PNG, reducing file sizes while maintaining quality
  * More laptop cameras used in recent models will work out-of-the-box, following up on work done in Fedora Linux 41
  * System boot times should be faster, as the plymouth system component will no longer load the full graphics driver before showing the system splash screen
  * With the Anaconda installer running as a native Wayland application, language selections now sync between the live environment and installed system
  * Executable file placement is simpler, as anything previously in _/usr/sbin_ is now merged into _/usr/bin_



### Wrap-up

The Fedora Project and the KDE Community hope that you’ll find the Fedora KDE Plasma Desktop 42 to be a trustworthy, powerful and easy-to-use desktop operating system. When you’re ready to check it out, [click here for download links and verification instructions][5].

If you use and enjoy Fedora KDE, consider contributing in the [Fedora Project][6], the [KDE Community][7], the [Fedora KDE Special Interest Group][8], or all of the above!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-for-fedora-kde-plasma-desktop-42/

作者：[John Kizer][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/johnandmegh/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/Whats-new-in-Fedora-KDE-42-v2-816x345.jpg
[2]: https://fedoraproject.org/kde/
[3]: https://www.raptorcs.com/
[4]: https://fedoramagazine.org/new-in-fedora-running-x86-programs-on-arm-systems/
[5]: https://fedoraproject.org/kde/download
[6]: https://docs.fedoraproject.org/en-US/project/join/
[7]: https://community.kde.org/Get_Involved
[8]: https://fedoraproject.org/wiki/SIGs/KDE
