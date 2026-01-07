[#]: subject: "First Good News of 2026! COCOS 4 Game Engine Goes Open Source"
[#]: via: "https://itsfoss.com/news/cocos-4-game-engine/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

First Good News of 2026! COCOS 4 Game Engine Goes Open Source
======

[![Warp Terminal][1]][2]

[COCOS][3] is a cross-platform game development platform popular in Asian markets, known for lightweight mobile and in-app games. Earlier in November 2025, [it was acquired][4] by Chinese gamification giant [SUD][5] for $72 million.

Just two months after that, SUD [has now announced][6] that COCOS 4 is available under **the MIT license** , with all commercial restrictions removed.

**The engine and editor have been separated**. Previously, _Cocos Creator_ referred to both components together across versions _1.x_ , _2.x_ , and _3.x_. COCOS now means the engine only, and the number 4 denotes the latest release number.

On the other hand, **PinK** is the new standalone IDE for COCOS. It will work as a production pipeline with built-in Agents and most visual-focused features from Cocos Creator will move to PinK over time.

The open source release for COCOS comes with the engine core, cross-platform code, [COCOS CLI][7], and full IDE headless mode. Cross-platform code covers all native platforms, with mini-game platform support rolling out gradually.

Core editing functions from the original Cocos Creator are transitioning to Headless Mode. These will be accessible via CLI and become part of the engine core.

SUD has set **no direct commercialization targets for COCOS 4** ( _read: will it make them money?_ ). They say that their focus is on reaching more developers and creating more game content critical to SUD's long-term business growth.

The open source approach was picked as **it was the fastest path to AI-native functionality**. The main argument is that AI can better understand open code and guide the engine to evolve in AI-friendly directions.

Pull requests are another goal. More PRs bring more developers. More developers make the engine stronger, basically like a [feedback loop][8].

Global reach is yet another focus, where the COCOS team wants both game developers and AI developers worldwide to be brought into a unified open source game engine ecosystem.

### Development Direction

COCOS 4 builds on _Cocos Creator 3.x_ with forward compatibility, and it follows [SemVer][9] rules, keeping a minimum six-month window between deprecating something and removing it.

**The developers are focusing on some key areas to take COCOS forward**. AI features come first. New stuff will ship as MCPs or Agents rather than traditional libraries. The engine is getting lighter and faster to run on any device with a screen.

Cross-platform support is expanding to Steam and other platforms. Old bugs like the [Spine][10]-related one are getting fixed, and performance improvements target things like rich text and lists.

Moreover, developers can modify any part of the engine code. They can even build an entirely new engine based on COCOS 4 if it suits them.

If you are interested, then you will find the source code and necessary documentation for COCOS 4 on its [GitHub][11] repository.

[COCOS 4][11]

* * *

**Suggested Read 📖:** [_Godot 4.5 Release Brings Accessibility Features, Shader Baker, and Stencil Buffer Support_][12]

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/cocos-4-game-engine/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.cocos.com/en
[4]: https://en.prnasia.com/releases/apac/sud-fully-acquires-cocos-511457.shtml
[5]: https://www.sud.tech/en
[6]: https://www.prnewswire.com/news-releases/cocos-4-is-here-fully-open-source-302652264.html
[7]: https://github.com/cocos/cocos-cli
[8]: https://dictionary.cambridge.org/us/dictionary/english/feedback-loop
[9]: https://semver.org/
[10]: https://esotericsoftware.com/
[11]: https://github.com/cocos/cocos4
[12]: https://itsfoss.com/news/godot-4-5-release/
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-186.png
