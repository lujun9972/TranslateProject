[#]: subject: "Relive the Golden Era: 5 Tools to Get Retro Feel on Linux"
[#]: via: "https://itsfoss.com/linux-retro-tools/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Relive the Golden Era: 5 Tools to Get Retro Feel on Linux
======

[![Warp Terminal][1]][2]

Retro techs are no longer _stranger things_. Just like vinyl records and vintage fashion, retro computing has captured our collective imagination, irrespective of the age group.

I mean, there's something deeply satisfying about amber-on-black terminals and chunky pixel fonts that modern UIs can't replicate.

The good thing here is that us Linux users are perfectly positioned to embrace this nostalgia wave.

No, I am not talking about those [ultra-lightweight distros][3] that involuntarily give retro vibes of late 90s and early 2000s. I am going to share a few interesting software that will help you get the retro feel on your modern Linux system.

### 1\. Cool Retro Term

I'll start with my favorite, that is also a functional tool.

[cool-retro-term][4] is a terminal emulator which mimics the look and feel of the old cathode tube screens. That's just about it. You do not get any special abilities, just the good-old look.

But here's the thing. You can use it like your regular terminal, it have vintage looks but the modern features still work the same.

There are more than one presets of colors and style available.

Cool Retro Term

**Installing Cool Retro Term**

You can install it on Ubuntu, Fedora, and Arch Linux using the commands respectively:

```

    sudo apt install cool-retro-term #For Debian/Ubuntu
    sudo dnf install cool-retro-term #For Fedora
    sudo pacman -Syu cool-retro-term #For Arch based distros

```

[Cool Retro Term][5]

### 2\. RSC8

RSC8 is a CHIP-8 virtual machine/emulator written in Rust with no_std core. It is yet another makeover for your terminal. So, if you like to use a retro terminal but built with Rust, give this a try.

RSC8 Chip-8 Virtual machine/emulator

Install it using [cargo][6].

```

    cargo install --locked --git https://github.com/jerryshell/rsc8

```

To use rsc8, you'll have to download ROMs of your choice from [this GitHub repo][7] and then use the following command:

```

    rsc8_tui <your_rom.ch8>

```

[RSC8][8]

### 3\. Retro Pie

[RetroPie][9] transforms your Raspberry Pi, ODroid C1/C2, or PC into a nostalgic gaming powerhouse.

It leverages platforms like Raspbian, EmulationStation, [RetroArch][10], and other innovative projects, allowing you to enjoy classic Arcade, home-console, and vintage PC games with minimal hassle.

RetroPie Walkthrough

Since there were multiple kinds of platforms/consoles in the past, there are different emulators for them.

But that's only half of the story. You also need to download ROMs that consist of games of that platform.

For example, if you want to play games that were available Nintendo's NES console, you download the ROM with NES games and then use the NES emulator in RetroPi to load this ROM. It's like inserting a virtual disk.

The problem here is that these ROMs are often deemed illegal to distribute, and hence the websites that host them are often removed.

Playing Super Mario World in RetroPie

**Installing RetroPi**

Please ensure that you have git installed on your system as you'll have to clone the Git repo here.

```

    cd
    git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git

```

Run the setup script:

```

    cd RetroPie-Setup
    sudo ./retropie_setup.sh

```

Follow the onscreen instructions for a basic installation.

[RetroPie][11]

### 4\. Hot Dog Linux

Hot Dog Linux is an X11 Window Manager with Windows 3.1 Hot Dog Stand, Amiga Workbench, Atari ST GEM, Mac Classic and Aqua UI pre-installed.

> HOTDOG is an acronym that stands for Horrible Obsolete Typeface and Dreadful Onscreen Graphics.

HOTDOG Linux

It is built using Objective-C and uses bitmapped graphics, low DPI displays. There are no unicode support here.

**Installing Hot Dog Linux:**

[Download the ISO][12] and install in VirtualBox. Make sure 3D acceleration is enabled.

[HOTDOG Linux][13]

🚧

It only worked in GNOME Boxes for me.

### 5\. DOSBox or DOSBox Staging

DOSBox is free and open-source software that allows you to emulate the MS-DOS operating systems from the previous century.

It allows you to play the 8-bit games.

Playing Doom2 in DOSBox

DOSBox also emulates CPU:286/386 realmode/protected mode, Directory FileSystem/XMS/EMS, Tandy/Hercules/CGA/EGA/VGA/VESA graphics, a SoundBlaster/Gravis Ultra Sound card for excellent sound compatibility with older games.

[DOSBox][14]

**Installing DOSBox**

On Ubuntu, and Arch, you can use the following commands respectively:

```

    sudo apt install dosbox #For Ubuntu/Debina
    sudo pacman -Syu dosbox #For Arch

```

#### DOSBox Staging

Fedora ships with [DOSBox Staging][15], a modern continuation of DOSBox. DOSBox Staging is also [available in Flathub][16].

For Arch, it is in [AUR][17]. And, for Ubuntu and Mint, add the following PPA to get it installed:

```

    sudo add-apt-repository ppa:feignint/dosbox-staging
    sudo apt-get update
    sudo apt install dosbox-staging

```

[DOSBox Staging][18]

### Wrapping Up

Linux enables users to have a godly amount of customization options. Whether you want your desktop to look clean, and contemporary, or you want to give it a retro look, there are certainly a few tools for that.

Come to think of, I should do a tutorial on how to give a retro makeover to your Linux distro, somewhat like the modern makeover video of Linux Mint.

[Subscribe to It's FOSS YouTube Channel][19]

Linux makes it easy to bring the retro vibe back to life. Whether it’s an old-school terminal, a full-blown vintage desktop, or classic games from the 90s, there’s a tool for every kind of nostalgia.

What is your favorite tool that we missed listing here? Let me know in the comments below.

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][20].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][21] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][21]

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-retro-tools/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/super-lightweight-distros/
[4]: https://itsfoss.com/cool-retro-term/
[5]: https://github.com/Swordfish90/cool-retro-term
[6]: https://itsfoss.com/install-rust-cargo-ubuntu-linux/
[7]: https://github.com/Timendus/chip8-test-suite
[8]: https://github.com/jerryshell/rsc8
[9]: https://github.com/RetroPie
[10]: https://www.retroarch.com/
[11]: https://retropie.org.uk
[12]: https://fmamp.com/download/
[13]: https://github.com/arthurchoung/HOTDOG
[14]: https://www.dosbox.com/
[15]: https://github.com/dosbox-staging/dosbox-staging
[16]: https://flathub.org/apps/io.github.dosbox-staging
[17]: https://aur.archlinux.org/packages/dosbox-staging
[18]: https://www.dosbox-staging.org
[19]: https://www.youtube.com/@itsfoss
[20]: https://itsfoss.com/plus-member-resources/
[21]: https://itsfoss.com/lifetime-membership/
