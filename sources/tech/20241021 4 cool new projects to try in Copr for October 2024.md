[#]: subject: "4 cool new projects to try in Copr for October 2024"
[#]: via: "https://fedoramagazine.org/four-cool-new-projects-to-try-in-copr-for-october-2024/"
[#]: author: "Jiri Kyjovsky https://fedoramagazine.org/author/nikromen/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 cool new projects to try in Copr for October 2024
======

![4 package to try from the Copr repos][1]

[Copr][2] is a build-system for anyone in the Fedora community. It hosts thousands of projects for various purposes and audiences. Some of them should never be installed by anyone, some are already being transitioned to the official Fedora Linux repositories, and the rest are somewhere in between. Copr gives you the opportunity to install 3rd party software that is not available in Fedora Linux repositories, try nightly versions of your dependencies, use patched builds of your favourite tools to support some non-standard use-cases, and just experiment freely.

This article takes a closer look at interesting projects that recently landed in Copr.

If you don’t know [how to enable a repository][3] or if you are concerned about whether [is it safe to use Copr][4], please consult the [project documentation][5].

### Hyprland

[Hyprland][6] is a beautiful Wayland compositor for Linux, offering advanced window management, eye-candy animations, and high customizability. It gives users fine control over their desktop environment, making it perfect for those who value both aesthetics and functionality.

![][7]

#### Installation instructions

The [repo][8] currently provides _Hyprland_ and _many more_ packages needed for your setup like _ags_ or _swww_ for Fedora 39, 40, 41, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable solopasha/hyprland
    sudo dnf install hyprland

```

### hblock

Improve your security and privacy by blocking ads, tracking, and malware domains with [hBlock][9]. This POSIX-compliant shell script compiles lists of such domains from multiple sources and creates a hosts file to block connections to them. You just need to use the following command:

```

    hblock

```

This will generate an _/etc/hosts_ file with the blocked domains. Keep in mind that hBlock **replaces your system’s existing hosts file** by default, so it’s a good idea to back it up before running the script.

#### Installation instructions

The [repo][10] currently provides _hblock_ for Fedora 39, 40, 41, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable pesader/hblock
    sudo dnf install hblock

```

### Ungoogled Chromium

[Ungoogled Chromium][11] is a privacy-enhanced version of the Chromium browser, designed to remove all Google services dependencies and tracking. It offers the same speed and functionality as regular Chromium but without the built-in connections to Google. This makes it ideal for users who want more control over their data and a more private browsing experience, while still enjoying the benefits of an open-source, lightweight browser.

![][12]

#### Installation instructions

The [repo][13] currently provides _ungoogled-chromium_ for Fedora 39, 40, 41, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable wojnilowicz/ungoogled-chromium
    sudo dnf install ungoogled-chromium

```

### Floorp

[Floorp][14] is a privacy-focused web browser based on Firefox, designed to enhance user security and reduce tracking. It removes telemetry and includes built-in tools for blocking ads and trackers, providing a cleaner browsing experience. With its user-friendly interface, Floorp is an excellent choice for those looking to protect their online privacy.

![][15]

#### Installation instructions

The [repo][16] currently provides _floorp_ for Fedora 39, 40, 41, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable sneexy/floorp
    sudo dnf install floorp

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/four-cool-new-projects-to-try-in-copr-for-october-2024/

作者：[Jiri Kyjovsky][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/nikromen/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/copr-magazine-816x345.jpg
[2]: https://copr.fedorainfracloud.org/
[3]: https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo
[4]: https://docs.pagure.org/copr.copr/user_documentation.html#is-it-safe-to-use-copr
[5]: https://docs.pagure.org/copr.copr/user_documentation.html
[6]: https://hyprland.org/
[7]: https://fedoramagazine.org/wp-content/uploads/2024/10/hyprland-1024x640.png
[8]: https://copr.fedorainfracloud.org/coprs/solopasha/hyprland/
[9]: https://github.com/hectorm/hblock
[10]: https://copr.fedorainfracloud.org/coprs/pesader/hblock
[11]: https://github.com/ungoogled-software/ungoogled-chromium
[12]: https://fedoramagazine.org/wp-content/uploads/2024/10/ungoogled-chromium.png
[13]: https://copr.fedorainfracloud.org/coprs/wojnilowicz/ungoogled-chromium
[14]: https://floorp.app/en
[15]: https://fedoramagazine.org/wp-content/uploads/2024/10/floorp.png
[16]: https://copr.fedorainfracloud.org/coprs/sneexy/floorp
