[#]: subject: "Fedora Linux 41 is here!"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-41/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Linux 41 is here!
======

![][1]

Background image by Yotam Guttman

I’m happy to once again announce an early release of Fedora Linux 41. Every cycle, our Quality team carefully validates candidate builds against our [release criteria][2], and this time around, we felt confident that we were ready at our early target date. Thank you and congratulations to everyone in Fedora who worked so hard to make this possible, and to all of our upstream projects — and to everyone who helps build a better world by engaging with community-built free and open source software.

What do we have in store for you this time around? A ton of updates to thousands of packages, ranging from tiny patches to big new features. Read the highlights below to find out more. Or, just jump right in!

### Upgrade

If you have an existing system, [Upgrading Fedora to a New Release][3] is easy, and in most cases not much more of a process than rebooting for regular updates (except you’ll have more time to go get some coffee).

### Fresh installation

If you’re new to Fedora Linux (welcome!) or just want to start fresh, [download the install media for our flagship Editions][4] (Workstation, Cloud, Server, CoreOS, IoT), [for one of our Atomic Desktops][5] (including Silverblue and Kinoite), or [for alternate desktop options][6] (like KDE Plasma, Xfce, or the new “Miracle” spin).

### What’s new?

#### **DNF 5**

Fedora Linux 41 defaults to a new major release of the command-line package management tool DNF. This version is faster, smaller and requires fewer supporting packages. This eliminates the need for “microdnf” for containers and memory-constrained systems — now, the same DNF can be used across containers, servers, desktops and devices.

#### **Desktop Updates**

Fedora Workstation 41 is based on GNOME 47. Read [What’s New in Fedora Workstation 41?][7] for details. Notably for command-line users, we’ve changed the default terminal to [Ptyxis][8]. It’s more lightweight, but has some nice new features as well. (GNOME Terminal is still there if you need some of the flexibility it offers.)

Fedora KDE Plasma Desktop ships with the latest KDE 6.2 release. See [What’s New in Fedora KDE 41?][9] for more. We also have a new Spin featuring [KDE Plasma Mobile][10].

If you’re interested in trying something new, take a look at [Fedora Miracle][11]! Miracle is a new desktop environment built on Mir and Wayland. It features tiling window management _and_ flashy graphics and smooth window animations.

#### **New options for image mode**

We’re shipping image-based Fedora variants (such as Atomic Desktops, CoreOS and Fedora IoT) with a new tool called “bootc”. This is the successor to rpm-ostree, building on those ideas in a more flexible way — and letting you use container patterns to define your personal flavor of Fedora. (Shout out to our friends over at [Universal Blue][12], a Fedora downstream project which pioneered this approach!)

If you’re eager to try this, it’s easy to switch from rpm-ostree to bootc. For example, for Fedora IoT, run the following command:

```

    sudo bootc switch quay.io/fedora/fedora-iot

```

Soon, you’ll be able to use DNF 5 to seamlessly manage locally-installed packages, instead of needing to call rpm-ostree or bootc directly. (This is [work in progress][13]!)

Image-mode systems also now benefit from [bootupd][14], which allows users to apply bootloader updates more easily — for example, if there is an update to the Secure Boot database.

#### **Secure Boot support for systems which need the proprietary Nvidia driver**

Although we don’t ship proprietary software, we want people to actually be able to use the hardware they have, so we worked to make it easy to install the proprietary drivers from third-party repositories. However, as more and more systems are shipping with Secure Boot enabled, we temporarily removed that option. Now it’s back. When you install the driver, GNOME Software will create a [Machine Owner Key which you can manually enable][15].

#### **MIPI, and Pipewire camera support in Firefox**

This is exciting! The cameras shipping in new laptops use an interface called “MIPI”, which expects a lot more from the operating system. Previously, these were a pain to get working. Now we have integrated support for Intel IPU6 attached MIPI cameras. We’re also shipping Firefox with PipeWire for video enabled by default. The new cameras need this — and as an added bonus, you get a nice clear indicator in the GNOME top bar when your camera is on.

### Zero-day updates

There are several important release-day bugfix and security updates available today as well. If you upgrade from an earlier Fedora Linux release, you’ll get them as part of that. For new installations, please make sure to check for and apply updates as soon as possible.

### In the unlikely event of a problem…

If you run into a problem, visit our [Ask Fedora][16] user support forum. This includes a category where we collect [common issues][17] and solutions or work-arounds.

### Or if you just want to say “hello”…

Drop by our [“virtual watercooler” on Fedora Discussion][18] and join a conversation, share something interesting, and introduce yourself. We’re always glad to see new people!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-41/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/10/Fedora_linux_41_release-816x345.jpg
[2]: https://fedoraproject.org/wiki/Fedora_Release_Criteria
[3]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/
[4]: https://fedoraproject.org/#editions
[5]: https://fedoraproject.org/atomic-desktops/
[6]: https://fedoraproject.org/spins
[7]: https://fedoramagazine.org/whats-new-fedora-workstation-41
[8]: https://devsuite.app/ptyxis/
[9]: https://fedoramagazine.org/whats-new-in-fedora-kde-41
[10]: https://fedoraproject.org/spins/kde-mobile
[11]: https://fedoraproject.org/spins/miraclewm
[12]: https://universal-blue.org/
[13]: https://docs.fedoraproject.org/en-US/bootc/dnf/#_using_dnf_at_runtime
[14]: https://github.com/coreos/bootupd
[15]: https://docs.fedoraproject.org/en-US/quick-docs/mok-enrollment/
[16]: https://ask.fedoraproject.org/
[17]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f41
[18]: https://discussion.fedoraproject.org/c/fun/8
