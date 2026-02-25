[#]: subject: "Someone is Bringing Fedora Linux to Phones (And It’s Not Red Hat)"
[#]: via: "https://itsfoss.com/news/fedora-pocketblue-remix-overview/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Someone is Bringing Fedora Linux to Phones (And It’s Not Red Hat)
======

[![Warp Terminal][1]][2]

The mobile Linux space is [more active than most people realize][3]. Projects like [postmarketOS][4], [Ubuntu Touch][5], and [KDE Plasma Mobile][6] have been chipping away at the idea that your phone or tablet has to run something made by Google or Apple.

And while none of them are household names yet, they are picking up real interest from power users who want more control over their hardware. Of course, most people stick with [Android][7] or [iOS][8], and that is fine.

Both platforms are mature, well-supported, and not going anywhere. But for the ones who want something genuinely open and free of platform lock-in, things are getting better.

One such offering is [Fedora Pocketblue Remix][9], which is a community-powered project that offers [Fedora Atomic][10] images for mobile devices.

🚧

This piece of software is a work-in-progress, don't risk your daily driver mobile device with this, use a spare!

### Fedora Pocketblue Remix: What's in Store?

![A Poco F1 device running Fedora Pocketblue Remix. Pic courtesy of Fish 🐟️ \(the lead dev\).][11]

Before getting into the project, first let's talk about what Fedora Atomic actually is and why it matters here.

Traditional Linux installations are what you might call "[ _mutable_][12]." You install packages, tweak configs, and over time the system drifts from its original state. That is fine for general use, but it can lead to breakage and makes it harder to reliably recover a broken system.

With Fedora Atomic, **the base system is read-only and stays that way**. Updates are applied as complete image swaps rather than individual package changes, similar in concept to how [SteamOS][13] handles updates on the Steam Deck. If something goes wrong, you can roll back to the previous image.

Pocketblue takes this foundation and adapts it for mobile hardware. Under the hood, it uses [OCI][14] containers, [OSTree][15], and [Bootc][16] to build and distribute system images. These are built on top of upstream Fedora Atomic images [Silverblue][17] and [Kinoite][18], so this is not a from-scratch derivative.

The available images vary slightly by device, **but most supported hardware gets five variants** with different interface options: _GNOME Desktop_ , _GNOME Mobile_ , _Plasma Desktop_ , _Plasma Mobile_ , and [_Phosh_][19].

📋

The Orange Pi 3 LTS gets one extra option, a TTY image for a headless, no-desktop setup.

**As for what's supported** , the current list includes the _Xiaomi Pad 5_ , _Xiaomi Pad 6_ , _OnePlus 6_ and _6T_ , _Xiaomi Poco F1_ , and the _Orange Pi 3 LTS_. As a side-note, the OnePlus 6/6T and Poco F1 both run on the [Qualcomm SDM845][20] chipset, which has seen strong mainline Linux support over the years thanks to community effort.

The source code lives on [GitHub][21], and [the documentation site][9] is a useful resource to get Fedora Pocketblue Remix installed on supported devices. There are also [Matrix][22] and [Telegram][23] communities for support and discussion.

[Fedora Pocketblue Remix][21]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/fedora-pocketblue-remix-overview/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/open-source-alternatives-android/
[4]: https://postmarketos.org/
[5]: https://www.ubuntu-touch.io/
[6]: https://fedoraproject.org/spins/kde-mobile/
[7]: https://www.android.com/
[8]: https://www.apple.com/os/ios/
[9]: https://pocketblue.github.io/
[10]: https://www.fedoraproject.org/atomic-desktops/
[11]: https://itsfoss.com/content/images/2026/02/fedora-pocketblue-remix-demo-runefish.jpg
[12]: https://www.ibm.com/think/topics/mutable-vs-immutable
[13]: https://store.steampowered.com/steamos/
[14]: https://opencontainers.org/
[15]: https://ostreedev.github.io/ostree/
[16]: https://github.com/bootc-dev/bootc
[17]: https://www.fedoraproject.org/atomic-desktops/silverblue/
[18]: https://www.fedoraproject.org/atomic-desktops/kinoite/
[19]: https://phosh.mobi/
[20]: https://www.qualcomm.com/processors/application-processors/products/sdm845
[21]: https://github.com/pocketblue/pocketblue
[22]: https://matrix.to/#/#pocketblue:federated.nexus
[23]: https://t.me/fedoramobility
