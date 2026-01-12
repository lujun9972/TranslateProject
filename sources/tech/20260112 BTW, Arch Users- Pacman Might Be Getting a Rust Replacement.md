[#]: subject: "BTW, Arch Users! Pacman Might Be Getting a Rust Replacement"
[#]: via: "https://itsfoss.com/news/pacman-rust-treatment/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

BTW, Arch Users! Pacman Might Be Getting a Rust Replacement
======

[![Warp Terminal][1]][2]

[Arch Linux][3] users know that Pacman is an essential piece of kit that handles everything from installing and removing software to managing dependencies and [keeping the entire system up to date][4].

But recent developments suggest there could be a successor in the works. A new project called [Arch Linux Package Management][5] (ALPM) has been making significant progress, and it's built entirely in Rust.

### Is Pacman Old News?

A recent [year-end report][6] from the Arch Linux development team has shed light on just how much work has gone into the ALPM project. It reveals that the [Sovereign Tech Fund][7]'s 15 months of funding have allowed the team to accomplish a lot.

During this funding period, **the devs completed six major milestones** , covering things like formal specifications for packaging data formats to cryptographic verification of distribution artifacts.

If you didn't know what the ALPM project is about, it is an undertaking that takes advantage of [Rust][8] to provide a suite of libraries and tools designed to handle every aspect of Arch Linux package management.

However, this has left many ( _including myself_ ) wondering **if Pacman will be replaced with this one day** , plus, there's talk of [a difference in the licensing][9] for the [ALPM][10] and [Pacman][11] projects.

While Pacman is licensed under the [GNU General Public License][12], ALPM uses dual licensing with [Apache 2.0][13] and [MIT][14].

Just so you understand, GPL is a " _copyleft_ " license that requires any derivative works to also be open source and GPL licensed, while MIT and Apache 2.0 are permissive licenses that allow the code to be used in proprietary software with fewer restrictions.

**GPL ensures improvements remain open to everyone, while MIT makes it easier for projects to adopt the code without legal complications**. As of writing, the developers haven't taken an official stance on whether this would replace Pacman.

Though, considering the compatibility with Pacman, we could see a backwards compatibility approach similar to [how sudo-rs was implemented on Ubuntu][15].

In that case, [Ubuntu started shipping sudo-rs as the default][16] while keeping the original sudo available as a fallback, with users continuing to type `sudo` as before while the system runs the newer Rust version underneath. A similar transition could happen with Pacman and ALPM, I think.

* * *

**Suggested Read 📖:** [_Getting Started With Pacman Commands_][17]

![][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/pacman-rust-treatment/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://archlinux.org/
[4]: https://itsfoss.com/pacman-syu/
[5]: https://alpm.archlinux.page/
[6]: https://devblog.archlinux.page/2026/a-year-of-work-on-the-alpm-project/
[7]: https://www.sovereign.tech/tech/arch-linux-package-management
[8]: https://rust-lang.org/
[9]: https://x.com/LundukeJournal/status/2010388666711961921
[10]: https://github.com/archlinux/alpm
[11]: https://gitlab.archlinux.org/pacman/pacman
[12]: https://www.gnu.org/licenses/gpl-3.0.en.html
[13]: https://www.apache.org/licenses/LICENSE-2.0
[14]: https://opensource.org/license/mit
[15]: https://itsfoss.com/sudo-vs-sudo-rs/
[16]: https://itsfoss.com/news/ubuntu-25-10-sudo-rs/
[17]: https://itsfoss.com/pacman-command/
[18]: https://itsfoss.com/content/images/icon/android-chrome-512x512-205.png
