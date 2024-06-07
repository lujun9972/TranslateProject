[#]: subject: "blendOS v4 Released With Android App Support"
[#]: via: "https://news.itsfoss.com/blendos-v4-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

blendOS v4 Released With Android App Support
======
blendOS's next big upgrade is here
[![][1]][2]

blendOS is a [future-proof immutable Linux distro][3] based on Arch Linux, which also acts as a unique immutable and atomic variant of the former.

I previously came across this when I covered the [blendOS v3 release][4], which was a game-changer for the project, with major changes and additions across the board. Almost a year later, we now have a new release.

Termed by its developers as “ _a groundbreaking release that redefines blendOS_ ”, the blendOS v4 release marks an important new chapter in the development of this relatively new Linux distro.

Join me as I explore this new release.

💡

Fun fact: blendOS's logo was inspired from our featured image when we first covered about the project.

## 🆕 blendOS v4: What's New?

![][5]

As a [rolling-release][6] distro, blendOS always keeps itself updated with the most recent advancements in the Linux world.

So, with this release we have **Linux kernel 6.9.3-arch1-1** powering it all, and [GNOME 46][7] being the default desktop environment, with other options like KDE Plasma, Xfce, Budgie, and MATE also being made available.

Moreover, starting with this release, **blendOS has become fully declarative** , allowing users to install any kernels, packages, and drivers from the various Arch repos and AUR.

You also get **support for Android applications** , which can be enabled through the “ _System_ ” app on Wayland sessions of GNOME and KDE Plasma.

Additionally, there is a new GUI application, paired with a CLI counterpart, that will let you **create custom containers** for emulating other distros such as Debian, Ubuntu, Fedora, and CentOS.

When this is used, packages such as _.deb_ , _.rpm_ , and _.apk_ will be installed to their relevant containers, and users would be able to launch them like any other app on their system.

![][8]

The developers gave an example of how this could be used:

> For instance, apt in a Debian container named deb can be accessed and used in the host shell as apt.deb.

> Any applications (GUI or CLI) open within containers are indistinguishable from native applications installed on the host, and automatically appear in the app grid/launcher if you're using a desktop environment.

That reminds of [QubesOS][9], which features something similar that is implemented on a more foundational scale.

In any case, to get more details on the new blendOS release, you can go through the official [announcement blog][10].

## 📥 Get blendOS v4

The [official website][11] lists many download mirrors for you to get the blendOS v4 release, but, at the time of writing, many of those were offline. I had downloaded from the German mirror “ _Sahilister_ ” to test this release out.

[blendOS v4][11]

If you need help with installation, the [documentation][12] is a great place to start. You will also find [instructions][13] to switch the desktop environment using the “ _tracks_ ” feature, if the default one (GNOME) is not your cup of tea.

Those interested in contributing to the development, or just want to look at the source code, can visit its [GitLab][14] repo.

**Suggested Read** 📖

![][15]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/blendos-v4-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/immutable-linux-distros/
[4]: https://news.itsfoss.com/blendos-v3-released/
[5]: https://news.itsfoss.com/content/images/2024/06/blendOS_v4-1.jpg
[6]: https://itsfoss.com/rolling-release/
[7]: https://news.itsfoss.com/gnome-46-release/
[8]: https://news.itsfoss.com/content/images/2024/06/blendOS_v4_b.jpg
[9]: https://news.itsfoss.com/qubes-os-4-2-release/
[10]: https://blendos.co/blog/2024/06/05/blendos-v4-released-arch-linux-made-immutable-declarative-and-atomic/
[11]: https://blendos.co/download/
[12]: https://blendos.co/install/
[13]: https://blendos.co/install/post-install/arch-user-guide/#switching-to-other-desktop-environments-or-a-clean-arch-like-system-tracks
[14]: https://git.blendos.co/blendOS
[15]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
