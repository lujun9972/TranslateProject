[#]: subject: "Good News for Mobile App Developers: Skip Is Now Open Source"
[#]: via: "https://itsfoss.com/news/skip-goes-open-source/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Good News for Mobile App Developers: Skip Is Now Open Source
======

[![Warp Terminal][1]][2]

If you are into mobile app development, then you most likely know of [Swift][3], Apple's programming language for building iOS, macOS, and other platform apps. While it flourishes in the [Apple][4] ecosystem, its ventures into the [Android][5] landscape are nothing but tedious.

This is where cross-platform frameworks come in, but sadly, many of these compromise on performance or rely on non-native UI rendering that can feel out of place on both platforms.

[Skip][6] is one such tool that takes a different approach. It converts Swift code to run natively on both iOS and Android, delivering native apps instead of wrapped web apps or mangled interfaces.

And as it turns out, the tool has been [open-sourced][7].

### Skip Embraces Open Source

![][8]

Ditching its earlier subscription and licensing model, the Skip team has fully opened up the tool, as the [Skip 1.7][9] release removes all paywalls and makes the source code publicly available.

The open-sourced components include " _ **skipstone**_ ," the core engine that powers Skip, which is responsible for project creation, Xcode plugin functions, converting iOS projects to Android, bundling resources, creating platform bridges, packaging apps, and exporting projects.

Existing paid subscribers who were on the _Small Business_ or _Professional_ plan [will be automatically switched][10] to either an _Individual_ or _Supporter_ sponsorship tier depending on their earlier monetary contributions.

Skip says that **they have been operating without venture capital since the start** , and while it gave them control, it created funding challenges. They **now completely rely on community funding** , asking for support through [GitHub Sponsors][11] for individuals and corporate packages for businesses.

Concluding the announcement, Skip stated that:

> Opening Skip to the community marks the next step in its evolution. Software is never finished — especially a tool that supports modern Swift and Kotlin, SwiftPM and Gradle, Xcode and Android Studio, iOS and Android, and the ongoing growth of SwiftUI and Jetpack Compose.
>
> It’s a demanding pursuit, and we’re committed to it. But sustaining and expanding this work depends on the support of developers who believe in Skip’s mission.

### The Sauce

If you are a developer or just a curious Penguin, then you will find the source code for Skip on its [GitHub project page][12], with listings for the engine, the website, and various tools.

[Skip (engine source code)][13]

Other than that, the existing [skip.tools][6] website is being moved to the [skip.dev][14] domain, which acts as the new home for hosting all of Skip's documentation, case studies, and blogs.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/skip-goes-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.swift.org/
[4]: https://www.apple.com/
[5]: https://www.android.com/
[6]: https://skip.tools/
[7]: https://skip.dev/blog/skip-is-free/
[8]: https://itsfoss.com/content/images/2026/01/skip-website-hero-pic.jpeg
[9]: https://github.com/skiptools/skip/releases/tag/1.7.0
[10]: https://skip.dev/sponsor/
[11]: https://github.com/sponsors/skiptools
[12]: https://github.com/skiptools
[13]: https://github.com/skiptools/skip
[14]: https://skip.dev/
