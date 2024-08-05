[#]: subject: "Manjaro Linux Starts Experimenting With An Immutable Offering"
[#]: via: "https://news.itsfoss.com/manjaro-immutable-experiment/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Manjaro Linux Starts Experimenting With An Immutable Offering
======
Manjaro Linux could become a more reliable option with immutability at
its core. What do you think?
[![][1]][2]

[Immutable Linux distributions][3] are a type of distro that are future-proof to quite some extent thanks to how they operate. In such systems, the core of the operating system is left untouched, with the root file system being read-only.

What this allows in is flexibility in handling updates, where a broken update wouldn't deem the operating system unrecoverable ( _looking at you Ubuntu_ ). Some popular options include [NixOS][4], [Vanilla OS][5], [Fedora Silverblue][6], etc.

You can find more [immutable distro options][7] in our list.

Of course, not everyone is a fan of such distros, with some believing that it's a gimmick.

This is where [Manjaro Linux][8] comes in, it's a community favorite [user-friendly Arch-based distro][9] that caters to a wide variety of use cases. Its developers have now dipped their toes into the immutable pond thanks to a recent announcement.

Let's see what they have been up to. 😃

🚧

This is an under-development Linux distro, general use or production use is not recommended.

### Manjaro Immutable: What to Expect?

![][10]

Introduced as **a community testing release** , Manjaro Immutable is powered by [Arkdep][11], the popular toolkit for creating immutable btrfs-based systems, and [Arkane Linux][12], an “ _opinionated, immutable, atomic, multi-root Arch-based distribution_ ”.

As this is **an experimental release** , the developers of Manjaro hope to collect feedback from the community to see how the tech underneath Manjaro Immutable fares in day-to-day use. Do keep in mind that this doesn't guarantee a full release someday.

When [asked][13] by a community member **whether this would become an official variant for Manjaro** , [Roman Gilg][14], CTO at Manjaro Linux said that:

> Our plan is definitely for it to become an official variant of Manjaro. With the community testing version we’re now gathering some feedback on what people expect from such a variant and what should still go in there or what could be slimmed down.

There was also [a question][15] asking **whether an ARM version was planned**.

To that, Manjaro developer [Dennis ten Hoove][16] added that it would be possible. However, it's untested, and nothing is planned as of now. But, they might try something in the future.

### 📥 Get Manjaro Immutable

You can get the community testing ISO from the official [download mirror][17].

You can either install it on bare metal, or opt for running it on a [virtual machine][18] using VirtualBox or QEMU. Do remember that **enabling EFI is mandatory** , and a minimum 32 GB of storage is required to install the thing.

[Manjaro Immutable (direct download)][17]

Users who want to go the extra mile can **provide feedback to the developers** by joining the dedicated [Matrix channel][19] for it, or by replying to the [initial announcement][20] on the Manjaro forum.

_💬 Are you looking forward to using an immutable Manjaro? Let me know below!_

**Suggested Read** 📖

![][21]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/manjaro-immutable-experiment/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/immutable-distro/
[4]: https://nixos.org/
[5]: https://news.itsfoss.com/vanilla-os-2-orchid/
[6]: https://fedoraproject.org/silverblue/
[7]: https://itsfoss.com/immutable-linux-distros/
[8]: https://manjaro.org/
[9]: https://itsfoss.com/arch-based-linux-distros/
[10]: https://news.itsfoss.com/content/images/2024/08/Manjaro_Immutable_Testing.jpg
[11]: https://github.com/arkanelinux/arkdep
[12]: https://news.itsfoss.com/arkane-linux/
[13]: https://forum.manjaro.org/t/manjaro-immutable-out-now-for-community-testing/166364/2
[14]: https://www.linkedin.com/in/roman-gilg/
[15]: https://forum.manjaro.org/t/manjaro-immutable-out-now-for-community-testing/166364/14
[16]: https://github.com/dennis1248
[17]: https://download.manjaro.org/manjaro-gnome-immutable/20240801/manjaro-gnome-immutable-2024.08.01-x86_64.iso
[18]: https://itsfoss.com/virtual-machine/
[19]: https://matrix.to/#/%23Manjaro-Immutable:matrix.org
[20]: https://forum.manjaro.org/t/manjaro-immutable-out-now-for-community-testing/166364
[21]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
