[#]: subject: "Good News! EA Is Expanding Its Anti-Cheat to ARM64, and Linux Could Be Next"
[#]: via: "https://itsfoss.com/news/ea-anti-cheat-expansion-plans/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Good News! EA Is Expanding Its Anti-Cheat to ARM64, and Linux Could Be Next
======

[![Warp Terminal][1]][2]

A listing on [Electronic Arts'][3] (EA) job portal has us wondering if the game developer finally considers Linux to be a platform _worthy_ of their support.

EA recently put up a listing for a [Senior Anti-Cheat Engineer, ARM64][4], looking for someone to join its SPEAR ( _Secure Product Engineering & Anti-Cheat Response_) team. The role is focused on expanding their in-house kernel-level anti-cheat solution, [EA Javelin][5], to run natively in [Windows on ARM64][6].

The person will be responsible for developing **a native _ARM64_ driver for Javelin** and porting the existing solution over from _x86_64_. Building and maintaining automated test pipelines to validate the anti-cheat on ARM hardware is also part of the job.

This makes sense given where the Windows handheld market is heading. ARM-based Windows devices are a growing segment, and as more players game on them, security solutions need to adapt.

![This warped gallery shows some sections of EA's job posting.][7]

**Where's Linux** , you ask? Look at the bottom of the responsibility requirements, and you will see the following:

> Chart a path for EA Javelin Anticheat to support additional OS and hardware in the future, such as Linux and Proton.

That one line is doing a lot of heavy lifting. It **points to EA at least thinking about bringing Javelin to the Linux kernel and to Proton**. It is clearly a long-term goal rather than an immediate one, as Windows on ARM64 is still _numero uno_.

Linux needs no introduction, but if you were thinking what the heck is [Proton][8]. It is a compatibility layer developed by [Valve][9], built on top of [Wine][10], that allows Linux users to run Windows games without needing a [Winslop][11] install.

The [Steam Deck][12], Valve's popular Linux-based handheld, relies heavily on it to run the vast majority of its game library. And when you look further, without Proton, many of the games playable on Steam Deck simply would not work on Linux.

### Things Are Looking Up?

Linux as a gaming platform has been gaining traction. The Steam Deck put it in the hands of a much wider audience, and the broader desktop Linux community has kept that momentum going.

The track record from big publishers, however, has not been great. EA itself pulled Linux and Steam Deck support for Apex Legends [in late 2024][13], arguing that the open nature of Linux made it harder to keep cheaters out. Rockstar followed a similar path, with GTA V Online [quietly kicking Linux users][14] after rolling out BattlEye.

Going back more, [Roblox joined the club in 2023][15], when its Hyperion anti-cheat blocked Wine entirely, ending years of unofficial Linux support. But **Linux gaming keeps growing regardless** , and game publishers who want a slice of that market will have to take note.

Then there's Sony, which seems to be going backwards, [pulling back from the PC gaming market][16] ( _paywalled, grr_ ) for its flagship single-player titles. Anonymous spokespersons from the company have disclosed that titles like [Ghost of Yōtei][17] and [Saros][18] will only be available on the [PlayStation 5][19] series of consoles.

**It is a strange time**. One major publisher is quietly hinting at Linux support in a job listing, while another is seemingly retreating from PC. For Linux gamers, the situation remains mixed, but at least someone is headed in the right direction.

* * *

💬 _Your thoughts? Is EA serious about Linux support, or is it just not that important to them?_

**Suggested Read 📖:** [_AI's RAM Hunger Finds a New Victim in the Orange Pi Neo Linux Handheld_][20]

![][21]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ea-anti-cheat-expansion-plans/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.ea.com/
[4]: https://jobs.ea.com/en_US/careers/JobDetail/Senior-Anti-Cheat-Engineer-ARM64/212781
[5]: https://www.ea.com/security/news/eaac-deep-dive
[6]: https://www.microsoft.com/en-us/software-download/windows11arm64
[7]: https://itsfoss.com/content/images/2026/03/ea-senior-anti-cheat-engineer-job-posting-1.png
[8]: https://github.com/ValveSoftware/Proton
[9]: https://www.valvesoftware.com/en/
[10]: https://www.winehq.org/
[11]: https://itsfoss.com/news/microsoft-angry-over-microslop/
[12]: https://store.steampowered.com/steamdeck/
[13]: https://itsfoss.com/news/apex-legends-drops-steam-deck/
[14]: https://itsfoss.com/news/linux-players-gta-v-support-dropped/
[15]: https://itsfoss.com/news/roblox-linux-end/
[16]: https://www.bloomberg.com/news/articles/2026-03-04/sony-pulls-back-from-playstation-games-on-pc
[17]: https://www.playstation.com/en-us/games/ghost-of-yotei/
[18]: https://www.playstation.com/en-us/games/saros/
[19]: https://www.playstation.com/en-us/ps5/
[20]: https://itsfoss.com/news/orange-pi-neo-delayed/
[21]: https://itsfoss.com/content/images/icon/android-chrome-512x512-315.png
