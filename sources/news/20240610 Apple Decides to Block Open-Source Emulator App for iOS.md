[#]: subject: "Apple Decides to Block Open-Source Emulator App for iOS"
[#]: via: "https://news.itsfoss.com/apple-blocks-utm-se/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Apple Decides to Block Open-Source Emulator App for iOS
======
Apple being Apple.
[![][1]][2]

[Apple][3] has a long-running history of guarding their [walled garden][4] by not allowing much interoperability with other standards that are the current norm in the industry, while also going on to reinvent, giving features a novel-sounding name.

Of course, the European Union's [Digital Markets Act][5] (DMA) has been successful in making Apple do things that they wouldn't ever do, if it weren't the law to do so.

However, Apple still does its best to gate keep developers who aren't their own, and one such recent incident caught my attention that involves their typical “ _my way or the highway_ ” approach to things.

### Apple Loves to Gatekeep: When Will They Stop?

Posted on [X][6] by the UTM project, they revealed that **Apple rejected their application for publishing the UTM SE app after a two-month-long review process** , citing that “Rule 4.7” of their [App Review Guidelines][7] didn't apply to it.

> [pic.twitter.com/SNux03qjJh][8]
>
> — UTM (@UTMapp) [June 9, 2024][9]

That rule is meant to allow game emulators, mini apps, chatbots, plugins, etc. to be published on the [App Store][10].

The developers of UTM mention that Apple even went the extra step, and disallowed the publishing of UTM SE on third-party marketplaces. They added that:

> The App Store Review Board determined that “PC is not a console” regardless of the fact that there are retro Windows/DOS games for the PC that UTM SE can be useful in running.

Well, that's not surprising because they [might soon kill the third-party rival app stores][11] anyway 😑

💡

If you are not familiar, UTM is a [QEMU][12]-powered open-source emulator/virtual machine host for iOS and macOS, a popular tool to run alternative operating systems ( _ _such as ones based on Linux, or even Windows__ ) on Apple devices.

It can run on non-jailbroken devices via sideloading on iOS 11,2, and 13. For iOS 14 or later, jailbreak is a necessary step. The video below shows it in action. 👇

UTM SE was supposed to be **a non-JIT version of UTM** , which would've allowed users to easily run other operating systems on their iOS devices, albeit without the performance advantage that [JIT][13] offers.

However, as you might have read in the tweet above, **the developers will not be pushing for it to be published on the app store** anymore as they think it is a “subpar experience and isn't worth fighting for”. They would go ahead if Apple were to change their decision.

In UTM SE's case, Apple didn't seem to clarify what actually went wrong with its publishing on the App Store, and left the developers asking questions.

A similar case happened with Dolphini OS where the developers had to learn the [hard way][14] that **Apple still doesn't allow non-browser apps to make use of JIT**.

If you ask me, Apple could really take some pointers from Google here, who have allowed that on Android for quite some time now. When it comes to publishing apps on the [Play Store][15], their support is generally more concise, too.

If you are interested in the UTM project, you can check out its [official website][16], or its [GitHub][17] repo for learning more.

[UTM][16]

**Suggested Read** 📖

![][18]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/apple-blocks-utm-se/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.apple.com/
[4]: https://en.wikipedia.org/wiki/Closed_platform
[5]: https://digital-markets-act.ec.europa.eu/index_en
[6]: https://x.com/UTMapp/status/1799647652134654045
[7]: https://developer.apple.com/app-store/review/guidelines/
[8]: https://t.co/SNux03qjJh
[9]: https://twitter.com/UTMapp/status/1799647652134654045?ref_src=twsrc%5Etfw
[10]: https://www.apple.com/app-store/
[11]: https://www.bloomberg.com/news/articles/2024-05-20/altstore-goes-to-absurd-lengths-for-third-party-iphone-apps
[12]: https://www.qemu.org/
[13]: https://en.wikipedia.org/wiki/Just-in-time_compilation
[14]: https://oatmealdome.me/blog/why-dolphin-isnt-coming-to-the-app-store/
[15]: https://play.google.com/store/
[16]: https://getutm.app/
[17]: https://github.com/utmapp/UTM
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
