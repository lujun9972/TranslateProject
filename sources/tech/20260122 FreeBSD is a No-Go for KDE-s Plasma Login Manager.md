[#]: subject: "FreeBSD is a No-Go for KDE's Plasma Login Manager"
[#]: via: "https://itsfoss.com/news/plasma-login-manager-drops-freebsd/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

FreeBSD is a No-Go for KDE's Plasma Login Manager
======

[![Warp Terminal][1]][2]

[FreeBSD][3] is a Unix-like operating system that has roots in Berkeley Software Distribution (BSD), which itself originated from research conducted at the University of California, Berkeley, in the 1970s.

The OS is known for its advanced networking features, security capabilities, and freedom-focused licensing, finding use in a wide range of hardware ranging from embedded systems to being the backbone of major cloud services.

Unfortunately, it looks like **KDE's Plasma Login Manager won't be working on it** , as [an accepted merge request][4] sees the focus turn to compatibility on Linux systems.

### FreeBSD Left Behind?

[Nicolas Fella][5], a KDE engineer, submitted the merge request to drop FreeBSD support from Plasma Login Manager, saying that **it relies on systemd/logind, and that FreeBSD is not supported**.

In this particular case, systemd and logind look like hard dependencies of the login manager, which means the software is built to work exclusively with these components and cannot function without them.

And, to further clarify, [systemd][6] is a popular init system and service manager that has become the de facto standard on Linux ( _whether some like it or not_ ), and [logind][7] is a component of systemd that is responsible for user session management.

Though Plasma Login Manager being dropped from FreeBSD support **doesn't mean that KDE has abandoned the operating system altogether**. FreeBSD users [can still run the KDE Plasma desktop environment][8] and continue using [SDDM][9], the current login manager that works just fine on such systems.

Plus, it's not like FreeBSD prioritizes staying near the bleeding edge [like Fedora does][10].

### My Take on This

I kind of understand why KDE might've gone with this approach; if their focus is on Linux and systemd-based systems, dedicating resources to unused FreeBSD code doesn't make sense.

As for FreeBSD, I am sure users of this operating system won't really care much for missing out on this as they have plenty of login manager options available. The platform itself [is growing quite well][11] too!

* * *

**Suggested Read 📖:** [_Fedora 44 Will Be the First Distro to Adopt KDE's Plasma Login Manager_][10]

![][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/plasma-login-manager-drops-freebsd/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.freebsd.org/
[4]: https://invent.kde.org/plasma/plasma-login-manager/-/merge_requests/42
[5]: https://invent.kde.org/nicolasfella
[6]: https://systemd.io/
[7]: https://www.freedesktop.org/software/systemd/man/latest/systemd-logind.service.html
[8]: https://community.kde.org/FreeBSD/Setup
[9]: https://github.com/sddm/sddm
[10]: https://itsfoss.com/news/fedora-44-plasma-login-manager/
[11]: https://itsfoss.com/news/freebsd-laptop-adoption/
[12]: https://itsfoss.com/content/images/icon/android-chrome-512x512-234.png
