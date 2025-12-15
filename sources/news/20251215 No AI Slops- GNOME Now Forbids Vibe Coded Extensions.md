[#]: subject: "No AI Slops! GNOME Now Forbids Vibe Coded Extensions"
[#]: via: "https://itsfoss.com/news/no-ai-extension-gnome/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

No AI Slops! GNOME Now Forbids Vibe Coded Extensions
======

[![Warp Terminal][1]][2]

[Shell Extensions][3] are one of the best things about using GNOME. They let you customize your desktop exactly how you want it. I personally use quite a few to keep my workflow streamlined.

_If you are new to this, then we have a detailed guide on_ [_using GNOME extensions_][4] _that covers the basics._

However, **maintaining the extension ecosystem isn't easy**. The GNOME extensions team reviews every submission for issues and malicious code, a time-consuming process that's gotten harder lately thanks to [AI slop][5].

### AI Slop is Not Welcome

GNOME has updated its [extension review guidelines][6] to reject AI-generated code. The new rule states that submissions with clear signs of AI generation will not be approved.

[This change][7] comes after the team noticed a surge in extensions with unnecessary code patterns. [Javad Rahmatzadeh][8], who reviews extensions for GNOME, mentioned **spending over 6 hours some days** reviewing more than 15,000 lines of code.

During all that, he found out that **unnecessary try-catch blocks were appearing in many new extensions**. When he asked the developers about it, they confirmed it was the result of AI usage.

The updated review guidelines now list what will trigger rejection: large amounts of unnecessary code, inconsistent code style, imaginary API usage, comments serving as LLM prompts, and any other indication that the code is AI-generated.

And, to be clear, **using AI as a learning tool or for code completions is still allowed**. The policy targets developers who generate entire extensions without understanding the code.

This isn't something new. Many projects [are taking steps][9] to prevent AI slop from overwhelming existing systems. GNOME's approach is actually really good.

Many new developers are increasingly relying on AI-powered tools to learn, and a [blanket ban][10] wouldn't really be constructive, if you ask me.

Via: [Phoronix][11]

**Suggested Read 📖** : _Btw,_ [_Tiling Shell_][12] _is my favorite GNOME shell extension._

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/no-ai-extension-gnome/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://extensions.gnome.org/
[4]: https://itsfoss.com/gnome-shell-extensions/
[5]: https://en.wikipedia.org/wiki/AI_slop
[6]: https://gjs.guide/extensions/review-guidelines/review-guidelines.html#extensions-must-not-be-ai-generated
[7]: https://blogs.gnome.org/jrahmatzadeh/2025/12/06/ai-and-gnome-shell-extensions/
[8]: https://wiki.gnome.org/jrahmatzadeh.html
[9]: https://itsfoss.com/news/fedora-ai-guidelines/
[10]: https://en.wiktionary.org/wiki/blanket_ban
[11]: https://www.phoronix.com/news/GNOME-Extensions-Block-AI
[12]: https://itsfoss.com/news/tiling-shell-gnome-extension/
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-114.png
