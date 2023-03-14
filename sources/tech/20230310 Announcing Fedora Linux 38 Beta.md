[#]: subject: "Announcing Fedora Linux 38 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora-38-beta/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 38 Beta
======

![The text "Fedora Linux 38 Beta" on the default Fedora Linux 38 background image: cumuloform clouds with a green field in the background][1]

The Fedora Project is pleased to announce the immediate availability of Fedora Linux 38 Beta, the next step towards our planned Fedora Linux 38 release at the end of April.

Download this prerelease from our Get Fedora site:

  * [Get Fedora 38 Workstation Beta ][2]
  * [Get Fedora 38 Server Beta][3]
  * [Get Fedora 38 IoT Beta][4]
  * [Get Fedora 38 Cloud Beta][5]
  * [Get Fedora 38 CoreOS Beta][6]



Or, check out one of our popular variants, including KDE Plasma, Xfce, and other desktop environments, as well as images for ARM devices like the Raspberry Pi:

  * [Get Fedora Spins 38 Beta][7]
  * [Get Fedora Labs 38 Beta][8]
  * [Get Fedora Linux 38 Beta for ARM][9]



### Beta Release Highlights

#### Fedora Workstation

Fedora 38 Workstation Beta includes GNOME 44. It’s currently in beta, with a final release expected at the end of March. GNOME 44 includes a lot of great improvements, including a new lock screen, a “background apps” section on the quick menu, and improvements to accessibility settings . In addition, enabling third-party repositories now enables an unfiltered view of applications on Flathub.

#### Other updates

We always strive to bring new security features to users quickly. Packages are now built with stricter compiler flags that protect against buffer overflows. The rpm package manager uses a Sequoia-based OpenPGP parser instead of its own implementation.

If you’re profiling applications, you’ll appreciate the frame pointers now built into official packages. This makes Fedora Linux a great platform for developers looking to improve Linux application performance.

Of course, there’s the usual update of programming languages and libraries: Ruby 3.2, gcc 13, LLVM 16, Golang 1.20, PHP 8.2, and much more!

### Testing needed

Since this is a Beta release, we expect that you may encounter bugs or missing features. To report issues encountered during testing, contact the Fedora QA team via the [test mailing list][10] or in the #quality channel on Fedora Chat. As testing progresses, common issues are tracked in the [“Common Issues” category][11] on Ask Fedora.

For tips on reporting a bug effectively, read [how to file a bug][12].

### What is the Beta Release?

A Beta release is code-complete and bears a very strong resemblance to the final release. If you take the time to download and try out the Beta, you can check and make sure the things that are important to you are working. Every bug you find and report doesn’t just help you, it improves the experience of millions of Fedora Linux users worldwide! Together, we can make Fedora rock-solid. We have a culture of coordinating new features and pushing fixes upstream as much as we can. Your feedback improves not only Fedora Linux, but the Linux ecosystem and free software as a whole.

### More information

For more detailed information about what’s new on Fedora Linux 38 Beta release, you can consult the [Fedora Linux 38 Change set][13]. It contains more technical information about the new packages and improvements shipped with this release.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-38-beta/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/03/f38-beta-816x345.jpg
[2]: https://getfedora.org/workstation/download/
[3]: https://getfedora.org/server/download/
[4]: https://getfedora.org/iot/download/
[5]: https://alt.fedoraproject.org/en/cloud/
[6]: https://getfedora.org/en/coreos/download
[7]: https://spins.fedoraproject.org/prerelease
[8]: https://labs.fedoraproject.org/prerelease
[9]: https://arm.fedoraproject.org/prerelease
[10]: https://lists.fedoraproject.org/archives/list/test%40lists.fedoraproject.org/
[11]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/f38
[12]: https://docs.fedoraproject.org/en-US/quick-docs/howto-file-a-bug/
[13]: https://fedoraproject.org/wiki/Releases/38/ChangeSet
