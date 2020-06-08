[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Configure Gaming Mouse on Linux Using Piper GUI Tool)
[#]: via: (https://itsfoss.com/piper-configure-gaming-mouse-linux/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

How to Configure Gaming Mouse on Linux Using Piper GUI Tool
======

_**Brief: Piper is a nifty GUI application that helps you configure your gaming mouse on Linux.**_

Usually, when you [switch from Windows to Linux][1], you lose access to a lot of [GUI][2] (Graphical User Interface) tools to manage gaming peripherals. You can still enjoy [playing games on Linux][3], but the ability to configure your mouse is a big deal if you are more than a casual gamer.

Recently, I came across a handy tool that lets you configure your gaming mouse on Linux. Let me share how it works and whether it is worth trying.

Bestseller No. 1

[][4]

[PICTEK Gaming Mouse Wired [7200 DPI] [Programmable] [Breathing Light] Ergonomic Game USB Computer Mice RGB Gamer Desktop Laptop PC Gaming Mouse, 7 Buttons for Windows 7/8/10/XP Vista Linux, Black][4]

$22.99 [][5]

### Piper: A GUI tool to manage your gaming mouse on Linux

![][6]

[Piper][7] is an open-source tool that you can use for configure gaming peripherals on Linux. Technically, Piper is a graphical frontend to the [ratbagd DBus daemon][8] — but you don’t need to worry about it if you aim to use the GUI.

In this article, I’ll give you a brief overview as I test it on my **Logitech G502** gaming mouse.

Preview | Product | Price |
---|---|---|---
![Logitech G502 Proteus Spectrum RGB Tunable Gaming Mouse, 12,000 DPI On-The-Fly DPI Shifting, Personalized Weight and Balance Tuning with \(5\) 3.6g Weights, 11 Programmable Buttons][9] ![Logitech G502 Proteus Spectrum RGB Tunable Gaming Mouse, 12,000 DPI On-The-Fly DPI Shifting, Personalized Weight and Balance Tuning with \(5\) 3.6g Weights, 11 Programmable Buttons][9] | [Logitech G502 Proteus Spectrum RGB Tunable Gaming Mouse, 12,000 DPI On-The-Fly DPI Shifting,...][10] | $74.88 | [Buy on Amazon][11]

### Features of Piper

It’s a dead simple tool. You get the ability to configure the following things of your gaming mouse with the help of Piper:

  * Change [DPI][12] (Resolution) and [Polling rate][13]
  * Map buttons
  * Control LEDs
  * Add multiple profiles



Please note that not all gaming mouse work with Piper at this time. Please check the [list of support devices][14] before you try it out.

Here’s how it works and looks:

#### Change DPI &amp; Polling Rate

![][15]

With Piper, you get to set different DPI levels to switch from. It’s quite easy tweak it because of the slider present.

Not just limited to the DPI settings, but you can also control the polling rate (or the sensitivity). Of course, depending on your mouse, the option may look different, but you don’t really need to change the sensitivity of your mouse for the most part.

#### Configure Buttons

![][16]

This is extremely important for most of the users, especially, if you want to utilize [macros][17] or simply want to change the mapping of your buttons.

As you can observe in the screenshot above, I was able to tweak each and every button.

I’ve re-mapped the DPI increase/decrease button and replaced it with a macro to dabble between multiple workspaces on [Pop OS 20.04][18].

#### Control LEDs

![][19]

Well, there’s no use of having RGB lighting if you can’t tweak or control them. With Piper, you can easily control the LED lights of your gaming mouse (if your mouse has this feature). It works pretty well for my **G502**.

#### Multiple Profiles

You also get the ability to manage multiple profiles to switch from — so you don’t have to fiddle around with the settings always.

In case you didn’t know, each profile can have different button mapping, LED setting, and DPI settings.

### Installing Piper On Linux

To get started, you need to ensure that you have [libratbag][8] installed. Some Linux distributions have it pre-installed, like Pop!_OS.

For Ubuntu-based distros, you can type in the following command to install it if you didn’t have it already:

```
sudo apt install ratbagd
```

You can follow the [official installation instructions][20] if you need it for Debian, Arch or Fedora.

Once done, you can finally install Piper by typing the following command (for Ubuntu-based distros):

```
sudo apt install piper
```

You can get installation instructions for other Linux distributions in their [wiki on GitHub][21].

You also get a [Flatpak package][22] available. In case you don’t know how to install it, I suggest you to refer our [Flatpak guide][23] to know more.

[Download Piper][7]

### Wrapping Up

Piper is an amazing GUI tool to easily configure a gaming mouse on Linux considering that you have one of the supported devices.

You will find many supported devices from Logitech, Etekcity, GSkill, Roccat, and Steelseries. So, I’d say it should come in handy for serious Linux gamers.

Have you tried Piper yet? Let me know your thoughts in the comments below.

--------------------------------------------------------------------------------

via: https://itsfoss.com/piper-configure-gaming-mouse-linux/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/reasons-switch-linux-windows-xp/
[2]: https://en.wikipedia.org/wiki/Graphical_user_interface
[3]: https://itsfoss.com/linux-gaming-guide/
[4]: https://www.amazon.com/dp/B01FZ3BR5S?tag=chmod7mediate-20&linkCode=osi&th=1&psc=1&keywords=gaming%20mouse (PICTEK Gaming Mouse Wired [7200 DPI] [Programmable] [Breathing Light] Ergonomic Game USB Computer Mice RGB Gamer Desktop Laptop PC Gaming Mouse, 7 Buttons for Windows 7/8/10/XP Vista Linux, Black)
[5]: https://www.amazon.com/gp/prime/?tag=chmod7mediate-20 (Amazon Prime)
[6]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/06/piper-gui.png?ssl=1
[7]: https://github.com/libratbag/piper
[8]: https://github.com/libratbag/libratbag
[9]: https://i0.wp.com/m.media-amazon.com/images/I/41xxUrMt7nL._SL160_.jpg?ssl=1
[10]: https://www.amazon.com/dp/B019OB663A?tag=chmod7mediate-20&linkCode=ogi&th=1&psc=1 (Logitech G502 Proteus Spectrum RGB Tunable Gaming Mouse, 12,000 DPI On-The-Fly DPI Shifting, Personalized Weight and Balance Tuning with (5) 3.6g Weights, 11 Programmable Buttons)
[11]: https://www.amazon.com/dp/B019OB663A?tag=chmod7mediate-20&linkCode=ogi&th=1&psc=1 (Buy on Amazon)
[12]: https://en.wikipedia.org/wiki/Dots_per_inch
[13]: https://wiki.archlinux.org/index.php/Mouse_polling_rate
[14]: https://github.com/libratbag/libratbag/tree/master/data/devices
[15]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/06/piper-dpi.png?ssl=1
[16]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/06/piper-buttons.png?ssl=1
[17]: https://en.wikipedia.org/wiki/Macro_(computer_science)
[18]: https://itsfoss.com/pop-os-20-04-review/
[19]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/06/piper-led-control.png?ssl=1
[20]: https://github.com/libratbag/libratbag/wiki/Installation
[21]: https://github.com/libratbag/piper/wiki/Installation
[22]: https://flathub.org/apps/details/org.freedesktop.Piper
[23]: https://itsfoss.com/flatpak-guide/
