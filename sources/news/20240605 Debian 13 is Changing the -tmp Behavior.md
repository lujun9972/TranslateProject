[#]: subject: "Debian 13 is Changing the /tmp Behavior"
[#]: via: "https://news.itsfoss.com/debian-13-tmp-mounting/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Debian 13 is Changing the /tmp Behavior
======
Debian 13 has decided on a new way to mount the /tmp directory.
[![][1]][2]

Nowadays, most popular distributions use the [Tmpfs][3] file system to handle temporary files. When in use, such files are loaded onto volatile memory ( _RAM in this case_ ), instead of a persistent storage device like an SSD or Hard disk.

What this accomplishes is the removal of temporary files/folders after a reboot, resulting in saved storage space, and no clutter. Moreover, you also benefit from faster retrieval times compared to persistent storage devices.

Sure, there are disadvantages, such as on systems without enough swap space where Tmpfs could take over large amounts of memory, but that's an issue if you are running with a modest amount of RAM.

Surprisingly enough, Debian never really caught on to the trend. Going back to 2012, there were calls to switch to a tmpfs system of handling temporary files, but, it never really came to pass, until now, that is.

### Debian Finally Takes the Leap: Better Late than Never?

![][4]

Announced by Debian developer [Luca Boccassi][5] on the _debian-devel_ [mailing list][6]. **Debian has finally switched to a RAM-based Tmpfs system of handling /tmp files** for the upcoming [Debian 13 “Trixie”][7] release.

In this set up, /tmp would be a Tmpfs by default, with files over 10 days being deleted on new installations, and for /var/tmp, the allowance period is longer, with files over 30 days being deleted from the persistent storage.

This has **already been implemented in the testing builds of Debian Trixie**.

As I mentioned earlier, this is not something new, calls for it were made before too.

Luca [rekindled][8] an earlier discussion from 2020, which had mentioned how Debian's systemd implementation didn't match systemd's default behavior for handling /tmp and /var/tmp.

Of course, doing that led to a series of discussions and arguments among members before a decision was made.

One such argument was by [Michael Biebl][9], who feared about the potential effects of cleaning temporary files by default. He mentioned that “ _Defaults are defaults, they are trivially and fully overridable where needed if needed._ ”, and that gathering feedback from all affected parties was required to make an informed decision.

Luca replied with the following:

> It's impossible to have defaults that make everyone happy, there will
>  always be someone who doesn't like any choice one might pick (there
>  are people unhappy with the current ones too).

He also asked; “ _what would break where, and how to fix it?_ ”

In response to that, many reasonable questions were asked by others, but, ultimately, Luca went ahead with this change.

In my opinion, it is great to see Debian at long last joining other distros in implementing _Tmpfs_ and automatic deletion of files for the /tmp and /var/tmp folders*.* Not doing so has been allowing unnecessary junk files to clog up the local storage.

With this development, another question arises; **Will Ubuntu follow in a similar path?**

We all know that Ubuntu usually more or less conforms to what Debian does, unless it is the matter of [Snaps][10], then it does its thing. 😉

Needless to say, Ubuntu [has chosen][11] ( _comment #4_ ) to follow the same path, with one key difference, for now, they won't be extending the cleanup age for /tmp to the 30 days period, they intend to do it later.

Furthermore, they won't be backporting these changes to older Ubuntu releases.

After this decision was made public, [lively conversation][12] among the members of the community has ensued, with one person saying that:

> /var/tmp, IMO, shouldn't exist--the idea of temporary files that should persist beyond a reboot is tech debt, those files should exist under a proper /var/{cache,lib} directory. Podman uses this directory and it drives me nuts.

_💬 What do you think of the move? Did Debian pick the right course of action? Add your thoughts below!_

📋

Thanks [LWN][13] for bringing this to my attention. You guys do a great job! 😃

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/debian-13-tmp-mounting/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.kernel.org/doc/html/latest/filesystems/tmpfs.html
[4]: https://news.itsfoss.com/content/images/2024/06/debian-13-to-switch-rambased-temp-1.png
[5]: https://www.linkedin.com/in/luca-boccassi/
[6]: https://lists.debian.org/debian-devel/2024/05/msg00456.html
[7]: https://www.debian.org/releases/trixie/
[8]: https://lists.debian.org/debian-devel/2024/05/msg00014.html
[9]: https://salsa.debian.org/biebl
[10]: https://snapcraft.io/
[11]: https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1870585
[12]: https://news.ycombinator.com/item?id=40578414
[13]: https://lwn.net/SubscriberLink/975565/bcce68a68d82d63a/
