[#]: subject: "4 cool new projects to try in Copr for March 2025"
[#]: via: "https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-march-2025/"
[#]: author: "nikromen https://fedoramagazine.org/author/nikromen/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 cool new projects to try in Copr for March 2025
======

![4 package to try from the Copr repos][1]

This [article series][2] takes a closer look at interesting projects that recently landed in Copr.

[Copr][3] is a build-system for anyone in the Fedora community. It hosts thousands of projects with a wide variety of purposes, targeting diverse groups of users. Some of them should never be installed by anyone, some are already transitioning into the official Fedora repositories, and others fall somewhere in between. Copr allows you to install third-party software not found in the standard Fedora repositories, try nightly versions of your dependencies, use patched builds of your favourite tools to support some non-standard use-cases, and experiment freely.

If you don’t know [how to enable a repository][4] or if you are concerned about whether [is it safe to use Copr][5], please consult the [project documentation][6].

### Spotify Qt

**Spotify-qt** is an unofficial lightweight Spotify client developed in Qt, intended as a faster, smaller alternative to the official Spotify application. Actual playback requires another Spotify client running in the background (for example [librespot][7]), which can be easily configured within the app. Note that controlling playback requires Spotify Premium.

**Key features:**

  * Low resource consumption
  * Highly customizable
  * Multiplatform support



For more detailed information, see the [FAQ][8]. For instance, you can find there a step-by-step guide on configuring your own Spotify application in the Spotify Dashboard.

![][9]

#### Installation instructions

The [repo][10] currently provides _spotify-qt_ for Fedora 40, 41, 42, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable kraxarn/spotify-qt
    sudo dnf install spotify-qt

```

### Ghostty

**Ghostty** is a terminal emulator that wants to balance speed, rich functionality, and provide a native and friendly user interface. While many terminal emulators choose between performance and features, ghostty aims to excel at both while providing a native look and feel.

**Key features:**

  * Supports multiple windows, tabs, and split views out of the box
  * GPU acceleration
  * Platform-native UI (on macOS and Linux)



![][11]

#### Installation instructions

The [repo][12] currently provides _ghostty_ and _ghostty-git_ (for those who want the latest build from the main branch) for Fedora 40, 41, 42, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable pgdev/ghostty
    sudo dnf install ghostty  # (or ghostty-git)

```

### Zen Browser

**Zen Browser** centres its design around vertical tabs. This is a concept shared by browsers like Vivaldi, Brave, and especially Arc Browser. Zen Browser provides features like Split View, Zen Sidebar (a detachable sidebar for quick side-by-side browsing), and Zen Glance (for previewing a site without leaving your current page). You can also organize your tabs with “workspaces,” allowing you to separate personal-related and work-related contexts.

**Key features:**

  * Strong privacy focus – blocks trackers, ads, and other unwanted content
  * Modern interface with focus on vertical tab management
  * Split View and detachable sidebar
  * Workspaces to keep tab groups organized



![][13]

#### Installation instructions

The [repo][14] currently provides _zen-browser_ for Fedora 40, 41, 42, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable sneexy/zen-browser
    sudo dnf install zen-browser

```

### LACT

**LACT** is a powerful tool for advanced control and monitoring of AMD, Nvidia, and Intel GPUs on Linux. It allows you to view detailed information about your GPU, monitor performance and thermal data, configure power limits, customize fan curves, and even overclock GPU and VRAM clocks if supported by your driver. LACT does not rely on X11 extensions, so it should work in any desktop session environment.

**Key features:**

  * GPU information display and monitoring
  * Power limit configuration, fan curve customization
  * Overclocking



To check whether your hardware is supported and how to configure LACT properly, please take a look at [the documentation][15].

![][16]

#### Installation instructions

The [repo][17] currently provides _lact_ for standard installation, _lact-headless_ for a setup without GUI, and _lact-libadwaita_ for GUI built with Libadwaita, all for Fedora 40, 41, 42, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable ilyaz/LACT
    sudo dnf install lact  # (or with -headless or -libadwaita)

```

and then enable the service

```

    sudo systemctl enable --now lactd

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-march-2025/

作者：[nikromen][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/nikromen/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/copr-magazine-816x345.jpg
[2]: https://fedoramagazine.org/series/copr/
[3]: https://copr.fedorainfracloud.org/
[4]: https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo
[5]: https://docs.pagure.org/copr.copr/user_documentation.html#is-it-safe-to-use-copr
[6]: https://docs.pagure.org/copr.copr/user_documentation.html
[7]: https://github.com/librespot-org/librespot
[8]: https://github.com/kraxarn/spotify-qt/wiki/Frequently-Asked-Questions
[9]: https://fedoramagazine.org/wp-content/uploads/2025/03/image-1024x590.png
[10]: https://copr.fedorainfracloud.org/coprs/kraxarn/spotify-qt
[11]: https://fedoramagazine.org/wp-content/uploads/2025/03/pic.png
[12]: https://copr.fedorainfracloud.org/coprs/pgdev/ghostty
[13]: https://fedoramagazine.org/wp-content/uploads/2025/03/pic2-1024x713.png
[14]: https://copr.fedorainfracloud.org/coprs/sneexy/zen-browser/
[15]: https://github.com/ilya-zlobintsev/LACT?tab=readme-ov-file#hardware-support
[16]: https://fedoramagazine.org/wp-content/uploads/2025/03/image-1-767x1024.png
[17]: https://copr.fedorainfracloud.org/coprs/ilyaz/LACT/
