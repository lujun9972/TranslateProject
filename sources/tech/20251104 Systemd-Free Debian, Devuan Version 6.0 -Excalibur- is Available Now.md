[#]: subject: "Systemd-Free Debian, Devuan Version 6.0 "Excalibur" is Available Now"
[#]: via: "https://itsfoss.com/news/devuan-6-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Systemd-Free Debian, Devuan Version 6.0 "Excalibur" is Available Now
======

[Devuan][1] is a Linux distribution that takes a different approach from most popular distros in the market. It is based on Debian but offers users [complete freedom from systemd][2].

The project emerged in 2014 when a group of developers decided to offer [init freedom][3]. Devuan maintains compatibility with Debian packages while providing alternative init systems like SysVinit and OpenRC.

With a [recent announcement][4], a new Devuan release has arrived with some important quality of life upgrades.

## ⭐ Devuan 6.0: What's New?

![][5]

Codenamed " _Excalibur_ ", this release arives after extensive testing by the Devuan community. It is based on [Debian 13 "Trixie"][6] and inherits most of its improvements and package upgrades.

Devuan 6.0 ships with [Linux kernel 6.12][7], an LTS kernel that brings real-time PREEMPT_RT support for time-critical applications and improved hardware compatibility.

On the desktop environment side of things, [Xfce 4.20][8] is offered as the default one for the live desktop image, with additional options like KDE Plasma, MATE, Cinnamon, LXQt, and LXDE.

The package management system gets a major upgrade with [APT 3.0][9] and its new Solver3 dependency resolver. This backtracking algorithm handles complex package installations more efficiently than previous versions. Combined with the color-coded output, the package management experience is more intuitive now.

This Devuan release also **makes the merged-/usr filesystem layout compulsory** for all installations. Users upgrading from Daedalus (Devuan 5.0) must install the `usrmerge` package before attempting the upgrade.

Similarly, new installations [now use tmpfs][10] for the `/tmp` directory, storing temporary files in RAM instead of on disk. This improves performance through faster read and write operations.

And, following Debian's lead, **Devuan 6.0 does not include an i386 installer ISO**. The shift away from 32-bit support is now pretty much standard across major distributions. That said, i386 packages are still available in the repositories.

The next release, Devuan 7, is codenamed " _ **Freia**_ ". Repositories are already available for those adventurous enough to be early testers.

## 📥 Download Devuan 6.0

This release supports multiple CPU architectures, including **amd64** , **arm64** , **armhf** , **armel** , and **ppc64el**. You will find the relevant installation media on the [official website][11], which lists HTTP mirrors and torrents.

Existing Devuan 5.0 "Daedalus" users can follow the [official upgrade guide][12].

[Devuan 6.0][11]

**Suggested Read** 📖

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/devuan-6-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.devuan.org/
[2]: https://itsfoss.com/systemd-free-distros/
[3]: https://www.devuan.org/os/init-freedom
[4]: https://www.devuan.org/os/announce/excalibur-release-announce-2025-11-02
[5]: https://itsfoss.com/content/images/2025/11/devuan-6-0-about-dialog-apt-version.png
[6]: https://itsfoss.com/debian-13-release/
[7]: https://itsfoss.com/linux-kernel-6-12/
[8]: https://itsfoss.com/xfce-4-20-release/
[9]: https://itsfoss.com/apt-3-release/
[10]: https://itsfoss.com/debian-13-tmp-mounting/
[11]: https://www.devuan.org/get-devuan
[12]: https://www.devuan.org/os/documentation/install-guides/excalibur/upgrade-to-excalibur
[13]: https://itsfoss.com/content/images/icon/android-chrome-192x192-318.png
