[#]: subject: "The answer is 42! Fedora Linux 42, that is."
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-42/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The answer is 42! Fedora Linux 42, that is.
======

![][1]

Seventy-five thousand generations ago, our ancestors set a vast computer in motion, asking it to produce the ultimate Linux distribution…

No, wait. It wasn’t quite that long ago. That was a different thing. But in both, the answer to life, the universe, and everything turns out to be: forty-two. In our case, _Fedora Linux 42_ , which is now officially released.

Every Fedora Linux release is a gigantic community effort — it does almost seem infinitely improbable that all of this software made by a whole planet of open source developers could come together so nicely. Yet, here we are again! Thank you so much to everyone who works so hard on Fedora and in all of our upstream projects.

### Upgrade in place

If you have an existing system, [Upgrading Fedora Linux to a New Release][2] is easy. In most cases, it’s not very different from just rebooting for regular updates, except you’ll have a little more time to get a hot beverage from the machine. Perhaps something almost, but not quite, entirely unlike tea.

### Or, start fresh

If this is your first time ~~in space~~ running Fedora Linux, or if you just want to start fresh on an uninhabited system, [download the install media for our flagship Editions][3] (Workstation, KDE Plasma Desktop, Cloud, Server, CoreOS, IoT), [for one of our Atomic Desktops][4] (including Silverblue and Kinoite), or [for alternate desktop options][5] (like Cinnamon, Xfce, or the new and appropriately-thematic Cosmic Desktop spin).

### What’s new?

We’ve promoted our KDE Plasma Desktop offering to “Edition” status. The Fedora KDE team has been hard at work making sure bugs get fixed and everything is polished just so. We’re confident that this can stand along our other amazing flagship offerings.

I know the naming is a bit confusing, with GNOME-powered “Workstation” using a generic label while KDE Plasma Desktop has the tech right in the name. We’ll get that figured out eventually. If you don’t know where to start, don’t panic. Pick one and see how it goes. They’re both excellent desktop environments with great upstream communities, and the same Fedora system underneath it all.

We also have a new alternative desktop choice: COSMIC. This is a modern, written-all-in-Rust desktop environment from our friends over at System76.

Perhaps most excitingly, we have a new installation interface! The previous UI was designed to manage a lot of before-you-even-start configuration choices. Over the past decade, though, we’ve gone to “get the full system installed with no fuss, then set up what you need from a complete environment”. That made the “hub and spoke” model more confusing than helpful. The new UI is streamlined and sleek, just like the Heart of Gold.

Of course, there are other big changes, as well as the usual updates to thousands of packages. See the [Fedora Linux 42 Release Notes][6] for all of the details, and don’t miss the “What’s New?” posts here on Fedora Magazine.

### Last minute warning!

No, it’s not the Vogons, but it is ugly. We discovered a problem with the Live boot media at the last minute, and since the release was already out of the airlock, we can’t do much about it. It doesn’t damage anything, but is annoying: just booting the Live media adds an unexpected entry to the UEFI boot loader _even when Fedora Linux 42 is not installed to the local system._

This is primarily a concern when you are dual-booting with a different operating system, or if you’re just running the Live image and not intending to actually install.

The problem is mostly ~~harmless~~ cosmetic, but still, we should have caught it sooner. Apparently this was posted in our local planning office, but we didn’t go down to the basement past the “Beware of the Leopard” sign to find it.

You can read more about this in the [Common Bugs entry for this issue][7], including how to remove the unwanted entry (and how to avoid the problem altogether).

### What else could go wrong?

We hope nothing will, but if you run into a problem, visit our [Ask Fedora][8] user support forum. This includes a category where we collect [common issues][9] and solutions or work-arounds.

### A last note

![][10]

As you may already know, this is my last release as Fedora Project Leader. We’re welcoming Jef Spaleta into the role, with a handover at Flock to Fedora in June. It’s tempting to sign off with “so long, and thanks for all the fish” — but I’m not planning on going far. I’ll be around Fedora stuff until the (restaurant at the) end of the universe.

A good hitchhiker always knows where their towel is. If you’ve lost track of yours, don’t worry. We’ve got you covered. In collaboration with the Fedora Design Team, our friends at Hello Tux are offering what I think you’ll agree is [the _most hoopy distro swag ever made_][11]. We’ll be handing them out at Flock in Prague. I hope to see you there, but if you can’t make it, you can order one at a discount with the code _FEDORA5._

### Comments, congratulations, and so forth

Let’s talk over at [Fedora Discussion][12]. See you there!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-42/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/F42_release-816x345.jpg
[2]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/
[3]: https://fedoraproject.org/#editions
[4]: https://fedoraproject.org/atomic-desktops/
[5]: https://fedoraproject.org/spins
[6]: https://docs.fedoraproject.org/en-US/fedora/f42/release-notes/
[7]: https://discussion.fedoraproject.org/t/148774
[8]: https://ask.fedoraproject.org/
[9]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f42
[10]: https://fedoramagazine.org/wp-content/uploads/2025/04/f42-towel-768x1024.webp
[11]: https://www.hellotux.com/fedora
[12]: https://discussion.fedoraproject.org/t/the-answer-is-42-fedora-linux-42-that-is/148771
