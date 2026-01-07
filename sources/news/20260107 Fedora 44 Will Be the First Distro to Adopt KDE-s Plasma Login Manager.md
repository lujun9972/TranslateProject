[#]: subject: "Fedora 44 Will Be the First Distro to Adopt KDE's Plasma Login Manager"
[#]: via: "https://itsfoss.com/news/fedora-44-plasma-login-manager/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora 44 Will Be the First Distro to Adopt KDE's Plasma Login Manager
======

[![Warp Terminal][1]][2]

KDE recently announced that Plasma 6.8 [will drop X11 support completely][3]. When that happens, the Wayland session will be the only one remaining.

But there's another major development underway in the KDE ecosystem, and Fedora is on course to become the first distribution to ship it.

### Plasma Login Manager is In

Fedora 44, which is set to release on [April 14, 2026][4], will ship with [Plasma Login Manager][5] (PLM) as the default login screen for all KDE variants. This replaces [SDDM][6], which has been the go-to for years.

Neal Gompa, a well-known Fedora contributor and KDE packager, [proposed the change][7] back in early December 2025, and [the FESCo approved it][8] yesterday.

The switch affects:

  * Fedora [KDE Plasma Desktop Edition][9]
  * Fedora [KDE Plasma Mobile Spin][10]
  * Fedora [Kinoite][11]



_All KDE-based_ [_Fedora Labs_][12] _will also get the change since they carry over packages from the_ [_Desktop Edition_][13] _._

According to the change proposal, this allows Fedora to " _continue providing the highest quality, leading edge integrated KDE Plasma experience_ " by using the recommended software stack.

If you didn't know, PLM is [a new login manager][14] that will release alongside KDE Plasma 6.6 in February. It is being prepped to support multi-monitor setups, HDR, virtual keyboards, full power management, and screen readers.

Going through the GitLab repository for Plasma Login Manager ( _linked above_ ), I noticed a warning about it being " _ **in a prototype state**_ " and not being recommended for general or production use.

Another person also had the same concerns, to which Neal [replied][15]:

> The information in the README is out of date with current estimate of usefulness. The production release is going to be part of Plasma 6.6. At this point, it’s been considered in a good enough state that efforts have begun to integrate it in KDE Linux as well.

> If it does indeed turn out to be problematic by the time freeze rolls around, it’s trivial to back out and switch back to SDDM.

_So, that's taken care of._ 😅

**As for you, the user** , you won't be seeing anything major shift unless you had a custom theme installed, then you will have to switch back to SDDM to regain the functionality.

The commands for doing that would be:

```

    sudo dnf install sddm sddm-kcm sddm-wayland-plasma

    systemctl enable --force sddm.service

```

#### You Can Test it Now!

🚧

Test it on a spare machine or a [virtual machine][16], as this is not meant for general or production use.

First, you have to install [Fedora Rawhide][17] and ensure that you run the `sudo dnf update` command before the next steps.

![][18]

Now, run the following command to get the Plasma Login Manager:

```

    sudo dnf install plasma-login-manager kcm-plasmalogin

```

When prompted, enter your password. Verify the packages and OpenPGP keys, then type ' _Y_ ' and hit _Enter_ to accept.

After that, run the following command to switch to the Plasma Login Manager:

```

    sudo systemctl enable --force plasmalogin.service

```

![][19]

And this one to reboot your computer:

```

    sudo reboot

```

If everything goes well, you should be shown the new Plasma Login Manager screen post-boot. **For me, it didn't work** when I tried testing it on a virtual machine, so your mileage may vary.

Anyhow, I like how Fedora is generally one of the first ones to adopt such new components, bringing us Linux users closer to the bleeding edge.

Via: [Phoronix][20]

* * *

**Suggested Read 📖:** [_Best Linux Distributions Based on KDE_][21]

![][22]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/fedora-44-plasma-login-manager/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/kde-plasma-to-drop-x11-support/
[4]: https://fedorapeople.org/groups/schedule/f-44/f-44-all-tasks.html#:~:text=Current%20Final%20Target%20date
[5]: https://invent.kde.org/plasma/plasma-login-manager
[6]: https://github.com/sddm/sddm
[7]: https://fedoraproject.org/wiki/Changes/PlasmaLoginManager
[8]: https://pagure.io/fesco/issue/3523
[9]: https://fedoraproject.org/kde/
[10]: https://fedoraproject.org/spins/kde-mobile
[11]: https://fedoraproject.org/atomic-desktops/kinoite/
[12]: https://fedoraproject.org/labs
[13]: https://itsfoss.com/news/fedora-kde-official/
[14]: https://blog.davidedmundson.co.uk/blog/a-roadmap-for-a-modern-plasma-login-manager/
[15]: https://discussion.fedoraproject.org/t/f44-change-proposal-plasmaloginmanager-selfcontained/175466/6
[16]: https://itsfoss.com/virtual-machine/
[17]: https://dl.fedoraproject.org/pub/fedora/linux/development/rawhide/Workstation/x86_64/iso/
[18]: https://itsfoss.com/content/images/2026/01/fedora-rawhide-plm-setup-1.png
[19]: https://itsfoss.com/content/images/2026/01/fedora-rawhide-plm-setup-3.png
[20]: https://www.phoronix.com/news/Fedora-44-KDE-To-Plasma-Login
[21]: https://itsfoss.com/best-kde-distributions/
[22]: https://itsfoss.com/content/images/icon/android-chrome-512x512-192.png
