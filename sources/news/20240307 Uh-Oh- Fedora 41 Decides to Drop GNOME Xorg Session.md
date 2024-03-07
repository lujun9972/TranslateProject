[#]: subject: "Uh-Oh! Fedora 41 Decides to Drop GNOME Xorg Session!"
[#]: via: "https://news.itsfoss.com/fedora-41-to-drop-xorg/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Uh-Oh! Fedora 41 Decides to Drop GNOME Xorg Session!
======
Fedora 41 is done with Xorg!
2024 seems to be a significant year for Wayland! We have been seeing a major shift towards its adoption lately, in ways previously unseen.

Take for instance [KDE Plasma 6][1], which defaulted to Wayland with the option to use X11 as a second choice, or Wine 9.0, which has already [started experimenting][2] with a Wayland driver earlier this year.

And, Fedora needs no introduction with Wayland. It has been using Wayland as its display server for a long time now.

However, now [Fedora][3] is all set to drop installing [X11][4] session by default on its flagship GNOME variant with the upcoming Fedora 41 release. Let's see what they plan to do.

![][5]

**What's happening:** What initially started off as [a suggestion][6] to no longer install GNOME Xorg sessions by default on Fedora, saw many key people from the Fedora community joining in and sharing their opinion.

**The consensus** was that they would be fine with removing X11 support from Fedora as long as it was documented properly, and users were able to easily switch back to the X11 session if they wanted to.

One of the community members was ready to get started on removing X11 from the Fedora 40 release, as it would have complemented the GNOME-equipped version of [Fedora Asahi Remix][7], where they do not provide any X11 packages.

But, others chipped in and pointed out that it is too late now, as Fedora 40 is too far ahead in its development cycle for such a major change.

They also added that they would have to vote on it, and that it would take a while.

Two weeks later, the [Fedora Workstation Working Group][8], which operates under [FESCo][9], had a meeting and **agreed on removing X11 support from Fedora 41 onwards** 😱

![][10]

Interestingly, something similar [was suggested][11] by GNOME dev Michael Catanzaro six months ago, but, that kind of died down. With this new push, and the approval by the Fedora Workstation WG, there are renewed hopes that this will finally see the light of day.

There are already two pull requests in place, one is for [splitting the X11 session][12] into a separate subpackage, and the other is to [mark the X11 session][13] subpackage as deprecated.

**Does it Matter?**

Yes!, you see, GNOME has already [started work][14] on dropping support for X11, and you already know that KDE Plasma now ships with Wayland by default.

Of course, this would give confidence to the distros trying to make the entire switch as well.

Including, but not limited to the [Linux Mint 21.3][15] (with experimental support) and the [KaOS 2024.01 release][16], with the ability to switch back to X11. They intend to ditch the X11 session in the near future.

Then there's the recently released [Fedora Asahi Remix 39][17] which follows a solid Wayland only approach, with support for HiDPI displays.

**When to Expect:** If you were to look at the [release cycle][18] of Fedora, then **sometime around October 2024 with Fedora 41** would be a good bet. If there are any delays, it might get pushed forward by a few weeks, but it should land around that time.

Reddit is already up and about over this decision by Fedora, and many are hopeful about this. A Redditor, Brage Fuglseth, [adds][19] that:

> Let’s hope that as many of the remaining Wayland issues as possible get resolved before the release of F41! Given that that happens, I’m really looking forward to even more of the Fedora community getting to experience Wayland in all its glory ✨

I agree with them on that. There are **plenty of issues with Wayland that need fixing** before it becomes the norm. I sincerely hope that the distro developers listen to community feedback before making major changes such as this.

When this happens, you need to install it manually to be able to use Xorg.

But, we have to start somewhere, right? Wayland is the way to go. X11 had a good run, but it's time for a change.

_💬 What do you think? Is a Wayland-only future viable for you?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/fedora-41-to-drop-xorg/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/kde-plasma-6/
[2]: https://news.itsfoss.com/wine-9-0-release/
[3]: https://fedoraproject.org/
[4]: https://en.wikipedia.org/wiki/X_Window_System
[5]: https://news.itsfoss.com/content/images/2024/03/Fedora_39_3.png
[6]: https://pagure.io/fedora-workstation/issue/414
[7]: https://news.itsfoss.com/fedora-asahi-remix-apple/
[8]: https://docs.fedoraproject.org/en-US/workstation-working-group/
[9]: https://docs.fedoraproject.org/en-US/fesco/
[10]: https://news.itsfoss.com/content/images/2024/03/fedora-issue-screenshot.jpg
[11]: https://pagure.io/fedora-workstation/issue/395
[12]: https://src.fedoraproject.org/rpms/gnome-shell-extensions/pull-request/3
[13]: https://src.fedoraproject.org/rpms/gnome-session/pull-request/12
[14]: https://news.itsfoss.com/gnome-wayland-xorg/
[15]: https://news.itsfoss.com/linux-mint-21-3-release/
[16]: https://news.itsfoss.com/kaos-2024-01-release/
[17]: https://news.itsfoss.com/fedora-asahi-remix-39-release/
[18]: https://en.wikipedia.org/wiki/Fedora_Linux_release_history
[19]: https://www.reddit.com/r/Fedora/comments/1b8d08g/comment/ktognax/
