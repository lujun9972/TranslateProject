[#]: subject: "Linux Mint Wants Fewer Releases Each Year (For Good Reasons)"
[#]: via: "https://itsfoss.com/news/linux-mint-longer-release-cycle/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Mint Wants Fewer Releases Each Year (For Good Reasons)
======

[![Warp Terminal][1]][2]

[Linux Mint][3] might be changing how often it releases new versions. Clement Lefebvre, the project lead, has revealed that the team is thinking about moving away from their current release schedule.

Currently, Linux Mint **follows a tight release timeline** where they ship a new release every six months, plus maintain and ship new releases of [Linux Mint Debian Edition][4] (LMDE).

The problem with this approach, as Clement adds, is that **the developers are spending more time fixing, testing, and releasing instead of developing features**. He further says that they have run out of codenames and that the next Linux Mint release will be based on an LTS release ( _presumably Ubuntu 26.04 LTS_ ).

If you were looking for my two cents on this, **I hope they extend their release schedule** , as rushing through things doesn't really help, especially when it is something as important as a widely popular Linux distro used by beginner and power users alike.

Clement wrapped up the announcement by sharing the following:

> Stay tuned, we’ll have more information on this. Obviously the codenames strategy doesn’t matter much, but we are very interested in adopting a longer development cycle.

### Wait, There's More!

The development cycle news wasn't the only thing he talked about. There are some notable improvements coming to Linux Mint, and one of them is a big deal for those waiting for [Wayland][5] support.

Anyone who is a regular on the [Linux Mint Forums][6] will know that there have been reliability issues with it. Clement has had to apologize for how slow and unreliable the forums were last month due to an overwhelming amount of traffic from bots, AI crawlers, and scripts that the server couldn't handle.

The team has since upgraded the server with 10x CPU capacity and doubled the bandwidth. They have also implemented better traffic filtering alongside the existing [Sucuri WAF][7] to keep the bad actors out.

They are also working on keyboard layout improvements after learning that some users prefer logical layouts that don't match their physical keyboard and **an entirely new Cinnamon screensaver**.

_**This is the final piece before Linux Mint gains full Wayland support.**_

You see, the current screensaver only works on X11 as a standalone GTK application. The new one will work on both Wayland and X11, natively rendered by Cinnamon's compositor.

This is expected to deliver smoother animations during screen lock and a more integrated look since it will use the same toolkit as the applets, panel, and menus.

Plus, there's **a new user administration tool** called `mintsysadm` coming to handle user accounts and details. It'll support home directory encryption during user creation, which was previously only available during OS installation, has webcam support for taking profile pictures, and includes [HiDPI support][8] for showing avatars clearly on modern displays.

* * *

**Suggested Read 📖:** [_Ubuntu Ditches The Software and Updates Tool_][9]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/linux-mint-longer-release-cycle/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://linuxmint.com/
[4]: https://linuxmint.com/download_lmde.php
[5]: https://wayland.freedesktop.org/
[6]: https://forums.linuxmint.com/
[7]: https://sucuri.net/website-firewall/
[8]: https://wiki.archlinux.org/title/HiDPI
[9]: https://itsfoss.com/news/ubuntu-software-and-updates-removal/
