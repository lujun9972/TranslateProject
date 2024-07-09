[#]: subject: "Fedora 41 Workstation With GNOME To Be Wayland Only!"
[#]: via: "https://news.itsfoss.com/fedora-41-gnome-wayland/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora 41 Workstation With GNOME To Be Wayland Only!
======
Fedora's flagship ISO will only feature Wayland, ditching X11.
[![][1]][2]

If you have been staying in touch with the happenings in the Linux distribution space, then you may know that many popular projects are pushing for a [Wayland][3]-only future, with support for [X11][4] not being a priority anymore.

Ubuntu, for example, has been Wayland by default since 21.04, but, they only recently made Wayland [the default session][5] for NVIDIA users with 24.10 thanks to improvements in the proprietary driver and support for [explicit sync on Wayland][6].

On the desktop environment side, the [KDE Plasma 6][7] release made Wayland the default session, and GNOME is already on track for [a Wayland-only future][8], dropping X11 entirely.

Fedora, of course, was one of the first ones to debut with Wayland by default with the **GNOME flagship edition since version 25** , released back in 2016.

So, the next step, to entirely remove X11, was a long time in the making.

### X11 Gets The Boot: Wayland Is The New Favorite?

![Lock screen of a pre-release version of Fedora 41 Workstation][9]

Spotted first by [Phoronix][10], the Fedora Engineering Steering Committee ( _FESCo_ ) has [voted][11] in favor _(8 for, 0 against)_ of **dropping X11 support from the installation images** ( _ISOs_ ) for the GNOME edition of the upcoming Fedora Workstation 41 release.

This means that the flagship offering will now be Wayland-only by default. Despite this, the **GNOME X11 packages will remain in the repositories** , maintained by the GNOME SIG/Workstation WG, allowing users to add lost functionality back into their system, should they need it.

📋

In the future, X11 packages might be dropped entirely, even from the repos.

Of course, **existing users don't need to worry** , as they will not be affected by this change, and upgrading to newer Fedora releases (41+) won't remove the X11 session from their installations, this only affects new installations.

Those looking to run X11 apps can also breathe easy, as [Xwayland][12] is still going to be included in the installation image, enabling you to run apps that don't play nice with Wayland.

Even though the vote passed with an overwhelming majority, there were some things that were brought up by [Zbigniew Jędrzejewski-Szmek][13], which they think could possibly delay this implementation to Fedora 42.

They were worried that there could be situations where the lack of packages on the installation media could prevent the initiation of X11 as a fallback, which was known to work previously.

To which [Neal Gompa][14] added that:

> Right now, whatever we support now in GNOME Wayland is all that is available in the live environments, since it's impossible to select GNOME X11 for a user without a password.

> GNOME X11 is currently not being deleted from the distribution, it's merely going to require installation after initial install.
>
> This is only adding one more step for those who need/want GNOME X11.

In any case, this move has been approved, and it is coming. When I tested the pre-release version of Fedora 41 Workstation, it still had the X11 support intact. I expect it to be gone in the coming days.

If you want to see how it fares after the X11 removal, then you can get it from the [official index][15] after a few days from when this article was published.

[Fedora 41 Workstation (pre-release)][15]

🚧

I cannot stress this enough, but the pre-release is not meant for production use.

_💬 Are you happy with this move? Couldn't be more bummed out? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/fedora-41-gnome-wayland/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://wayland.freedesktop.org/
[4]: https://www.x.org/
[5]: https://news.itsfoss.com/ubuntu-24-10-nvidia-wayland/
[6]: https://news.itsfoss.com/explicit-sync-wayland/
[7]: https://news.itsfoss.com/kde-plasma-6/
[8]: https://news.itsfoss.com/gnome-wayland-xorg/
[9]: https://news.itsfoss.com/content/images/2024/07/Fedora_41_Pre-Release_Lockscreen.png
[10]: https://www.phoronix.com/news/Fedora-WS-Wayland-Only-ISOs
[11]: https://pagure.io/fesco/issue/3226
[12]: https://wayland.freedesktop.org/xserver.html
[13]: https://fedoraproject.org/wiki/User:Zbyszek
[14]: https://www.linkedin.com/in/ngompa
[15]: https://dl.fedoraproject.org/pub/fedora/linux/development/rawhide/Workstation/x86_64/iso/
