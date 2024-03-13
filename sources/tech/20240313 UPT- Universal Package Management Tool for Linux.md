[#]: subject: "UPT: Universal Package Management Tool for Linux"
[#]: via: "https://itsfoss.com/upt/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

UPT: Universal Package Management Tool for Linux
======

[![Warp Terminal][1]][2]

The world of software packages on Linux and other Unix-based systems is quite a savannah: each system has its own singular package management approach, making a hell the life of who has to deal with multiple platforms.

There are [Pacman][3] for Arch Linux and derivatives, [Alpine Package Keeper][4] (a.k.a. APK), [Advanced Package Tool][5] (a.k.a. APT) for Debian GNU/Linux and derivatives, [Aptitude][6], a front-end for APT, [Snapcraft][7] for Ubuntu and derivatives, [Yellowdog Updater Modified][8] (a.k.a. Yum) for RPM-based systems, [Slackpkg][9] for Slackware, [Emerge][10] for Gentoo, the `guix` command on [Guix][11], and `nix-env` on [NixOS][12], among others, not to mention [`pkg`][13] on FreeBSD, [Homebrew][14] for macOS, and [Scoop][15] for Windows. Every one of those has its own way of management, forcing you to learn different ways to do the same thing.

In short, it’s really a mess… or is it?

### Enter UPT

A developer called [sigoden][16] has created a universal tool called [Universal Package-management Tool][17], or **UPT** for short, able to put things together in this jungle. Once you have it installed, you won’t need to learn another package management’s _lifestyle_ again.

UPT is written in Rust so you need to [install Rust and Cargo on Ubuntu][18] or whatever Linux distribution you are using.

I recommend installing the [`rustup`][19] package for your system – GNU/Linux systems usually have a `rustup` package available in their repositories.

📋

All the following commands are intended to be performed by the root user, unless stated otherwise, so don’t forget to run your `sudo -i` command.

```

    # On Debian GNU/Linux and derivatives:
    apt install gcc make rustup

    # On Arch Linux and derivatives:
    packman -S gcc make rustup

    # On Alpine:
    apk add gcc make rustup
    rustup-init
    source ~/.cargo/env

    # On RPM-based systems:
    yum install gcc make rustup

    # On macOS with Homebrew (not Linux, obviously)
    brew install clang make rustup

```

📋

I use `clang` instead of `gcc`, and it works as well for me, you’re just going to need to set your `CC` and `CPP` environment variables, if you also want to use it too, to `clang` and `clang++ -E` respectively.

After installing `rustup`, don’t forget to add `$HOME/.cargo/bin` to your `PATH`. If you’re using Bash as shell (usually the default shell), you have to add the following line to `~/.bash_profile`:

```

    export PATH $HOME/.cargo/bin:$PATH

```

If your shell is Zsh, you can add the same line above to `~/.zshrc` instead. Don’t forget to reload the shell.

Now you can install the `upt` command tool:

```

    rustup default stable
    cargo install upt

```

If you want to use an administration user (e.g. in the wheel or sudo group), you should perform the same commands above as the administrator user.

All set! Now you have a single package management tool you can use the same way across your systems.

### Using UPT

Updating the package manager:

```

    sudo upt update

```

![upt update][20]

Installing a package:

```

    sudo upt install package_name

```

![Install package][21]

Upgrading a package:

```

    sudo upt upgrade package_name

```

![Upgrade a package][22]

Upgrading all installed packages:

```

    sudo upt upgrade

```

![Upgrade packages][23]

Removing a package:

```

    sudo upt remove package_name

```

![Remove a package][24]

Searching for a package (`vtk` for instance):

```

    sudo upt search vtk

```

![Search for a package][25]

If the same package is available in apt (deb), Snap, Flatpak etc., which one should UPT choose while installing? It is determined by the order listed in [this table][26].

To prefer a snap package over another, you can set the `UPT_TOOL` environment variable. On the bottom of your bashrc file, add the line:

```

    export UPT_TOOL='snap'

```

Now, if you run (do not use sudo on the below command):

```

    sudo upt install vlc

```

It will prompt for a password. Give it and the snap package will be installed.

0:00

/0:15

1×

Install snap package using UPT

You can see that, the snap version of VLC has been installed.

![Snap version of VLC is installed][27]

### Conclusion

As you can see, UPT needs initial effort to install, which is not a lot for seasoned Linux users.

Unfortunately, although the package manager is the same across different systems, it’s still a front-end for each system's default package manager. That means package names are still the same used by each distro, you can’t use a single package name for different systems.

For instance, if you want to install the Python development package, you’ll need different packages for different systems:

```

    # On Alpine, Debian GNU/Linux, and derivatives
    upt install python3-dev

    # On RPM-based systems:
    upt install python3-devel

    # On Arch Linux
    upt install python

```

![Package Python has no installation candidate][28]

For Ubuntu users, there is a similar tool called Nala that my interest you.

![][29]

I hope you like learning about such interesting CLI tools. Stay tuned for more.

✍️

[Rodrigo Montegasppα Cacilhας][30] is a Linux veteran with over 25 years of experience playing with Linux systems and writing code.

--------------------------------------------------------------------------------

via: https://itsfoss.com/upt/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://wiki.archlinux.org/title/Pacman
[4]: https://docs.alpinelinux.org/user-handbook/0.1a/Working/apk.html
[5]: https://wiki.debian.org/Apt
[6]: https://tracker.debian.org/pkg/aptitude
[7]: https://snapcraft.io/
[8]: http://yum.baseurl.org/
[9]: https://slackpkg.org/
[10]: https://wiki.gentoo.org/wiki/Emerge
[11]: https://guix.gnu.org/
[12]: https://nixos.org/
[13]: https://man.freebsd.org/cgi/man.cgi?query=pkg
[14]: https://brew.sh/
[15]: https://scoop.sh/
[16]: https://github.com/sigoden
[17]: https://crates.io/crates/upt
[18]: https://itsfoss.com/install-rust-cargo-ubuntu-linux/
[19]: https://rustup.rs/
[20]: https://itsfoss.com/content/images/2024/03/upt-update-command-run.svg
[21]: https://itsfoss.com/content/images/2024/03/install-package-upt.svg
[22]: https://itsfoss.com/content/images/2024/03/upgrade-a-package.svg
[23]: https://itsfoss.com/content/images/2024/03/upt-upgrade-command.svg
[24]: https://itsfoss.com/content/images/2024/03/remove-a-package-using-upt.svg
[25]: https://itsfoss.com/content/images/2024/03/search-for-a-package.svg
[26]: https://itsfoss.com/upt/%7C%20Tool%20%20%20%20%20%20%20%20%7C%20Install%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20Uninstall%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20Upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20Search%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20Info%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20Update%20Index%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20Upgrade%20All%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20List%20Installed%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20-----------%20%7C%20---------------------------%20%7C%20---------------------------%20%7C%20-------------------------------%20%7C%20--------------------------%20%7C%20------------------------------%20%7C%20------------------------%20%7C%20------------------------%20%7C%20---------------------------------%20%7C%20%7C%20upt%20%20%20%20%20%20%20%20%20%7C%20upt%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20upt%20remove/uninstall%20$pkg%20%20%20%7C%20upt%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20upt%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20upt%20info/show%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20upt%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20upt%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20upt%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20apk%20%20%20%20%20%20%20%20%20%7C%20apk%20add%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20del%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apk%20list%20-I/--installed%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20apt%20%20%20%20%20%20%20%20%20%7C%20apt%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apt%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apt%20install%20--only-upgrade%20$pkg%20%7C%20apt%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apt%20show%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apt%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apt%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20apt%20list%20-i/--installed%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20brew%20%20%20%20%20%20%20%20%7C%20brew%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20brew%20uninstall%20$pkg%20%20%20%20%20%20%20%20%20%7C%20brew%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20brew%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20brew%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20brew%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20brew%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20brew%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20cards%20%20%20%20%20%20%20%7C%20cards%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20cards%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20cards%20install%20-u/--upgrade%20$pkg%20%7C%20cards%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20cards%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20cards%20sync%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20cards%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%7C%20cards%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20choco%20%20%20%20%20%20%20%7C%20choco%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20choco%20uninstall%20$pkg%20%20%20%20%20%20%20%20%7C%20choco%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20choco%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20choco%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20choco%20upgrade%20all%20--noop%20%7C%20choco%20upgrade%20all%20%20%20%20%20%20%20%20%7C%20choco%20list%20-l/--local-only%20%20%20%20%20%20%20%20%7C%20%7C%20dnf%20%20%20%20%20%20%20%20%20%7C%20dnf%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20dnf%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20dnf%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20dnf%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20dnf%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20dnf%20check-update%20%20%20%20%20%20%20%20%20%7C%20dnf%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20dnf%20list%20--installed%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20emerge%20%20%20%20%20%20%7C%20emerge%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20emerge%20--depclean%20$pkg%20%20%20%20%20%20%7C%20emerge%20--update%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20emerge%20--search%20$pkg%20%20%20%20%20%20%20%7C%20emerge%20--info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20emerge%20--sync%20%20%20%20%20%20%20%20%20%20%20%20%7C%20emerge%20-vuDN%20@world%20%20%20%20%20%20%7C%20qlist%20-lv%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20eopkg%20%20%20%20%20%20%20%7C%20eopkg%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20eopkg%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20eopkg%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20eopkg%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20eopkg%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20eopkg%20update-repo%20%20%20%20%20%20%20%20%7C%20eopkg%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%7C%20eopkg%20list-installed%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20flatpak%20%20%20%20%20%7C%20flatpak%20install%20$pkg%20%20%20%20%20%20%20%20%7C%20flatpak%20uninstall%20$pkg%20%20%20%20%20%20%7C%20flatpak%20update%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20flatpak%20search%20$pkg%20%20%20%20%20%20%20%20%7C%20flatpak%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20-%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20flatpak%20update%20%20%20%20%20%20%20%20%20%20%20%7C%20flatpak%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20guix%20%20%20%20%20%20%20%20%7C%20guix%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20show%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20refresh%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20guix%20package%20-I/--list-installed%20%20%7C%20%7C%20nix-env%20%20%20%20%20%7C%20nix-env%20-i/--install%20$pkg%20%20%20%7C%20nix-env%20-e/--uninstall%20$pkg%20%7C%20nix-env%20-u/--upgrade%20$pkg%20%20%20%20%20%20%20%7C%20nix-env%20-qaP%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20nix-env%20-qa%20--description%20$pkg%20%7C%20nix-channel%20--update%20%20%20%20%20%7C%20nix-env%20-u/--upgrade%20%20%20%20%20%7C%20nix-env%20-q/--query%20--installed%20%20%20%20%7C%20%7C%20opkg%20%20%20%20%20%20%20%20%7C%20opkg%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20find%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20opkg%20list%20--installed%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20pacman%20%20%20%20%20%20%7C%20pacman%20-S%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-Rs%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-S%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-Ss%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-Si%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-Sy%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-Syu%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pacman%20-Q%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20pkg%20%20%20%20%20%20%20%20%20%7C%20pkg%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20info%20-a/--all%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20pkg(termux)%20%7C%20pkg%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20uninstall%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20show%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20upgrade%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkg%20list-installed%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20pkgman%20%20%20%20%20%20%7C%20pkgman%20install%20$pkg%20%20%20%20%20%20%20%20%20%7C%20pkgman%20uninstall%20$pkg%20%20%20%20%20%20%20%7C%20pkgman%20update%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkgman%20search%20$pkg%20%20%20%20%20%20%20%20%20%7C%20-%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkgman%20refresh%20%20%20%20%20%20%20%20%20%20%20%7C%20pkgman%20update%20%20%20%20%20%20%20%20%20%20%20%20%7C%20pkgman%20search%20-i%20-a%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20prt-get%20%20%20%20%20%7C%20prt-get%20install%20$pkg%20%20%20%20%20%20%20%20%7C%20prt-get%20remove%20$pkg%20%20%20%20%20%20%20%20%20%7C%20prt-get%20update%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20prt-get%20search%20$pkg%20%20%20%20%20%20%20%20%7C%20prt-get%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20ports%20-u%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20prt-get%20sysup%20%20%20%20%20%20%20%20%20%20%20%20%7C%20prt-get%20listinst%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20scoop%20%20%20%20%20%20%20%7C%20scoop%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20scoop%20uninstall%20$pkg%20%20%20%20%20%20%20%20%7C%20scoop%20update%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20scoop%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20scoop%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20scoop%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20scoop%20update%20*%20%20%20%20%20%20%20%20%20%20%20%7C%20scoop%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20slackpkg%20%20%20%20%7C%20slackpkg%20install%20%3Cslackpkg%3E%20%7C%20slackpkg%20remove%20%3Cslackpkg%3E%20%20%7C%20slackpkg%20upgrade%20%3Cslackpkg%3E%20%20%20%20%20%7C%20slackpkg%20search%20%3Cslackpkg%3E%20%7C%20slackpkg%20info%20%3Cslackpkg%3E%20%20%20%20%20%20%20%7C%20slackpkg%20update%20%20%20%20%20%20%20%20%20%20%7C%20slackpkg%20upgrade-all%20%20%20%20%20%7C%20ls%20-1%20/var/log/packages%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20snap%20%20%20%20%20%20%20%20%7C%20snap%20install%20--classic%20$pkg%20%7C%20snap%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20snap%20refresh%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20snap%20find%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20snap%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20-%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20snap%20refresh%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20snap%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20urpm%20%20%20%20%20%20%20%20%7C%20urpmi%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20urpme%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20urpmi%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20urpmq%20-y/--fuzzy%20$pkg%20%20%20%20%20%20%7C%20urpmq%20-i%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20urpmi.update%20-a%20%20%20%20%20%20%20%20%20%20%7C%20urpmi%20--auto-update%20%20%20%20%20%20%7C%20rpm%20-q/--query%20--all%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20winget%20%20%20%20%20%20%7C%20winget%20install%20$pkg%20%20%20%20%20%20%20%20%20%7C%20winget%20uninstall%20$pkg%20%20%20%20%20%20%20%7C%20winget%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20winget%20search%20$pkg%20%20%20%20%20%20%20%20%20%7C%20winget%20show%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20-%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20winget%20upgrade%20--all%20%20%20%20%20%7C%20winget%20list%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20xbps%20%20%20%20%20%20%20%20%7C%20xbps-install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%7C%20xbps-remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20xbps-install%20-u/--update%20$pkg%20%20%20%7C%20xbps-query%20-Rs%20$pkg%20%20%20%20%20%20%20%20%7C%20xbps-query%20-RS%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20xbps-install%20-S/--sync%20%20%20%7C%20xbps-install%20-u/--update%20%7C%20qxbps-query%20-l/--list-pkgs%20%20%20%20%20%20%20%20%7C%20%7C%20yum%20%20%20%20%20%20%20%20%20%7C%20yum%20install%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20yum%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20yum%20upgrade%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20yum%20search%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%7C%20yum%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20yum%20check-update%20%20%20%20%20%20%20%20%20%7C%20yum%20update%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20yum%20list%20--installed%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20%7C%20zypper%20%20%20%20%20%20%7C%20zypper%20install%20$pkg%20%20%20%20%20%20%20%20%20%7C%20zypper%20remove%20$pkg%20%20%20%20%20%20%20%20%20%20%7C%20zypper%20update%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20zypper%20search%20$pkg%20%20%20%20%20%20%20%20%20%7C%20zypper%20info%20$pkg%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7C%20zypper%20refresh%20%20%20%20%20%20%20%20%20%20%20%7C%20zypper%20update%20%20%20%20%20%20%20%20%20%20%20%20%7C%20zypper%20search%20-i/--installed-only
[27]: https://itsfoss.com/content/images/2024/03/upt-install-snap.png
[28]: https://itsfoss.com/content/images/2024/03/python-has-no-installation-candidate.png
[29]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[30]: https://github.com/cacilhas
