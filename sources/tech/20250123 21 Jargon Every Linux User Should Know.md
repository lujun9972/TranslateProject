[#]: subject: "21 Jargon Every Linux User Should Know"
[#]: via: "https://itsfoss.com/linux-jargon/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

21 Jargon Every Linux User Should Know
======

[![Warp Terminal][1]][2]

Whether you are a Windows/macOS user, or someone who is new to computers, Linux often comes as a challenge to everyone when they encounter unfamiliar terms.

You do not usually come across Linux-specific jargon in standard high school academic computer books, unless there is a dedicated chapter for Linux.

So, for the majority of users who never used Linux, the terms associated will sound alien to them.

With this article, I aim to change that by explaining some of the important jargon that should help you navigate the Linux world better.

### 1\. Kernel

The core of an operating system that interacts with the hardware, and software to help you take control of it, is a kernel.

And, Linux is just a kernel. We have an article that explains [what Linux is][3] for more details.

Every operating system is built on top of a kernel, like the Windows NT kernel for Windows, and the XNU kernel for Apple's macOS.

### 2\. Distro

A distro (short for distribution) is a complete operating system package built on top of a [Linux kernel][3].

There can be 100s of Linux distros. Each of them can differ in terms of its desktop environment, package manager, software pre-installed, user interface, Linux kernel version, and its use-cases. The combination of such system components that you like should be your preferred Linux distro.

Some of the examples of a distro include Ubuntu, Fedora, Arch Linux, and Linux Mint. Furthermore, there are distros that are based on other existing distros. For instance, Linux Mint is based on Ubuntu, and Ubuntu is based on Debian.

It can be confusing to choose a distro based on what's available. So, I recommend going through the list of the [best Linux distributions][4] for all kinds of users.

![][5]

### 3\. Dual Booting

The technique of having two operating systems installed in a single computer is called dual booting.

You can decide to use either of them, whether you have two Linux distros or one Linux and Windows operating system.

If you are considering doing it, you must know about the [dual booting myths][6] before proceeding.

![][7]

### 4\. Grub

Grub is the boot manager program (or bootloader) that lists the operating systems installed on your computer. You can find it on most popular Linux distributions, with some exceptions like Pop!_OS.

If you didn't know, a bootloader is a program that starts when you boot up the computer and loads the kernel to execute. You get to customize the order of it, and also customize the look of it to some extent.

You can learn more about [grub in our jargon buster article][8].

![][9]

### 5\. Desktop Environment

The desktop environment is a component of a Linux distribution that provides a graphical user interface (GUI) to interact with all the tech.

It includes elements like icons, toolbar, wallpaper, widgets, and more.

You can get a detailed explanation of [what a desktop environment is][10] in our article and explore all the available desktop environments here:

![][11]

My favorite desktop environments include GNOME and KDE Plasma.

### 6\. Display server

Display server is the core tech of what enables you to see and have a graphical user interface (GUI). Without it, you will not have a GUI to interact with.

It is not the same as desktop environment. In fact, a desktop environment includes a display server under-the-hood to make things possible.

You might have heard about X11, and Wayland sessions, those are the types of display servers available. Explore more here:

![][12]

### 7\. Display Manager

The display manager is a program that gives login capabilities to the user in a desktop environment.

Some popular display managers are GDM, LightDM, and SSDM. You can learn more about it here:

![][13]

### 8\. GNOME Shell

The user interface component in the GNOME desktop environment that is responsible to managing actions like window switching, notifications, and launching applications is the GNOME shell.

You can customize the behavior and add more functionalities to it using [GNOME shell extensions][14].

### 9\. Terminal Emulator

The terminal emulator is a text-based program that lets you type in commands for the computer to process. Some may even prefer to all it the command-line interface (just like the command prompt in Windows).

By default, every Linux distribution offers a terminal emulator with a set of capabilities. However, you can choose to install a separate one to get more functionalities or a different look/feel.

You can explore our list of available [Linux terminal emulators][15] to try out some cool options.

### 10\. Sudo

Sudo is a command on Linux that gives you elevated privileges (or root privileges) temporarily.

It is used whenever you want to make a system modification, or want to simply access a system file. The user is asked to prove that they are the administrators of the computer by typing in the password whenever sudo is used in a command.

Interestingly, the password is not visible when you type it in the terminal for security purposes.

### 11\. Package Manager

A tool that lets you install, manage, and remove applications on your Linux distro, is the package manager. It can be terminal-centric or one with a graphical user interface (GUI).

For instance, APT package manager for .deb files is terminal-focused. And, Synaptic is a GUI-based tool.

Every Linux distro has a different package manager. However, some package managers are predominantly found in most of the Linux distributions. For more information, you can check out our [package manager explainer][16]:

![][17]

### 12\. End of Life

End of Life (EOL) is a term used to point out the particular date/year after which a software will stop receiving any maintenance or security updates. In our context, it can be a Linux distribution. However, it is a term used for all kinds of software.

For instance, the End of Life for Ubuntu 24.04 LTS is April 2029. The End of Life differs based on the release cycle of the distribution, which I shall mention in the next point.

**Suggested Read 📖**

![][18]

### 13\. Long-Term Support (LTS) and Non-LTS Release

A release cycle is the period when you can expect a software to get a new upgrade while marking the end of life of the current version.

If you find something that mentions — Long-Term Support (LTS) release, it means that the software will get updates for a long duration of time, focusing on its stability over bleeding-edge changes.

Depending on the software or the distro, the duration will differ. For instance, every LTS release of Ubuntu gets at least **five years of updates** , and its flavours get only **three years of updates**.

And, non-LTS is the opposite of it, meaning, the software will get updates for a shorter duration (or limited time).

For instance, Ubuntu 24.10 will be supported for only nine months.

### 14\. Point and Rolling Release

A point release is a minor update to a major version of the software. For instance, Linux Mint 22.1 is a point update to Linux Mint 22.

On the contrary, a [rolling release][19] does not increment in any similar form. It just gets updates, small or big, with every new push by the developer team after its initial big release. For instance, Arch Linux is one of the [best rolling release distros][20].

![][21]

### 15\. Snap, Flatpak, and AppImage

Snap, Flatpak, and, AppImage are three different universal packaging formats for Linux software. Unlike DEB or RPM packages, you can use Snap/Flatpak/AppImage packages on any Linux distributions.

Technically, they have certain differences among each other, but they serve a similar aim, to make things cross-distribution friendly and remove the hassle of dependencies.

**Suggested Read 📖**

![][22]

### 16\. Tiling Window Manager

Tiling Window Manager is a program that lets you organize your windows in a tile layout. It is a mighty utility to make the best use of your screen space while keeping things organized.

It boosts your productivity, and also makes your desktop experience prettier.

**Suggested Read 📖**

![][23]

### 17\. Upstream and Downstream

In terms of Linux software lingo, upstream is often referred to an original project from which the current software is based on. It can be a kernel, or a distro, or an app in our context. And, the downstream is the one that takes things from the upstream.

For instance, the Linux kernel releases are upstream, and the distro developers customizing it and using it will be termed as downstream.

You can learn more in our article here:

![][24]

### 18\. Daemon

A daemon is a utility program that runs in the background to make sure certain services are running and monitored. For instance, the system update daemon makes sure to check for updates at a regular interval of time.

Get more insights on this on our article here:

![][25]

### 19\. TTY

When it comes to Linux, TTY is an abstract device in UNIX and Linux. Sometimes it refers to a physical input device such as a serial port, and sometimes it refers to a virtual TTY where it allows users to interact with the system ([reference][26]).

![][27]

### 20\. Immutable Distro

Considering you already know what a distro is, an [immutable distro][28] is just a type of distro where you cannot modify the core of the operating system (in other words, it is read-only).

This makes it a safer experience, and a more reliable one. Immutable distros have gained popularity recently, and you can find plenty of [immutable distros][29] to try the concept for yourself.

![][30]

### 21\. Super Key

The Windows key that you normally know and love is the super key for Linux. It acts as the command button (like macOS) with which you can perform a range of keyboard shortcuts.

So, if someone says press the super key, it is just the Windows key on most keyboards. In some rare instance, the keyboard button could have a Linux icon over a Windows one.

![][31]

### Conclusion

It helps to know the common technical terms, specially if you are in discussion on online forums.

Of course, there is no end to jargon. There are many more that didn't make to this list. There will be newer ones as we progress with time.

What are your favorites Linux jargon that you learned recently? Share it with us in the comments 😄

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-jargon/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/what-is-linux/
[4]: https://itsfoss.com/best-linux-distributions/
[5]: https://itsfoss.com/content/images/icon/android-chrome-192x192-231.png
[6]: https://itsfoss.com/dual-boot-myths/
[7]: https://itsfoss.com/content/images/icon/android-chrome-192x192-232.png
[8]: https://itsfoss.com/what-is-grub/
[9]: https://itsfoss.com/content/images/icon/android-chrome-192x192-233.png
[10]: https://itsfoss.com/what-is-desktop-environment/
[11]: https://itsfoss.com/content/images/icon/android-chrome-192x192-234.png
[12]: https://itsfoss.com/content/images/icon/android-chrome-192x192-235.png
[13]: https://itsfoss.com/content/images/icon/android-chrome-192x192-245.png
[14]: https://itsfoss.com/gnome-shell-extensions/
[15]: https://itsfoss.com/linux-terminal-emulators/
[16]: https://itsfoss.com/package-manager/
[17]: https://itsfoss.com/content/images/icon/android-chrome-192x192-236.png
[18]: https://itsfoss.com/content/images/icon/android-chrome-192x192-237.png
[19]: https://itsfoss.com/rolling-release/
[20]: https://itsfoss.com/best-rolling-release-distros/
[21]: https://itsfoss.com/content/images/icon/android-chrome-192x192-238.png
[22]: https://itsfoss.com/content/images/icon/android-chrome-192x192-239.png
[23]: https://itsfoss.com/content/images/icon/android-chrome-192x192-240.png
[24]: https://itsfoss.com/content/images/icon/android-chrome-192x192-242.png
[25]: https://itsfoss.com/content/images/icon/android-chrome-192x192-243.png
[26]: https://unix.stackexchange.com/questions/4126/what-is-the-exact-difference-between-a-terminal-a-shell-a-tty-and-a-con
[27]: https://itsfoss.com/content/images/icon/android-chrome-192x192-244.png
[28]: https://itsfoss.com/immutable-distro/
[29]: https://itsfoss.com/immutable-linux-distros/
[30]: https://itsfoss.com/content/images/icon/android-chrome-192x192-246.png
[31]: https://itsfoss.com/content/images/icon/android-chrome-192x192-247.png
