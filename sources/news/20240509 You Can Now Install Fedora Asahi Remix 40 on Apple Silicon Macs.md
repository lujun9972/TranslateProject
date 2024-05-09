[#]: subject: "You Can Now Install Fedora Asahi Remix 40 on Apple Silicon Macs"
[#]: via: "https://news.itsfoss.com/fedora-asahi-remix-40-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

You Can Now Install Fedora Asahi Remix 40 on Apple Silicon Macs
======
It's time to run Fedora 40 on your Apple Silicon computers.
Folks who want to try out Linux on their Apple Silicon-equipped Mac devices usually opt for [Asahi Linux][1], an open-source project that teamed up with [Fedora][2] back in 2023 to bring [the complete Linux experience][3] to Apple Silicon.

The very first result of that collaboration came in the form of the [Fedora Asahi Remix 39][4] release, received [very positively][5] by the community. We are now almost halfway into 2024, and there's a new Fedora Asahi Remix release.

Allow me to take you through the highlights of this release.

### Fedora Asahi Remix 40: What's New?

![][6]

Based on the recently introduced [Fedora 40][7], this release of Fedora Asahi Remix takes advantage of all the things that are offered with its base distro. It features things like **better network privacy** , **high-level systemd security hardening** , and **updated apps/packages**.

Asahi's developers also worked on bringing **support for OpenGL 4.6 and OpenGL ES 3.2 on Apple M1/M2 chips**. They achieved that by implementing a new driver that is conformant to the [OpenGL standards][8].

The developers have said to **expect better compatibility with modern OpenGL loads** such as Blender. You can dive into the technical aspects by referring to the blog by [Alyssa Rosenzweig][9], who works on the Asahi graphics driver.

On the desktop side of things, Fedora Asahi Remix 40 features two desktop environments that cater to different use cases and choices.

![An image of Plasma 6 for reference.][10]

The default desktop environment, KDE Plasma, has been updated to the [Plasma 6][11] release, which now features **a custom Calamares-based initial setup wizard**. You also get to take advantage of things like the **wide-ranging** **user interface improvements** , **a better Discover app** , **tweaked system settings** , and more.

![An image of GNOME 46 for reference.][12]

On the GNOME side, we now have the [GNOME 46][13] release, which features **updated core apps** , **a new online accounts system** , **better fractional support** , **a new default wallpaper** , **improved notifications** , and more.

### 📥 Get Fedora Asahi Remix 40

You can get this release by running the following command on a _macOS 13.5_ or _macOS 14.2_ -equipped device:

```

    curl https://fedora-asahi-remix.org/install | sh

```

After running that, just follow the prompts on the screen to get it installed. But, if you are an **existing user** , then you can follow the [upgrade guide][14].

The [official website][15] is also a great place to look if you have any doubts.

[Fedora Asahi Remix 40][15]

There are **two other variants** too: A minimal image, which allows you to fine-tune your experience, and a server image meant for setting up a server.

_💬 Do you have Fedora Asahi Remix installed on your Mac device? What do you think?_

**Suggested Read** 📖

![][16]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/fedora-asahi-remix-40-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://asahilinux.org/
[2]: https://fedoraproject.org/
[3]: https://news.itsfoss.com/fedora-asahi-remix-apple/
[4]: https://news.itsfoss.com/fedora-asahi-remix-39-release/
[5]: https://www.reddit.com/r/AsahiLinux/comments/18m3xmc/introducing_fedora_asahi_remix_39/
[6]: https://news.itsfoss.com/content/images/2024/05/Fedora_Asahi_Remix_40.jpg
[7]: https://news.itsfoss.com/fedora-40-release/
[8]: https://www.khronos.org/conformance/adopters/conformant-products/opengl
[9]: https://rosenzweig.io/blog/conformant-gl46-on-the-m1.html
[10]: https://news.itsfoss.com/content/images/2024/05/KDE_Plasma_6.png
[11]: https://news.itsfoss.com/kde-plasma-6/
[12]: https://news.itsfoss.com/content/images/2024/05/GNOME_46.png
[13]: https://news.itsfoss.com/gnome-46-release/
[14]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/
[15]: https://asahilinux.org/fedora/
[16]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
