[#]: subject: "What’s new for Fedora Atomic Desktops in Fedora 41"
[#]: via: "https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-41/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new for Fedora Atomic Desktops in Fedora 41
======

![][1]

Background image by Yotam Guttman

[Fedora 41 has been released][2]! 🎉 So let’s see what arrives with the new releases for the Fedora Atomic Desktops variants (Silverblue, Kinoite, Sway Atomic and Budgie Atomic).

### bootupd enabled by default for UEFI systems (BIOS coming soon)

After a long wait and a lot of work and testing, bootloader updates are finally enabled by default for Atomic Desktops.

For now, only UEFI systems will see their bootloader automatically updated on boot as it is the safest option. Automatic updates for classic BIOS systems will be enabled in the upcoming weeks.

If you encounter issues when updating old systems, take a look at the [Manual action needed to resolve boot failure for Fedora Atomic Desktops and Fedora IoT][3] Fedora Magazine article which includes instructions to manually update UEFI systems.

Once you are on Fedora 41, there is nothing more to do.

See the [Enable bootupd for Fedora Atomic Desktops and Fedora IoT][4] change request and the tracking issue [atomic-desktops-sig#1][5].

### First step towards Bootable Containers: dnf5 and bootc

The next major evolution for the Atomic Desktops will be to transition to [Bootable Containers][6].

We have established a roadmap ([atomic-desktops-sig#26][7]) and for Fedora 41, we added dnf5 and [bootc][8] to the Bootable Container images of Atomic Desktops.

Those images are currently built in the Fedora infrastructure ([example][9]) but not pushed to the container registry.

The images currently available on [quay.io/fedora][10] ([Silverblue][11], [Kinoite][12], etc.) are mirrored from the ostree repository and thus do not yet include dnf5 and bootc.

Once [releng#12142][13] has been completed, they will be replaced by the Bootable Container images.

In the mean time, you can take a look at the unofficial images (see the [Changes in unofficial images][14] section below).

See the [DNF and bootc in Image Mode Fedora variants][15] change request and the tracking issue [atomic-desktops-sig#48][16].

### What’s new in Silverblue

#### GNOME 47

Fedora Silverblue comes with the latest [GNOME 47 release][17].

For more details about the changes that alongside GNOME 47, see [What’s new in Fedora Workstation 41][18] on the Fedora Magazine and [Fedora Workstation development update – Artificial Intelligence edition][19] from Christian F.K. Schaller.

#### Ptyxis as default terminal application

Ptyxis is a terminal for GNOME with first-class support for containers, and thus works really well with [Toolbx][20] (and [Distrobox][21]). This is now the default terminal app and it brings features such as native support for light/dark mode and user-customizable keyboard shortcuts.

See [Ptyxis][22]’ website.

#### Wayland only

Fedora Silverblue is now Wayland only by default. The packages needed for the X11 session will remain available in the repositories maintained by the GNOME SIG and may be overlayed on Silverblue systems that require them.

See the [Wayland-only GNOME Workstation Media][23] change request and the tracking issue: [atomic-desktops-sig#41][24].

### What’s new in Kinoite

#### KDE Plasma 6.2

Fedora Kinoite ships with [Plasma 6.2][25], [Frameworks 6.7][26] and [Gear 24.08][27].

See also [What’s New in Fedora KDE 41?][28] on the Fedora Magazine.

#### Kinoite Mobile

Kinoite Mobile is currently only provided as unofficial container images. See the [Changes in unofficial images][14] section below.

See the [KDE Plasma Mobile Spin and Fedora Kinoite Mobile][29] change request.

### What’s new in Sway Atomic

Fedora Sway Atomic comes with the latest [1.10 Sway release][30].

### What’s new in Budgie Atomic

Nothing specific this release. The team is working on Wayland support.

### Changes in unofficial images

Until we complete the work needed in the Fedora infrastructure to build and push official container images for the Atomic Desktops (see [releng#12142][13]), I am providing unofficial builds of those. They are built on GitLab.com CI runners, use the official Fedora packages and the same sources as the official images.

You can find the configuration and list on [gitlab.com/fedora/ostree/ci-test][31] and the container images at [quay.io/organization/fedora-ostree-desktops][32].

#### New unofficial images: Kinoite Mobile & COSMIC Atomic

With Fedora 41, we are now building two new unofficial images: Kinoite Mobile and COSMIC Atomic. They join our other unofficial images: XFCE Atomic and LXQt Atomic.

See [How to make a new rpm-ostree desktop variant in Fedora?][33] if you are interested in making those images official Fedora ones.

See the [KDE Plasma Mobile Spin and Fedora Kinoite Mobile][29] change request and the [Fedora COSMIC Desktop Environment Special Interest Group (SIG)][34] page.

#### Renaming the Sericea and Onyx unofficial images to Sway Atomic and Budgie Atomic

If you are using the [Sericea][35] or [Onyx][36] container images, please migrate to the new Atomic names for Sericea & Onyx ([sway-atomic][37] and [budgie-atomic][38]) as we will remove the images published under the old name soon, likely before Fedora 42.

We will likely rename the official container images as well.

### Smaller changes common to all desktops

#### Unprivileged updates

The polkit policy controlling access to the rpm-ostree daemon has been updated to:

  * Enable users to update the system without having elevated privileges or typing a password. Note that this change only applies to system updates and repository meta updates; no other operations.
  * Reduce access to the most privileged operations (such as changing the kernel arguments, or rebasing to another image) of rpm-ostree for administrators to avoid mistakes. Only the following operations will remain password-less to match the behavior of package mode Fedora with the dnf command:
    * install and uninstall packages
    * upgrade the image
    * rollback the image
    * cancel transactions
    * cleanup deployment



See the [Unprivileged updates for Fedora Atomic Desktops][39] change request and the tracking issue [atomic-desktops-sig#7][40].

#### “Alternatives” work again

The alternatives command ([alternatives(8)][41]) is now working on Atomic Desktops.

See the tracking issue [atomic-desktops-sig#51][42] for more details and documentation.

#### Fixes for LUKS unlock via TPM

Support for unlokcing a LUKS partition with the TPM is now included in the initramfs.

See the tracking issue [atomic-desktops-sig#33][43] and the in progress documentation [silverblue-docs#176][43].

### Universal Blue, Bluefin, Bazzite and Aurora

Our friends in the [Universal Blue][44] project have prepared the update to Fedora 41 already. For [Bazzite][45], you can find all the details in [Bazzite F41 Update: New Kernel, MSI Claw Improvements, VRR Fixes, Better Changelogs, GNOME 47 & More][46].

For [Bluefin][47] (and similarly for [Aurora][48]), see [Bluefin GTS is now based on Fedora 40][49].

I heavily recommend checking them out, especially if you feel like some things are missing from the Fedora Atomic Desktops and you depend on them (NVIDIA proprietary drivers, extra media codec, etc.).

### What’s next

We have made lot of progress [since the last time][50], thus this section is going to be more exciting!

#### Roadmap to Bootable Containers

As I mentionned in [First step towards Bootable Containers: dnf5 and bootc][51], the next major evolution for the Atomic Desktops will be to transition to [Bootable Containers][6]. See also the [Fedora bootc documentation][52].

We have established a roadmap ([atomic-desktops-sig#26][7]) and we need your help to make this a smooth transition for all of our existing users.

#### composefs

Moving to composefs is one of the items on the roadmap to Bootable Containers. composefs is the next step for ostree based systems and will enable us to provide better integrity and security in the future.

For Fedora 41, we moved [Fedora CoreOS and Fedora IoT][53] to [composefs][54].

For the Atomic Desktops, this is planned for Fedora 42 as we still have a few issues to resolve. See the [Enabling composefs by default for Atomic Desktops][55] change request and the tracking issue [atomic-desktops-sig#35][56].

#### Custom keyboard layout set on installation

This fix is important for setups where the root disk is encryptd with LUKS and the user is asked a passphrase on boot. Right now, the keyboard layout is not remembered and defaults to the US QWERTY layout. Unfortunately this fix did not land in time for Fedora 41 but this will be part of the Fedora 42 installations ISOs. Help us test this by installing systems from a Rawhide ISO to confirm that this issue is fixed.

If you are impacted by this issue, see the tracking issue [atomic-desktops-sig#6][57] for the manual workarounds.

#### Unifying the Atomic Desktops documentation

We would like to unify the documentation for the Fedora Atomic Desktops into a single one instead of having per desktop environments docs which are mostly duplicate of one another and need to be constantly synced.

See the tracking issue [atomic-desktops-sig#10][58].

### Where to reach us

We are looking for contributors to help us make the Fedora Atomic Desktops the best experience for Fedora users.

  * [Atomic Desktops SIG][59]: [Issue tracker (gitlab.com/fedora/ostree/sig)][60], [#atomic-desktops:fedoraproject.org][61]
  * Silverblue: [Workstation Working Group][62], [#silverblue:fedoraproject.org][63]
  * Kinoite: [KDE SIG][64], [#kinoite:fedoraproject.org][65]
  * Sway Atomic: [Sway SIG][66], [#sway:fedor][67][a][67][project.org][67]
  * Budgie Atomic: [Budgie SIG][68], [#budgie:fedoraproject.org][69]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-41/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/11/Whats_New_Fedora_41_Atomic_Desktops-816x345.jpg
[2]: https://fedoramagazine.org/announcing-fedora-linux-41/
[3]: https://fedoramagazine.org/manual-action-needed-to-resolve-boot-failure-for-fedora-atomic-desktops-and-fedora-iot/
[4]: https://fedoraproject.org/wiki/Changes/FedoraSilverblueBootupd
[5]: https://gitlab.com/fedora/ostree/sig/-/issues/1
[6]: https://containers.github.io/bootable/
[7]: https://gitlab.com/fedora/ostree/sig/-/issues/26
[8]: https://containers.github.io/bootc/
[9]: https://kojipkgs.fedoraproject.org/compose/rawhide/latest-Fedora-Rawhide/compose/Silverblue/x86_64/images/
[10]: https://quay.io/organization/fedora
[11]: https://quay.io/repository/fedora/fedora-silverblue?tab=tags
[12]: https://quay.io/repository/fedora/fedora-kinoite?tab=tags
[13]: https://pagure.io/releng/issue/12142
[14]: https://tim.siosm.fr/blog/2024/10/30/fedora-atomic-desktops-41/#changes-in-unofficial-images
[15]: https://fedoraproject.org/wiki/Changes/DNFAndBootcInImageModeFedora
[16]: https://gitlab.com/fedora/ostree/sig/-/issues/48
[17]: https://release.gnome.org/47/
[18]: https://fedoramagazine.org/whats-new-fedora-workstation-41/
[19]: https://blogs.gnome.org/uraeus/2024/06/14/fedora-workstation-development-update-artificial-intelligence-edition/
[20]: https://containertoolbx.org/
[21]: https://distrobox.it/
[22]: https://gitlab.gnome.org/chergert/ptyxis
[23]: https://fedoraproject.org/wiki/Changes/WaylandOnlyGNOMEWorkstationMedia
[24]: https://gitlab.com/fedora/ostree/sig/-/issues/41
[25]: https://kde.org/announcements/plasma/6/6.2.0/
[26]: https://kde.org/announcements/frameworks/6/6.7.0/
[27]: https://kde.org/announcements/gear/24.08.0/
[28]: https://fedoramagazine.org/whats-new-in-fedora-kde-41/
[29]: https://fedoraproject.org/wiki/Changes/Fedora_KDE_Plasma_Mobile
[30]: https://github.com/swaywm/sway/releases/tag/1.10
[31]: https://gitlab.com/fedora/ostree/ci-test
[32]: https://quay.io/organization/fedora-ostree-desktops
[33]: https://tim.siosm.fr/blog/2023/06/21/rpm-ostree-variants-fedora/
[34]: https://fedoraproject.org/wiki/SIGs/COSMIC
[35]: https://quay.io/repository/fedora-ostree-desktops/sericea?tab=tags
[36]: https://quay.io/repository/fedora-ostree-desktops/onyx?tab=tags
[37]: https://quay.io/repository/fedora-ostree-desktops/sway-atomic?tab=tags
[38]: https://quay.io/repository/fedora-ostree-desktops/budgie-atomic?tab=tags
[39]: https://fedoraproject.org/wiki/Changes/UnprivilegedUpdatesAtomicDesktops
[40]: https://gitlab.com/fedora/ostree/sig/-/issues/7
[41]: https://www.mankier.com/8/alternatives
[42]: https://gitlab.com/fedora/ostree/sig/-/issues/51
[43]: https://github.com/fedora-silverblue/silverblue-docs/pull/176
[44]: https://universal-blue.org/
[45]: https://bazzite.gg/
[46]: https://universal-blue.discourse.group/t/bazzite-f41-update-new-kernel-msi-claw-improvements-vrr-fixes-better-changelogs-gnome-47-more/4726
[47]: https://projectbluefin.io/
[48]: https://getaurora.dev/
[49]: https://universal-blue.discourse.group/t/bluefin-gts-is-now-based-on-fedora-40/4782
[50]: https://tim.siosm.fr/blog/2024/04/29/fedora-atomic-desktops-40/#whats-next
[51]: https://tim.siosm.fr/blog/2024/10/30/fedora-atomic-desktops-41/#first-step-towards-bootable-containers-dnf5-and-bootc
[52]: https://docs.fedoraproject.org/en-US/bootc/
[53]: https://fedoraproject.org/wiki/Changes/ComposefsAtomicCoreOSIoT
[54]: https://github.com/containers/composefs
[55]: https://fedoraproject.org/wiki/Changes/ComposefsAtomicDesktops
[56]: https://gitlab.com/fedora/ostree/sig/-/issues/35
[57]: https://gitlab.com/fedora/ostree/sig/-/issues/6
[58]: https://gitlab.com/fedora/ostree/sig/-/issues/10
[59]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[60]: https://gitlab.com/fedora/ostree/sig/-/issues
[61]: https://matrix.to/#/#atomic-desktops:fedoraproject.org
[62]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[63]: https://matrix.to/#/#silverblue:fedoraproject.org
[64]: https://fedoraproject.org/wiki/SIGs/KDE
[65]: https://matrix.to/#/#kinoite:fedoraproject.org
[66]: https://fedoraproject.org/wiki/SIGs/Sway
[67]: https://matrix.to/#/#sway:fedoraproject.org
[68]: https://fedoraproject.org/wiki/SIGs/Budgie
[69]: https://matrix.to/#/#budgie:fedoraproject.org
