[#]: subject: "cURL Gets Rid of Its Bug Bounty Program Over AI Slop Overrun"
[#]: via: "https://itsfoss.com/news/curl-closes-bug-bounty-program/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

cURL Gets Rid of Its Bug Bounty Program Over AI Slop Overrun
======

[![Warp Terminal][1]][2]

Last year in May, the [cURL][3] project's bug bounty program [was inundated with AI slop][4], where many bogus reports were opened on [HackerOne][5], leaving the cURL maintainers to go through garbage.

The problem didn't stop even after [Daniel Stenberg][6], the creator of cURL, threatened to ban anyone whose bug report was found to be [AI slop][7]. We are now in 2026, and the situation has reached a tipping point.

📋

For context, cURL is an open source command-line tool used by billions of devices worldwide.

### cURL Says Enough is Enough

![The notice for your perusal.][8]

Daniel has submitted [a pull request][9] on GitHub that removes all mentions of the bug bounty program from cURL's documentation and website. Coinciding with that, the project's [security.txt][10] file has been updated with some blunt language that makes the new policy crystal clear.

The cURL team intends to make a proper announcement in the coming days, though many outlets have already covered the news of this happening, _so I would say they ought to get on it ASAP!_ 😆

The program **officially ends in a few days on January 31, 2026**. After that, security researchers can still report issues through [GitHub][11] or the project's [mailing list][12], **but there won't be any cash involved**.

What pushed them over the edge?, you ask. Well, just weeks into 2026, **seven HackerOne reports came in within a 16-hour period** in just one week. Some were actual bugs, but none of them were security vulnerabilities. By the time Daniel posted his [recent weekly report][13], they'd already dealt with 20 submissions in 2026.

The main goal here is said to be stopping the flood of garbage reports. By eliminating the money incentive, they are hoping people ( _or bots?_ ) will stop wasting the security team's time with half-baked, unresearched submissions.

He also gives a stern warning to wannabe AI sloppers, saying that:

> This is a balance of course, but I also continue to believe that exposing, discussing and ridiculing the ones who waste our time is one of the better ways to get the message through: you should NEVER report a bug or a vulnerability unless you actually understand it - and can reproduce it. If you still do, I believe I am in the right to make fun of - and be angry at - the person doing it.

So, yeah, that's that. **If people still don't understand that AI slop is harmful** to such sensitive pieces of software, then sure, they can go ahead and make a fool of themselves.

* * *

**Suggested Read 📖:** [_Open Source Project LLVM Says Yes to AI-Generated Code_][14]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/curl-closes-bug-bounty-program/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://curl.se/
[4]: https://itsfoss.com/news/curl-ai-slop/
[5]: https://hackerone.com/curl
[6]: https://www.linkedin.com/in/danielstenberg/
[7]: https://en.wikipedia.org/wiki/AI_slop
[8]: https://itsfoss.com/content/images/2026/01/curl-bug-bounty-program-notice.png
[9]: https://github.com/curl/curl/pull/20312
[10]: https://curl.se/.well-known/security.txt
[11]: https://github.com/curl/curl
[12]: https://curl.se/mail/
[13]: https://lists.haxx.se/pipermail/daniel/2026-January/000143.html
[14]: https://itsfoss.com/news/llvm-ai-policy/
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-236.png
