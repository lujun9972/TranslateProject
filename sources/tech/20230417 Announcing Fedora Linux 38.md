[#]: subject: "Announcing Fedora Linux 38"
[#]: via: "https://fedoramagazine.org/announcing-fedora-38/"
[#]: author: "Matthew Miller https://fedoramagazine.org/author/mattdm/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Announcing Fedora Linux 38
======

![][1]

Today I’m excited to share the results of the hard work of thousands of Fedora Project contributors: the Fedora Linux 38 release is here! With this release, we’re starting a new on-time streak. In fact, we’re ready a week early!

As always, you should make sure your system is fully up-to-date before upgrading from a previous release. Can’t wait to get started? [Download][2] while you read!

### New website

Did you click the download link above? You may have noticed that the [website][2] looks different. This is the result of over a year of work by our Websites & Apps Team, in partnership with the Design and Infrastructure team, as well as the community at large. Right now, you’ll see pages for each of our five Editions, but this is only a start. The [Spins][3] and [Labs][4] websites will be updated in the future. Eventually, this will provide a foundation for bringing more of our websites together. I’m very excited about the visual refresh and the fact that this will make our websites more self-service for teams within Fedora — and very proud of the amazing community team that came together to create this.

### New Spins

Fedora Linux 38 introduces several new Spins ­— variants that showcase different desktop environments. The popular Budgie Desktop environment, first packaged for Fedora in F37, now has its own Spin. The Fedora Budgie Spin aims to provide the premiere Budgie Desktop experience on top of Fedora Linux, the leading edge platform for developers and users alike.

For fans of tiling window managers, we now offer the Sway window manager in a Spin and in an rpm-ostree version we call “Sericea”. Sway uses the modern Wayland protocol and aims to be a drop-in replacement for the i3 window manager.

If you want to use Fedora Linux on your mobile device, F38 introduces a Phosh image. Phosh is a Wayland shell for mobile devices based on Gnome. This is an early effort from our [Mobility SIG][5]. If your device isn’t supported yet, we welcome your contributions!

### Desktop improvements

Fedora Workstation focuses on the desktop experience. As usual, Fedora Workstation features the latest GNOME release. [GNOME 44][6] includes a lot of great improvements, including a new lock screen, a “background apps” section on the quick menu, and improvements to accessibility settings. In addition, enabling third-party repositories now enables an unfiltered view of applications on Flathub.

With this release, we’ve shortened the default timeout when services shut down. This helps your system power off faster — important when you need to grab your laptop and go.

Of course, we produce more than just the Editions. [Fedora Spins][7] and [Labs][8] target a variety of audiences and use cases, including [Fedora Comp Neuro][9], which provides tools for computational neuroscience, and desktop environments like [Fedora LXQt][10], which provides a lightweight desktop environment. And, don’t forget our alternate architectures: [ARM AArch64, Power, and S390x][11].

### Sysadmin improvements

Microdnf — the lighter-weight version of the default package manager — is replaced by dnf5. [dnf5][12] brings performance improvements, a smaller memory footprint, and a new daemon that can provide an alternative to PackageKit. You can start testing dnf5 now before it becomes the default in a future Fedora Linux release.

For mainframe admins, we increased the minimal architecture level for IBM Z hardware to z13. This enables you to benefit from the new features of that platform and get better CPU performance.

We always strive to bring new security features to users quickly. Packages are now built with stricter compiler flags that protect against buffer overflows. The rpm package manager uses a Sequoia-based OpenPGP parser instead of its own implementation.

### Other updates

If you’re profiling applications, you’ll appreciate the framer pointers now built into official packages. This makes Fedora Linux a great platform for developers looking to improve Linux application performance.

Following our “[First][13]” foundation, we’ve updated key programming language and system library packages, including gcc 13, Golang 1.20, LLVM 16, Ruby 3.2, TeXLive2022, PHP 8.2, and many more.

We’re excited for you to try out the new release! Go to <https://fedoraproject.org/> and download it now. Or if you’re already running Fedora Linux, follow the [easy upgrade instructions][14]. For more information on the new features in Fedora Linux 38, see the [release notes][15].

### In the unlikely event of a problem…

If you run into a problem, visit our [Ask Fedora][16] user support forum. This includes a category for [common issues][17].

### Thank you everyone

Thanks to the thousands of people who contributed to the Fedora Project in this release cycle. We love having you in the Fedora community. I hope to see you in Cork this August for the return of [Flock to Fedora][18].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/announcing-fedora-38/

作者：[Matthew Miller][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/04/f38-816x345.jpg
[2]: https://fedoraproject.org/
[3]: https://spins.fedoraproject.org
[4]: https://labs.fedoraproject.org
[5]: https://fedoraproject.org/wiki/Mobility
[6]: https://release.gnome.org/44/
[7]: https://spins.fedoraproject.org/
[8]: https://labs.fedoraproject.org/
[9]: https://labs.fedoraproject.org/en/comp-neuro/
[10]: https://spins.fedoraproject.org/en/lxqt/
[11]: https://alt.fedoraproject.org/alt/
[12]: https://dnf5.readthedocs.io/en/latest/
[13]: https://docs.fedoraproject.org/en-US/project/#_first
[14]: https://docs.fedoraproject.org/en-US/quick-docs/upgrading/
[15]: https://docs.fedoraproject.org/en-US/fedora/f38/release-notes/
[16]: https://ask.fedoraproject.org/
[17]: https://discussion.fedoraproject.org/tags/c/ask/common-issues/82/none/f38/l/latest
[18]: https://flocktofedora.org/
