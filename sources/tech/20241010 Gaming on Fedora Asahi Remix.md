[#]: subject: "Gaming on Fedora Asahi Remix"
[#]: via: "https://fedoramagazine.org/gaming-on-fedora-asahi-remix/"
[#]: author: "Davide CavalcaNeal Gompa https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Gaming on Fedora Asahi Remix
======

![][1]

Better support for gaming on [Fedora Asahi Remix][2] has been a long standing user request. Today at [XDC 2024][3], we announced [the preliminary availability of our game playing toolkit][4], integrating x86 emulation with MS Windows compatibility. This toolkit, with the conformant [Vulkan 1.3][5] and [OpenGL 4.6][6] drivers, enables playing commercial AAA games on Apple Silicon Macs running Fedora Asahi Remix 40. For more details, see Alyssa’s [talk][7] and [blog][8] [p][8][ost][8] , or head over to our [documentation][9].

[Fedora Asahi Remix][2] is developed in close collaboration with the [Fedora Asahi SIG][10] and the [Asahi Linux][11] project. As part of our work on the Remix, we’ve also been working on a [Change][12] to integrate the FEX emulator into Fedora Linux 42. The goal is to provide a delightful out-of-box experience for users that want to run x86_32 and x86_64 binaries on their AArch64 systems. Today’s release provides a preview of this work. It allows us to perfect the integration and improve the experience on Apple Silicon systems. The aim is for Fedora KDE systems, on AArch64, to offer this functionality out of the box for all supported Fedora ARM desktop systems.

Please report any Remix-specific issues in our [tracker][13]. You may also reach out in our [Discourse forum][13] or our [Matrix room][14] for user support.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/gaming-on-fedora-asahi-remix/

作者：[Davide CavalcaNeal Gompa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/dcavalca/https://fedoramagazine.org/author/ngompa/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/10/Gaming_on_Fedora_Asahi_remix-816x345.jpg
[2]: https://fedora-asahi-remix.org/
[3]: https://indico.freedesktop.org/event/6/page/28-overview
[4]: https://alx.sh/gaming
[5]: https://www.khronos.org/conformance/adopters/conformant-products#submission_7910
[6]: https://rosenzweig.io/blog/conformant-gl46-on-the-m1.html
[7]: https://indico.freedesktop.org/event/6/contributions/284/
[8]: https://rosenzweig.io/blog/aaa-gaming-on-m1.html
[9]: https://docs.fedoraproject.org/en-US/fedora-asahi-remix/x86-support/
[10]: https://fedoraproject.org/wiki/SIGs/Asahi
[11]: https://asahilinux.org/
[12]: https://fedoraproject.org/wiki/Changes/FEX
[13]: https://discussion.fedoraproject.org/c/neighbors/asahi/92
[14]: https://matrix.to/#/#asahi:fedoraproject.org
