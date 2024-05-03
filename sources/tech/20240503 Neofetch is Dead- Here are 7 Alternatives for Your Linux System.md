[#]: subject: "Neofetch is Dead! Here are 7 Alternatives for Your Linux System"
[#]: via: "https://itsfoss.com/neofetch-alternatives/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Neofetch is Dead! Here are 7 Alternatives for Your Linux System
======

[![Warp Terminal][1]][2]

Neofetch, the favorite tool for [displaying system information in ASCII format in the terminal][3], is no longer being developed.

Its GitHub repository is now [archived][4]. It didn't see any development for the past three years anyway.

Neofetch developer Dylan's GitHub page says he has "taken up farming".

![Developer says he has taken up farming][5]

When I asked for proof, he sent me this photo.

![Is that a farm in ASCII format?][6]

Okay, I just made up the last part for humor purposes 😉

So, here's the deal. Neofetch is not being developed anymore. Although it is still available in the repositories of many distributions and will remain for a couple of more releases, I presume.

Still, it would be a good idea to use some actively developed tool to flex your Linux desktop setup.

Let me share a few worthy Neofetch alternatives for your ASCII needs.

### Fastfetch

Fastfetch is similar to Neofetch. It offers heavy customization possibilities, including tweaking the appearance of logos! You remember that [Neoftech was extremely customizable][7], don't you?

![Fastfetch][8]

Fastfetch uses JSONC (JSON with Comments) for configuration. If you are curious, there are [some presets available][9] for you to get started.

If you are using Ubuntu 22.04 or later, you can install it using the PPA. Yes, PPA to rescue even in the Snap world of Ubuntu.

```

    sudo add-apt-repository ppa:zhangsongcui3371/fastfetch
    sudo apt update
    sudo apt install fastfetch

```

For other distros like Arch Linux and Fedora, you can use their package managers to install fastfetch (if it is available).

[Fastfetch][10]

### screenFetch

screenFetch is a “Bash Screenshot Information Tool”, that can be used to generate system information along with the ASCII logo of the distribution. It is basically a bash script and is easily extendable.

I think screenFetch existed even before Neofetch 🤔

![screenFetch][11]

screenFetch is basically a bash script and is easily extendable.

To install screenFetch in Ubuntu, open a terminal and run:

```

    sudo apt install screenfetch

```

It is also available in the default repositories of Arch Linux, Fedora, etc.

[screenFetch][12]

### macchina

macchina is a system information fetching tool written in Rust 🦀 (some people would use it just for that)

It uses a TOML file for its configuration, which is usually placed at `~/.config/macchina/macchina.toml`.

![Macchina][13]

💡

If the configuration file is not showing any effect, you can specify it while running, like `macchina --config <location of config file>`.

macchina also offers a theming system that is outside the configuration file. This is also a TOML file, and they have an example theme called [Hydrogen][14]!

You can either use the pre-built binary [available to download from the releases page][15], or install it to your system.

It's a Rust tool, so you can [install cargo first][16] and then use it for the installation:

```

    cargo install macchina

```

It is also available to install from AUR for [Arch Linux users][17].

[macchina][18]

### NerdFetch

Written in shell script, NerdFetch is a [POSIX compatible][19] system information fetching tool. It uses Nerd fonts. So, to get the most out of it, you need to have [a Nerd font][20] installed.

![NerdFetch][21]

Apart from default, NerdFetch works in three more modes, like:

  * Use `-c` for Cozette: May need [Cozette font][22]
  * Use `-p` for Phosphor: May need [Phosphor icons][23].
  * Use `-e` for Emojis



![NerdFetch with fancy options][24]

[Arch Linux users can use yay][25] or some other AUR helper:

```

    yay -S nerdfetch

```

Others can install it in a bit nerdier fashion:

```

    sudo curl -fsSL https://raw.githubusercontent.com/ThatOneCalculator/NerdFetch/main/nerdfetch -o /usr/bin/nerdfetch
    sudo chmod u+x /usr/bin/nerdfetch

```

[NerdFetch][26]

### Archey

Archey is a simple system information tool written in Python. It is a fork of the original Archey (Linux) system tool, and it is lightweight and fast.

![Archey][27]

Before installing Archey, make sure you have the following dependencies:

  * Essential: `python3`, `python3-distro`, `python3-netifaces`.
  * Recommended: `procps`, `dnsutils`, `lm-sensors`, etc. [Visit their documentation][28] for more recommended packages.



You can [download the deb file from the releases page][29] and install it on Ubuntu.

🚧

I have faced some issues while running this in Ubuntu, but on Arch Linux, it ran fine. Arch 1, Ubuntu 0 🥊

For Arch Linux users, install it using any AUR helper:

```

    yay -S archey4

```

Archey uses JSON file as configuration tool, which is usually placed at:

  * `/etc/archey4/config.json` (system preferences)
  * `~/.config/archey4/config.json` (user preferences)
  * `./config.json` (local preferences)



The preference order is **local preferences > user preferences > system preferences**.

[Archey system tool][30]

### HyFetch

HyFetch is a fork of Neofetch, with **LGBTQ+ pride flags** 🏳️‍🌈.

The configuration file of HyFetch is located at `~/.config/neowofetch/config.conf`. It is similar to tweaking the Neofetch.

![hyfetch][31]

You can install HyFetch from the official repositories of Ubuntu.

```

    sudo apt install hyfetch

```

It is also available in Arch Linux's repositories. The documentation provides [more installation methods][32].

During the initial run, it will ask for several configurations, such as the color scheme, brightness adjustment, etc., through a text prompt. It also displays the appearance of each choice for easy selection.

You can rerun the configuration anytime by using the command:

```

    hyfetch -c

```

[HyFetch][33]

### cpufetch

Unlike the rest in this list, [cpufetch][34] only shows the CPU details with a neat logo.

![CPUFetch: Image Credits: cpufetch][35]

By default, it prints the CPU logo according to the system color scheme, but also provides methods to change it.

cpufetch is available in the repositories of Ubuntu. Which means it's quite easily installable.

```

    sudo apt install cpufetch

```

📋

There is a project called [GPUFetch][36], that is CPUFetch for GPUs.

[cpufetch][37]

### More ASCII fun

Why just stop here? How about some more ASCII things?

![][38]

There are more tools to explore here.

![][38]

And finally, let's raise a glass to Neofetch 🥂 It will be missed.

--------------------------------------------------------------------------------

via: https://itsfoss.com/neofetch-alternatives/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/display-linux-logo-in-ascii/
[4]: https://github.com/dylanaraps/neofetch
[5]: https://itsfoss.com/content/images/2024/05/neofetch-dev-github.png
[6]: https://itsfoss.com/content/images/2024/05/farm-ascii.png
[7]: https://itsfoss.com/using-neofetch/
[8]: https://itsfoss.com/content/images/2024/05/fastfetch-default-1.png
[9]: https://github.com/fastfetch-cli/fastfetch/tree/dev/presets
[10]: https://github.com/fastfetch-cli/fastfetch
[11]: https://itsfoss.com/content/images/2024/05/screenfetch.png
[12]: https://github.com/KittyKatt/screenFetch
[13]: https://itsfoss.com/content/images/2024/05/macchina.png
[14]: https://github.com/Macchina-CLI/macchina/blob/main/contrib/themes/Hydrogen.toml
[15]: https://github.com/Macchina-CLI/macchina/releases/
[16]: https://itsfoss.com/install-rust-cargo-ubuntu-linux/
[17]: https://aur.archlinux.org/packages/macchina
[18]: https://github.com/Macchina-CLI/macchina
[19]: https://itsfoss.com/posix/
[20]: https://www.nerdfonts.com/font-downloads
[21]: https://itsfoss.com/content/images/2024/05/nerdfetch.png
[22]: https://github.com/slavfox/Cozette
[23]: https://github.com/phosphor-icons/homepage/releases/tag/v2.0.0
[24]: https://itsfoss.com/content/images/2024/05/NerdFetch-options.png
[25]: https://itsfoss.com/install-yay-arch-linux/
[26]: https://github.com/ThatOneCalculator/NerdFetch
[27]: https://itsfoss.com/content/images/2024/05/archey-1.png
[28]: https://github.com/HorlogeSkynet/archey4?tab=readme-ov-file#highly-recommended-packages
[29]: https://github.com/HorlogeSkynet/archey4/releases/
[30]: https://github.com/HorlogeSkynet/archey4
[31]: https://itsfoss.com/content/images/2024/05/5-hyfetch.png
[32]: https://github.com/hykilpikonna/hyfetch?tab=readme-ov-file#installation
[33]: https://github.com/hykilpikonna/hyfetch
[34]: https://itsfoss.com/cpufetch/
[35]: https://itsfoss.com/content/images/2024/05/cpufetch.gif
[36]: https://github.com/Dr-Noob/gpufetch
[37]: https://github.com/Dr-Noob/cpufetch
[38]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
