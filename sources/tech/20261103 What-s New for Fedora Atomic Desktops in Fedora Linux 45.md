[#]: subject: "What’s New for Fedora Atomic Desktops in Fedora Linux 45"
[#]: via: "https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-linux-45/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s New for Fedora Atomic Desktops in Fedora Linux 45
======

![][1]

[Fedora 45 is now available!][2] 🎉 So let’s see what this new release for the Fedora Atomic Desktops variants includes for Silverblue, Kinoite, Sway Atomic, Budgie Atomic and COSMIC Atomic.

### Changes for all Atomic Desktops

#### Completed the migration to the new Fedora forge

Everything related to the Atomic Desktops now resides in the [atomic-desktops organization][3].

The only remaining repo on GitLab.com/fedora is the one used to build the unofficial bootable container images ([gitlab.com/fedora/ostree/ci-test][4]). The migration of this repo will occur in the future, as well.

#### Anaconda Web UI

The Atomic Desktops installer ISOs now use the new Anaconda WebUI. This follows the same change that occurred for [Fedora Workstation 42][5] and [Fedora 43 Spins][6].

This also enables remote installation of a system using a Web browser on another machine over HTTPS.

See the Fedora Change pages for the [switch to the WebUI][7] and for [Web based remote][8] [i][8][nstallations][8].

#### Installer images (ISO) and disk images built by Image Builder

The installer images (ISO) are now built by Image Builder. While there should not be any immediate visible changes, this will help us move to the bootable container images in the future.

This also enables us to offer pre-installed disk images for Silverblue and Kinoite. Those images are currently in preview and only those variants are covered for now. They are the only ones with a first boot experience from a disk image.

See the [Fedora Change page][9] for further information.

#### General Fedora changes worth noting

The following changes are part of the [general set of changes that come with Fedora Linux 45][10] and are worth noting for Atomic Desktops users:

  * [Podman 6.0 & 6.1][11]: The latest version of the container management tool. See the blog posts:
    * [Introducing Podman v6.0.0][12]
    * [Podman 6 Configuration File Changes][13]
    * [Podman 6.1.0: Volume Renaming, Machine Restarts, and a Long List of Bug Fixes][14]
    * Support for slirp4netns and the BoltDB backend have been removed.
  * [oo7 Secrets Service Provider][15]: New secrets backend, enabled for all variants at the exception of Kinoite.
  * [DRM Panic Frontend][16]: An easier way to report kernel crashes using a web interface. Hopefully you will never see it!



### What’s new in Silverblue

Fedora Silverblue comes with the latest [GNOME 51 release][17].

For more details about the changes alongside GNOME 51, see [What’s new in Fedora Workstation 45 on the Fedora Magazine][18].

### What’s new in Kinoite

Fedora Kinoite ships with [Plasma 6.7][19], [Frameworks 6.31][20] and [Gear 26.08][21].

[Plasma 6.8][22] is expected to land right after the release.

See also [What’s new in Fedora KDE Plasma Desktop 45][23] on the Fedora Magazine.

### What’s new in Sway Atomic

Fedora Sway Atomic comes with the latest [1.12 Sway release][24].

### What’s new in Budgie Atomic

Fedora Budgie Atomic comes with the [brand new version 10.10.3 of Budgie Desktop][25]: New Favorites in Budgie Menu, re-introduced Keyboard applet with Wayland support, massive improvements to our desktop view, primary monitor selection, and more! See the 10.10.3 Budgie release announcement.

### What’s new in COSMIC Atomic

Fedora COSMIC Atomic comes with the [1.10.0 release of the COSMIC desktop][26].

### Universal Blue, Bluefin, Bazzite, Aurora and secureblue

Our friends in the [Universal Blue project][27] ([Bazzite][28], [Bluefin][29], [Aurora][30]) have prepared the update to Fedora 45. Look for upcoming [announcements in their Discourse][31].

As always, I heavily recommend checking them out, especially if you feel like some things are missing from the Fedora Atomic Desktops and you depend on them (NVIDIA drivers, extra media codec, out of tree kernel drivers, etc.).

If you have an interest in more security focused variants, I recommend taking a look at the [secureblue][32] project.

### What’s next

#### Roadmap to Bootable Containers and bootc / CoreOS / Atomic unification

A lot of work is happening to make the transition to Bootable Containers as smooth as possible for our existing users. You can look at the roadmap for this transition at [atomic-desktops#26][33].

Most of the progress in this release cycle was (again) focused on getting our bootable container images ready for general consumption in Fedora. A part of this work is being able to build them reliably in the Fedora Infra.

The people involved in the bootc, CoreOS and other Atomic variants are working on this effort as part of the new Atomic SIG. See [atomic#137][34] and the [project board][35].

#### Making it easier to derive images into Fedora Remix images

Work is in progress to make it easier to create derived container images from the Fedora Atomic Desktops images, notably in order to comply with the logo and branding policy.

Once this is ready, we may start publishing “Fedora Remix” branded container images of the Fedora Atomic Desktops. Those images will not include official Fedora branding and will thus be better suited for projects that want to layer their changes on top.

See [atomic-desktops#125][36] and [atomic-desktops#132][37].

#### Helping us with a few nasty bugs

If you have an interest in contributing to Fedora Atomic Desktops, here are some bugs that we will have to fix in the short term. We would greatly appreciate help with the following issues from the [ticket tracker][38]:

  * Fixing root mount options ([atomic-desktops#72][39]): This is a long standing and mostly invisible bug that impacts performance.
  * Moving away from nss-altfiles ([atomic-desktops#108][40]): This is another long standing source of issues that new users regularly face.



#### Where to reach us

We are looking for contributors to help us make the Fedora Atomic Desktops the best experience for Fedora users. The following are Matrix rooms that may be of interest to potential contributors:

  * [Atomic Desktops SIG][41]: [Organization on Fedora’s Forge][3], [#atomic-desktops:fedoraproject.org][42]
  * Silverblue: [Workstation W][43][o][43][rking Group][43], [#silverblue:fedoraproject.org][44]
  * Kinoite: [KDE SIG][45], [#kinoite:fedoraproject.org][46]
  * Sway Atomic: [Sway SIG][47], [#sway:fedoraproject.org][48]
  * Budgie Atomic: [Budgie SIG][49], [#budgie:fedoraproject.org][50]
  * COSMIC Atomic: [COSMIC SIG][51], [#cosmic:fedoraproject.org][52]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-linux-45/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/10/new_in_Atomic_desktop_45.svg
[2]: https://fedoramagazine.org/announcing-fedora-linux-45/
[3]: https://forge.fedoraproject.org/atomic-desktops
[4]: https://gitlab.com/fedora/ostree/ci-test
[5]: https://fedoraproject.org/wiki/Changes/AnacondaWebUIforFedoraWorkstation
[6]: https://fedoraproject.org/wiki/Changes/AnacondaWebUIforFedoraSpins
[7]: https://fedoraproject.org/wiki/Changes/Anaconda_WebUI_Fedora_Atomic
[8]: https://fedoraproject.org/wiki/Changes/Web_Based_Remote_Installation_Support_For_Atomic_Desktops
[9]: https://fedoraproject.org/wiki/Changes/BuildAtomicDesktopsWithImageBuilder
[10]: https://fedoraproject.org/wiki/Releases/45/ChangeSet
[11]: https://fedoraproject.org/wiki/Changes/Podman6
[12]: https://blog.podman.io/2026/07/introducing-podman-v6-0-0/
[13]: https://blog.podman.io/2026/06/podman-6-configuration-file-changes/
[14]: https://blog.podman.io/2026/08/podman-6-1-0-volume-renaming-machine-restarts-and-a-long-list-of-bug-fixes/
[15]: https://fedoraproject.org/wiki/Changes/oo7_Secrets_Service_Provider
[16]: https://fedoraproject.org/wiki/Changes/DrmPanicFrontend
[17]: https://release.gnome.org/51/
[18]: https://fedoramagazine.org/whats-new-fedora-workstation-45/
[19]: https://kde.org/announcements/plasma/6/6.7.0/
[20]: https://kde.org/announcements/frameworks/6/6.31.0/
[21]: https://kde.org/announcements/gear/26.08.0/
[22]: https://kde.org/announcements/plasma/6/6.8.0/
[23]: https://fedoramagazine.org/whats-new-in-fedora-kde-plasma-desktop-45/
[24]: https://github.com/swaywm/sway/releases/tag/1.12
[25]: https://buddiesofbudgie.org/blog/budgie-10-10-3-released
[26]: https://github.com/pop-os/cosmic-epoch/releases#release-epoch-1.10.0
[27]: https://universal-blue.org/
[28]: https://bazzite.gg/
[29]: https://projectbluefin.io/
[30]: https://getaurora.dev/
[31]: https://universal-blue.discourse.group/tag/announcements
[32]: https://secureblue.dev/
[33]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/26
[34]: https://forge.fedoraproject.org/atomic/tracker/issues/137
[35]: https://forge.fedoraproject.org/atomic/-/projects/750
[36]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/125
[37]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/132
[38]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues
[39]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/72
[40]: https://forge.fedoraproject.org/atomic-desktops/tracker/issues/108
[41]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[42]: https://matrix.to/#/#atomic-desktops:fedoraproject.org
[43]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[44]: https://matrix.to/#/#silverblue:fedoraproject.org
[45]: https://fedoraproject.org/wiki/SIGs/KDE
[46]: https://matrix.to/#/#kinoite:fedoraproject.org
[47]: https://fedoraproject.org/wiki/SIGs/Sway
[48]: https://matrix.to/#/#sway:fedoraproject.org
[49]: https://fedoraproject.org/wiki/SIGs/Budgie
[50]: https://matrix.to/#/#budgie:fedoraproject.org
[51]: https://fedoraproject.org/wiki/SIGs/COSMIC
[52]: https://matrix.to/#/#cosmic:fedoraproject.org
