[#]: subject: "SnowflakeOS: NixOS in a Frosty Package"
[#]: via: "https://news.itsfoss.com/snowflake-os/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

SnowflakeOS: NixOS in a Frosty Package
======
NixOS, but more? Try this!
Many users [get started with NixOS][1] by experimenting and finding out what suits them the best. However, for beginners, it might be too much to handle at first.

Then there are some who like to distro hop, always on the lookout for new distro options that they haven't tried yet.

With this first look, we will take a look at **a** [**NixOS**][2] **-based Linux distribution** called **“SnowflakeOS** ”, which focuses on being beginner-friendly while still appealing to the more seasoned users out there.

🚧

This distro is under active development, it is not recommended for production use.

### SnowflakeOS: What to Expect?

![][3]

A clean and minimal experience for starters. The lead developer, [Victor Fuentes][4], mentions that SnowflakeOS is similar to NixOS, but with “ _added tools and opinionated configuration_ ”.

When I checked it out, SnowflakeOS was powered by [Linux kernel 6.5][5] and had recently merged with the [Snowfall][6] organization to take advantage of its repositories.

#### Initial Impressions 👨‍💻

I tried installing it on a virtual machine, but, sadly, **it didn't go as expected** , and the installation failed. But, as you can see below, the installer does give you useful options to tweak your SnowflakeOS installation.

![][7]

I continued on to test out the live environment, and I noticed that SnowflakeOS featured a slightly older [GNOME 44.5][8] release, but that's not an issue, everything works as expected.

![][9]

SnowflakeOS also ships with a decent set of apps, most of which are from GNOME. There are apps like Geary, Maps, Cheese, XTerm and more.

![][10]

If the pre-installed apps don't cut it for you, then you can also make use of [Nix Software Center][11], which is an app store that was developed primarily for Nix and takes many cues from GNOME Software.

And, this goes without saying, but **you also get access to over 100,000 packages** from [Nixpkgs][12].

![][13]

All things considered, what SnowflakeOS offers in its current state is very impressive, and newer releases should improve upon that.

If you are interested in getting it, refer to the section below. 👇

### 📥 Get SnowflakeOS

You can grab the alpha release of SnowflakeOS from the [official website][14].

At the time of writing, there was no concrete release timeline for a beta release or even a stable release. But this is how it goes for major undertakings such as this.

[SnowflakeOS][14]

If you are interested in helping with the development of SnowflakeOS, then you can visit its [GitHub repo][15] to get started.

_💬 Would you use this NixOS derivative? Let me know below!_

**Suggested Read** 📖

![][16]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/snowflake-os/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/nixos-tutorials/
[2]: https://nixos.org/
[3]: https://news.itsfoss.com/content/images/2024/05/SnowflakeOS_a.png
[4]: https://github.com/vlinkz
[5]: https://news.itsfoss.com/linux-kernel-6-5-release/
[6]: https://snowfall.org/
[7]: https://news.itsfoss.com/content/images/2024/05/SnowflakeOS_b.png
[8]: https://discourse.gnome.org/t/gnome-44-5-released/17300/2
[9]: https://news.itsfoss.com/content/images/2024/05/SnowflakeOS_c.png
[10]: https://news.itsfoss.com/content/images/2024/05/SnowflakeOS_d.png
[11]: https://github.com/snowfallorg/nix-software-center
[12]: https://github.com/NixOS/nixpkgs
[13]: https://news.itsfoss.com/content/images/2024/05/SnowflakeOS_e.png
[14]: https://snowflakeos.org/
[15]: https://github.com/snowfallorg
[16]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
