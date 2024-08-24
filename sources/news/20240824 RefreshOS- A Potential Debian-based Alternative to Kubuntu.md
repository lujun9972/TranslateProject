[#]: subject: "RefreshOS: A Potential Debian-based Alternative to Kubuntu"
[#]: via: "https://news.itsfoss.com/refreshos/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

RefreshOS: A Potential Debian-based Alternative to Kubuntu
======
It may not be too exciting, but it's an alternative to exist. What do
you think?
[![][1]][2]

In a never-ending stream of distributions [based on Debian][3], we sometimes get to see some options that offer something novel, something that sets them apart from the rest.

One such distribution is [RefreshOS][4], which offers a “fresh” ( _pun intended_ ) take on what a Debian-based Linux distribution can be. Initially released in 2022, it has been under the radar until now.

With this [First Look][5], we will see what it has to offer. 😃

### RefreshOS: Overview ⭐

![The Beagle is lost in thoughts][6]

This debian-based distro is the brainchild of [Jordan Tyler Burchett][7], a developer out of Rogersville, Tennessee. Originally, **RefreshOS used to be based on Kubuntu 20.04**.

But, with the recent RefreshOS 2.0 “ _Boundless Beagle_ ” release, the base is now [Debian 12][8] “Bookworm”, with **Linux kernel 6.1.0-23-amd64** powering it.

Some **key highlights** include:

  * The Beagle
  * Being User-Friendly
  * Having Sensible Defaults



#### Initial Impressions 👨‍💻

I tested RefreshOS on a [virtual machine][9] using [Boxes][10] on my Fedora 40-equipped laptop. When I first booted into the ISO, the [Calamares][11] installer showed up in the live environment, and I proceeded with installation right away.

![The Calamares installer on RefreshOS][12]

The **installation experience is nothing you have not already seen** on other distros, and it went ahead as one would expect. Nothing extraordinary to note, apart from the cool-looking RefreshOS branding.

![][13]

After the installation was done, I was taken to **a neat desktop** , which was running [KDE Plasma 5.27.5][14], with the **X11 session as the default**. At first glance, everything is almost like the vanilla experience ( _without changes)_ found on KDE Plasma, and it was nice.

_More on why I said “almost” later._ 😶‍🌫️

![][15]

The **application suite** mostly consists of the ones developed by KDE, except for apps like [Brave][16] as the web browser, [LXTerminal][17] as the terminal emulator, [Xfburn][18] for burning physical disks, and a few others.

![][19]

However, there was **an issue**. When I first launched Brave, [KWalletManager][20] popped up, asking me for a password. I entered the user password, but it didn't work. If you didn't know, this is used by other apps to store their secrets ( _password/logins_ ) behind encryption.

![Follow the screenshots left to right][21]

I resolved that issue by deleting the existing wallet named “ _kdewallet_ ”, and creating a new one with the same name. If you face that issue, do what I did. First, open Wallet Manager on RefreshOS, then go into the “ _File_ ” menu and select “ _Delete Wallet…_ ”.

Finally, create a new wallet by going into the same “ _File_ ” menu. You can follow what the screenshots above show; just ensure that you give it the same name as mentioned earlier.

![][22]

You may have noticed how RefreshOS **uses a different app launcher** than the usual one KDE Plasma has. That is thanks to the use of the [Avalon Menu][23], which, I think, is a more familiar experience for users switching from Windows.

![][24]

Of course, **you can change the default behavior** by right-clicking on the launcher, then going into the “ _Show Alternatives…_ ” menu and selecting “ _Application Launcher_ ”. Follow the images attached above for more info. 👆

You can choose from a full-screen application dashboard, two KDE app launchers, and the Plasma drawer. On the package management front, **RefreshOS doesn't come with Flatpak and Snap support by default** but comes equipped with the venerable [APT][25] installed by default.

The developers did that to maintain “ _a pure, vanilla experience_ ”, and I respect that.

But, if you'd like, **you can easily add the missing support** by following our guides on using [Flatpak][26] and [Snap][27].

#### Closing Thoughts

I was **impressed with the polished experience RefreshOS offers** , and that too on a newly integrated base, with me running it on a virtual machine. On bare metal, the overall experience should be even better.

I truly hope this distribution catches on as a viable alternative to Ubuntu for the people who want a “ _Klean_ ” KDE Plasma experience with a Debian base but without the “ _Snappiness_ ” of the former.

### 📥 Get RefreshOS

The latest release of RefreshOS can be sourced from the [official website][28], which also lists the older releases if you want to check those out.

Before you begin, do keep in mind that sometimes **the download mirrors are inconsistent** , resulting in slow downloads. In my case, using a [VPN][29] solved the issue.

I sincerely hope they add some more mirrors to cover various parts of the world.

[RefreshOS][28]

Should you run into any issues, the RefreshOS developers recommend visiting the [Debian][30] and [KDE][31] support pages.

For more info about this distro, you can give Jordan's [DEV blog][32] a read.

_💬 Are you going to try out RefreshOS? Do let me know how it goes in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/refreshos/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/debian-based-distros/
[4]: https://refreshos.org/
[5]: https://news.itsfoss.com/tag/first-look/
[6]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_a.jpg
[7]: https://x.com/JTBurchett
[8]: https://news.itsfoss.com/debian-12-release/
[9]: https://itsfoss.com/virtual-machine/
[10]: https://apps.gnome.org/Boxes/
[11]: https://calamares.io/
[12]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_b.jpg
[13]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_e2.jpg
[14]: https://kde.org/announcements/plasma/5/5.27.5/
[15]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_e.jpg
[16]: https://brave.com/
[17]: https://github.com/lxde/lxterminal
[18]: https://docs.xfce.org/apps/xfburn/start
[19]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_f.jpg
[20]: https://apps.kde.org/kwalletmanager5/
[21]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_g.jpg
[22]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_k-1.jpg
[23]: https://store.kde.org/p/1386465/
[24]: https://news.itsfoss.com/content/images/2024/08/Refresh_OS_l-1.jpg
[25]: https://en.wikipedia.org/wiki/APT_(software)
[26]: https://itsfoss.com/flatpak-guide/
[27]: https://itsfoss.com/install-snap-linux/
[28]: https://refreshos.org/downloads.html
[29]: https://itsfoss.com/best-vpn-linux/
[30]: https://www.debian.org/support
[31]: https://kde.org/support/
[32]: https://dev.to/jordantylerburchett/announcing-the-launch-of-refreshos-20-boundless-beagle-35eo
