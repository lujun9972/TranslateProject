[#]: subject: "4 cool new projects to try in Copr for March 2024"
[#]: via: "https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-march-2024/"
[#]: author: "Miroslav Suchý https://fedoramagazine.org/author/msuchy/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

4 cool new projects to try in Copr for March 2024
======

![4 package to try from the Copr repos][1]

[Copr][2] is a build-system for anyone in the Fedora community. It hosts thousands of projects for various purposes and audiences. Some of them should never be installed by anyone, some are already being transitioned to the official Fedora Linux repositories, and the rest are somewhere in between. Copr gives you the opportunity to install 3rd party software that is not available in Fedora Linux repositories, try nightly versions of your dependencies, use patched builds of your favorite tools to support some non-standard use-cases, and just experiment freely.

This article takes a closer look at interesting projects that recently landed in Copr.

If you don’t know [how to enable a repository][3] or if you are concerned about whether [is it safe to use Copr][4], please consult the [project documentation][5].

### PyInstaller

Do you need to ship your Python script to a customer? And for a reason, you cannot use either RPM or Flatpak? Try PyInstaller! You just use the following command:
```

```

pyinstaller yourscript.py
```

```

and pyinstaller will extract your dependencies and bundle everything together. It will create a _yourscript_ binary (ELF) and the _yourscript/_ directory with all these bundles. I tried it with one of my small scripts, and it created a 566 MB big directory and 20MB binary. See [PyInstaller documentation][6] for how to use it.

#### Installation instructions

The [repo][7] currently provides PyInstaller for EPEL 9, Fedora 38, 39, 40, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable slaanesh/PyInstaller
    sudo dnf -y install python3-pyinstaller

```

### Anime Games Launcher

[Anime Games Launcher][8] is very similar to [Lutris][9], but focuses on Anime Games only. It is a wrapper around Wine and allows you to launch the game. E.g. you can run a very popular game GenShin. You can do the same with Lutris, but it certainly requires more effort. With Anime Games Launcher, it was literally two clicks.

![][10]

#### Installation instructions

The [repo][11] currently provides Launcher for Fedora 39, 40, and Fedora Rawhide. To install it, use these commands:

```

    sudo dnf copr enable retrozinndev/anime-games-launcher
    sudo dnf install anime-games-launcher
    anime-games-launcher

```

### ec2-instance-connect

[AWS EC2 Instance Connect Configuration][12] is a set of configurations and scripts that allows you to connect to a VM instance from the AWS dashboard using [EC2 Instance Connect][13]. For the connections, SSH is used – so this is a configuration for SSH and several supporting tools. This repository is owned by [Major Hayden][14], a [Cloud SIG][15] member. The description of this project is “initial packaging”, so we may find this package in core Fedora one day.

#### Installation instructions

The [repo][16] currently provides packages for RHEL 9, Fedora 39, and Fedora Rawhide. To install it, use this command:

```

    sudo dnf copr enable mhayden/ec2-instance-connect

```

### Gitea

I will quote [Wikipedia][17]:

> “Gitea ([/ɡɪˈtiː/][18]) is a forge software package for hosting software development version control using Git as well as other collaborative features like bug tracking, code review, continuous integration, kanban boards, tickets, and wikis. It supports self-hosting but also provides a free public first-party instance…”

This [Copr project][19] includes packages that allow you to deploy the self-hosted instance.

![][20]

#### Installation instructions

The [repo][19] currently provides packages for Fedora 38, 39, and 40. To install it, use this command:

```

    sudo dnf copr enable felfert/gitea

```

See upstream [installation instructions][21].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/4-cool-new-projects-to-try-in-copr-for-march-2024/

作者：[Miroslav Suchý][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/msuchy/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/copr-magazine-816x345.jpg
[2]: https://copr.fedorainfracloud.org/
[3]: https://docs.pagure.org/copr.copr/how_to_enable_repo.html#how-to-enable-repo
[4]: https://docs.pagure.org/copr.copr/user_documentation.html#is-it-safe-to-use-copr
[5]: https://docs.pagure.org/copr.copr/user_documentation.html
[6]: https://pyinstaller.org/en/stable/
[7]: https://copr.fedorainfracloud.org/coprs/slaanesh/PyInstaller/
[8]: https://github.com/an-anime-team/anime-games-launcher
[9]: https://lutris.net/
[10]: https://fedoramagazine.org/wp-content/uploads/2024/02/Screenshot_20240222_091230-1024x714.png
[11]: https://copr.fedorainfracloud.org/coprs/retrozinndev/anime-games-launcher
[12]: https://github.com/aws/aws-ec2-instance-connect-config
[13]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html
[14]: https://accounts.fedoraproject.org/user/mhayden/
[15]: https://fedoraproject.org/wiki/Cloud_SIG
[16]: https://copr.fedorainfracloud.org/coprs/mhayden/ec2-instance-connect/
[17]: https://en.wikipedia.org/wiki/Gitea
[18]: https://en.wikipedia.org/wiki/Help:IPA/English
[19]: https://copr.fedorainfracloud.org/coprs/felfert/gitea
[20]: https://fedoramagazine.org/wp-content/uploads/2024/02/gitea-1024x521.png
[21]: https://docs.gitea.com/installation/linux-service
