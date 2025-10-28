[#]: subject: "What’s new for Fedora Atomic Desktops in Fedora Linux 43"
[#]: via: "https://fedoramagazine.org/whats-new-fedora-atomic-desktops-in-fedora-linux-43/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new for Fedora Atomic Desktops in Fedora Linux 43
======

![][1]

[Fedora Linux 43 has been released][2]! 🎉 So, let’s see what is included in this new release for the Fedora Atomic Desktops variants (Silverblue, Kinoite, Sway Atomic, Budgie Atomic and COSMIC Atomic).

## **Changes for all variants**

### zstd compressed initrds

Alongside the rest of Fedora, we are now compressing our initrds with the Zstandard (zstd) algorithm. This should make the initrd a bit smaller and the boot a bit faster.

See the [Fedora Change request][3] and the tracking issue [atomic-desktops-sig#34][4].

### 2 GB boot partition

Along with the rest of Fedora, systems will install with a 2GB _/boot_ partition. This should make things easier with the growing initrd sizes (mostly due to firmwares). Existing systems will require a backup and re-install to benefit from this change.

See the [Fedora Change request][5].

### wireguard-tools added

We are adding the wireguard-tools to all variants. Users will still need to use the graphic interface in their desktop environment to configure WireGuard connections. However, it should now be easier to debug issues using the wg tool. This change was decided too late to be included in the installation ISO but it will come via an update.

See [silverblue#390][6] and [kde-sig#381][7].

### plocate removed

We removed plocate from all variants.

See [atomic-desktops-sig#81][8].

## What’s new in Silverblue

### GNOME 49

Fedora Silverblue comes with the latest [GNOME 49 release][9].

For more details about the changes that alongside GNOME 48, see [What’s new in Fedora Workstation 43][10] on the Fedora Magazine.

### Workaround for Third Party page hang

We temporarily removed the Third Party page shown during the first boot as it was causing issues. Users will be asked if they want to enable Third Party repositories when they open GNOME Software.

This will be re-enabled once we figure out where the bug is.

See [silver][11][b][11][lue#650][11] and [atomic-desktops-sig#74][12].

### openssl added for GSConnect

We added the openssl command line tool to Silverblue, to make the GSConnect extension work without having to resort to package layering or sysexts.

See [silverblue#201][13].

## What’s new in Kinoite

### KDE Plasma 6.4

Fedora Kinoite ships with [Plasma 6.4][14], [Frameworks 6.18][15] and [Gear 25.08][16].

See also [What’s New in Fedora KDE Plasma Desktop 43?][17] on the Fedora Magazine.

### Weekly automatic updates by default

Updates will now be automatically applied on a weekly basis, for Flatpaks and the system. You can configure the frequency or disable auto-updates in the system settings.

See the [Fedora Change request][18] and the tracking issue [kde-sig#342][19].

## What’s new in Sway Atomic

Fedora Sway Atomic comes with the latest [1.11 Sway release][20].

## What’s new in Budgie Atomic

Fedora Budgie Atomic comes with the latest [10.9.3 Budgie release][21]. Budgie 10.9.3 is a bug-fix and GNOME 49 compatibility release.

## What’s new in COSMIC Atomic

Fedora COSMIC Atomic comes with the latest beta release of the COSMIC desktop.

## Changes in unofficial images

### XFCE Atomic & LXQt Atomic dropped in Fedora 43

Starting with Fedora 43, we will no longer build XFCE Atomic & LXQt Atomic unofficial images.

## Universal Blue, Bluefin, Bazzite and Aurora

Our friends in the [Universal Blue project][22] ([Bazzite][23], [Blu][24][e][24][fin][24], [Aur][25][o][25][ra][25]) have prepared the update to Fedora 43. Look for upcoming [announcements in their Discourse][26].

As always, I heavily recommend checking them out, especially if you feel like some things are missing from the Fedora Atomic Desktops and you depend on them (NVIDIA drivers, extra media codec, out of tree kernel drivers, etc.).

## What’s next

### Roadmap to Bootable Containers

The next major evolution for the Atomic Desktops will be to transition to [Bootable Containers][27]. See also the [Fedora bootc documentation][28].

We have established a roadmap ([atomic-desktops-sig#26][29]) and we need your help to make this a smooth transition for all of our existing users.

### New home for the Fedora sysexts

We have moved the systemd system extensions (sysexts) to a [new GitHub o][30][rganization][30]. The sysexts are now split between those built exclusively from Fedora packages and those built from various community sources. Make sure to update your systemd-sysupdate configs to point to the new URLs.

### Moving to Fedora’s new Forge based on Forgejo

Now that [Fedora’s new forge is available][31], we will start moving our repos there. You can find the new organization at [forge.fedoraproject.org/atomic-desktops][32]. We will likely start by moving the documentation and then issue tracker and the sources.

## Where to reach us

We are looking for contributors to help us make the Fedora Atomic Desktops the best experience for Fedora users.

  * [Atomic Desktops SIG][33]: [New Fedora Forge organization][32], [Issue tracker (gitlab.com/fedora/ostree/sig)][34], [#atomic-deskt][35][o][35][ps:fedoraproject.org][35]
  * Silverblue: [Workstation Working Group][36], [#silverblue:f][37][e][37][doraproject.org][37]
  * Kinoite: [KDE SIG][38], [#kinoite:fedoraproject.org][39]
  * Sway Atomic: [Sway SIG][40], [#sway:fedoraproject.org][41]
  * Budgie Atomic: [Budgie SIG][42], [#budgie:fedoraproject.org][43]
  * COSMIC Atomic: [COSMIC SIG][44], [#cosmic:fedoraproject.org][45]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-fedora-atomic-desktops-in-fedora-linux-43/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/10/New_in_atomic_desktops_for_f43-816x345.jpg
[2]: https://fedoramagazine.org/announcing-fedora-linux-43/
[3]: https://fedoraproject.org/wiki/Changes/InitrdZstdDefault
[4]: https://gitlab.com/fedora/ostree/sig/-/issues/34
[5]: https://fedoraproject.org/wiki/Changes/2GbootPartition
[6]: https://github.com/fedora-silverblue/issue-tracker/issues/390
[7]: https://pagure.io/fedora-kde/SIG/issue/381
[8]: https://gitlab.com/fedora/ostree/sig/-/issues/81
[9]: https://release.gnome.org/49/
[10]: https://fedoramagazine.org/whats-new-fedora-workstation-43/
[11]: https://github.com/fedora-silverblue/issue-tracker/issues/650
[12]: https://gitlab.com/fedora/ostree/sig/-/issues/74
[13]: https://github.com/fedora-silverblue/issue-tracker/issues/201
[14]: https://kde.org/announcements/plasma/6/6.4.0/
[15]: https://kde.org/announcements/frameworks/6/6.18.0/
[16]: https://kde.org/announcements/gear/25.08.0/
[17]: https://fedoramagazine.org/whats-new-in-fedora-kde-plasma-desktop-43/
[18]: https://fedoraproject.org/wiki/Changes/KDEKinoiteAutoUpdateByDefault
[19]: https://pagure.io/fedora-kde/SIG/issue/342
[20]: https://github.com/swaywm/sway/releases/tag/1.11
[21]: https://github.com/BuddiesOfBudgie/budgie-desktop/releases/tag/v10.9.3
[22]: https://universal-blue.org/
[23]: https://bazzite.gg/
[24]: https://projectbluefin.io/
[25]: https://getaurora.dev/
[26]: https://universal-blue.discourse.group/tag/announcements
[27]: https://containers.github.io/bootable/
[28]: https://docs.fedoraproject.org/en-US/bootc/
[29]: https://gitlab.com/fedora/ostree/sig/-/issues/26
[30]: https://github.com/fedora-sysexts
[31]: https://communityblog.fedoraproject.org/forging-fedoras-future-with-forgejo/
[32]: https://forge.fedoraproject.org/atomic-desktops
[33]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[34]: https://gitlab.com/fedora/ostree/sig/-/issues
[35]: https://matrix.to/#/#atomic-desktops:fedoraproject.org
[36]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[37]: https://matrix.to/#/#silverblue:fedoraproject.org
[38]: https://fedoraproject.org/wiki/SIGs/KDE
[39]: https://matrix.to/#/#kinoite:fedoraproject.org
[40]: https://fedoraproject.org/wiki/SIGs/Sway
[41]: https://matrix.to/#/#sway:fedoraproject.org
[42]: https://fedoraproject.org/wiki/SIGs/Budgie
[43]: https://matrix.to/#/#budgie:fedoraproject.org
[44]: https://fedoraproject.org/wiki/SIGs/COSMIC
[45]: https://matrix.to/#/#cosmic:fedoraproject.org
