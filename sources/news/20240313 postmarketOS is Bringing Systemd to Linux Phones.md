[#]: subject: "postmarketOS is Bringing Systemd to Linux Phones"
[#]: via: "https://news.itsfoss.com/postmarketos-systemd/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

postmarketOS is Bringing Systemd to Linux Phones
======
Systemd is making its way to phones, with postmarketOS. This is an
interesting development.
postmarketOS is a security-focused, [open-source Android alternative][1] based on [Alpine Linux][2], which follows a modular approach to development. The whole operating system is divided into small packages that can be installed on devices sharing the same CPU architecture.

All of that, as a result, keeps [postmarketOS][3] quite bloat-free in nature, with the user also having the freedom to build it manually, while excluding any packages that they don't want on their smartphone.

Interestingly, with a recent announcement, the developers have now signalled a shift towards systemd, in a bid to improve how the development of postmarketOS progresses.

Let's see what they intend to do.

**Suggested Read** 📖

![][4]

**What's Happening:** The developers of postmarketOS are switching from using the [OpenRC][5] _init system_ to the [systemd][6] _init system_. If you didn't know, an _init system_ is among the first programs to run besides the kernel when a Linux distribution is booted.

The main reason behind this move was the fact that **OpenRC didn't go well when working with KDE Plasma or GNOME**. The developers had to use systemd [polyfills][7] ( _consider them to be a bridge_ ) to make those desktop environments behave well with OpenRC.

And, as you might have guessed, this was only an improvised solution that was not really a practical choice in the long term. Even though the devs would've liked to develop what they term as a “ _vaguely competitive alternative to systemd_ ”, they would rather focus on working on postmarketOS instead.

After thoughtfully considering the above, the developers moved on to address these issues simply by providing a systemd version of postmarketOS.

In conversation with [The Register][8], postmarketOS project member, [Oliver Smith][9] also added:

> KDE and GNOME stacks power three of the four most-used phone UIs that we have in postmarketOS: Plasma Mobile, GNOME Mobile, and Phosh.

> Our goal is to have postmarketOS become usable by regular folks, who are currently using iOS and Android. So if we don't support KDE and GNOME anymore, then we have no chance of making a system that works for the casual user.

That does seem like the logical choice. If you don't make a smartphone operating system as user-friendly as possible, would mainstream users ever bother to install an alternative to iOS and Android, such as postmarketOS?

The developers also shared **some** **advantages that switching to systemd brings** , such as in-built boot-time analysis, a socket activation feature to facilitate easy printer support, better privilege controls and more.

**When to Expect:** As it turns out, they have already made available a proof of concept (POC) version of postmarketOS with systemd on their [official index][10], with a GNOME build which works on a limited number of devices.

[postmaketOS (systemd) (POC)][10]

If you are interested in building your own image, you can head over to the [GitLab issue][11], which has the relevant instructions. But, for a stable build that you can just plop into your old smartphone, you will have to wait a little longer.

For more details on this switch to systemd, you can also refer to the official [announcement blog][12].

_💬 What do you think of this? Is the switch to systemd the right decision?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/postmarketos-systemd/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/open-source-alternatives-android/
[2]: https://alpinelinux.org/
[3]: https://postmarketos.org/
[4]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[5]: https://wiki.gentoo.org/wiki/Project:OpenRC
[6]: https://systemd.io/
[7]: https://en.wikipedia.org/wiki/Polyfill_(programming)
[8]: https://www.theregister.com/2024/03/11/postmarketos_goes_systemd/
[9]: https://ollieparanoid.github.io/
[10]: https://mirror.postmarketos.org/temp.fdcc091b56f5/
[11]: https://gitlab.com/postmarketOS/pmaports/-/issues/2632
[12]: https://postmarketos.org/blog/2024/03/05/adding-systemd/
