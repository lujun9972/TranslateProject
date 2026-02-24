[#]: subject: "Ladybird Browser Just Ported C++ Code to Rust in 2 Weeks Thanks to AI"
[#]: via: "https://itsfoss.com/news/ladybird-web-browser-rustification/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ladybird Browser Just Ported C++ Code to Rust in 2 Weeks Thanks to AI
======

[![Warp Terminal][1]][2]

We are used to seeing web browsers that are either based on [Chromium][3] or [Firefox][4], and many people are fed up of the [duopoly][5]-like situation here. [Ladybird][6] is a breath of fresh air here, being a truly independent browser with its own engine built from scratch.

While development has been going on in full swing, we are yet to see an official release as of now. The first alpha release for it is set for release sometime in 2026 for Linux and macOS.

Nevertheless, the developers of it have just announced that they are implementing some Rust bits into it.

### What's Happening?

![Placeholder Source: Ladybird][7]

For a while now, the Ladybird team has been on the lookout for a memory-safe language to eventually replace [C++][8]. [Swift][9] was considered at one point, but **poor C++ interoperability and limited platform support** outside Apple's ecosystem ruled it out.

[Rust][10] was actually evaluated and rejected back in 2024. The reasoning was that it didn't play well with C++-style [object-oriented programming][11], which the web platform relies on heavily. But after another year of searching, the lead developer of Ladybird, [Andreas Kling][12], decided it was time to be pragmatic.

The fact that both Firefox and Chromium have already started bringing Rust into their codebases also helped make the case.

### How's it Done?

Andreas started with [LibJS][13], Ladybird's JavaScript engine, since its core parts are fairly isolated from the rest of the codebase and already have strong test coverage. Rather than writing Rust code from scratch, he used [Claude Code][14] and [Codex][15] to do the heavy lifting on the translation.

He made it very clear that **human oversight was involved** , with every decision about what to port, in what order, and how the Rust code should be structured coming from him. Post execution, many review passes were performed, pitting different models against each other to catch mistakes.

Two weeks later, the port was done. About 25,000 lines of Rust, something Andreas says would have eaten up several months of manual work. The results held up well too, passing over 52,000 [test262][16] tests and around 12,000 Ladybird regression tests with no failures and no performance nerfs on any JavaScript benchmarks.

He also goes on to add that:

> Beyond the test suites, I’ve done extensive testing by browsing the web in a lockstep mode where both the C++ and Rust pipelines run simultaneously, verifying that output is identical for every piece of JavaScript that flows through them.

**Rust is not taking over as the project's main focus though**. C++ is still front and center, and the Rust porting work is more of a slow, long-term effort running alongside it. The two will coexist through defined boundaries.

Contributors [interested in helping][17] with the port are also **being asked to coordinate with the core team** first before jumping in.

You can go through the [announcement blog][18] to get further information on this.

* * *

**Suggested Read 📖:** [_Not Every Browser is Built on Chrome_][4]

![][19]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ladybird-web-browser-rustification/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.chromium.org/
[4]: https://itsfoss.com/firefox-based-browsers/
[5]: https://en.wikipedia.org/wiki/Duopoly
[6]: https://ladybird.org/
[7]: https://itsfoss.com/content/images/2026/02/ladybird-early-build.png
[8]: https://isocpp.org/
[9]: https://www.swift.org/
[10]: https://rust-lang.org/
[11]: https://en.wikipedia.org/wiki/Object-oriented_programming
[12]: https://awesomekling.github.io/about/
[13]: https://github.com/LadybirdBrowser/ladybird/tree/master/Libraries/LibJS
[14]: https://code.claude.com/docs/en/overview
[15]: https://openai.com/codex/
[16]: https://github.com/LadybirdBrowser/libjs-test262
[17]: https://github.com/LadybirdBrowser
[18]: https://ladybird.org/posts/adopting-rust/
[19]: https://itsfoss.com/content/images/icon/android-chrome-512x512-292.png
