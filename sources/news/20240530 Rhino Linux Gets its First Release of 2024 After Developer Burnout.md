[#]: subject: "Rhino Linux Gets its First Release of 2024 After Developer Burnout"
[#]: via: "https://news.itsfoss.com/rhino-linux-2024-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Rhino Linux Gets its First Release of 2024 After Developer Burnout
======
Rhino Linux gets its first release of the year, with much-needed
refinements to the package manager.
[![][1]][2]

Among the vast array of Ubuntu-based distributions, Rhino Linux is arguably one of the [best rolling release Linux distros][3] around, which had been receiving regular updates until last year, when the [2023.4 release][4] was introduced.

Come February 2024, the developers of Rhino Linux put out [a post][5] on their website outlining the project's situation, which involved maintainer burnout, internal squabbles, and the need for a proper code of conduct as well as better maintainer documentation.

As a result, the development of Rhino Linux had to be paused to give everyone involved a much-needed break and to give them a bit of time to strategize how to move forward.

Now, at the end of May 2024, the team has revealed that they have begun talks on how to structure Rhino Linux going forward and have already put together a Rhino Linux constitution with a focus on community participation.

Alongside that, they also introduced the new **Rhino Linux 2024.01** release. So, let's get into it right away.

### Rhino Linux 2024.01: What to Expect?

![][6]

Being offered in **three different kernels for different platforms** , Rhino Linux 2024.01 is powered by _Linux kernel 6.9.1-generic_ for desktops, _Linux kernel 6.9.0-okpine_ for Pine64 devices, and _Linux kernel 6.8.0-raspi_ for the Raspberry Pi series of devices.

Interestingly, this release mostly focuses on improvements related to [Pacstall][7], the default package manager on Rhino Linux.

Included in Rhino Linux 2024.01 are the improvements from the Pacstall [5.0.0][8] and [5.1.0][9] releases.

You get things like easy porting of packages from AUR into Pacstall, execution of _pacscript_ functions inside isolated environments with bwrap, better handling of multiple repositories, and an updated [Packscript 101][10] wiki.

However, **this release does have a few issues** that users should be aware of. When you are running the live environment, the desktop icon for launching Calamares installer doesn't show up; you can launch it from the App Grid instead.

Moreover, there is a sizing issue with the global menu plugin in the panel due to some updates made to Xfce which the Rhino Linux team has temporarily remedied.

Other than that, there are the usual package updates and miscellaneous fixes; you can find the announcement in the official [blog][11].

### Get Rhino Linux 2024.01

You can grab the latest Rhino Linux release from the [official website][12]. If you are interested in the source code, then you can visit its [GitHub][13] repo.

[Rhino Linux 2024.01][12]

**For existing users** , they can run the following command to upgrade to this release:

```

    rpk update -y

```

Just remember to back up your data before initiating the upgrade process.

**Suggested Read** 📖

![][14]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/rhino-linux-2024-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/best-rolling-release-distros/
[4]: https://news.itsfoss.com/rhino-linux-2023-4-release/
[5]: https://rhinolinux.org/news-11.html
[6]: https://news.itsfoss.com/content/images/2024/05/Rhino_Linux_2024.01.png
[7]: https://pacstall.dev/
[8]: https://github.com/pacstall/pacstall/releases/tag/5.0.0
[9]: https://github.com/pacstall/pacstall/releases/tag/5.1.0
[10]: https://github.com/pacstall/pacstall/wiki/Pacscript-101
[11]: https://rhinolinux.org/news-13.html
[12]: https://rhinolinux.org/download.html
[13]: https://github.com/rhino-linux
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
