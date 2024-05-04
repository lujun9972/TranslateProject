[#]: subject: "Systemd Looks to Replace sudo with run0"
[#]: via: "https://news.itsfoss.com/systemd-run0/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Systemd Looks to Replace sudo with run0
======
It's time for a new sudo command?
[systemd][1] is a vital init system that is integrated tightly with many popular Linux distributions out there. It provides a system and service manager that runs just after the Linux kernel initializes, acting as the first process on boot (PID 1).

It has had its [share of controversies][2], but it is undoubtedly one of the most crucial building blocks of a Linux system.

Of similar significance is [sudo][3], a program that many of you might already be aware of. It lets users with a lower level of security privilege run commands as root to accomplish tasks that they otherwise couldn't perform.

With a [recent post][4] on Mastodon, the creator of systemd, [Lennart Poettering][5], announced **** an alternative to sudo called “ **run0** ” which aims to address a few pitfalls introduced by sudo.

### Moving Away from Sudo: What's Happening?

![][6]

Introduced as part of the upcoming systemd 256 release, run0 is a new tool that is a [symbolic link][7] used to fire up an existing tool called _“systemd-run_ ”. With this, you can expect similar behavior to sudo, but with the key difference of it not being a [SUID binary][8].

How run0 works is that it sends a query to the service manager to execute a command under the user's [UID][9]. It then allocates a new [PTY][10] for that and transfers the data both ways from the initial [TTY][11] to the newly created PTY.

Lennart also adds that:

> One could say, "run0" is closer to behaviour of "ssh" than to "sudo", in many ways. Except that it doesn't bother with encryption or cryptographic authentication, key management and stuff, but instead relies on the kernel's local identification mechanisms.

Even though he knew about OpenBSD's sudo alternative, “[doas][12]”, he mentions that it is still a SUID binary. The issue with those is that they feature a large attack surface that can easily be exploited, and any mistakes could lead to considerable ramifications.

Anyhow, among all those things, Lennart also shared that, by default, **run0 will change the color of the background** to a “reddish tone” when you are operating with elevated user rights, as a way to remind you of the fact.

If the default color is not your cup of tea, then you could use “ _\--background= color_ ”, where “ _color_ ” could be any one of the [ANSI colors][13]. You could also put “ _switch_ ” instead of “ _color_ ” to disable the coloring of the background.

When someone [asked][14] how the adoption of this tool might be, seeing that run0 is harder to type than sudo, Lennart added that:

> The command line of run0 is intentionally kept close to sudo's. But that's were the compatibility really ends, i.e. /etc/sudoers and so on we're never going to add compat for.

> From my perspective run0 should be fine already for a distro to replace sudo with. But let's see how this plays out, I am pretty sure there might be a feature or two we still need to add before the first distros decide it's ready to switch over.

After reading all that, you're maybe wondering.

### When will run0 Arrive?

As things stand now, **we already have the first release candidate (RC) for systemd 256** , which includes run0. That being said, we are just a few more RCs away from the final release, which is expected to come equipped with a stable run0 experience among other improvements.

If you can't wait, then you can check out systemd v256-rc1 on [GitHub][15].

[systemd v256-rc1][15]

_💬 Which one would you prefer to use, sudo or run0? Let us know in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/systemd-run0/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://systemd.io/
[2]: https://itsfoss.com/systemd-init/
[3]: https://www.sudo.ws/
[4]: https://mastodon.social/@pid_eins/112353324518585654
[5]: https://0pointer.de/blog/
[6]: https://news.itsfoss.com/content/images/2024/05/systemd_run0.png
[7]: https://linuxhandbook.com/symbolic-link-linux/
[8]: https://rootrecipe.medium.com/suid-binaries-27c724ef753c
[9]: https://linuxhandbook.com/uid-linux/
[10]: https://en.wikipedia.org/wiki/Pseudoterminal
[11]: https://itsfoss.com/what-is-tty-in-linux/
[12]: https://en.wikipedia.org/wiki/Doas
[13]: https://en.wikipedia.org/wiki/ANSI_escape_code
[14]: https://mastodon.social/@TheStroyer/112353498259021192
[15]: https://github.com/systemd/systemd/releases/tag/v256-rc1
