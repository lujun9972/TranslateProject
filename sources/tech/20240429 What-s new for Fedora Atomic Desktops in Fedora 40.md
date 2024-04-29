[#]: subject: "What’s new for Fedora Atomic Desktops in Fedora 40"
[#]: via: "https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-40/"
[#]: author: "Timothée Ravier https://fedoramagazine.org/author/siosm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s new for Fedora Atomic Desktops in Fedora 40
======

![][1]

Image provide by the Fedora Team

[Fedora 40 has been released!][2] 🎉 So let’s see what comes in this new release for the Fedora Atomic Desktops variants (Silverblue, Kinoite, Sway Atomic and Budgie Atomic).

### Introducing Fedora Atomic Desktops[][3]

[][3]

As you might have guessed from the title, we are now called Fedora Atomic Desktops! See the [Introducing Fedora Atomic Desktops][4] Fedora Magazine article for all the details.

The summary is that the Fedora Atomic Desktops are made up of four atomic spins:

  * Fedora Silverblue
  * Fedora Kinoite
  * Fedora Sway Atomic (was Fedora Sericea)
  * Fedora Budgie Atomic (was Fedora Onyx)



And we have a [landing page on fedoraproject.org][5].

### Status update on bootloader updates (bootupd integration)[][6]

[][6]

Unfortunately, we could not land [bootupd][7] support in this release due to an issue found late in Anaconda’s handling of bootupd installations which relied on incomplete functionality in bootupd.

We will attempt to add bootupd again after the release, via an update.

If you encounter Secure Boot errors or need to update your bootloader in the meantime, you can try the instructions from [fedora-silverblue#543][8]. Make sure to have a Live USB ready in case you encounter an issue. Please make backups beforehand.

We are hoping to land improvements to bootupd that should simplify this process.

See: [atomic-desktops-sig#1][9].

### What’s new in Silverblue[][10]

[][10]

#### Latest GNOME release[][11]

[][11]

Fedora Silverblue comes with the latest [GNOME 46 release][12].

For more details about the changes that comes with GNOME 46, see [What’s new in Fedora Workstation 40][13] on the Fedora Magazine and [Fedora Workstation 40 – what are we working on][14] from Christian F.K. Schaller.

#### No longer overlay language packages (langpack) by default[][15]

GNOME Software will no longer overlay the langpack packages for your locale on the first update. This should make updates much faster as they won’t need to overlay packages anymore (unless you explicitly decide to overlay some packages).

If you are updating from a previous release, you will have to remove this overlayed package manually. For example:

1\. Find the overlayed package using rpm-ostree status:

```

    $ rpm-ostree status
    State: idle
    Deployments:
    ● fedora:fedora/40/x86_64/silverblue
                      Version: 40.20240410.1 (2024-04-10T03:43:23Z)
                       Commit: 2428fdbec13787633b3bcd79d4f002ab48582bae8c6a473ca357a1ad43573a94
                 GPGSignature: Valid signature by E8F23996F23218640CB44CBE75CF5AC418B8E74C
              LayeredPackages: langpacks-fr

      fedora:fedora/40/x86_64/silverblue
                      Version: 40.20240402.0 (2024-04-02T00:39:43Z)
                       Commit: 634c8097165e6aab2baeaca6ae6d1ea2a7f11fba9f4955297bcf0fc2507047be
                 GPGSignature: Valid signature by E8F23996F23218640CB44CBE75CF5AC418B8E74C
              LayeredPackages: langpacks-fr

```

2\. Remove the overlayed package and reboot:

```

    $ rpm-ostree uninstall langpacks-fr
    ...

```

Note that this will remove the dictionaries for the corresponding language from your system and thus for applications included in the image.

For Flatpaks, the dictionaries are downloaded according to the languages set in the Flatpak config. If you have set your preferred languages in GNOME Settings, this configuration should have been set already. For example:

```

    # Get the current config
    $ flatpak config --list
    languages: en;fr;de (default: en)
    extra-languages: *unset*

    # Set the languages to use
    $ flatpak config --set languages "en;fr"

```

See the [flatpak-config][16] documentation for more details.

Also note that with this change the translated man pages for system commands will also be removed. To get the man pages back, you can install them in a container using toolbox for example:

```

    $ toolbox create
    $ toolbox enter
    $ sudo dnf install man-pages-fr

```

See: [atomic-desktops-sig#14][17].

### What’s new in Kinoite[][18]

[][18]

#### KDE Plasma 6[][19][][19]

Fedora Kinoite ships with [Plasma 6, Frameworks 6 and Gear 24.02][20] ([Fedora Change][21]). See also [What’s New in Fedora KDE 40?][22] on the Fedora Magazine.

#### Wayland only

Fedora Kinoite is now Wayland only. Legacy X11 applications will run using XWayland. See [Fedora 40: X11 is now unsupported][23].

If you have an NVIDIA GPU and encounter issues, I recommend looking at Universal Blue images (see below), waiting for an upcoming NVIDIA driver update that will hopefully improve Wayland support or trying out the updated Nouveau / NVK stack for supported cards.

#### KDE Apps as Fedora Flatpaks

A subset of KDE Apps are now installed by default as Fedora Flatpaks by Ananconda for new installations. The Flatpaks are [not installed on updates][24] but you can install them from the Fedora Flatpak remote or from Flathub.

#### KDE Flatpaks on Flathub

Most KDE Apps are directly published and maintained on Flathub by the KDE community and we have mostly completed the transition to the Qt 6.6 and KDE Framework 6 Runtime.

You can track the progress for the remaining apps in [kde/teams/flathub#26][25].

### What’s new in Sway Atomic

Fedora Sway Atmoic comes with the latest [1.9 Sway release][26].

### What’s new in Budgie Atomic

Fedora Budgie Atomic ships with the latest release of the [Budgie Desktop 10.9][27] “release series”. Budgie 10.9 features some initial porting work to libxfce4windowing as it progresses towards its move to Wayland and redesigns its Bluetooth applet with new direct (dis-)connect functionality.

Additionally, Fedora Budgie Atomic ships with the latest Budgie Control Center and takes into use budgie-session. As Buddies of Budgie officially supports Fedora, Budgie Desktop has also received numerous backported bug fixes to provide Fedora users an even better experience.

You can learn more about the latest happenings in Budgie on the [Buddies of Budgie blog][28].

### What’s next

Unfortunately, this section will be short this time, as there has not been much progress on our future plans [since the last time][29].

We will provide an updated article when more information becomes available.

#### Teaser for improved update support in Discover for Kinoite

![][30]

### Universal Blue, Bluefin, Bazzite and Aurora

Our friends in the Universal Blue, Bluefin and Bazzite projects also released updates for their images.

Universal Blue is now considered [Generally Available][31] alongside [Bluefin][32].

For all your gaming needs, [Bazzite reached version 3.0][33], rebasing on our fresh Fedora 40 images.

They are also introducing [Aurora][34], a KDE Plasma and Kinoite based alternative to Bluefin. See the [Introduction to Aurora][35] post for all the details.

### Where to reach us

We are looking for contributors to help us make the Fedora Atomic Desktops the best experience for Fedora users.

  * Atomic Desktops SIG: [Wiki page][36], [Issue tracker][37], [#atomic-desktops:fedoraproject.org][38]
  * Silverblue: [Workstation Working Group][39], [#silverblue:fedoraproject.org][40]
  * Kinoite: [KDE SIG][41], [#kinoite:fedoraproject.org][42]
  * Sway Atomic: [Sway SIG][43], [#sway:fedoraproject.org][44]
  * Budgie Atomic: [Budgie SIG][45], [#budgie:fedoraproject.org][46]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-new-for-fedora-atomic-desktops-in-fedora-40/

作者：[Timothée Ravier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/siosm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/04/whats_new_Atomic_Fedora_40-816x346.jpg
[2]: https://fedoramagazine.org/announcing-fedora-linux-40/
[3]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#introducing-fedora-atomic-desktops
[4]: https://fedoramagazine.org/introducing-fedora-atomic-desktops/
[5]: https://fedoraproject.org/atomic-desktops/
[6]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#status-update-on-bootloader-updates-bootupd-integration
[7]: https://fedoraproject.org/wiki/Changes/FedoraSilverblueBootupd
[8]: https://github.com/fedora-silverblue/issue-tracker/issues/543#issuecomment-2048350047
[9]: https://gitlab.com/fedora/ostree/sig/-/issues/1
[10]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#whats-new-in-silverblue
[11]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#latest-gnome-release
[12]: https://release.gnome.org/46/
[13]: https://fedoramagazine.org/whats-new-fedora-workstation-40/
[14]: https://blogs.gnome.org/uraeus/2024/03/28/fedora-workstation-40-what-are-we-working-on/
[15]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#no-longer-overlay-langpacks-by-default
[16]: https://docs.flatpak.org/en/latest/flatpak-command-reference.html#flatpak-config
[17]: https://gitlab.com/fedora/ostree/sig/-/issues/14
[18]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#whats-new-in-kinoite
[19]: https://tim.siosm.fr/blog/wip/fedora-atomic-desktops-40.html#kde-plasma-6 (Permalink)
[20]: https://kde.org/announcements/megarelease/6/
[21]: https://fedoraproject.org/wiki/Changes/KDE_Plasma_6
[22]: https://fedoramagazine.org/whats-new-in-fedora-kde-40/
[23]: https://fedoraproject.org/wiki/KDE/X11_Unsupported
[24]: https://gitlab.com/fedora/ostree/sig/-/issues/8
[25]: https://invent.kde.org/teams/flathub/issues/-/issues/26
[26]: https://github.com/swaywm/sway/releases/tag/1.9
[27]: https://buddiesofbudgie.org/blog/budgie-10-9-released
[28]: https://buddiesofbudgie.org/blog
[29]: https://tim.siosm.fr/blog/2023/11/22/fedora-atomic-desktops-39/#whats-next
[30]: https://tim.siosm.fr/assets/images/kinoite-discover-update-size.png
[31]: https://universal-blue.discourse.group/t/universal-blue-is-now-generally-available/1233
[32]: https://universal-blue.discourse.group/t/bluefin-is-now-generally-available/1234
[33]: https://universal-blue.discourse.group/t/announcing-bazzite-3-0/1218
[34]: https://getaurora.dev/
[35]: https://universal-blue.discourse.group/t/introduction-to-aurora/1235
[36]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[37]: https://gitlab.com/fedora/ostree/sig/-/issues
[38]: https://matrix.to/#/#atomic-desktops:fedoraproject.org
[39]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[40]: https://matrix.to/#/#silverblue:fedoraproject.org
[41]: https://fedoraproject.org/wiki/SIGs/KDE
[42]: https://matrix.to/#/#kinoite:fedoraproject.org
[43]: https://fedoraproject.org/wiki/SIGs/Sway
[44]: https://matrix.to/#/#sway:fedoraproject.org
[45]: https://fedoraproject.org/wiki/SIGs/Budgie
[46]: https://matrix.to/#/#budgie:fedoraproject.org
