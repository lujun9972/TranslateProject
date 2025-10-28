[#]: subject: "Fedora Linux 43 is here!"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-43/"
[#]: author: "Jef Spaleta https://fedoramagazine.org/author/jspaleta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Linux 43 is here!
======

![][1]

I’m excited to announce my very first Fedora Linux release as the new Fedora Project Leader. Fedora Linux 43 is here! 43 releases! Wow that’s a lot. I was thinking about proposing special tetracontakaitrigon stickers to celebrate this release, but I’m not sure anyone would notice they weren’t circles.

Thank you and congrats to everyone who has contributed to Fedora to this release, and in all the releases leading up to this one. I’m grateful to be back with a chance to take stewardship of the collaboration as the Fedora Project leader. I’ve been getting my feet under me as much as I can in these first few months. I’m looking forward to writing up some longer missives about where I want to steer this ship, but for right now I just want to highlight some of the changes you should expect to encounter in the latest release of Fedora Linux. Read the highlights below to find out more. Or if you are ready just jump right in!

### Upgrade

If you have an existing system, [Upgrading Fedora Linux to a New Release][2] is easy. In most cases, it’s not very different from just rebooting for regular updates, except you’ll have a little more time to grab a coffee.

### Fresh Install

If this is your first time running Fedora Linux, or if you just want to start fresh with Fedora, [download the install media for our flagship Editions][3] (Workstation, KDE Plasma Desktop, Cloud, Server, CoreOS, IoT), [for one of our Atomic Desktops][4] (Silverblue, Kinoite, Cosmic, Budgie, Sway), or [for alternate desktop options][5] (like Cinnamon, Xfce, Sway, or others).

### What’s new?

As usual, with Fedora, there are just too many individual changes and improvements to go over in detail. You’ll want to take a look at the [release notes][6] for that.

#### Notable User Visible Changes

There are, however, a few notable user visible changes in this release. For those of you installing fresh Fedora Linux 43 Spins, you may be greeted with the new Anaconda WebUI. This was the default installer interface for Fedora Workstation 42, and now it’s the default installer UI for the Spins as well.

If you are a GNOME desktop user, you’ll also notice that the GNOME is now Wayland-only in Fedora Linux 43. GNOME upstream has deprecated X11 support, and has disabled it as a compile time default in GNOME 49. Upstream GNOME plans to fully remove X11 support in GNOME 50.

#### Plumbing Upgrades

Beyond the user-visible changes, there are a couple of significant bits of plumbing that should go unnoticed for most users but are a big deal, nonetheless.

Fedora Linux 43 will be the first release with RPM 6.0. Like I said, this should go unnoticed to end-users, but it is a significant change. RPM 6.0 provides some interesting security enhancements, like multiple key signing of packages. This should help future-proof package signing as we transition to post-quantum-crypto OpenPGP keys in future releases.

We’re also moving forward with our bootc enablement story. Fedora CoreOS is now buildable from a Fedora base bootc image using a Containerfile, instead of needing to be composed with a custom tool. That means anyone with podman can build the Fedora CoreOS image, whether manually or via CI/CD automation.

Fedora CoreOS (FCOS) is also changing how it’s issuing updates to users in Fedora 43. Instead of using an OSTree repository, FCOS updates will be delivered exclusively as OCI images. FCOS 42 provided both OSTree repository and OCI registry as a transition for users. In FCOS 43, the OSTree updates are disabled entirely.

### Save the Date: Fedora Linux 43 Release Party!

To celebrate all this incredible community work, we’ll be hosting a virtual Fedora Linux 43 Release Party! Please **save the date for Friday, 21 November**. We’re still finalizing the schedule and speakers, so registration isn’t open just yet, but more details will be shared soon. You can keep an eye on the [Fedora Linux 43 Release Party Schedule wiki page][7] for the latest updates!

### If you hit a snag

If you run into a problem, visit our [Ask Fedora][8] user support forum. This forum includes a category where we collect [common issues][9] and solutions or work-arounds.

### Just drop by and say “hello”

Drop by our [“virtual watercooler” on Fedora Discussion][10] and join a conversation, share something interesting, and introduce yourself. We’re always glad to see new people!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-43/

作者：[Jef Spaleta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jspaleta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/10/Fedora_linux_43_release-816x345.jpg
[2]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/
[3]: https://fedoraproject.org/#editions
[4]: https://fedoraproject.org/atomic-desktops/
[5]: https://fedoraproject.org/spins
[6]: https://docs.fedoraproject.org/en-US/fedora/latest/release-notes/
[7]: https://fedoraproject.org/wiki/Fedora_Linux_43_Release_Party_Schedule
[8]: https://ask.fedoraproject.org/
[9]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f43
[10]: https://discussion.fedoraproject.org/c/fun/8
