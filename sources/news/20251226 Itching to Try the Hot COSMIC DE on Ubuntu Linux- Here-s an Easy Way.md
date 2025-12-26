[#]: subject: "Itching to Try the Hot COSMIC DE on Ubuntu Linux? Here's an Easy Way"
[#]: via: "https://itsfoss.com/install-cosmic-de-ubuntu/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Itching to Try the Hot COSMIC DE on Ubuntu Linux? Here's an Easy Way
======

[![Warp Terminal][1]][2]

[COSMIC][3] has been quite the undertaking. System76 spent years building this Rust-based desktop environment from scratch, and it finally got a stable release with [Pop!_OS 24.04 LTS][4].

During my testing of it, the experience was quite good. The window tiling is slick, the desktop settings allow for a wide range of customization, and the gaming experience is okay.

POP!_OS ** itself is Ubuntu-based but if you are already using Ubuntu, you don't need to remove Ubuntu just to try COSMIC. There is [an unofficial PPA][5] that packages the fledgling desktop environment for Ubuntu.

__Just a quick demo of COSMIC on Ubuntu 24.04 LTS.__

🚧

This is ****an unofficial way to get COSMIC on Ubuntu.**** Installing multiple desktop environments on the same distro sometimes leads to conflicts. I once had two network managers when I installed MATE and GNOME on the same Ubuntu installation. We have rust-based implementation, so you may end up with double entries for some elements. You may have to reinstall one of the desktop environments and remove the other to clean up the system. Basically, don't try this method if you easily get overwhelmed.

### How do you install COSMIC desktop on Ubuntu?

You add the unofficial PPA with `sudo add-apt-repository ppa:hepp3n/cosmic-epoch` and then install COSMIC desktop with `sudo apt install cosmic-session`. Once installed, log out from the system and choose COSMIC session from the login screen.

Before I show the steps in detail, **you have to understand that this PPA could interact with many critical packages** like [Mesa][6], [Wayland][7], [LLVM Toolchain 20][8], and the Rust compiler. I tested this on a fresh installation of [Ubuntu 24.04 LTS][9] to ensure a conflict-free installation, but **I am unsure how this PPA will behave when applied to an existing installation**.

This PPA **should also work for Ubuntu 24.04-based distros** like [Linux Mint 22.x][10], [Zorin OS 18][11], and [elementary OS 8.x][12]. The same warning applies for these distros as well.

![][13]

First, open your terminal and run this command to add the PPA:

```

    sudo add-apt-repository ppa:hepp3n/cosmic-epoch

```

The system will ask for your password and show you information about the PPA. Press `Enter` to confirm.

After adding the PPA, update your package list. This step is not needed in Ubuntu as adding a new repo automatically triggers package cache update.

```

    sudo apt update

```

![][14]

Now install the COSMIC desktop session with:

```

    sudo apt install cosmic-session

```

⚠️ During the installation, you'll be prompted to choose a [display manage][15]r ( _the login screen_ ). This is an important decision. Use the arrow keys to select your choice and press `Enter`.

If you want to go full COSMIC, select `cosmic-greeter`. This is what I did during my testing. But if you plan to keep using GNOME or want to switch between desktop environments, stick with `gdm3` ( _GNOME Display Manager_ ).

That is **the safer choice** if you are not ready to commit fully to COSMIC.

![][16]

Once the installation completes, log out of your current session. At the login screen, look for the session switcher. On `gdm3`, this is usually a gear icon or a dropdown menu in the bottom-right corner.

Click on it and select _COSMIC_ from the list of available sessions. Then log back in.

If everything goes well, your system should boot into the COSMIC desktop environment. You'll see the familiar workspace switcher on the top-left, and the application launcher and dock at the bottom.

### Going back to GNOME

I'll quickly tell you the steps:

  * Log out from the system, and then choose GNOME and log into the GNOME session
  * [Reset back to GDM][17] by using the command: `sudo dpkg-reconfigure gdm3` and when asked, make GDM the default display manager.
  * Now that you are back with GNOME properly, you can remove COSMIC: `sudo apt remove cosmic-session`



Via: [OMG! Ubuntu][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-cosmic-de-ubuntu/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://system76.com/cosmic
[4]: https://itsfoss.com/news/pop-os-24-04-review/
[5]: https://launchpad.net/~hepp3n/+archive/ubuntu/cosmic-epoch
[6]: https://launchpad.net/ubuntu/+source/mesa
[7]: https://launchpad.net/ubuntu/+source/wayland
[8]: https://launchpad.net/ubuntu/+source/llvm-toolchain-20
[9]: https://itsfoss.com/ubuntu-24-04-lts-review/
[10]: https://itsfoss.com/linux-mint-22/
[11]: https://itsfoss.com/news/zorin-os-18-release/
[12]: https://itsfoss.com/news/elementary-os-8-1-release/
[13]: https://itsfoss.com/content/images/2025/12/cosmic-on-ubuntu-add-ppa.png
[14]: https://itsfoss.com/content/images/2025/12/cosmic-on-ubuntu-install.png
[15]: https://itsfoss.com/display-manager/
[16]: https://itsfoss.com/content/images/2025/12/cosmic-on-ubuntu-session-switcher.png
[17]: https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/
[18]: https://www.omgubuntu.co.uk/2025/12/install-cosmic-desktop-ubuntu-24-04-ppa
