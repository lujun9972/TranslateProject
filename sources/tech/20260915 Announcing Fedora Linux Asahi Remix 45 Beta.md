[#]: subject: "Announcing Fedora Linux Asahi Remix 45 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora_asahi_remix_45_beta/"
[#]: author: "Davide CavalcaNeal Gompa https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux Asahi Remix 45 Beta
======

![][1]

We are happy to announce the availability of Fedora Linux Asahi Remix 45 Beta. This pre-release will bring the [freshly announced][2] Fedora Linux 45 Beta to Apple Silicon Macs. We expect to announce general availability of Fedora Linux Asahi Remix 45 in about a month. This will coincide with the overall Fedora Linux 45 release.

[Fedora Linux Asahi Remix][3] is developed in close collaboration with the [Fedora Asahi SIG][4] and the [Asahi Linux][5] project. Fedora Asahi Remix 45 Beta includes all of the [Changes][6] from Fedora Linux 45. Notably, this is the first Fedora Asahi Remix release to include out of the box initial support for Apple M3, M3 Pro and M3 Max systems, which are now [officially supported][7] by Asahi Linux upstream. The GPU drivers to enable performant 3D acceleration on these M3 systems are not included at this point and will be available via a Mesa update in the future. This release also includes support for hardware accelerated H.264 and VP9 video decoding for all Apple Silicon systems; additionally, Apple M3 systems include support for AV1 decoding.

You can try out Fedora Asahi Remix 45 Beta today by following our [installation guide][8]. Existing systems, running Fedora Asahi Remix 43 or 44, can be updated following the usual Fedora [upgrade process][9]. Upgrades via Fedora Workstation’s Software application are unfortunately not supported and DNF’s [System Upgrade][10] plugin has to be used.

Since this is a beta release, we expect that you may encounter bugs or missing features. Please report any Remix-specific issues in our [tracker][11]. You may also reach out in our [Discourse forum][12] or our [Matrix room][13] for user support.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora_asahi_remix_45_beta/

作者：[Davide CavalcaNeal Gompa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/09/f45_asahi_remix_beta_rls-816x345.jpg
[2]: https://fedoramagazine.org/announcing-fedora-linux-45-beta/
[3]: https://fedora-asahi-remix.org/
[4]: https://fedoraproject.org/wiki/SIGs/Asahi
[5]: https://asahilinux.org/
[6]: https://fedoraproject.org/wiki/Releases/45/ChangeSet
[7]: https://asahilinux.org/2026/09/m2-episode-1/
[8]: https://docs.fedoraproject.org/en-US/fedora-asahi-remix/installation/
[9]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/#_upgrading_to_the_next_fedora_kde_release
[10]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[11]: https://pagure.io/fedora-asahi/remix-bugs/issues
[12]: https://discussion.fedoraproject.org/c/neighbors/asahi/92
[13]: https://matrix.to/#/#asahi:fedoraproject.org
