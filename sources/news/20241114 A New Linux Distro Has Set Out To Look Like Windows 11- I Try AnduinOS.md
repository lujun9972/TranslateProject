[#]: subject: "A New Linux Distro Has Set Out To Look Like Windows 11: I Try AnduinOS!"
[#]: via: "https://news.itsfoss.com/anduin-os/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A New Linux Distro Has Set Out To Look Like Windows 11: I Try AnduinOS!
======
We take a brief look at AnduinOS, trying to mimic the Windows 11 look.
Is it worth it?
[![][1]][2]

Let's face it, the masses are set in their ways with [Windows][3], refusing to move away from the proprietary operating system because that is what they have been using since they got their first computer.

On the other hand, people who are searching for a change, where they don't have to buy pricey [Apple Mac][4] hardware, usually opt for an easy-to-use Linux distribution like Ubuntu, Linux Mint, Pop!_OS, or Fedora.

However, those distributions look and feel different from Windows 11, making it an issue for people who are used to the Windows interface. So, there are [Linux distributions that target to replace Windows 11][5].

That is where a new Linux distro called **AnduinOS** comes in.

Keep on reading to learn more. 🤓

🚧

Note that this distro is relatively new and is not likely to replace your daily driver/production system anytime soon. Do thorough research about it before trying it on your main system.

**Suggested Read** 📖

![][6]

### AnduinOS: The Windows Experience On Linux

![Reminds you of Windows 11, doesn't it?][7]

AnduinOS is **an open source operating system based on** [**Debian**][8], with the lead of the project — [Anduin Xue][9].

It seems there is an interesting approach for developing it. Even though AnduinOS is based on Debian, its software package base and Linux kernel are closely associated with Ubuntu Jammy Jellyfish aka [22.04 LTS][10]. The **configuration files for the distro show that it is Ubuntu** to ensure optimum compatibility with Ubuntu-specific software.

It is a brand-new distribution that tries to mix in the benefits of Debian and Ubuntu into one package.

AnduinOS received its first stable release back in September, with some **key features** of it being:

  * **A Small ISO Size**
  * **Active Development**
  * **Intuitive User Interface**



### My Impressions

I took the recently released AnduinOS 1.0.2 for a test run on a virtual machine on [Fedora 40][11], and **it performed really well**. The installation experience was a familiar one, with AnduinOS taking me through it without any problems.

![][12]

On boot, **the desktop immediately reminded me of Windows 11** , with a taskbar at the bottom that housed pinned apps and an application launcher. When I took a look under the hood, I found out that it was all powered by a customized version of [GNOME 42.9][13].

There was also a handy quick settings widget and a [weather widget][14] in the taskbar. That is a neat addition to comfort Windows users.

![Fastfetch is handy to show what a Linux distro's got.][15]

As for **the pre-installed applications** , there are many, like Firefox, Nautilus file manager, System Monitor, GNOME [Extensions][16] ( _has many pre-installed extensions_ ), and a few other GNOME apps.

For adding new apps, there is an App Store listing, but it is not a standalone app, but rather [a webpage][17], which lists out instructions to get popular apps.

![][18]

For package management via the terminal, you can find **** [**APT**][19] **installed by default** , but tools like [Flatpak][20] and [Snap][21] will have to be manually installed as AnduinOS does not ship with those by default.

Overall, it tries to get the look and feel right.

However, the software installation side is messy at the moment. If they want to target Windows users, they should feature a software center, not expect users to follow instructions to type in a command to install their favorite software.

Or, they can fix that part by shipping with Flatpak, and an app store listing them same via Flathub. Just a thought 🤔

Well, I know that no Linux distribution is perfect from every angle. However, considering they are trying to offer something in 2024, I would say they missed a significant part of the experience while focusing on the other.

**Suggested Read** 📖

![][22]

### Try AnduinOS

You can download the latest release of AnduinOS from its [official website][23], and should you run into any troubles during installation or usage, [the documentation][24] is a handy resource to fall back on.

[AnduinOS][23]

If you were searching for the source code, head to the project's [GitLab][25] and [GitHub][26] repos, both of which host the same files.

If you would like to learn more about how the development of AnduinOS came about, you can go through the [AnduinOS 1.0 release blog][27] ( _use a translator, as it is in simplified Chinese_ ).

**Suggested Read** 📖

![][6]

* * *

[Get It's FOSS Plus Membership][28]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/anduin-os/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.microsoft.com/windows
[4]: https://www.apple.com/mac/
[5]: https://itsfoss.com/windows-like-linux-distributions/
[6]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[7]: https://news.itsfoss.com/content/images/2024/11/AnduinOS_a.jpg
[8]: https://www.debian.org/
[9]: https://gitlab.aiursoft.cn/anduin
[10]: https://news.itsfoss.com/ubuntu-22-04-release/
[11]: https://news.itsfoss.com/fedora-40-release/
[12]: https://news.itsfoss.com/content/images/2024/11/AnduinOS_b.jpg
[13]: https://discourse.gnome.org/t/gnome-42-9-released/14014
[14]: https://extensions.gnome.org/extension/750/openweather/
[15]: https://news.itsfoss.com/content/images/2024/11/AnduinOS_c.jpg
[16]: https://itsfoss.com/gnome-shell-extensions/
[17]: https://docs.anduinos.com/Applications/Introduction.html
[18]: https://news.itsfoss.com/content/images/2024/11/AnduinOS_d.jpg
[19]: https://en.wikipedia.org/wiki/APT_(software)
[20]: https://flatpak.org/
[21]: https://en.wikipedia.org/wiki/Snap_(software)
[22]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[23]: https://www.anduinos.com/
[24]: https://docs.anduinos.com/
[25]: https://gitlab.aiursoft.cn/anduin/anduinos
[26]: https://github.com/Anduin2017/AnduinOS
[27]: https://anduin.aiursoft.cn/post/2024/9/1/anduin-os-10
[28]: https://itsfoss.com/#/portal/signup
