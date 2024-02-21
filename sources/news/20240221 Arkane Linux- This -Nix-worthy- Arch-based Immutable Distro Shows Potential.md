[#]: subject: "Arkane Linux: This 'Nix-worthy' Arch-based Immutable Distro Shows Potential"
[#]: via: "https://news.itsfoss.com/arkane-linux/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Arkane Linux: This 'Nix-worthy' Arch-based Immutable Distro Shows Potential
======
A GNOME-centered take on immutability with Arch Linux.
You know, there are plenty of [future-proof immutable Linux distros][1] out there that offer the advantages of immutability for those who like the security and stability offered by these distros.

For those who are not familiar with the concept, an immutable distro is one that makes sure that the core of the operating system is left untouched. It is made possible because the root file system of an immutable distro is read-only by default.

Arkane Linux is one such immutable distro that markets itself as “ _an opinionated, immutable, atomic, multi-root Arch-based distribution_ ”. Let's see how it holds up.

🚧

Before we begin, keep in mind that this distro is in active development. It may not be a suitable replacement for production.

### Arkane Linux: Overview ⭐

![][2]

The **Arch-based distribution** is offered in **two variants** , the flagship version of Arkane Linux is immutable with the GNOME desktop environment (DE), and the other one is a non-immutable variant also equipped with GNOME.

Of course, with the immutable variant, you can revert to the last deployment of the system if an update goes south.

It also tries to offer a **modern** **GNOME-centric minimal experience** (yet a full-featured user experience).

In other words, Arch Linux base ensures that you get the latest tech, and the distro will adopt newer GNOME apps/defaults over what you get with the vanilla GNOME experience.

If you are not a fan of that, you can easily change it to any other DE thanks to _Arkdep_ , a custom toolkit developed by the lead developer for Arkane Linux; more on that later.

Some **key highlights** of Arkane Linux include:

  * **Easily Adaptable**
  * **A Minimal Experience**
  * **Power of Immutability**



#### Initial Impressions 👨‍💻

I fired it up on a virtual machine using VirtualBox, but I had to ensure that EFI was enabled; otherwise it would not boot. For bare metal, you will need to ensure that UEFI is enabled in the BIOS before you set out to try out Arkane Linux.

On first boot, **the installer** started up with a language selection screen that had many popular languages.

![][3]

After I was done with that, **** a welcome screen popped up with a classy looking Fox, the logo/mascot for Arkane Linux.

![][4]

The next step was **the disk configuration menu** that allowed me to create new partitions, format disks, and even encrypt the disk with a PIN as shown below.

![][5]

Then came **the user setup** where I was able to set a username, password, enable automatic login, select the timezone and time/date formats.

![][6]

After everything was set, I began the installation. I had to rely on the terminal progress, as the default behavior is just a spinning circle, which didn't really let me know of the progress.

![][7]

Just a quick reboot later, after the installation was done, I was taken into this **minimal-looking desktop with a beautiful wallpaper**.

At the time of writing, Arkane Linux was running **GNOME 45.4** powered by **Linux kernel 6.7.5.** Of course, you can expect the latest kernel options with it as an Arch-based [rolling release][8] distro.

![][9]

The developer mentions that:

> By default Arkane Linux is configured with and to make use of currently relevant and/or upcoming technologies and software.

You can see the usual GNOME apps, and a couple of other useful GNOME Circle apps as extras like:

  * **Celluloid video player**
  * **Amberol music player**
  * **Sound Recorder**
  * **GNOME Boxes**
  * **Extension Manager**



And, Firefox was included as the default web browser.

Not just limited to the apps you see now. The team mentions that they will adopt newer GNOME apps as defaults if/when they mature to give you a modern user experience with every update.

![][10]

And finally, we have _Arkdep_ , which is a custom toolkit that the lead developer says is an “ _OS deployment manager_ ” and not a package manager. This can be used to build, deploy or even maintain immutable, btrfs-based, multi-root systems with ease.

![][11]

According to the dev, this uses a “more simplistic brute-force approach to immutability” where the entire core of the operating system is replaced when you update the base image.

They also [shared][12] a helpful example:

> As an experiment I build a KDE version, it took me 10 minutes to spin a KDE image adapted from the GNOME config.

If you are interested in learning more about _Arkdep_ , then you can refer to its [GitHub repo][13].

**Suggested Read** 📖

![][14]

### 📥 Get Arkane Linux

In its current form, Arkane Linux is **only available for AMD64 systems** , the developer intends to work on introducing more hardware support, with **support for RISC-V already in the works**. But, it will take some time.

Until then, you can head over to the [official website][15] to get the immutable flagship, or the non-immutable version.

[Arkane Linux][15]

If you are interested in the development of Arkane Linux, then you can head over to its [GitHub project][16] page or join its [Matrix chat][17].

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/arkane-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/immutable-linux-distros/
[2]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_a.jpg
[3]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_b.jpg
[4]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_c.jpg
[5]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_e.jpg
[6]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_h.jpg
[7]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_i.jpg
[8]: https://itsfoss.com/rolling-release/
[9]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_j.jpg
[10]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_l.jpg
[11]: https://news.itsfoss.com/content/images/2024/02/Arkane_Linux_m.jpg
[12]: https://www.reddit.com/r/linux/comments/1auaedi/arkane_linux_an_opinionated_immutable_atomic/
[13]: https://github.com/arkanelinux/arkdep
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://arkanelinux.org/downloads
[16]: https://github.com/arkanelinux
[17]: https://matrix.to/#/%23arkanelinux:matrix.org
