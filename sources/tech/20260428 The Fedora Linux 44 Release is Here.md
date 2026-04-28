[#]: subject: "The Fedora Linux 44 Release is Here!"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-44/"
[#]: author: "Jef Spaleta https://fedoramagazine.org/author/jspaleta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Fedora Linux 44 Release is Here!
======

![][1]

Madeline Peck © CC BY-SA 4.0

I’m excited to announce that Fedora Linux 44 is here! Keep reading to discover highlights of Fedora Linux 44, or if you are ready, just jump right in and give Fedora Linux 44 a try!

### Thanks to everyone who helped!

Thank you and congrats to everyone who has contributed to this release. And thanks to everyone who showed up for the virtual release party last Friday. We celebrated a little early this year, just after the go/no-go meeting made the release official. If you weren’t able to join us live, you can watch the recording and hear about some of the great work from the contributors involved.

### **Looking to upgrade?**

If you have an existing system, [Upgrading Fedora Linux to a New Release][2] is easy. In most cases, it’s not very different from just rebooting for regular updates, except you’ll have a little more time to grab a coffee.

### **Ready to Fresh Install?**

If this is your first time running Fedora Linux, or if you just want to start fresh with Fedora, [download the install media for our flagship Editions][3] (Workstation, KDE Plasma Desktop, Cloud, Server, CoreOS, IoT), or one of our [Atomic Desktops][4] (Silverblue, Kinoite, Cosmic, Budgie, Sway), or [alternate desktop options][5] (like Cinnamon, Xfce, Sway, or others).

### **What’s new?**

As usual with Fedora Linux, there are just too many individual changes and improvements to go over in detail. You’ll want to take a look at the [release notes][6] for that.

#### **Notable User Visible Changes**

##### Anaconda

For those of you installing fresh Fedora Linux 44 Spins, you may notice a change in how Anaconda handles network devices. Anaconda now only creates network profiles for devices configured during installation (by boot options, kickstart, or interactively in UI) instead of providing default profiles for all devices. This change will simplify post-installation network configuration for users who need to customize after installation.

##### Workstation

Fedora Linux 44 Workstation ships with the latest GNOME release, GNOME 50. This comes with a long list of refinements to your desktop, including everything from accessibility to color management and remote desktop. Many of the applications that are installed by default on Fedora Workstation have also seen improvements, from Document Viewer to File Manager and Calendar. To learn more about these and other changes, you can read the [**GNOME 50 release notes**][7] **.**

##### KDE Plasma Desktop

KDE Plasma Desktop: If you are a KDE user, you should also notice a couple of very obvious changes. Fedora KDE Plasma Desktop 44 is based on the latest Plasma 6.6, which includes the new Plasma Login Manager and Plasma Setup to provide a more cohesive and integrated experience from the moment the computer is powered on for the first time. The installation process has been simplified, enabling you to easily set up Fedora KDE Plasma Desktop for a computer for a friend or a loved one.


#### **Plumbing Upgrades**

Beyond the user-visible changes, there are some important plumbing changes user should be aware of.

##### OpenSSL Cert File Handling Improvements

The loading time of OpenSSL has been improved by making use of directory-hash support for ca-certificates. This improvement required changes to where some certificate bundles are stored on the filesystem. You can read the specific [Change][8] details for more information.

##### The MariaDB default version is now 11.8

MariaDB packages use a versioned package layout, which allows Fedora to deliver both, mariadb-10.11 and mariadb-11.8 for users. The “distribution default” unversioned MariaDB packages now install the 11.8 versions in Fedora Linux 44. User doing upgrades to Fedora Linux 44 won’t notice the change in the default. For new users installing MariaDB for the first time, unless you specify the version, you’ll now get 11.8 by default.

##### Wine NTSYNC

The NTSYNC kernel module is enabled for select packages by package recommendation (notably Wine and Steam), which can improve compatibility and performance when running Windows applications (especially games). When packages that recommend the wine-ntsync package are installed, the package recommendation ensures NTSYNC is configured automatically on subsequent boots, so that users don’t have to manually enable NTSYNC.

##### Fedora Cloud boot partition using Btrfs

The /boot partition has been replaced with a Btrfs subvolume for Fedora Cloud images that support it. This results in better space utilization and smaller images.

### **If you hit a snag**

If you run into a problem, visit our [Ask Fedora][9] user support forum. This forum includes a category where we collect [common issues][10] and solutions or work-arounds.

### **Just drop by and say “hello”**

Drop by our [“virtual watercooler” on Fedora Discussion][11] and join a conversation, share something interesting, and introduce yourself. We’re always glad to see new people!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-44/

作者：[Jef Spaleta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jspaleta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/04/fedora-linux-44-1-816x345.jpg
[2]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/
[3]: https://fedoraproject.org/#editions
[4]: https://fedoraproject.org/atomic-desktops/
[5]: https://fedoraproject.org/spins
[6]: https://docs.fedoraproject.org/en-US/fedora/latest/release-notes/
[7]: https://release.gnome.org/50/
[8]: https://fedoraproject.org/wiki/Changes/droppingOfCertPemFile
[9]: https://ask.fedoraproject.org/
[10]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f44
[11]: https://discussion.fedoraproject.org/c/fun/8
