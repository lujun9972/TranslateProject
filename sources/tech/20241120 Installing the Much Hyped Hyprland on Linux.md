[#]: subject: "Installing the Much Hyped Hyprland on Linux"
[#]: via: "https://itsfoss.com/install-hyprland/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing the Much Hyped Hyprland on Linux
======

[![Warp Terminal][1]][2]

Hyprland is a dynamic tiling window compositor that is both highly customizable and provides plenty of eye candy.

It is also very popular in Linux ricing groups these days. And why not? If you are into customizing the looks of your desktop, Hyprland is surely worth all the hype.

Take a look at the screenshot below.

![Image credit: flick0][3]

The official Hyprland video provides more detailed visuals:

Now, I am not trying to discourage you, but these things take a lot of effort if you try to configure on your own. Alternatively, you can use the dot files from someone else and get the same look as theirs.

I believe it's a good learning experience but something that should be done on a secondary system.

I tried it on a VM and although, Hyprland it is not officially supported in virtuacl machines, it still worked for most parts in my testing.

🚧

Hyprland is in highly active development. Unlike GNOME and other desktop environments, you don't get a stable release which is supported for years.

### Things to note before installing Hyprland

Before you start installing [Hyprland][4], you need to understand a few points about stability and compatibility.

  * Hyprland is not a beginner-centric window compositor.
  * It is Wayland-only and not all Xorg-only application will work on Hyprland.
  * Nvidia GPUs have limited compatibility due to their proprietary nature.
  * It is not officially supported in virtual machines, but somehow it works. To get a better result, you should try it on a bare metal.
  * If you are installing on a virtual machine, like VirtualBox, enable 3D Acceleration. Moreover, allow a RAM of at least 4 GB.



🚧

I suggest either you try it in a spare machine first, or keep another stable window manager in the system, so that you don't lose your work while experimenting with Hyprland.

### Install Hyprland with Arch Linux using archinstall script

Arch Linux, [NixOS][5] and openSUSE Tumbleweed are the most supported distribution when it comes to Hyprland.

In Arch Linux, if you are using the `archinstall` script, you have an option to select Hyprland as the desktop in Profile → Type → Desktop → Hyprland.

![Hyprland in Archinstall script][6]

As you can see in the screenshot above, the installer has selected some necessary dependencies for Hyprland to work.

On the next step, it will ask you to have access to hardware. Here, I have gone with Polkit.

Similarly, the greeter will be automatically set to SDDM.

📋

If you are installing Hyprland as the only option, it is better to select SDDM. In case you are installing Hyprland on a GNOME setup, there is no need to install and configure SDDM, as GDM just works fine.

On the additional packages installation prompt, install `hyprpaper` and `waybar`. Or do that after install and login.

```

    sudo pacman -Syu hyprpaper waybar

```

📋

Hyprpaper is the wallpaper manager and Waybar is the bar, that host necessary panel buttons.

That's it. You will have a working Hyprland set up.

🚧

Hyprpaper needs to be enabled and configured to get a proper wallpaper to your screen. This will be discussed in another article.

#### Install Hyprland in base install

If you have installed [Arch Linux base installation following our guide][7], then you need to install the Hyprland separately. To do that, log in to the base install and run the command:

```

    sudo pacman -Syu hyprland hyprpaper xdg-desktop-portal-hyprland waybar wofi kitty sddm

```

Then enable the SDDM service using:

```

    sudo systemctl enable sddm.service

```

Now, restart the system and login to Hyprland session.

### Install Hyprland in Ubuntu

Hyprland is also available in the default repo of Ubuntu since 24.10 Oracular Oriole. But it is highly not recommended to install Hyprland from this package.

Instead, I will discuss another method, through which you can set up a working Hyprland on Ubuntu.

🚧

Here, I am using Ubuntu 24.0.1 as the distro. The method mentioned below has separate repositories for other versions. Please check you Ubuntu version before continuing.

#### Things to keep in mind before proceeding

  * You should back up your system and important data before start installing.
  * Ensure an active, uninterrupted internet connection.
  * Version older than 24.04 won't work.
  * Do not install SDDM.



Once you are ready, let's install.

#### Install Hyprland in Ubuntu 24.04

First, you need to enable the source packages repo in Ubuntu. Search for Software and Updates and open it.

![Open Software and Updates][8]

Go to the tab and enable the checkbox near sources.

![Enable Source Code][9]

Click on close, and then use the Reload button. Now, update your system and install all pending updates.

```

    sudo apt update && sudo apt upgrade

```

We use the Automated Hyprland Installer for Ubuntu to install Hyprland on Ubuntu. This offers a fast method to get started with Hyprland.

[Ubuntu-Hyprland][10]

🚧

There are methods to build Hyprland from source, but there are many hiccups included, which will put you in a long troubleshooting loop.

Clone the Hyprland installer third-party repository.

```

    git clone -b 24.04 --depth 1 https://github.com/JaKooLit/Ubuntu-Hyprland.git ~/Ubuntu-Hyprland-24.04

```

Now, move inside the directory and give the installer file (`install.sh`) execution permission.

```

    cd ~/Ubuntu-Hyprland-24.04
    chmod +x install.sh

```

Run the installer.

🚧

You should NOT run the installer as root.

```

    ./install.sh

```

This will start the installer.

![Hyprland Installer][11]

🚧

Only Hyprland up to v0.39.1 is compatible with Ubuntu 24.04. This is because of the version of required dependency in the Ubuntu repo remains as is, and Hyprland is a heavily active project, that changes the dependency requirements quite often.

Read the note carefully and proceed by entering `y`.

Now, some questions will be asked on the topics:

  * NVIDIA GPU: Hyprland may not work properly with NVIDIA, as said in an earlier section.
  * Install GTK Themes for Dark Light function.
  * Configure Bluetooth
  * Install Thunar file manager.
  * Install SDDM: This should be NO (n). Since Ubuntu has GDM and it works well.
  * Install XDG-DESKTOP-PORTAL-HYPRLAND: This should be YES (y).
  * Install ZSH
  * Install nwg-look: This is for GTK Theming. It will take a long time to build. So you can skip (n) this.
  * Installing on Asus ROG Laptops.
  * Preconfigured Dot files: Yes (y), if you don't want to configure the looks from scratch.



![Installer Queries][12]

When asked, enter the sudo password to start installation.

Sit back and wait, while the installer completes the set-up process.

When asked, “Would you like to try to remove other XDG-Desktop-Portal-Implementations?”, give no.

Similarly, at the last stage, you will be asked to add yourself (the current user) to the input group. This might be necessary for some waybar functionalities.

If you are running in a VM and/or selected dot file install option, you will be asked more configuration options like:

  * Select keyboard Layout
  * Set Monitor resolution
  * Set time format
  * Keep/disable rainbow border animation.



These are shown in the screenshot below.

![Preset Dot Files][13]

It also provides an option to download more wallpapers, but the size is greater than 600 MB.

Once all queries are answered properly, it will set the configuration accordingly.

Reboot the system.

When the system is rebooted, select the Hyprland session and Log in using your password.

![Login to Hyprland][14]

You will be logged into the Hyprland desktop session.

![Ubuntu Hyprland \(Click to enlarge the image\)][15]

### Installing Hyprland in other Distributions

Hyprland is available in the repos of many other Linux distributions like openSUSE, Fedora, etc. The basic installation can be performed on these devices using:

  * In Fedora,



```

    sudo dnf install hyprland

```

There is also [a COPR repository][16] for Fedora users for more updates.

  * In openSUSE



```

    sudo zypper in hyprland

```

You can read the [official detailed installation manual][17] for other distribution.

I'll be covering the waybar configuration and Hyprland customization tips in future articles. Stay tuned and [subscribe to our FOSS Weekly newsletter][18] so that you don't miss them.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-hyprland/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/11/hyprland.webp
[4]: https://hyprland.org/
[5]: https://itsfoss.com/nixos-tutorials/
[6]: https://itsfoss.com/content/images/2024/10/hyprland-in-archinstall.png
[7]: https://itsfoss.com/install-arch-linux/
[8]: https://itsfoss.com/content/images/2024/10/software-and-updates-1.png
[9]: https://itsfoss.com/content/images/2024/10/enable-source-code-in-ubuntu.png
[10]: https://github.com/JaKooLit/Ubuntu-Hyprland/tree/24.04
[11]: https://itsfoss.com/content/images/2024/10/hyprland-installer-start.png
[12]: https://itsfoss.com/content/images/2024/10/all-installer-questions-hyprland.png
[13]: https://itsfoss.com/content/images/2024/10/4-disable-rainbow-borders.png
[14]: https://itsfoss.com/content/images/2024/10/login-to-hyprland.png
[15]: https://itsfoss.com/content/images/2024/10/hyprland-in-ubuntu.webp
[16]: https://copr.fedorainfracloud.org/coprs/solopasha/hyprland
[17]: https://wiki.hyprland.org/Getting-Started/Installation/
[18]: https://itsfoss.com/newsletter/
