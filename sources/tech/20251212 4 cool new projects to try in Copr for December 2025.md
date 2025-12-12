[#]: subject: "4 cool new projects to try in Copr for December 2025"
[#]: via: "https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-december-2025/"
[#]: author: "Jiri Kyjovsky https://fedoramagazine.org/author/nikromen/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 cool new projects to try in Copr for December 2025
======

![4 package to try from the Copr repos][1]

This [article series][2] takes a closer look at interesting projects that recently landed in Copr.

[Copr][3] is a build-system for anyone in the Fedora community. It hosts thousands of projects with a wide variety of purposes, targeting diverse groups of users. Some of them should never be installed by anyone, some are already transitioning into the official Fedora repositories, and others fall somewhere in between. Copr allows you to install third-party software not found in the standard Fedora repositories, try nightly versions of your dependencies, use patched builds of your favourite tools to support some non-standard use-cases, and experiment freely.

If you don’t know [how to enable a repository][4] or if you are concerned about whether [is it safe to use Copr][5], please consult the [project documentation][6].

### Vicinae

[Vicinae][7] is a fast application launcher written in C++/QT. Inspired by tool Raycast, it provides instant app and file search and clipboard history. It also includes built-in utilities such as a calculator and web search, along with support for extensions written in TypeScript. It is designed to be highly responsive and native for Wayland environment. Therefore, if you like keeping your hands on the keyboard or want a customizable, extensible launcher for your desktop, Vicinae may be worth trying.

![][8]

#### Installation instructions

The [repo][9] currently provides _vicinae_ for Fedora 42, 43, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable scottames/vicinae
    sudo dnf install vicinae

```

### UZDoom

[UZDoom][10] is a modern DOOM source port that builds upon classic GZDoom engine, offering hardware-accelerated rendering, an updated scripting system, improved mod support, and high-quality audio playback. At the same time, it maintains compatibility with classic WAD files while making the experience smooth on current systems.

Whether you are playing the original episodes or diving into extensive mod packs, UZDoom offers a convenient way to enjoy them.

#### Installation instructions

The [repo][11] currently provides _uzdoom_ for Fedora 42, 43, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable nalika/uzdoom
    sudo dnf install uzdoom

```

### Plasma Panel Colorizer

[Plasma Panel Colorizer][12] is a widget for KDE Plasma that allows you to customize the panel’s appearance. In addition, it offers options for background tinting, blur, custom opacity levels, shadows, floating panels, or themes that differ from the stock Plasma look. It also includes full blur support and is updated for Plasma 6, making it easy to adjust your panel exactly the way you want.

![][13]

#### Installation instructions

The [repo][14] currently provides _plasma-panel-colorizer_ for Fedora 42, 43, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable peridot-augustus/plasma-panel-colorizer
    sudo dnf install plasma-panel-colorizer

```

### sfizz-ui

[Sfizz-ui][15] is the graphical interface for the _sfizz_ sampler engine, which is an open-source player for SFZ instrument libraries. The UI provides an accessible way to load SFZ instruments, adjust parameters, and integrate the sampler into your workflow. It also includes plugin support such as LV2 and VST3, making it suitable for music creation in a Linux DAW environment.

For musicians, sound designers, or anyone using SFZ sample libraries, sfizz-ui offers a polished interface.

#### Installation instructions

The [repo][16] currently provides _sfizz-ui_ for Fedora 41, 42, and 43. To install it, use these commands:

```

    sudo dnf copr enable lexridge/sfizz-ui
    sudo dnf install sfizz-ui

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-december-2025/

作者：[Jiri Kyjovsky][a]
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
[7]: https://github.com/vicinaehq/vicinae
[8]: https://fedoramagazine.org/wp-content/uploads/2025/12/image.png
[9]: https://copr.fedorainfracloud.org/coprs/scottames/vicinae/
[10]: https://github.com/UZDoom/UZDoom
[11]: https://copr.fedorainfracloud.org/coprs/nalika/uzdoom/
[12]: https://github.com/luisbocanegra/plasma-panel-colorizer
[13]: https://fedoramagazine.org/wp-content/uploads/2025/12/image-1-969x1024.png
[14]: https://copr.fedorainfracloud.org/coprs/peridot-augustus/plasma-panel-colorizer
[15]: https://github.com/sfztools/sfizz-ui
[16]: https://copr.fedorainfracloud.org/coprs/lexridge/sfizz-ui/
