[#]: subject: "Arch Linux Guided Installer v2.8.1 Release Tests LVM Support!"
[#]: via: "https://news.itsfoss.com/archinstall-lvm/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Arch Linux Guided Installer v2.8.1 Release Tests LVM Support!
======
Experimental support for LVM sounds interesting.
[![][1]][2]

[Arch Linux][3] is a popular Linux distribution that I am sure needs no introduction. Many users flock to it thanks to its no-nonsense approach towards being a distro, and of course, the privilege to say “ _I use Arch, btw_ ” everywhere they go.

Like other distros, it too features some foundational components that make it such a great package, one such component has received a major update.

Months after the [previous release][4], **Arch Install 2.8.1** has arrived with a long-awaited feature that many had requested over the years.

Allow me to walk you through it.

### Archinstall 2.8.1: What's New?

![Source: Daniel Girtler][5]

Thanks to the contribution of Daniel Girtler, Arch Install now features **experimental support for the Logical Volume Manager** (LVM), allowing users to choose it as a default partitioning layout during installation.

Users also have **two encryption options** available, one is _LVM on LUKS_ , and the other is _LUKS on LVM_ , which have been tested to work with both systemd and GRUB.

Don't think that this is it for LVM support on Arch Install, Daniel has shared some ideas which will see the partitioning/LVM menu being reworked; as you can see above, it's not really that user-friendly.

Then there are the plans to support encryption for LVMs across partitions, an option to manually configure LVM, and to deal with pre-mounted LVM volumes for the _Pre-mount_ menu option.

You can check out Daniel's [pull request][6] for learning more about this implementation on Arch Install.

If you were wondering what Arch Install is. It is a guided/automated text-based installer for Arch Linux, which comes pre-configured with a few installers under it.

You can always refer to our tutorial that describes the process:

![][7]

As for [LVM][8], it is a storage method where partitions are independent of the disk layout, allowing for abstraction of storage, making it simpler to extend/shrink partitions with the help of “ _Virtual Partitions_ ”.

Of course, **that was not the only change with this release** , there were some other significant ones too:

  * Arch Install now features an updated Finnish translation
  * Adds a few [essential applications][9] to the Hyprland desktop profile
  * Addresses [an issue][10] with unmounting all partitions
  * Features initial work on a new menu implementation [using curses][11], and refactoring of several core functions.



If this release piqued your interest, you can go through its [changelog][12] to learn more about it. For those who want to make the jump to this release, they can refer to its [GitHub][13] repo.

[Arch Install 2.8.1 (GitHub)][13]

_💬 What are your thoughts on this release? Happy that LVM support finally landed?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/archinstall-lvm/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://archlinux.org/
[4]: https://github.com/archlinux/archinstall/releases/tag/v2.8.0
[5]: https://news.itsfoss.com/content/images/2024/06/Arch_Install_LVM.png
[6]: https://github.com/archlinux/archinstall/pull/2104
[7]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[8]: https://wiki.archlinux.org/title/LVM
[9]: https://github.com/archlinux/archinstall/pull/2481
[10]: https://github.com/archlinux/archinstall/pull/2498
[11]: https://github.com/archlinux/archinstall/pull/2506
[12]: https://github.com/archlinux/archinstall/releases/tag/v2.8.1
[13]: https://github.com/archlinux/archinstall
