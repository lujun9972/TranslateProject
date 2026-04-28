[#]: subject: "What’s New for Fedora Atomic Desktops in Fedora Linux 44"
[#]: via: "https://fedoramagazine.org/whats-new-fedora-atomic-desktops-in-fedora-linux-44/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s New for Fedora Atomic Desktops in Fedora Linux 44
======

![][1]

[Fedora Linux 44 has been released][2]! 🎉 So, let’s see what is included in this new release for the Fedora Atomic Desktop variants (Silverblue, Kinoite, Sway Atomic, Budgie Atomic and COSMIC Atomic).

### Changes for all Atomic Desktops

#### Issue tracker moved to the new Fedora forge

We have moved the [cross-variants issue tracker][3] to the new [Fedora forge][4]. This is the best place to file issues that impacts all variants or to coordinate work between all of them. If you have issues specific to a given desktop environment then we usually prefer to track them in each respective SIG trackers. These are available on the [README for the atomic-desktops organization][5].

#### Unified documentation, hosted on the new forge

The [unified documentation for all Atomic Desktops][6] is finally live! Unfortunately the translations have not been migrated so we will need help to re-translate everything again, once the translation setup is ready with the new forge. It should be mostly copy/paste from the previous docs and this time we will only have to translate the docs once and not for every (new) variant.

See the tracking issue [atomic-desktops#10][7].

#### Removal of FUSE version 2 libraries

FUSE version 2 has been deprecated and unmaintained for a while so we have removed it from the images. In practice, this means two things:

  * If you are using AppImages, some of them may not work anymore.
  * If you are using legacy backends with Plasma Vault on Kinoite, you need to migrate your data.



See the [Fedora Change][8] and the tracking issue [atomic-desktops#50][9]. The implications are detailed below.

##### AppImages and the FUSE 2 libraries

Some AppImages are still using an old AppImage runtime that relies on FUSE 2 libraries being available on the host. See the [Discussion thread][10] for examples on how to check the runtime of an AppImage.

If some of your AppImages do not work on Fedora Atomic Desktops 44, we recommend:

  * Looking for a Flatpak for the application and giving it another try. Consider helping upstream package their application as a Flatpak.
  * Reporting the issue upstream so that they are aware that they should use a newer runtime. Consider helping upstream with this as well.



##### EncFS or CryFS backends for Plasma Vaults are removed

KDE upstream no longer recommends using the EncFS nor CryFS backends for Plasma Vaults, notably because they rely on the FUSE 2 libraries. If you are using one of those backends, you should migrate your data to a new vault using the only maintained backend (gocryptfs). Ideally this should occur before the update to Fedora Linux 44. If you have already updated to Fedora Linux 44 and need access to your data, you can layer the needed packages (cryfs or fuse-encfs) using rpm-ostree install <package>, then migrate your data and finally reset the layers with rpm-ostree reset.

#### Dropping compatibility for pkla Polkit rules

Support for the legacy pkla Polkit rules format has been removed. It is unlikely that you were relying on support for those rules as most of the ecosystem has moved on to the new JavaScript based format.

See the [Fedora Change][11] and the tracking issue [atomic-desktops#102][12].

### What’s New in Silverblue

#### GNOME 50

Fedora Silverblue comes with the latest [GNOME 50 release][13]. For more details about the changes that occur alongside GNOME 50, see [What’s New in Fedora Workstation 44][14] on the Fedora Magazine.

### What’s New in Kinoite

#### KDE Plasma 6.6

Fedora Kinoite ships with [Plasma 6.6][15], [Frameworks 6.24][16] and [Gear 25.12][17].

See also [What’s New in Fedora KDE Plasma Desktop 44][18] in the Fedora Magazine.

#### KDE Plasma Login Manager replaces SDDM

The brand new Plasma Login Manager replaces SDDM to provide a more integrated experience with systemd and the KDE Plasma session.

See the [Fedora Ch][19][ange][19].

#### Unified out of the box experience with KDE Plasma Setup (OEM installation)

Thanks to the new Plasma Setup, it is now possible to install the system with Anaconda with minimal configuration and then complete the installation on the first boot by creating a new user and selecting the timezone. This is great when you want to install Fedora Kinoite on a computer and don’t want to setup a user in advance.

See the [Fedora Change][20].

### What’s New in Sway Atomic

Nothing specific for this release.

### What’s New in Budgie Atomic

Fedora Budgie Atomic comes with the latest [10.10.2 Budgie release][21]. This release brings Wayland support to Budgie Atomic. See the [10.10 release announcement][22] for more details.

### What’s New in COSMIC Atomic

Fedora COSMIC Atomic comes with the latest [1.0.8 release of the COSMIC desktop][23]. This is now considered stable.

### Universal Blue, Bluefin, Bazzite and Aurora

Our friends in the [Universal Blue project][24] ([Bazzite][25], [Bluefin][26], [Aurora][27]) have prepared the update to Fedora Linux 44. Look for upcoming [announcements in their Discourse][28].

As always, I heavily recommend checking them out, especially if you feel like some things are missing from the Fedora Atomic Desktops and you depend on them (NVIDIA drivers, extra media codec, out of tree kernel drivers, etc.).

### What’s Next

#### Helping us with a few nasty bugs

If you have an interest in contributing to Fedora Atomic Desktops, here are some bugs that we will have to fix in the short term. We would greatly appreciate help with:

  * Fixing root mount options ([atomic-desktops#72][29]): This is a long standing and mostly invisible bug that impacts performance.
  * Moving away from nss-altfiles ([atomic-desktops#108][30]): This is another long standing source of issues that new users regularly face.



#### Sealed Fedora Atomic Desktop bootable container images

Sealed images are now ready for testing! [See the other article for all the details][31].

#### Road map to Bootable Containers

A lot of work is happening to make the transition to Bootable Containers as smooth as possible for our existing users. You can look at the road map for this transition at [atomic-desktops#26][32].

One of the tasks is to move away from our unmaintained installation ISO building scripts to the new image-builder tooling. This is [planned for Fedora Linux 45 for the ostree variants][33] and support for Bootable Container [will follow right after][34].

Another task is to start building the Fedora Atomic Desktops Bootable Container images [using the Fedora Konflux instance][35].

### Where to reach us

We are looking for contributors to help us make the Fedora Atomic Desktops the best experience for Fedora users.

  * [Atomic Desktops SIG][36]: [Organization on Fedora’s Forge][5], [#atomic-desktops:fedoraproject.org][37]
  * Silverblue: [Workstation Working Group][38], [#silverblue:fedoraproject.org][39]
  * Kinoite: [KDE SIG][40], [#kinoite:fedoraproject.org][41]
  * Sway Atomic: [Sway SIG][42], [#sway:fedoraproject.org][43]
  * Budgie Atomic: [Bud][44][g][44][ie][44] [][44][SIG][44], [#budgie:fedoraproject.org][45]
  * COSMIC Atomic: [COSMI][46][C][46] [SIG][46], [#cosmic:fedoraproject.org][47]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-fedora-atomic-desktops-in-fedora-linux-44/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/03/New_in_atomic_desktops_for_F44-816x345.jpg
[2]: https://fedoramagazine.org/announcing-fedora-linux-44/
[3]: https://forge.fedoraproject.org/atomic-desktops/tracker
[4]: https://forge.fedoraproject.org
[5]: https://forge.fedoraproject.org/atomic-desktops
[6]: https://docs.fedoraproject.org/en-US/atomic-desktops/
[7]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/10
[8]: https://fedoraproject.org/wiki/Changes/AtomicDesktopDropFuse2
[9]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/50
[10]: https://discussion.fedoraproject.org/t/f44-change-proposal-atomic-desktops-drop-fuse-2-libraries-selfcontained/179410/4
[11]: https://fedoraproject.org/wiki/Changes/AtomicDesktopDropPklaCompat
[12]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/102
[13]: https://release.gnome.org/50/
[14]: https://fedoramagazine.org/whats-new-fedora-workstation-44/
[15]: https://kde.org/announcements/plasma/6/6.6.0/
[16]: https://kde.org/announcements/frameworks/6/6.24.0/
[17]: https://kde.org/announcements/gear/25.12.0/
[18]: https://fedoramagazine.org/whats-new-in-fedora-kde-plasma-desktop-44/
[19]: https://fedoraproject.org/wiki/Changes/PlasmaLoginManager
[20]: https://fedoraproject.org/wiki/Changes/Unified_KDE_OOBE
[21]: https://buddiesofbudgie.org/blog/budgie-10-10-2-released
[22]: https://buddiesofbudgie.org/blog/budgie-10-10-released
[23]: https://github.com/pop-os/cosmic-epoch/releases/tag/epoch-1.0.8
[24]: https://universal-blue.org/
[25]: https://bazzite.gg/
[26]: https://projectbluefin.io/
[27]: https://getaurora.dev/
[28]: https://universal-blue.discourse.group/tag/announcements
[29]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/72
[30]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/108
[31]: https://fedoramagazine.org/sealed-atomic-desktops-test-images
[32]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/26
[33]: https://fedoraproject.org/wiki/Changes/BuildAtomicDesktopsWithImageBuilder
[34]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/32
[35]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/91
[36]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[37]: https://matrix.to/#/#atomic-desktops:fedoraproject.org
[38]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[39]: https://matrix.to/#/#silverblue:fedoraproject.org
[40]: https://fedoraproject.org/wiki/SIGs/KDE
[41]: https://matrix.to/#/#kinoite:fedoraproject.org
[42]: https://fedoraproject.org/wiki/SIGs/Sway
[43]: https://matrix.to/#/#sway:fedoraproject.org
[44]: https://fedoraproject.org/wiki/SIGs/Budgie
[45]: https://matrix.to/#/#budgie:fedoraproject.org
[46]: https://fedoraproject.org/wiki/SIGs/COSMIC
[47]: https://matrix.to/#/#cosmic:fedoraproject.org
