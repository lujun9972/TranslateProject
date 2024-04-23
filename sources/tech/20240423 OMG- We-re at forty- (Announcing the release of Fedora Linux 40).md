[#]: subject: "OMG! We’re at forty! (Announcing the release of Fedora Linux 40)"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-40/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

OMG! We’re at forty! (Announcing the release of Fedora Linux 40)
======

![][1]

Image contributed by Consolation Obazee

Oh, wow. This feels like a big number! I’m proud to announce the 40th release of Fedora Linux, a community-built and community-maintained operating system that belongs to _all_ of us. I’m also happy to note that we’re back on track with an on-time release. Thank you to all Fedora contributors who made that possible, and who have, yet again, made this our best one ever.

This is also a _personally_ exciting number for me, because this marks the _20th_ release for which I’ve served as Fedora Project Leader. We’ve gone through a lot in this last decade, and I’m incredibly happy to see our community thrive and grow. In addition to many long-familiar names and faces, it’s exciting to see a new generation with new energy and ideas. In some cases, this is _literally_ a new generation, as many of you have grown up with Fedora. But at whatever age, I’m proud we’ve built such a welcoming and friendly community, and that we continue to work at improving our inclusiveness, diversity, and accessibility.

But anyway! Enough of that. Time to see what we’ve got for you in Fedora Linux 40! If you have a system already, [Upgrading Fedora to a New Release][2] is easy. If you’re new, or just curious, head to [Get Fedora][3] for installation options.

### Desktop news

Fedora Workstation Edition features the GNOME desktop environment, now updated to version 46. Check out [What’s New in Fedora Workstation 40?][4] for the highlights!

The KDE Spin now includes KDE Plasma 6, and runs with Wayland out of the box. Read more about that and other KDE Spin updates at [What’s New in Fedora KDE 40?][5]

We’re also officially reviving the “Fedora Atomic Desktop” brand for all of our variants which use ostree or image-based provisioning. Our technology isn’t really “immutable”, so this provides a better grouping. Read more about this at [Introducing Fedora Atomic Desktops][6] — but in short, Fedora Silverblue and Fedora Kinoite will remain, while the other desktop variants will become Fedora Sway Atomic and Fedora Budgie Atomic.

### Tools for AI development

Fedora Linux 40 ships with our first-ever PyTorch package. PyTorch is a popular framework for deep learning, and it can be difficult to reliably install with the right versions of drivers and libraries and so on. The current package only supports running on the CPU, without GPU or NPU acceleration, but this is just the first step. Our aim is to produce a complete stack with PyTorch and other popular tools ready to use on a wide variety of hardware out-of-the-box.

We’re also shipping with ROCm 6 — open-source software that provides acceleration support for AMD graphics cards. We plan to have that enabled for PyTorch in a future release.

### Updates all around!

As usual, we’ve rebuilt everything in the distribution using updated compilers and libraries (and, of course, those updated tools are ready for developers to use). These updates bring bugfixes, security improvements, and performance gains.

And, of course, hundreds of Fedora packagers and testers have worked to integrate the latest versions of open source software from thousands of upstream projects. Those projects, in turn, are made by an uncountable number of developers and contributors working on marketing, design, documentation, code, quality, translations, communications, events, governance, infrastructure, security, and so much more. Thank you again to everyone who makes Fedora amazing, and to everyone whose work has built this whole universe of free and open source software.

### Speaking of updates…

There are several important release-day bugfix and security updates available today as well. If you upgrade from an earlier Fedora Linux release, you’ll get them as part of that. For new installations, please make sure to check for and apply updates as soon as possible.

### In the unlikely event of a problem…

If you run into a problem, visit our [Ask Fedora][7] user support forum. This includes a category for [common issues][8].

### Or if you just want to say “hello”…

Drop by our [“virtual watercooler” on Fedora Discussion][9] and join a conversation, share something interesting, and introduce yourself.

Also, remember that our annual contributor conference, [Flock To Fedora][10], is coming up! It’ll be in Rochester, New York this August. The [call for session proposals][11] is still open, if you have something you’d like to share or work on. If you’re already a Fedora contributor, or are interested in being one, or think you might be, we’d love to see you there!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-40/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/04/Fedora_Linux_40_release-816x345.jpg
[2]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-new-release/
[3]: https://fedoraproject.org
[4]: https://fedoramagazine.org/whats-new-fedora-workstation-40
[5]: https://fedoramagazine.org/whats-new-in-fedora-kde-40
[6]: https://fedoramagazine.org/introducing-fedora-atomic-desktops/
[7]: https://ask.fedoraproject.org/
[8]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f40
[9]: https://discussion.fedoraproject.org/c/fun/8
[10]: https://flocktofedora.org/
[11]: https://communityblog.fedoraproject.org/flock-2024-cfp-until-april-21st/
