[#]: subject: "Announcing Fedora Linux 40 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-40-beta/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 40 Beta
======

![][1]

The Fedora Project is pleased to announce the immediate availability of Fedora Linux 40 Beta, the next step towards our planned Fedora Linux 40 release at the end of April.

Get the the prerelease of any of our editions from our project website:

  * [Fedora Workstation 40 Beta][2]
  * [Fedora Server 40 Beta][3]
  * [Fedora IoT 40 Beta][4]
  * [Fedora Cloud 40 Beta][5]
  * [Fedora CoreOS “next” stream][6]



Or, try one of our many different desktop variants (like KDE Plasma, Xfce, or Cinnamon) from [Fedora Linux Spins][7].

You can also update an existing system to the beta using [DNF system-upgrade][8].

### **Beta release highlights**

Some key things to try in this release!

[PyTorch][9] is a popular open-source machine learning framework. We want to make using this tool in Fedora Linux as easy as possible, and it’s now available for you to install with one easy command: sudo dnf install pytorch

Note that for this release, we’ve only included CPU support, but this lays the groundwork for future updates with support for accelerators like GPUs and NPUs. For now, this is suitable for playing around with the technology, and possibly for some light inference loads.

Fedora IoT now uses ostree native containers, or “bootable containers”. This showcases the next generation of the ostree technology for operating system composition. Read more in the documentation from [ostree][10] and [bootc][11].

Also on the immutable OS front, we’ve revived the “Atomic Desktop” brand for the growing collection of desktop spins based on ostree. An ever-expanding collection of obscure mineral names was fun, but hard to keep straight. We’re keeping well-known _Silverblue_ and _Kinoite_ , and other desktop environments will be, for example, _Fedora Sway Atomic_ and _Fedora Budgie Atomic._

### Other notable updates

Fedora KDE Desktop now ships with Plasma 6, thanks to a lot of hard work from the Fedora KDE Special Interest Group and the upstream KDE project, is Wayland-only. (Don’t worry — X11-native apps will still run under Wayland.)

Fedora Workstation 40 Beta brings us GNOME 46. We’re bringing you Podman 5 for container management. The AMD ROCm accelerator framework is updated to version 6. And, we’ve got the updated language stacks you expect from a new release: LLVM 18 (that’s clang and friends), as well as GCC 14 (with newer glibc, binutils, and gdb).

There are many other changes big and small across the release. See the official [Fedora Linux 40 Change Set][12] for more, and check your favorite software for improvements — and, since this is a beta… possibly bugs!

### **Testing needed**

As with any beta release, we expect that you may encounter bugs or missing features. To report issues encountered during testing, contact the Fedora Quality team via the [test mailing list][13] or in the [#quality channel on Fedora Chat][14]. As testing progresses, common issues are tracked in the [“Common Issues” category][15] on Ask Fedora.

For tips on reporting a bug effectively, read [how to file a bug][16].

### **What is the beta release?**

A beta release is code-complete and bears a very strong resemblance to the final release. If you take the time to download and try out the beta, you can check and make sure the things that are important to you are working. Every bug you find and report doesn’t just help you, it improves the experience of millions of Fedora Linux users worldwide! Together, we can make Fedora rock-solid. We have a culture of coordinating new features and pushing fixes upstream as much as we can. Your feedback improves not only Fedora Linux, but the Linux ecosystem and free software as a whole.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-40-beta/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/03/fedora-linux-40-beta-816x345.jpg
[2]: https://fedoraproject.org/workstation/download/
[3]: https://fedoraproject.org/server/download/
[4]: https://fedoraproject.org/iot/download/
[5]: https://fedoraproject.org/cloud/download/
[6]: https://fedoraproject.org/coreos/download/?stream=next
[7]: https://fedoraproject.org/spins/
[8]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[9]: https://pytorch.org/
[10]: https://coreos.github.io/rpm-ostree/container/
[11]: https://containers.github.io/bootc/intro.html
[12]: https://fedoraproject.org/wiki/Releases/40/ChangeSet
[13]: https://lists.fedoraproject.org/archives/list/test%40lists.fedoraproject.org/
[14]: https://chat.fedoraproject.org/#/room/#quality:fedoraproject.org
[15]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/f40
[16]: https://docs.fedoraproject.org/en-US/quick-docs/howto-file-a-bug/
