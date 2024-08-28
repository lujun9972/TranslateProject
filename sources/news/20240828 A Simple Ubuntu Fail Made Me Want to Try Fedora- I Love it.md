[#]: subject: "A Simple Ubuntu Fail Made Me Want to Try Fedora: I Love it!"
[#]: via: "https://news.itsfoss.com/ubuntu-fails-fedora-works/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A Simple Ubuntu Fail Made Me Want to Try Fedora: I Love it!
======
Ubuntu let me down after a simple change, and I'm here with Fedora.
[![][1]][2]

Over the years, I have seen many users complain that NVIDIA drivers on Linux are a mess, even on popular distributions like Ubuntu.

Similar to our editor's experience in his distro hopping journey, making him [switch from Ubuntu to Arch Linux][3].

For me, I never really faced such issues on my Ubuntu installations when using the recommended proprietary driver. Be it on a GTX 10-series desktop GPU or a RTX 30-series laptop GPU.

But, that smooth sailing came to an abrupt end recently. Join me as I take you through my experience switching NVIDIA drivers on an Ubuntu installation using the [GUI method][4].

### NVIDIA Drivers: Ubuntu's Achilles Heel?

0:00

/0:06

1×

Black screen after logging into the X11 session on Ubuntu 22.04.4 LTS.

You see, on my Dell G15 5530 laptop ( _featuring a RTX 3050 6 GB GPU_ ) equipped with Ubuntu 22.04.4 LTS, I had switched to the open-source [Nouveau][5] GPU driver from the proprietary NVIDIA 535 driver ( _the recommended driver_ ).

But, as you can see above, after the driver switch, logging back into the [X11][6] session of Ubuntu resulted in black screens on both the connected monitors, with Ubuntu refusing to move ahead and load up the interface.

The screenshots below show the method I used to switch drivers. 👇

![The GUI method, follow the images from left to right.][7]

I did another reboot, and I was finally able to see the interface, but that was a short-lived affair. The secondary 24" monitor displayed a white output, with the top part of the screen showing some content, going white as I moved the mouse cursor around.

On subsequent reboots, the case was the same: either I got a black screen or a white screen. After disconnecting the secondary monitor, the black screen issue was still present.

Do keep in mind that **I had Secure Boot disabled** when all this happened. I then switched to the [Wayland][8] session, and that was running just fine, or so I thought. 😑

Around the end of the day, I noticed that the boot behavior with the Wayland session was inconsistent, with random black screens on subsequent reboots.

And, to my surprise, using virtual machines on VirtualBox stopped working when I set out to test [RefreshOS][9]. Even existing machines threw the same errors; I could not take a screenshot for that.

**That is when I realized that such a basic GPU driver switch caused issues that warranted a fresh installation?** 🤯

And, that too, in 2024? Where the Ubuntu experience should have been more reliable than this?

I didn't bother troubleshooting it, as I felt it wouldn't have been worth the effort.

_Moreover, I was itching to distro hop_ 😄

**Suggested Read** 📖

![][10]

### Journey to Find a Replacement: Fedora 40

I then set out on a journey to find a replacement. First, I tried [Ubuntu 24.04 LTS][11], but it had the same black screen issue on login that was present the last time I tried daily driving it.

Then, I went on to try distros like [Pop!_OS 22.04][12], [EndeavourOS][13], and even tried reinstalling Ubuntu 22.04. But, I still faced the black screen on boot issue across those distros.

At the end of my patience, I gave [Fedora 40][14] Workstation a try. I tried it last because, earlier, Ankush, had [a mixed experience][15] on his NVIDIA 30-series GPU-equipped desktop, and I thought I would also face similar difficulties.

Surprisingly, for me, **Fedora came through**. I didn't face any of the issues I faced with both Ubuntu and the other distros I tried. Almost everything worked out of the box. I just had to install a few [GNOME extensions][16] to restore some missing functionality.

By default, the open-source Nouveau NVIDIA GPU driver was enabled, and my laptop didn't seem to have an issue with that, even when connecting an external monitor, that too on a Wayland session.

### Do I Miss Anything?

![Fedora 40 with a few GNOME extensions.][17]

There are a few things that I miss from Ubuntu, but that'stance, I miss being able to easily i okay. For instance, I miss being able to easily install _.deb_ packages, as many app developers just provide that, with the other options being to use the _.tar.gz_ package or to build from source. Here, we have _.rpm_ packages. So, not all is lost.

[Snaps][18] were cool to have too (by default), though [Flatpaks][19] have done a fantastic job of quickly making me forget that the former exists. Plenty of applications/tools are available as Flatpaks, and with the Flathub repos being enabled by default on Fedora, I have a good experience so far.

Though, I have yet to play any video games on this new setup, I expect it to perform worse than Ubuntu, as I have the Nouveau driver. I won't be switching to the proprietary driver anytime soon because I do not need it.

You can [install Nvidia drivers on Fedora][20] if you are wondering.

In the end, **I believe that both Ubuntu's broken driver switching mechanism and NVIDIA's reluctance to offer open-source drivers caused these issues**. If I were to do the same thing on a Windows machine, it would do the job without breaking a sweat.

NVIDIA should take pointers from how AMD handles GPU drivers for Linux. Doing that could go a long way toward making the experience a lot better for users on Linux.

_For now, I am happy with what Fedora has to offer; I will stay on it until something breaks, and I have to distro hop yet again 😉_

**Suggested Read** 📖

![][10]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-fails-fedora-works/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/archcraft-experience/
[4]: https://itsfoss.com/install-additional-drivers-ubuntu/
[5]: https://nouveau.freedesktop.org/
[6]: https://www.x.org/wiki/
[7]: https://news.itsfoss.com/content/images/2024/08/Fedora_Switch_b.png
[8]: https://wayland.freedesktop.org/
[9]: https://news.itsfoss.com/refreshos/
[10]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[11]: https://news.itsfoss.com/ubuntu-24-04-lts/
[12]: https://news.itsfoss.com/pop-os-22-04-release/
[13]: https://news.itsfoss.com/endevouros-5-anniversary/
[14]: https://news.itsfoss.com/fedora-40-release/
[15]: https://news.itsfoss.com/fedora-ubuntu-switch/
[16]: https://itsfoss.com/gnome-shell-extensions/
[17]: https://news.itsfoss.com/content/images/2024/08/Fedora_Switch_e.jpg
[18]: https://snapcraft.io/
[19]: https://flatpak.org/
[20]: https://itsfoss.com/install-nvidia-drivers-fedora/
