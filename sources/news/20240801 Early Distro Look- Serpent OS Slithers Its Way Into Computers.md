[#]: subject: "Early Distro Look: Serpent OS Slithers Its Way Into Computers"
[#]: via: "https://news.itsfoss.com/serpent-os-alpha/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Early Distro Look: Serpent OS Slithers Its Way Into Computers
======
The much anticipated independent Linux distro by the original creator of
Solus.
[![][1]][2]

In today's time when Linux distributions based on Debian, Fedora, and Arch are everywhere, it's a breath of fresh air when I come across [independent distros][3] that try to be different from the rest.

One such distro has been [Serpent OS][4], which many people have been eagerly waiting for since the past few years. Luckily, for them, the wait is now almost over.

With this [First Look][5], we will be taking a close look at a very early build of Serpent OS that's surprisingly quite usable.

🚧

This is an under-development operating system that's not meant for production or general use.

### Serpent OS: The Snek Has Arrived 🐍

![][6]

As the brainchild of [Ikey Doherty][7], Serpent OS has been a long-time coming, with a [recent announcement][8] bringing us a pre-alpha release powered by a tweaked [Linux kernel 6.10][9].

During the announcement Ikey added that:

> This is a super rough version of Serpent OS that is capable of being installed on baremetal hardware and VMs that support UEFI and OpenGL acceleration. It is however not recommended for use daily due to the early nature and a bunch of packages being wildly out of date.

If you went through our [earlier coverage][10], you know that **Serpent OS takes a distro-first approach** to handling things, where things that hold Linux back won't be tolerated.

#### Initial Impressions 👨‍💻

For getting started with Serpent OS, I downloaded the pre-alpha installable ISO from the official website and loaded it up on a virtual machine [using VirtualBox on Ubuntu][11], sticking to the live environment.

Before I could go about testing the waters, I had to enable EFI and 3D acceleration to make the ISO boot. The latter of which was essential in me running the distro properly, without it the apps would refuse to launch, or stay open.

Additionally, keep in mind that **Serpent OS is a rolling-release** [**UEFI**][12] **-only distro** that doesn't support [legacy boot][13].

I will be dividing my observations into **three key highlights** for easy understanding:

  * **CLI Installer**
  * **Minimal Experience**
  * **Moss Package Manager**



##### CLI Installer

![][14]

As the project is so early in the development process, it ships with a CLI installer that allows users to install Serpent OS on their computers, but it **requires manual partitioning** before anything can happen.

As the development progresses, there will eventually be a better installer, and the live mode will be completely removed.

##### Minimal Experience

![][15]

As for the desktop experience, it was quite a minimal affair, with this early release of Serpent OS featuring [GNOME 45.3][16], alongside **a very limited set of pre-installed applications** that included:

  * Mozilla [Firefox][17]
  * GNOME [Text Editor][18]
  * GNOME [Extensions][19]
  * [Loupe][20] Image Viewer
  * [Nautilus][21] File Manager



Surprisingly, there's **no Flatpak support out-of-the-box** , users will have to manually install it if they want to use it.

##### Moss Package Manager

![][22]

[moss][23] is unquestionably **one of the most important highlights of Serpent OS** , it's a Rust-based package manager that facilitates atomic transactions for package management by creating self-contained transactions, with the option for rolling back to earlier states.

To put it simply, package updates implemented with moss do not have any impact on other packages, while also allowing for the possibility of rolling back to earlier versions in the event of any issues.

#### Closing Thoughts

Ikey has shared that **they intend to add more options to the installer** so that users can install the upcoming [COSMIC][24] desktop environment easily, which is already in the Serpent OS repos.

[Carl Richell][25], founder and CEO of System76, recently shared a [sneak peek][26] of how COSMIC would look on Serpent OS:

> COSMIC running on [@Serpent_OS][27] [pic.twitter.com/bjX2cn4z4B][28]
>
> — Carl Richell (@carlrichell) [July 28, 2024][29]

I was impressed with what I saw, **COSMIC appears to be a great pair-up for Serpent OS**. Users should keep this in mind when the first stable release drops if they want a brand-new experience compared to the usual GNOME.

### 📥 Get Serpent OS

If you head to the [official website][30], you will find the installable pre-alpha ISO. There are a few others on that page too, but they are outdated.

[Serpent OS][30]

**For installing Serpent OS** , you will have to manually partition the disks [using fdisk][31], then make use of the CLI installer to install it:

```

    sudo lichen

```

Just ensure that if running on a [virtual machine][32], enable EFI and 3D acceleration, or the ISO may not boot or work properly.

If you have any further questions, you can go through the [documentation][33] and the announcement blog linked above. Those searching for the source code can go to the project's [GitHub][34] page.

_💬 Could Serpent OS be your daily driver one day? Sticking with some other distro? Let me know below!_

**Suggested Read** 📖

![][35]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/serpent-os-alpha/

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
[4]: https://serpentos.com/
[5]: https://news.itsfoss.com/tag/first-look/
[6]: https://news.itsfoss.com/content/images/2024/08/Serpent_OS_a.jpg
[7]: https://www.linkedin.com/in/ikeydoherty/
[8]: https://serpentos.com/blog/2024/08/01/serpent-os-prealpha0-released/
[9]: https://news.itsfoss.com/linux-kernel-6-10-release/
[10]: https://itsfoss.com/serpent-os-announcement/
[11]: https://itsfoss.com/install-virtualbox-ubuntu/
[12]: https://en.wikipedia.org/wiki/UEFI
[13]: https://en.wikipedia.org/wiki/BIOS
[14]: https://news.itsfoss.com/content/images/2024/08/Serpent_OS_b.png
[15]: https://news.itsfoss.com/content/images/2024/08/Serpent_OS_c.jpg
[16]: https://discourse.gnome.org/t/gnome-45-3-released/18995
[17]: https://www.mozilla.org/en-US/firefox/
[18]: https://apps.gnome.org/TextEditor/
[19]: https://apps.gnome.org/Extensions/
[20]: https://news.itsfoss.com/loupe-image-viewer/
[21]: https://itsfoss.com/nautilus-tips-tweaks/
[22]: https://news.itsfoss.com/content/images/2024/08/Serpent_OS_d.png
[23]: https://github.com/serpent-os/moss
[24]: https://news.itsfoss.com/pop-os-cosmic/
[25]: https://www.linkedin.com/in/carl-richell-9435781/
[26]: https://x.com/carlrichell/status/1817664631508459884
[27]: https://twitter.com/Serpent_OS?ref_src=twsrc%5Etfw
[28]: https://t.co/bjX2cn4z4B
[29]: https://twitter.com/carlrichell/status/1817664631508459884?ref_src=twsrc%5Etfw
[30]: https://serpentos.com/download/
[31]: https://www.digitalocean.com/community/tutorials/create-a-partition-in-linux
[32]: https://itsfoss.com/virtual-machine/
[33]: https://docs.serpentos.com/
[34]: https://github.com/serpent-os
[35]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
