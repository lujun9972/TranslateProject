[#]: subject: "Snapchat Opens Valdi Framework to Developers After 8 Years of Internal Use"
[#]: via: "https://itsfoss.com/news/snapchat-open-sources-valdi/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Snapchat Opens Valdi Framework to Developers After 8 Years of Internal Use
======

[Snap Inc.][1], the company behind Snapchat, has open-sourced Valdi, **a cross-platform mobile UI framework**. The social media company typically keeps its technology in-house, but this marks a surprising move into open source territory.

While there was no dedicated announcement for this on their news portal, [The New Stack][2] were the first ones to report this; I am assuming they received a press release for this.

Anyhow, let's dive into this interesting development.

### Valdi is Now Open Source

![][3]

Valdi is now available on GitHub under the **MIT license**. The framework **has powered Snapchat's production features for eight years** , and, with the accompanying license in place, developers can use, modify, and distribute the code freely, and there are no restrictions on commercial use.

Valdi compiles TypeScript code directly into native views for Android, iOS, and macOS. It does not use web views or JavaScript bridges. The framework **claims 2x faster time-to-first-render and uses 1/4 the memory compared to competitors**. These benchmarks were shared during Valdi's initial beta phase, when Snapchat first announced Valdi in August 2025 on [Hacker News][4].

Back then, the company sought beta testers and required NDAs for private repository access. The initial beta lasted three months before the public release, and Snapchat seems to have used this window to refine documentation and developer tooling.

The current repository includes **instant hot reload** , **full VSCode debugging support** , and **automatic view recycling**. It also features **a C++ layout engine** and **FlexBox layout system support** , and developers can embed Valdi components in existing native apps.

You can visit Valdi's [GitHub][5] repository for access to the source code and [the documentation][6]. There is also a [Discord server][7] for community support and developer discussions.

[Valdi][5]

#### Not Everyone is Convinced

Developer reception has been mixed. Reddit netizens are questioning Valdi's advantages over [React Native][8]. One of them, [SamsungProgrammer][9], asked:

> Why would people choose this over React Native?

To which another redditor, _idkhowtocallmyacc_ , responded with skepticism. They pointed out that **React Native's new architecture has also eliminated JavaScript bridges** , potentially negating Valdi's main selling point.

And that does make sense, to be honest. Ending that comment thread, a redditor called _balder1993_ , responded by saying that:

> Some people might have a thing for rewriting their whole app a few years later when the bugs start getting in the way.

Only time will tell if Valdi can escape Snapchat's shadow and find a broader developer audience.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/snapchat-open-sources-valdi/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.snap.com/
[2]: https://thenewstack.io/snapchat-open-sources-cross-platform-ui-framework/
[3]: https://itsfoss.com/content/images/2025/11/snapchat-valdi-github-repo.png
[4]: https://news.ycombinator.com/item?id=44867681
[5]: https://github.com/Snapchat/Valdi
[6]: https://github.com/Snapchat/Valdi/blob/main/docs/README.md
[7]: https://discord.com/invite/uJyNEeYX2U
[8]: https://reactnative.dev/
[9]: https://www.reddit.com/r/androiddev/comments/1orhx0s/comment/nnti5ny/
