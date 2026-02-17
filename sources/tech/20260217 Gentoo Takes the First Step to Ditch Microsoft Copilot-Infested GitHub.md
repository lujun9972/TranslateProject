[#]: subject: "Gentoo Takes the First Step to Ditch Microsoft Copilot-Infested GitHub"
[#]: via: "https://itsfoss.com/news/gentoo-github-switch-begins/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Gentoo Takes the First Step to Ditch Microsoft Copilot-Infested GitHub
======

[![Warp Terminal][1]][2]

Contributors to Gentoo Linux can now submit pull requests through [Codeberg][3] instead of [GitHub][4]. The repository mirror is already live ( _only the_ [_ebuild repo_][5]), with more of the project's Git infrastructure planned to follow along [in the coming months][6].

The move follows through on plans outlined in Gentoo's 2025 end-of-year review published [earlier this year][7], where the team had made it clear that they would be migrating repository mirrors away from GitHub.

They provided the following rationale for this change:

> Mostly because of the continuous attempts to force [Copilot][8] usage for our repositories, Gentoo currently considers and plans the migration of our repository mirrors and pull request contributions to Codeberg.

Developers can now submit pull requests through Codeberg using the [AGit workflow][9], which, the project says, **eliminates the need to maintain personal forks of the repository**. Gentoo has also published [detailed instructions][10] on their wiki for contributors making the switch.

### Why Does it Matter?

[Version control systems][11] track changes to code over time, allowing multiple developers to work on the same project without conflicts. These systems maintain a complete history of modifications and enable teams to roll back problematic updates when needed.

[Git][12] has become the dominant version control tool in software development, and many companies and organizations provide Git hosting services with features like pull requests, issue tracking, and continuous integration on top of the core version control functionality.

[GitHub][13] sits at the center of this ecosystem, with the platform hosting millions of repositories and serving as the default choice for many developers. But Microsoft's [acquisition of GitHub][14] in 2018 for $7.5 billion is a move that remains controversial.

Gentoo maintains mirrors of its repositories on GitHub **to simplify external contributions**. These mirrors duplicate the contents of Gentoo's primary Git infrastructure, which the project [hosts independently][15].

[Codeberg][16], on the other hand, promises no user tracking or third-party cookies. It runs on [Forgejo][17] and is maintained by a German nonprofit based in Berlin. If you notice, the organizational structure contrasts with GitHub's Big Tech ownership.

Ultimately, this provides **an alternative for contributors who prefer not to use GitHub** while the project continues its gradual transition away from the platform.

* * *

**Suggested Read 📖:** [_Top GitHub Alternatives to Host Your Open Source Projects_][18]

![][19]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/gentoo-github-switch-begins/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://codeberg.org/gentoo/gentoo
[4]: https://github.com/gentoo/gentoo
[5]: https://wiki.gentoo.org/wiki/Ebuild_repository
[6]: https://www.gentoo.org/news/2026/02/16/codeberg.html
[7]: https://www.gentoo.org/news/2026/01/05/new-year.html
[8]: https://github.com/features/copilot
[9]: https://forgejo.org/docs/latest/user/agit-support/
[10]: https://wiki.gentoo.org/wiki/Project:Codeberg/Pull_requests
[11]: https://about.gitlab.com/topics/version-control/
[12]: https://git-scm.com/
[13]: https://github.com/
[14]: https://news.microsoft.com/announcement/microsoft-acquires-github/
[15]: https://gitweb.gentoo.org/repo/gentoo.git
[16]: https://codeberg.org/
[17]: https://forgejo.org/
[18]: https://itsfoss.com/github-alternatives/
[19]: https://itsfoss.com/content/images/icon/android-chrome-512x512-283.png
