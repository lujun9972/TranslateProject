[#]: subject: "Announcing Fedora Linux 42 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-42-beta/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 42 Beta
======

![][1]

The [Fedora Project][2] is pleased to announce the availability of Fedora Linux 42 Beta! We have lots to share with you about our upcoming release of Fedora Linux 42, and we want to give you a sneak preview of what’s in this release in the beta version that is out now.

Get the the pre-release of any of our editions from our project website:

  * [Fedora Workstation 42 Beta][3]
  * [Fedora KDE Plasma Desktop 42 Beta][4]
  * [Fedora Server 42 Beta][5]
  * [Fedora IoT 42 Beta][6]
  * [Fedora Cloud 42 Beta][7]
  * [Fedora CoreOS “next” stream][8]



You can also update an existing system to the beta using [DNF system-upgrade][9].

### Beta Release Highlights

#### New Edition Alert

KDE Plasma Desktop has been promoted to edition status starting with Fedora Linux 42 Beta! You can expect to continue to enjoy the same level of quality from Fedora KDE Plasma Desktop that you always have. In addition, Fedora KDE Plasma Desktop is now supported on Power Systems (ppc64le). Also the full KDE stack (including KDE PIM) is now available on Power and we have installable live images for OpenPOWER based systems like the Talos Workstation from [Raptor Systems][10].

#### Fedora COSMIC Spin

We also have a brand new Spin in Fedora Linux 42 Beta – introducing the Fedora COSMIC spin! This new Rust-based desktop environment developed by System76, makers of Pop!_OS. COSMIC has many unique features, such as hybrid per-workspace window/tiling management, window stacks with tabs to switch between windows, and robust customization features that integrate with GTK and (later on) Qt!

#### Anaconda Changes

Anaconda has some pretty significant changes in Fedora Linux 42 Beta. They have introduced a new Web UI that is now the default for Fedora Workstation. This means that users can enjoy a smooth installation experience, with features such as an installation progress indicator, built in help, configuration review and more. This new feature also includes [Wizard][11] which will allow users to skip what they don’t need during installation.

The Anaconda team has launched a new web UI for partitioning in Fedora Linux 42 Beta. With this new feature, the biggest benefit to Fedora users is the new guided partitioning function. This provides a more powerful automatic partitioning, where the user will select a goal and have additional customizations possible. This change also comes with a new “Reinstall Fedora” option which allows users to easily reinstall their system if something goes wrong. It also adds support for dual-boot installation. Users just need to create some free space and don’t have to understand other details.

### Some **updates** to enjoy in Fedora Linux 42 Beta

This release will include the latest upstream release of python-setuptools. Setuptools is a package development process library designed to facilitate packaging Python projects. It enhances the former Python standard library distutils (distribution utilities).

There is also a DNF5 improvement that includes new logic that will remove expired and obsolete repository keys from the system. This means users can enjoy the automatic management of repository keys during software installation or upgrades.

We are also including the newest version of Ruby with this beta release. Ruby 3.4 is the latest stable version of Ruby. Many new features and improvements are included for the increasingly diverse and expanding demands for Ruby. With this major update from Ruby 3.3 in Fedora Linux 41 to Ruby 3.4 in Fedora Linux 42, Fedora Linux becomes the superior Ruby development platform.

In Fedora Workstation, we have also introduced the SDL3 transition and Wayland-by-default for SDL apps, and included the new GNOME well-being feature.

There are a lot more changes coming in Fedora Linux 42. The above is just a snippet! Please check out [the Fedora Linux 42 Change Set page][12] for a complete list of the changes included with this OS release.

### **Testing needed**

As with any beta release, we expect that you may encounter bugs or missing features. To report issues encountered during testing, contact the Fedora Quality team via the [test mailing list][13] or in the [#quality channel on Fedora Chat][14]. As testing progresses, common issues are tracked in the [“Common Issues” category][15] on [Ask Fedora][16].

For tips on reporting a bug effectively, read [how to file a bug][17].

### **What is the beta release?**

A beta release is code-complete and bears a very strong resemblance to the final release. If you take the time to download and try out the beta, you can check and make sure the things that are important to you are working. Every bug you find and report doesn’t just help you, it improves the experience of millions of Fedora Linux users worldwide! Together, we can make Fedora rock-solid. We have a culture of coordinating new features and pushing fixes upstream as much as we can. Your feedback improves not only Fedora Linux, but the Linux ecosystem and free software as a whole.

* * *

Comments are welcome on [discussion.fedoraproject.org][18]. For tech support, please use [ask.fedoraproject.org][16].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-42-beta/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/03/F42_beta_release-816x345.jpg
[2]: https://www.fedoraproject.org/
[3]: https://fedoraproject.org/workstation/download/?beta
[4]: https://fedoraproject.org/kde/download/?beta
[5]: https://fedoraproject.org/server/download/?beta
[6]: https://fedoraproject.org/iot/download/?beta
[7]: https://fedoraproject.org/cloud/download/?beta
[8]: https://fedoraproject.org/coreos/download/?stream=next
[9]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[10]: https://www.raptorcs.com/
[11]: https://communityblog.fedoraproject.org/anaconda-is-getting-a-new-suit-and-a-wizard/
[12]: https://fedoraproject.org/wiki/Releases/42/ChangeSet
[13]: https://lists.fedoraproject.org/archives/list/test%40lists.fedoraproject.org/
[14]: https://chat.fedoraproject.org/#/room/#quality:fedoraproject.org
[15]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/f40
[16]: https://discussion.fedoraproject.org/c/ask/6/none
[17]: https://docs.fedoraproject.org/en-US/quick-docs/howto-file-a-bug/
[18]: https://discussion.fedoraproject.org/t/fedora-linux-42-beta-is-here-the-announcement-comments-topic/147247
