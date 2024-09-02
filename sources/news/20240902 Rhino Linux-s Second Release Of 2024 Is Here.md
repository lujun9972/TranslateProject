[#]: subject: "Rhino Linux's Second Release Of 2024 Is Here!"
[#]: via: "https://news.itsfoss.com/rhino-linux-2024-2-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Rhino Linux's Second Release Of 2024 Is Here!
======
Rhino Linux is making significant progress with these quickupdates!
[![][1]][2]

Being one of the [best rolling release distros][3] out there, Rhino Linux is a popular Ubuntu-based distribution that's been pretty regular with updates since its first release. They had a brief developmental pause earlier this year due to maintainer burnout, but they have resumed since.

Just two months after the [previous release][4], the developers of Rhino Linux have [introduced][5] a new release. Let's check it out! 😃

### Rhino Linux 2024.2: What to Expect?

![][6]

We start with the **updated Linux kernels on the three Rhino Linux variants** , with _Linux 6.10.7_ for the Generic ISO, _Linux 6.9.0-okpine_ for the Pine64 images, and _Linux 6.8.0-raspi_ for the Raspberry Pi images.

Similarly, **the installer sees major upgrades** , with support for the [Nix][7] package manager, expanded containerization options that include popular names like Docker, Podman, Distrobox, and the addition of some useful tools like [Flatseal][8], VirtualBox, QEMU, etc.

The developers have also **introduced a new Unicorn theme** , which is a GTK/XFWM4/Kvantum theme that is more purple than before, and encompasses the whole system, with many apps featuring the color scheme as well.

And, finally, we have the [revamped documentation][9] that the Rhino Linux developers built using [Nextra][10], a Next.js framework for creating content-focused websites. They have ensured that all the content from the old wiki was carried over, with them also integrating [Pacstall][11]'s wiki for a one-stop experience.

### Get Rhino Linux 2024.2

The [official website][12] lists the three different variants of Rhino Linux for desktops, Pine64 devices and Raspberry Pi devices. The source code can be found on [GitHub][13].

[Rhino Linux 2024.2][12]

**For existing users** , after backing up their data, they can run the following command to upgrade to this release:

```

    rpk update -y

```

_💬 Been using Rhino Linux for a long time? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/rhino-linux-2024-2-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/best-rolling-release-distros/
[4]: https://news.itsfoss.com/rhino-linux-2024-release/
[5]: https://rhinolinux.org/news-15.html
[6]: https://news.itsfoss.com/content/images/2024/09/Rhino_Linux_2024.2.png
[7]: https://itsfoss.com/ubuntu-install-nix-package-manager/
[8]: https://itsfoss.com/flatseal/
[9]: https://wiki.rhinolinux.org/
[10]: https://nextra.site/
[11]: https://github.com/pacstall/pacstall
[12]: https://rhinolinux.org/download.html
[13]: https://github.com/rhino-linux
