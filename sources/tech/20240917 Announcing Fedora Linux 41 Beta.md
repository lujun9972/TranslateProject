[#]: subject: "Announcing Fedora Linux 41 Beta"
[#]: via: "https://fedoramagazine.org/announcing-fedora-linux-41-beta/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 41 Beta
======

![][1]

Today, the [Fedora Project][2] is pleased to announce the availability of Fedora Linux 41 Beta. While we’ll have more to share with the general availability of Fedora Linux 41 in about a month, there is plenty in the beta to get excited about now.

Get the the prerelease of any of our editions from our project website:

  * [Fedora Workstation 41 Beta][3]
  * [Fedora Server 41 Beta][4]
  * [Fedora IoT 41 Beta][5]
  * [Fedora Cloud 41 Beta][6]
  * [Fedora CoreOS “next” stream][7]



You can also update an existing system to the beta using [DNF system-upgrade][8].

### What is a Fedora Beta release?

Fedora beta releases are code-complete and will very closely resemble the final release. While the Fedora Project community will be testing this release intensely, we also want you to check and make sure the features you care about are working as intended. The bugs you find and report help make your experience better as well as for millions of Fedora Linux users worldwide! Together, we can help not only make Fedora Linux stronger, but as these fixes and tweaks get pushed upstream to the kernel community, we can contribute to the betterment of the Linux ecosystem and free software holistically.

### Some changes of note

#### Valkey replaces Redis

As Redis recently changed to a proprietary license, we have replaced Redis with Valkey. All software shipped by Fedora is open source and free software, in line with our [Freedom foundation][9]. If you are currently using Redis, see [How to move from Redis to Valkey][10] for migration help.

#### Goodbye**,** Python 2!

Starting with Fedora Linux 41, there will be no Python 2 in Fedora, other than PyPy. Packages requiring Python 2.7 at runtime will need to upgrade to a new version, or be retired also. Developers who still need to test their software on Python 2, or users of software that cannot be updated, can use containers with older Fedora releases.

#### Proprietary Nvidia driver installation with Secure Boot support

Although it can’t be part of Fedora Linux, we know that the Nvidia binary driver is pragmatically essential for many people. Previously, Nvidia driver installation had been removed from GNOME Software because it didn’t support Secure Boot, which is increasingly-often enabled by default on laptops. This change brings the option back for Fedora Workstation users with Secure Boot supported. This is good news for folks who want to use Fedora Linux for gaming and CUDA. The change also helps Fedora stay relevant for AI/LLVM workloads.

#### DNF 5 is here

In Fedora Linux 41, the dnf package management command will be updated to version 5. (DNF5 and bootc will be available on image-based Fedora variants such as Atomic desktops and Fedora IoT.) The new packages will make it simpler to build and update bootable container images based on these variants.

##### DNF and bootc in Image Mode Fedora Variants

In Fedora Linux 41, the DNF package manager will be updated to version 5. This release is faster, smaller, _and_ better. (Pick all three!) You won’t need to change habits — the command is still just dnf, and the basic syntax isn’t different. As one might expect with a major version, there _are_ some incompatible changes. See the [DNF 5 documentation][11] for details.

##### RPM 4.20

Under the hood, our lower-level package management tool is RPM, which also gets a new release, bringing new features for Fedora development. Users won’t see a direct impact immediately, but this update will help us make the distro better overall over time.

#### Reproducible-builds progress

A post-build cleanup is integrated into the RPM build process, making most Fedora packages now reproducible. That is, you can re-build a package from source and expect the package contents to be exactly identical. If this is interesting to you, check out [Fedora Reproducible Builds][12] for more.

#### New fedora-repoquery tool

Fedora-repoquery is a small command line tool for doing repoqueries of Fedora, EPEL, eln, and Centos Stream package repositories. It wraps dnf repoquery separating the cached repo data under separate repo names for faster cached querying. Repoqueries are frequently used by Fedora developers and users, so a more powerful tool like this is generally useful.

#### KDE Plasma Mobile Spin

KDE Plasma Mobile brings the KDE Plasma Desktop to a flexible, mobile format in Fedora 41 as a Spin. This promises to work on both phones, tablets and 2-in-1 laptops.

#### LXQt 2.0

LXQt in Fedora will be upgraded to v2.0, which notably ports the whole desktop to Qt 6 and adds experimental Wayland support.

#### New “Fedora Miracle” spin

The Miracle window manager is a tiling window manager based on the Mir compositor library. While it is a newer project, it contains many useful features such as a manual tiling algorithm, floating window manager support, support for many Wayland protocols, proprietary Nvidia driver support, and much more. Miracle will provide Fedora Linux with a high-quality Wayland experience built with support for all kinds of platforms, including low-end ARM and x86 devices. On top of this, Fedora Linux will be the first distribution to provide a Miracle-based spin, ensuring that it will become the de facto distribution for running Miracle.

> ## Missing Spins?
>
> A [technical glitch][13] means that a few of our spins didn’t build correctly for the beta release — Robotics, Jam, Design Suite, and ARM live images. We still expect these to be part of our final release. If you’re interested in testing these, watch the [Nightly Compose Finder][14] for good builds.

#### Let’s test Fedora 41 Beta together

Since this is a beta release, we expect that you may encounter bugs or missing features. To report issues encountered during testing, contact the Fedora QA team via the [test mailing list][15] or in the [#quality:fedoraproject.org channel on Fedora Chat][16] (Matrix). As testing progresses, common issues are tracked in the [“Common Issues” category][17] on [Ask Fedora][18].

For tips on reporting a bug effectively, read [how to file a bug][19].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-linux-41-beta/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/Fedora_linux_41_beta-816x345.jpg
[2]: https://www.fedoraproject.org/
[3]: https://fedoraproject.org/workstation/download/?beta
[4]: https://fedoraproject.org/server/download/?beta
[5]: https://fedoraproject.org/iot/download/?beta
[6]: https://fedoraproject.org/cloud/download/?beta
[7]: https://fedoraproject.org/coreos/download/?stream=next
[8]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading-fedora-offline/
[9]: https://docs.fedoraproject.org/en-US/project/#_what_is_fedora_all_about
[10]: https://fedoramagazine.org/how-to-move-from-redis-to-valkey/
[11]: https://dnf5.readthedocs.io/en/latest/changes.html
[12]: https://docs.fedoraproject.org/en-US/reproducible-builds/
[13]: https://pagure.io/releng/failed-composes/issue/6956#comment-931510
[14]: https://openqa.fedoraproject.org/nightlies.html
[15]: https://lists.fedoraproject.org/archives/list/test%40lists.fedoraproject.org/
[16]: https://chat.fedoraproject.org/#/room/#quality:fedoraproject.org
[17]: https://discussion.fedoraproject.org/c/ask/common-issues/82/none
[18]: https://ask.fedoraproject.org/
[19]: https://docs.fedoraproject.org/en-US/quick-docs/howto-file-a-bug/
