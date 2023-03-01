[#]: subject: "4 cool new projects to try in Copr for March 2023"
[#]: via: "https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-march-2023/"
[#]: author: "Jakub Kadlčík https://fedoramagazine.org/author/frostyx/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 cool new projects to try in Copr for March 2023
======

![][1]

This article introduces four new projects available in Copr, with installation instructions.

[Copr][2] is a build-system for anyone in the Fedora community. It hosts thousands of projects for various purposes and audiences. Some of them should never be installed by anyone, some are already being transitioned to the official Fedora Linux repositories, and the rest are somewhere in between. Copr gives you the opportunity to install 3rd party software that is not available in Fedora Linux repositories, try nightly versions of your dependencies, use patched builds of your favorite tools to support some non-standard use-cases, and just experiment freely.

If you don’t know [how to enable a repository][3] or if you are concerned about whether [it is safe to use Copr][4], please consult the [project documentation][5].

This article takes a closer look at interesting projects that recently landed in Copr.

## [][6] Sticky

Do you always forget your passwords, write them on sticky notes and post them all around your monitor? Well, please don’t use [Sticky][7] for that. But it is a great note-taking application with support for checklists, text formatting, spell-checking, backups, and so on. It also supports adjusting note visibility and organizing notes into groups.

![][8]

### [][9] Installation instructions

The [repo][10] currently provides Sticky for Fedora 36, 37, 38, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable a-random-linux-lover/sticky
    sudo dnf install sticky

```

## [][11] Webapp-manager

Generations of programmers spent over three decades creating, improving, and re-inventing [window managers][12] for us to disregard all of that, and live inside of a web browser with dozens of tabs. [Webapp-manager][13] allows you to run websites as if they were applications, and return to the previous paradigm.

![][14]

### [][15] Installation instructions

The [repo][16] currently provides webapp-manager for Fedora 36, 37, 38, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable kylegospo/webapp-manager
    sudo dnf install webapp-manager

```

## [][17] Umoria

[Umoria][18] (The Dungeons of Moria) is a single-player dungeon crawl game inspired by J. R. R. Tolkien’s novel The Lord of the Rings. It is considered to be the first [roguelike][19] game ever created. A player begins their epic adventure by acquiring weapons and supplies in the town level and then descends to the dungeons to face the evil that lurks beneath.

![][20]

### [][21] Installation instructions

The [repo][22] currently provides Umoria for Fedora 36, 37, 38, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable whitehara/umoria
    sudo dnf install umoria

```

## [][23] PyCharm

JetBrains [PyCharm][24] is a popular IDE for the Python programming language. It provides intelligent code completion, on-the-fly error checking, quick fixes, and much more. The [phracek/PyCharm][25] repository is a great example of a well-maintained project that lives in Copr and has for a long time. Created eight years ago for Fedora 20, it provided support for every subsequent Fedora release. It is now a part of the [Third-Party Repositories][26] that can be opted into during the Fedora installation.

![][27]

### [][28] Installation instructions

The [repo][25] currently provides PyCharm for Fedora 36, 37, 38, Fedora Rawhide, EPEL 7, 8, and 9. To install it, use these commands:

```

    sudo dnf copr enable phracek/PyCharm
    sudo dnf install pycharm-community

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-march-2023/

作者：[Jakub Kadlčík][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/frostyx/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/copr-magazine-816x345.jpg
[2]: https://copr.fedorainfracloud.org/
[3]: https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo
[4]: https://docs.pagure.org/copr.copr/user_documentation.html#is-it-safe-to-use-copr
[5]: https://docs.pagure.org/copr.copr/user_documentation.html
[6]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#sticky
[7]: https://github.com/linuxmint/sticky
[8]: https://fedoramagazine.org/wp-content/uploads/2023/02/sticky.png
[9]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#installation-instructions
[10]: https://copr.fedorainfracloud.org/coprs/a-random-linux-lover/sticky/
[11]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#webapp-manager
[12]: https://en.wikipedia.org/wiki/Window_manager
[13]: https://github.com/KyleGospo/webapp-manager
[14]: https://fedoramagazine.org/wp-content/uploads/2023/02/webapp-manager.png
[15]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#installation-instructions-1
[16]: https://copr.fedorainfracloud.org/coprs/kylegospo/webapp-manager/
[17]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#umoria
[18]: https://umoria.org/
[19]: https://en.wikipedia.org/wiki/Roguelike
[20]: https://fedoramagazine.org/wp-content/uploads/2023/02/umoria.png
[21]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#installation-instructions-2
[22]: https://copr.fedorainfracloud.org/coprs/whitehara/umoria/
[23]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#pycharm
[24]: https://www.jetbrains.com/pycharm/
[25]: https://copr.fedorainfracloud.org/coprs/phracek/PyCharm/
[26]: https://docs.fedoraproject.org/en-US/workstation-working-group/third-party-repos/
[27]: https://fedoramagazine.org/wp-content/uploads/2023/02/pycharm.png
[28]: https://github.com/frostyx/fedora-magazine/blob/main/2023-march.md#installation-instructions-3
