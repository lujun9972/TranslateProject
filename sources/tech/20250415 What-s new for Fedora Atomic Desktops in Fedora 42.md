[#]: subject: "What’s new for Fedora Atomic Desktops in Fedora 42"
[#]: via: "https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-42/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new for Fedora Atomic Desktops in Fedora 42
======

![][1]

[Fedora 42 has been released][2]! 🎉 So let’s see what arrives with the new releases for the Fedora Atomic Desktops variants (Silverblue, Kinoite, Sway Atomic and Budgie Atomic).

### New COSMIC Atomic variant

The new [COSMIC desktop][3] has been packaged for Fedora and a new Atomic variant created for it thanks to [Ryan Brue][4]. It is not yet available on the website but should be soon. See [fedora-websites#351][5].

See the [Fedora change request][6].

### Changes for all variants

#### composefs enabled by default

Following Fedora CoreOS in Fedora 41, Fedora Atomic Desktops are now using [composefs][7] by default. This is an important first step towards better integrity for the system content.

**Note:** As a side effect of this change, the systemd-remount-fs.service unit may fail to start on your system. Until we find a good way to fix this, a workaround is available in the [atomic-desktops-sig#72][8] issue or in the [common iss][9][ue thread][9] on the forum.

See the [Fedora change request][10] and the tracking issue [atomic-desktops-sig#35][11].

#### Migration to a static GRUB config

As part of the move to composefs, we had to migrate systems to use a static GRUB config.

This also removes the duplicate entries in the boot menu for installations that pre-dates Fedora 41.

The transition will happen automatically during the first boot on Fedora 42. You can verify that it worked by looking at the status of the bootloader-update service:

```

    $ sudo systemctl status bootloader-update.service

```

We are still missing documentation on how to change some GRUB settings now that the configuration is static. See the tracking issue [atomic-de][12][sktops-sig#73][12].

#### Custom keyboard layout set on installation (for LUKS unlock)

This fix is important for setups where the root disk is encrypted with LUKS and the user is asked for a passphrase on boot. The keyboard layout is now set by Anaconda as a kernel argument during installation. If you want to later change the keyboard layout used for the LUKS password prompt, you will have to update the kernel argument.

Example to set the keyboard layout to the french keyboard:

```

    $ sudo rpm-ostree kargs --append=vconsole.keymap=fr

```

Example to replace an existing layout by another:

```

    $ sudo rpm-ostree kargs --replace=vconsole.keymap=de

```

See [atomic-desktops-sig#6][13].

#### No longer building for PPC64LE

According to the countme statistics, we did not have users on PPC64LE so we decided to stop building the Fedora Atomic Desktops for that architecture.

If you relied on those images, you can migrate to Fedora Bootc images (which are available for PPC64LE) or use a conventional Fedora package based installation.

See the [Fedora change request][14].

### What’s new in Silverblue

#### GNOME 48

Fedora Silverblue comes with the latest [GNOME 48 release][15].

For more details about the changes that alongside GNOME 48, see [What’s new in Fedora Workstation 42][16] on the Fedora Magazine and [Looking ahead at 2025 and Fedora Workstation and jobs on offer!][17] from Christian F.K. Schaller.

### What’s new in Kinoite

#### KDE Plasma 6.3

Fedora Kinoite ships with [Plasma 6.3][18], [Frameworks 6.11][19] and [Gear 24.12][20]. See also
[What’s New in Fedora KDE 42?][21] on the Fedora Magazine.

### What’s new in Sway Atomic

Nothing specific this release.

### What’s new in Budgie Atomic

The default software center for Budgie Atomic is now Plasma Discover. To rebase from Fedora 41 to 42, you will have to use the command line as rebasing via GNOME Software will move your system to Fedora Silverblue.

See: [fedora-budgie/project/issue/5][22].

### Changes in unofficial images

Until we complete the work needed in the Fedora infrastructure to build and push official container images for the Atomic Desktops (see [releng#12142][23] and [cloud-image-uploader#37][24]), I am providing unofficial builds of those. They are built on GitLab.com CI runners, using the official Fedora packages and the same sources as the official images.

You can find the configuration and list on [gitlab.com/fedora/ostree/ci-test][25] and the container images at [quay.io/organization/fedora-ostree-][26][desktops][26].

#### Container images signed with cosign (sigstore)

The unofficial container images are now signed with cosign. You can configure your system to verify the signature of the images using the instructions from the [project README][27].

#### Container images available for aarch64

We are now building all our variants for the aarch64 architecture as well.

#### Goodbye to Sericea and Onyx (now Sway Atomic & Budgie Atomic)

We have now removed all container images under these names. Use the new names:

  * Sericea: [sway-atomic][28]
  * Onyx: [budgie-atomic][29]



### Unofficial, experimental Fedora Asahi Remix Atomic Desktops

We are now producing unofficial, experimental bootable container images targeting Apple Silicon, using the packages from the Fedora Asahi Remix project.

The images are in a working state, but the installation procedure is not ready for general use. We thus only recommend that you give this a try if you are ready to help with the development or are ready to re-install you system and lose data.

See: [fedora-asahi-remix-atomic-desktops project on GitHub][30]

### Universal Blue, Bluefin, Bazzite and Aurora

Our friends in the [Universal Blue project][31] ([Bazzite][32], [Bluefin][33], [Aurora][34]) have prepared the update to Fedora 42. Look for upcoming [announcements in their Discourse][35].

I heavily recommend checking them out, especially if you feel like some things are missing from the Fedora Atomic Desktops and you depend on them (NVIDIA proprietary drivers, extra media codec, out of tree kernel drivers, etc.).

### What’s next

#### Roadmap to Bootable Containers

The next major evolution for the Atomic Desktops will be to transition to [Bootable Containers][36]. See also the [Fedora bootc documentation][37].

We have established a roadmap ([atomic-desktops-sig#26][38]) and we need your help to make this a smooth transition for all of our existing users.

#### Turning the sysext experiment into a good experience

Systemd system extensions (sysexts) are a new option when you need some applications available on your system and can not run them in containers or as Flatpaks for various reasons. They offer an alternative approach to package layering as they do not increase update time and can be enabled or disabled as needed.

Support for sysexts is still in development for the Atomic Desktops but they already provide advantages over package layering for some use cases. See the currently experimental project: [github.com/travier/fedora-sysexts][39].

#### Unifying the Atomic Desktops documentation

We would like to unify the documentation for the Fedora Atomic Desktops into a single one instead of having per desktop environment docs which are mostly duplicate of one another and need to be constantly synced.

See the tracking issue [atomic-desktops-sig#10][40] if you want to help us do that.

### Where to reach us

We are looking for contributors to help us make the Fedora Atomic Desktops the best experience for Fedora users.

  * [Atomic Desktops SIG][41]: [Issue tracker (gitlab.com/fedora/ostree/sig)][42], [#atomic-desktops:fedoraproject.org][43]
  * Silverblue: [Workstation Working Group][44], [#silverblue:fedoraproject.org][45]
  * Kinoite: [KDE SIG][46], [#kinoite:fedoraproject.org][47]
  * Sway Atomic: [Sway SIG][48], [#sway:fedoraproject.org][49]
  * Budgie Atomic: [Budgie SIG][50], [#budgie:f][51][e][51][doraproject.org][51]
  * COSMIC Atomic: [COSMIC SIG][52], [#cosmic:fedoraproject.org][53]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-42/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/new_in_atomic_desktops_for_f42.svg
[2]: https://fedoramagazine.org/announcing-fedora-linux-42/
[3]: https://system76.com/cosmic/
[4]: https://codeberg.org/ryanabx
[5]: https://gitlab.com/fedora/websites-apps/fedora-websites/fedora-websites-3.0/-/issues/351
[6]: https://fedoraproject.org/wiki/Changes/FedoraCOSMIC
[7]: https://github.com/containers/composefs
[8]: https://gitlab.com/fedora/ostree/sig/-/issues/72
[9]: https://discussion.fedoraproject.org/t/systemd-remount-fs-service-failed-on-fedora-atomic-desktops-42/148562
[10]: https://fedoraproject.org/wiki/Changes/ComposefsAtomicDesktops
[11]: https://gitlab.com/fedora/ostree/sig/-/issues/35
[12]: https://gitlab.com/fedora/ostree/sig/-/issues/73
[13]: https://gitlab.com/fedora/ostree/sig/-/issues/6
[14]: https://fedoraproject.org/wiki/Changes/AtomicDesktopsNoPpc64le
[15]: https://release.gnome.org/48/
[16]: https://fedoramagazine.org/whats-new-fedora-workstation-42/
[17]: https://blogs.gnome.org/uraeus/2025/02/03/looking-ahead-at-2025-and-fedora-workstation-and-jobs-on-offer/
[18]: https://kde.org/announcements/plasma/6/6.3.0/
[19]: https://kde.org/announcements/frameworks/6/6.11.0/
[20]: https://kde.org/announcements/gear/24.12.0/
[21]: https://fedoramagazine.org/whats-new-in-fedora-kde-42/
[22]: https://pagure.io/fedora-budgie/project/issue/5
[23]: https://pagure.io/releng/issue/12142
[24]: https://pagure.io/cloud-image-uploader/issue/37
[25]: https://gitlab.com/fedora/ostree/ci-test
[26]: https://quay.io/organization/fedora-ostree-desktops
[27]: https://gitlab.com/fedora/ostree/ci-test#setup-container-image-signature-verification
[28]: https://quay.io/repository/fedora-ostree-desktops/sway-atomic?tab=tags
[29]: https://quay.io/repository/fedora-ostree-desktops/budgie-atomic?tab=tags
[30]: https://github.com/fedora-asahi-remix-atomic-desktops/images
[31]: https://universal-blue.org/
[32]: https://bazzite.gg/
[33]: https://projectbluefin.io/
[34]: https://getaurora.dev/
[35]: https://universal-blue.discourse.group/tag/announcements
[36]: https://containers.github.io/bootable/
[37]: https://docs.fedoraproject.org/en-US/bootc/
[38]: https://gitlab.com/fedora/ostree/sig/-/issues/26
[39]: https://github.com/travier/fedora-sysexts
[40]: https://gitlab.com/fedora/ostree/sig/-/issues/10
[41]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[42]: https://gitlab.com/fedora/ostree/sig/-/issues
[43]: https://matrix.to/#/#atomic-desktops:fedoraproject.org
[44]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[45]: https://matrix.to/#/#silverblue:fedoraproject.org
[46]: https://fedoraproject.org/wiki/SIGs/KDE
[47]: https://matrix.to/#/#kinoite:fedoraproject.org
[48]: https://fedoraproject.org/wiki/SIGs/Sway
[49]: https://matrix.to/#/#sway:fedoraproject.org
[50]: https://fedoraproject.org/wiki/SIGs/Budgie
[51]: https://matrix.to/#/#budgie:fedoraproject.org
[52]: https://fedoraproject.org/wiki/SIGs/COSMIC
[53]: https://matrix.to/#/#cosmic:fedoraproject.org
