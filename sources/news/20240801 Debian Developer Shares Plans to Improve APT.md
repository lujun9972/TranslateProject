[#]: subject: "Debian Developer Shares Plans to Improve APT"
[#]: via: "https://news.itsfoss.com/debian-apt/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Debian Developer Shares Plans to Improve APT
======
Some under-the-hood work that should make a good impact!
[![][1]][2]

[APT][3], short for Advanced Package Tool, is one of the most prevalent choices among all the different package managers, found mainly on [Debian][4] and other Debian-based distributions such as Ubuntu.

Since its introduction way back in 1998, APT has gotten better over the years, with constant patches being made to keep it relevant in the ever-evolving space of Linux-based distros.

A recent update saw the introduction of [APT 2.9.3][5], which shipped with an experimental dependency solver called **Solver3** , that's aiming to become the default solver in the near future. Thanks to [The New Stack][6], we now have a better look at what that might be like. 😃

Not to forget, we also got the new color, in case you missed it:

![][7]

### APT To Get A Boost: What to Expect?

![Just a stand-in image of APT][8]

Speaking during [DebConf 24][9], Debian Developer, [Julian Andres Klode][10] shared insights into how he had been working on the Solver3 project since 2010 during his spare time.

The [Solver3][11] is a dependency solving algorithm for APT, that starts with an empty set of packages, progressively adding any manually installed packages, then automatically installing any missing ones to resolve dependencies.

Compared to that, Julian points out that **the current solver takes 45% of the total build time** for rebuilding the dependency tree on Intel systems.

When measured at scale, the numbers add up, and there's plenty of time that's wasted in carrying out such a menial task. The Solver3, according to him, just takes 15% of the build time, and results in a 40% improvement in build times compared to the existing solver in his testing.

**Before he could arrive at this solution** , he had to go through three different approaches for handling dependencies. First, he tried to procure an external solver from FreeBSD called “[picosat][12]”, it didn't pan out owing to the many limitations of working with an external library.

Then, he tried describing the dependency tree as a “[pseudo-Boolean][13]” optimization problem, with three methods being employed, all of which entailed issues such as package sizes, weird optimization, and dependence on [global optimization][14].

And, finally, he tried a modular graph solver method, which was not used in the project, but did help with the outcome.

Of course, Julian does mention that **there's plenty of work to be done before this can be made the default** , he added that:

> This is going to be quite powerful, but we want to restrict it a bit to not pick solutions that actually don’t make sense. Packages for multiple architectures should be limited to only those architectures being used.

> Manually packages should only be removed upon explicit request, and a replacement package should designated when appropriate. Obsolete packages should also be considered only as a last choice.

He also feels that there's a need for more benchmarking to be done, comparing Solver3 with the existing solver once it is in production, and that he would also like to bring Solver3 closer to [MiniSat][15].

#### Want To Check It Out?

Currently, a beta release is planned as an opt-in for the upcoming Debian 13 “[Trixie][16]” release, which is said to arrive around February 2025.

As for when Solver3 would be made the default solver, if everything goes as planned with the beta release, then the follow-up Debian 14 “[Forky][17]” release is the prime candidate for it.

For an early look at Solver3's code, you can head to apt-pkg's main branch on Debian's [GitLab][18] repo, where you can search for “ _solver3_ ”.

[apt-pkg (GitLab)][18]

_💬 Are you looking forward to more efficient package management on APT? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/debian-apt/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://wiki.debian.org/Apt
[4]: https://www.debian.org/
[5]: https://tracker.debian.org/news/1529821/accepted-apt-293-source-into-unstable/
[6]: https://thenewstack.io/debian-retools-apt-for-superior-dependency-management/
[7]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[8]: https://news.itsfoss.com/content/images/2024/07/Apt_2.7.14.png
[9]: https://wiki.debian.org/DebConf/24
[10]: https://github.com/julian-klode
[11]: https://blog.jak-linux.org/2024/05/14/solver3/
[12]: https://cgit.freebsd.org/ports/tree/math/picosat
[13]: https://en.wikipedia.org/wiki/Pseudo-Boolean_function
[14]: https://en.wikipedia.org/wiki/Global_optimization
[15]: http://minisat.se/
[16]: https://www.debian.org/releases/trixie/
[17]: https://wiki.debian.org/DebianForky
[18]: https://salsa.debian.org/apt-team/apt/-/tree/main/apt-pkg
