[#]: subject: "Fedora Asahi Remix 44 is now available"
[#]: via: "https://fedoramagazine.org/fedora-asahi-remix-44-is-now-available/"
[#]: author: "Davide CavalcaNeal Gompa https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Asahi Remix 44 is now available
======

![][1]

We are happy to announce the general availability of Fedora Asahi Remix 44. This release brings [Fedora Linux 44][2] to Apple Silicon Macs.

[Fedora Asahi Remix][3] is developed in close collaboration with the [Fedora Asahi SIG][4] and the [Asahi Linux][5] project. This release incorporates all of the exciting improvements brought by [Fedora Linux 44][2]. Fedora Asahi Remix 44 also retires our vendored Mesa and virglrenderer packages. Users who have not already manually done so will be automatically transitioned to the upstream Mesa and virglrenderer packages provided by the upstream Fedora repositories.

Fedora Asahi Remix offers [KDE Plasma 6.6][6] as our flagship desktop experience, with all of the new and exciting features brought by [Fedora KDE Plasma Desktop 44][7]. [Plasma Setup][8] replaces the previous Calamares-based setup wizard, providing a Plasma-native experience for user account creation and system setup. Additionally, Plasma Login Manager is now the default greeter and session manager, replacing SDDM. This applies to _new_ installs only; users upgrading from previous versions of Fedora Asahi Remix will not have their configuration changed.

A GNOME variant is also available, featuring [GNOME 50][9], with both desktop variants matching what Fedora Linux offers. Fedora Asahi Remix also provides a Fedora Server variant for server workloads and other types of headless deployments. Finally, we offer a Minimal image for users that wish to build their own experience from the ground up.

You can install Fedora Asahi Remix today by following our [installation guide][10]. Existing systems running Fedora Asahi Remix 42 or 43 can be updated following the usual Fedora [upgrade process][11]. Upgrades via GNOME’s Software application are unfortunately not supported; either KDE’s Plasma Discover or DNF’s [System Upgrade][12] command must be used.

Please report any Remix-specific issues in our [tracker][13], or reach out in our [Discourse forum][14] or our [Matrix room][15] for user support.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-asahi-remix-44-is-now-available/

作者：[Davide CavalcaNeal Gompa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/04/Fedora_Asahi_remix_44-816x345.jpg
[2]: https://fedoramagazine.org/announcing-fedora-linux-44/
[3]: https://fedora-asahi-remix.org/
[4]: https://fedoraproject.org/wiki/SIGs/Asahi
[5]: https://asahilinux.org/
[6]: https://kde.org/announcements/plasma/6/6.6.0/
[7]: https://fedoramagazine.org/whats-new-in-fedora-kde-plasma-desktop-44/
[8]: https://kde.org/announcements/plasma/6/6.6.0/#plasma-setup
[9]: https://release.gnome.org/50/
[10]: https://docs.fedoraproject.org/en-US/fedora-asahi-remix/installation/
[11]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/#_upgrading_to_the_next_fedora_kde_release
[12]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[13]: https://forge.fedoraproject.org/asahi/remix-bugs/issues
[14]: https://discussion.fedoraproject.org/c/neighbors/asahi/92
[15]: https://matrix.to/#/#asahi:fedoraproject.org
