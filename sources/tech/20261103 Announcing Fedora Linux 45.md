[#]: subject: "Announcing Fedora Linux 45"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-45/"
[#]: author: "Aoife MoloneyJef Spaleta https://fedoramagazine.org/author/amoloney/https://fedoramagazine.org/author/jspaleta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 45
======

![][1]

The Fedora Project is pleased to announce the release of Fedora Linux 45!

Whether you use Fedora on your desktop, server, edge device, or cloud instance, Fedora Linux 45 brings polished desktop upgrades, powerful new installer features, and updated toolchains.

Every Fedora release is a major community effort – thank you to everyone in our community who helped build, test, and package this release!

### Upgrade

If you are already running Fedora Linux, upgrading to the new release is simple. Our [user documentation][2] shows you exactly how to start enjoying F45 easily.

### Or, start fresh

Looking for a clean install or setting up a new device? Head over to [getfedora.org][3] to grab installation media for our flagship Editions:

  * Fedora Workstation
  * Fedora KDE Plasma Desktop
  * Fedora Server
  * Fedora Cloud
  * Fedora CoreOS & Fedora IoT



You can also explore our Atomic Desktops (including Silverblue, Kinoite, and Sericea) or choose from alternate desktop options via Fedora Spins (such as Cinnamon, Xfce, MATE, or COSMIC).

## What’s new in Fedora Linux 45?

We have a lot of excellent content under the hood in this release. Below is only a snapshot of them. Take a spin through our [release notes][4] for individual changes, and details on each change.

One of the biggest highlights in Fedora Linux 45 is integrated support for Stratis storage right inside the Anaconda installer.

Stratis brings modern enterprise storage features to local storage while wrapping device-mapper, XFS, and LUKS in an easy-to-use interface. These features include thin provisioning (over-provisioning), storage pooling, dynamic filesystem sizing, snapshots, and encryption.

  * GUI Installs (Web UI & Cockpit Storage): When performing custom partitioning during installation, you can launch the Cockpit storage module directly from Anaconda. From there, you can build Stratis pools across one or more physical drives and create dynamic **/** and **/home filesystems** on demand.
  * Automated Installs (Kickstart): For system administrators and automated deployments, Anaconda now supports –type=stratis with autopart, alongside dedicated stratispool and stratisfs kickstart commands.



Read more details about this really cool change in this [article][5].

### Desktop Highlights & Ecosystem Updates

  * Latest Desktop Environments: Updated desktop stacks across GNOME, KDE Plasma, and community spins bring improved performance, refined Wayland support, and better fractional scaling.
  * Developer Toolchains: Updated development tools and runtime libraries ensure you have access to the latest language features, compiler optimizations, and core system utilities.
  * System & Kernel Enhancements: Powered by recent Linux kernel releases, Fedora 45 includes broad hardware support, improved power management for laptops, and enhanced container performance.



If you encounter any bugs or unexpected behavior after upgrading or installing, help is close at hand:

  * Visit the [Ask Fedora][6] discussion forum to ask questions and find answers.
  * Check the [Common Issues][7] section on Ask Fedora to see known issues and workarounds tracked during the release cycle.



**Important:** Two legacy NetworkManager VPN plugins—NetworkManager-vpnc and NetworkManager-fortisslvpn—are retiring and will be obsolete, starting in **Fedora Linux 45**. Please read [this article][8] for information on what you need to do to migrate your VPN connections to supported alternatives.

## Let’s keep the conversation going

We’d love to hear how Fedora Linux 45 works for you! Share your thoughts, post your desktop setups, or say hi to fellow community members over on [Fedora Discussion][9].

Enjoy Fedora Linux 45!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-45/

作者：[Aoife MoloneyJef Spaleta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/amoloney/https://fedoramagazine.org/author/jspaleta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/09/Fedora_LInux_45-816x345.jpg
[2]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[3]: https://getfedora.org
[4]: https://docs.fedoraproject.org/en-US/fedora/f45/release-notes/
[5]: https://fedoramagazine.org/installing-fedora-45-on-stratis-storage/
[6]: https://ask.fedoraproject.org
[7]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f45/1452
[8]: https://fedoramagazine.org/?p=44587
[9]: https://discussion.fedoraproject.org
