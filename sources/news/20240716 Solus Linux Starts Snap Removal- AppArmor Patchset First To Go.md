[#]: subject: "Solus Linux Starts Snap Removal: AppArmor Patchset First To Go"
[#]: via: "https://news.itsfoss.com/solus-linux-drop-snap/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Solus Linux Starts Snap Removal: AppArmor Patchset First To Go
======
Solus might be your next favorite distribution if you hate snaps.
[![][1]][2]

Solus is one of those Linux distributions that's [built from scratch][3]. Even though it has had its fair share of ups and downs, its developers have been able to consistently provide a reliable experience to their users.

Since some time, it has been shipping with pre-installed support for [Snaps][4], the infamous packaging format by Canonical. However, that is now changing.

For better or for the worse? I will leave that to you to decide. 🙃

### Removal of Snaps Begins: What To Expect?

![Solus 4.5][5]

[Announced][6] yesterday, the developers of Solus have dropped the AppArmor patchset provided by [Canonical][7] from their current Linux kernel branch, resulting in Snaps now running with “ _Partial_ ” confinement when using Solus's current kernel, their LTS kernel still has the patches, though.

If you were wondering whether AppArmor support was completely disabled, Solus team member [Rune Morling][8], clarified that in a [discussion][9] a few days ago, stating that:

> AppArmor support is still [enabled][10] in the kernel; it's only the Ubuntu-specific patchset necessary for snap confinement that has been dropped from my reading of the situation.

As for the “ _Partial confinement_ ” bit, the situation with it is quite perplexing.

My best guess is that it is a partial implementation of Snap confinement, and an inferior version of the “ _Strict_ ” level of confinement, which restricts snaps to run in isolation, with minimal access to the system.

But, here's the kicker, Canonical never really explained what that means in their [documentation][11], there's even an unresolved [bug report][12] that dates back to 2020, which outlines the same issue.

On Solus's part, the distro will start showing the following warning when a snap command is used:

> WARNING: snap is running with partial confinement. See [https://help.getsol.us/docs/user/software/third-party/snap][13] for details

Which can be hidden using:

> sudo snap hide-confinement-warning

Moving on, the above-mentioned **changes were done in a bid to reduce the maintenance overhead** for the developers. They now don't have to handle the patchset which contains over 60 individual patches, all maintained/updated by Canonical.

Which, according to the developers of Solus takes a long time, or sometimes doesn't even happen, with [Linux kernel 6.9][14] being an example of such an occurrence.

This also means that they no longer have to build ISO images on a team member's system, those can now be generated on their servers, making it easier to upload images to the download servers for their [OpenCollective][15] backers.

As for what's in store for the future, **the developers of Solus are aiming to completely remove support for Snap at the beginning of 2025**. They have made [Flatpaks][16] the go-to way for installing applications that aren't on Solus's repositories.

Users are advised to follow the [migration guide][17] to switch to Flatpak before the inevitable removal of Snap happens.

Of course, those who like using Snaps can follow the [official guide][18] to get it back. At the time of writing, it was not updated, but it should be when Snaps are completely removed from Solus.

_💬 As expected, not everyone is a fan of Snaps, and Solus is going to join one of the many distros out there, which don't ship with it. What are your thoughts on this?_

**Suggested Read** 📖

![][19]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/solus-linux-drop-snap/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/independent-linux-distros/
[4]: https://snapcraft.io/
[5]: https://news.itsfoss.com/content/images/2024/07/Solus_Linux_4.5_Snap.jpg
[6]: https://getsol.us/2024/07/15/dropping-apparmor-kernel-patches/
[7]: https://canonical.com/
[8]: https://fosstodon.org/@ermo
[9]: https://discuss.getsol.us/d/10750-dropping-apparmor-kernel-patches/15
[10]: https://github.com/getsolus/packages/blob/main/packages/l/linux-current/files/config#L9592
[11]: https://snapcraft.io/docs/snap-confinement
[12]: https://bugs.launchpad.net/snapd/+bug/1887204
[13]: https://help.getsol.us/docs/user/software/third-party/snap
[14]: https://news.itsfoss.com/linux-kernel-6-9-release/
[15]: https://opencollective.com/getsolus
[16]: https://flatpak.org/
[17]: https://help.getsol.us/docs/user/software/third-party/snap/
[18]: https://snapcraft.io/docs/installing-snap-on-solus
[19]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
