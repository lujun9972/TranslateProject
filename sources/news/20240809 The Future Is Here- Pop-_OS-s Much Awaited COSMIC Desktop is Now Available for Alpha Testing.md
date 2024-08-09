[#]: subject: "The Future Is Here! Pop!_OS's Much Awaited COSMIC Desktop is Now Available for Alpha Testing"
[#]: via: "https://news.itsfoss.com/pop-os-24-04-cosmic-alpha/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Future Is Here! Pop!_OS's Much Awaited COSMIC Desktop is Now Available for Alpha Testing
======
COSMIC Desktop debuts with insane customization options with Pop!_OS
24.04 LTS!
[![][1]][2]

[System76][3], creators of unique hardware and the popular Pop!_OS Linux distribution, have been on a long journey to develop a Wayland-only Rust-based [desktop environment][4] called “ **COSMIC** ”.

Seeing their approach of making user-friendly choices, many, including myself, had been waiting to see how this would turn out.

Thankfully, the wait is now almost over, as the developers have [introduced][5] a build of COSMIC with the **Pop!_OS 24.04 Alpha** release that offers an early look into it.

This goes without saying, this is **an under-development piece of software** that's not meant for daily or production use. We take a [First Look][6] at see what you can expect with it.

### COSMIC on Pop!_OS 24.04 Alpha: How Does It Fare?

![][7]

Even though this is an alpha release, **the developers have ensured that it is a usable experience for most users** by including things like their custom theming system, advanced window auto-tiling, new Rust-based COSMIC apps, and more.

I tested it on a [virtual machine][8] (VM) using VirtualBox on Ubuntu 22.04.4 LTS, with the Intel/AMD ISO loaded to get the alpha release installed.

Before I could get started, I had to enable EFI in the system settings, increase the video memory to 128 MB, and enable 3D acceleration to make the ISO boot on the VM.

_I have divided my experience into three sections for easy reading._ 👇

#### The Installer

![][9]

Pop!OS 24.04 Alpha's **installer was a breath of fresh air** , with **** a very minimal look and familiar feel **** to it. If you have installed Pop!_OS before, you will be right at home.

When I progressed further, I was shown options for a “ _Clean Install_ ”, which would handle the disk partitioning, erasing everything on the disk, another option to manually partition the disk [using GParted][10].

And, finally, there was an option to go into “ _Demo Mode_ ”, which is the live environment for the ISO.

![][11]

The **installation progress screen is what blew my mind** ( _pun intended_ ), with a very cool-looking [propulsion][12] animation.

#### The User Interface

![][13]

After installation was done, I was taken into **a login screen** which showed me the date/time, battery level, and network connection status. It also had many **helpful widgets** such as power controls, a session switcher, a user switcher, and a keyboard layout selector.

![][14]

Post-login, I was greeted with **a beautiful-looking COSMIC desktop** , which weirdly enough didn't feature the right-click context menu that pops-up. I guess that's because it is an alpha build.

At the very top of the screen was **the top panel** , which might feel familiar if you have used [GNOME][15], with a workspace switcher, an application menu, and a few applets towards the right-hand side.

**The dock** is what you would expect. It can be moved around, hidden, or completely disabled. You will also find that when using the super key **a quick launcher** pops up ( _can be changed_ ), which shows active applications, facilitates app opening, and can search through files.

There's also a fully-fledged application launcher called “ _App Library_ ”.

![][16]

Then came **the advanced window tiling and workspace features** of COSMIC, and I must say, they didn't disappoint.

As you can see above, I could tile windows effortlessly, with keyboard shortcuts letting me navigate between windows and workspaces without touching the mouse.

![Left: Desktop Settings Right: Theming Options][17]

As for the **customization potential of COSMIC** , the developers knew what they were doing, and oh my!🤯

You get simplified (and fine controls) options under _COSMIC Settings_ for tweaking the Wallpaper, Panel, Dock, Workspaces, and Window Management.

Under the Appearance menu, I could change the accent color, window background color, text color, and tweak the overall style to be more square.

![][18]

You can customize the colors of the elements to your heart's content, and reset to the default if you do not like it.

At the bottom of the screen, there was an “ _Experimental settings_ ” sub-menu, which let me change the icon theme for the whole system. Furthermore, you can **import/export** your appearance settings. So, you can share your theme style with fellow Pop!_OS users, that is sweet! 💯

#### The Apps

![][19]

In terms of applications, **the Rust-based core apps take the center stage** , with many to choose from. There's a file manager, a terminal emulator, a settings app, and finally, a proper app store, which lists an array of Flatpak applications.

All of those core apps have the COSMIC name attached to them, e.g., _COSMIC Files_ , _COSMIC Terminals_ , etc.

![][20]

Of course, there are **plenty of non-COSMIC apps** too, with the majority of them being well-known ones from GNOME. One thing I noticed was that such apps didn't have buttons to maximize/minimize the windows, only a button to close.

If you were wondering **whether Pop!_OS would be the only Linux distribution to feature COSMIC** , it's not! The desktop will be offered for many other distros, with System76, encouraging distributions to apply their brand's flair to it.

[Serpent OS][21] has already confirmed their plans to offer COSMIC when they replied to our post [on Mastodon][22], where they mentioned that:

> We're adding a metapackage for it, been keeping talks open with the very cool system76 camp as we want to offer a great representation of their work =)

Similarly, there's been [talk][23] of a **Fedora COSMIC spin** , which is showing promising signs. The progress on it seems to be going well, with one of the key people working on it, [Ryan Brue][24] mentioning on [Matrix][25] that:

> FYI: The first alpha of cosmic is out [https://system76.com/cosmic][5]

> The current instructions for Fedora link to my copr, but I told carl that once we get the packages upstreamed we can change the instructions to suggest upstream fedora for the stable releases, and the copr for git snapshots.

> Hoping for a smooth experience on the fedora end, but I'll be ready in case there's anything not working.

💡 COSMIC did not disappoint with its **insane customization options** and a **compact layout approach** for its first alpha release. I am now confident enough to say that System76 has got a winner on their hands.

### Get Pop!_OS 24.04 Alpha (COSMIC)

You can try this first Alpha release ( _Epoch 1_ ) of COSMIC by getting the Pop!_OS 24.04 Alpha ISO for [Intel/AMD][26] or [NVIDIA][27] systems (direct download links).

[Pop!_OS 24.04 Alpha][5]

If you want to try it on a different Linux distribution, then there are instructions to use it on [Arch][28], [Fedora][29], [NixOS][30], [openSUSE][31], and [Serpent OS][32]. For the source code, you should head to the project's [GitHub][33] repo.

This article only skimmed over the key highlights of this early release of COSMIC, you can go through our [earlier coverage][34] to dive deeper.

![][35]

_💬 It's finally here! Was the wait worth it? Share your thoughts in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/pop-os-24-04-cosmic-alpha/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://system76.com/
[4]: https://itsfoss.com/what-is-desktop-environment/
[5]: https://system76.com/cosmic
[6]: https://news.itsfoss.com/tag/first-look/
[7]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_a.jpg
[8]: https://itsfoss.com/virtual-machine/
[9]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_b.jpg
[10]: https://itsfoss.com/gparted/
[11]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_d.jpg
[12]: https://en.wikipedia.org/wiki/Spacecraft_propulsion
[13]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_e.jpg
[14]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_f.jpg
[15]: https://www.gnome.org/
[16]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_g.jpg
[17]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_h-1.jpg
[18]: https://news.itsfoss.com/content/images/2024/08/pop-os-cosmic-customizations.jpg
[19]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_i.jpg
[20]: https://news.itsfoss.com/content/images/2024/08/Pop-_OS_24.04_Alpha_COSMIC_j.jpg
[21]: https://news.itsfoss.com/serpent-os-alpha/
[22]: https://mastodon.social/@serpentos@fosstodon.org/112897373522622359
[23]: https://news.itsfoss.com/fedora-cosmic-spin/
[24]: https://www.linkedin.com/in/ryan-brue-b32728229/
[25]: https://matrix.to/#/%23cosmic:fedoraproject.org
[26]: https://pop-iso.sfo2.digitaloceanspaces.com/24.04/amd64/intel/9/pop-os_24.04_amd64_intel_9.iso
[27]: https://pop-iso.sfo2.digitaloceanspaces.com/24.04/amd64/nvidia/9/pop-os_24.04_amd64_nvidia_9.iso
[28]: https://wiki.archlinux.org/title/COSMIC
[29]: https://copr.fedorainfracloud.org/coprs/ryanabx/cosmic-epoch/
[30]: https://github.com/lilyinstarlight/nixos-cosmic
[31]: https://en.opensuse.org/Portal:COSMIC
[32]: https://docs.serpentos.com/docs/users/desktops/cosmic
[33]: https://github.com/pop-os/cosmic-epoch
[34]: https://news.itsfoss.com/pop-os-cosmic/
[35]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
