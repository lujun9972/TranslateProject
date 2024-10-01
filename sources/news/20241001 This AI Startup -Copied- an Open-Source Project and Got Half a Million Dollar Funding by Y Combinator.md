[#]: subject: "This AI Startup "Copied" an Open-Source Project and Got Half a Million Dollar Funding by Y Combinator"
[#]: via: "https://news.itsfoss.com/pearai-controversy/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This AI Startup "Copied" an Open-Source Project and Got Half a Million Dollar Funding by Y Combinator
======
AI startups, and open-source forks with VC funding. A bad match.
[![][1]][2]

There are plenty of people who do not actually understand AI and open-source (or its licensing).

But, they choose to jump on using those terms to market their products somehow superior to others 🤦

It has been happening for a while, and it may not be a big deal if done ethically.

However, I just came across a new AI startup that was backed by Y Combinator for its new AI-powered open-source editor, which is, in fact, a poorly organized fork of [Visual Studio Code][3], and [Continue][4] ( _an open-source AI extension for VS Code_ ).

### Launching Unfinished Products Is The New Fad

Making mistakes at launch (or just making unfinished products) and rectifying the issues after its launch is the new thing.

Even **MKBHD** , who pointed out this trend in his previous videos, got himself into it by launching a wallpaper app that was scrutinized for its subscription and other questionable practices.

So, it is not just young developers/entrepreneurs, but it is something everyone has in mind currently, I guess. And, it is a disastrous trend 😞

Coming to our context here, one of the co-founders of **PearAI** , launched it as a new open-source AI code editor on X:

> I just quit my 270 000$ job at Coinbase to join the first YCombinator fall batch with my cofounder [@not_nang][5].
>
> We're building PearAI, an open source AI code editor. Think a better Copilot, or open source Cursor. But you've heard this spiel already... 🧵⬇️ [pic.twitter.com/nYeycRKRHm][6]
>
> — FRYING PAN (@CodeFryingPan) [September 29, 2024][7]

The controversy started with this tweet where they explained the code editor's advantages by making a thread.

While that by itself is not an issue, but them **being a fork of VS Code and Continue, and launching it with a non-open-source enterprise-focused license was** a dealbreaker.

And, there are **three parts of this issue.** I'll get to that next.

Sure, they also [apologized][8] for all the mistakes (but we can't ignore the underlying issues).

### First: The Founders ChatGPT'd The License

One of the primary reasons behind the uproar was that the project had a non-open-source license on GitHub even if they launched it as an open-source product.

![Commit history of PearAI on GitHub for updating the non-open-source license][9]

The basic and impactful element of a software product — **the license**.

And, when a fellow X user asked one of the co-founders, they replied that they simply ChatGPT'd the license, with an awful tone:

![Credits: Alex Cohen on X][10]

You cannot have an attitude like that if you want users/community to have confidence in your ideas or product. I'm sure people make mistakes, but, while bringing a new product to the industry?

You have more at stake. And, we should not be the one telling them that. They probably knew it, but did not care enough (which is why we are here).

Of course, this reply has been deleted on X. But, if I was replying to that, I would say: " _If you are busy building it, you should have been busy being careful launching it better_ ".

Now, the **second issue....**

### Second: Make More Effort When Forking a Project

**PearAI** mentions that it is a fork of VS Code and Continue.

But, if we look at the commit history for a product that wants to build a better solution from existing open-source projects, is this the amount of effort you are willing to put:

![][11]

You can check the commit for renaming [here][12]. But, I agree to some of the comments saying, at least, they could have gone beyond renaming things, and changed the wording to reflect their vision.

It could be harsh to say that it was just **CTRL+C → CTRL+V**. However, even, when you are forking a project, and copying something, doing it better really matters. And, I don't think they have fared well here.

We also have other open-source AI code editors like Void, also backed by Y Combinator, but it looks like a decent effort on the fork with more features being highlight as its benefits.

So, when you are making a fork at a time when other forks exist, you need to take responsibility and effort to showcase how it's better from them.

But, when asked about it, the co-founder mentioned that they have a more active developer community (and more contributors) connected to their project.

Is that why users should choose your product, that's it?

Unfortunately, even that claim was not accurate enough as stated here:

> A lot of PearAI's claimed 100+ contributors are just from upstream vscode commits they merged into their fork. GitHub just lists them as contributors because it can't detect the commits come from vscode (their repo wasn't forked through GitHub). [https://t.co/XcEVmv2vVT][13] [pic.twitter.com/hlGFFB5OsP][14]
>
> — Gautam (@gautam_at) [September 29, 2024][15]

### Third: Y Combinator (YC) Funding These Projects Makes it Concerning

So, can any developer just fork an existing project with little-to-no-effort, and get VC funding?

Just because it had the hype term “AI” — the investors decided to fund it? Do they reject deserving open-source projects over products like Pear AI?

And, it is YC in this case. They were known to be a prestigious early-stage VC funding brand.

But, funding these kinds of projects makes their choices questionable. I agree with the thought shared by _Sven Schnieders_ on this matter:

![][16]

### So, What's The Solution?

I think we cannot stop such kind of product launches, and obvious mistakes by careless founders.

But, we should definitely raise our concern and voices regarding funding of such projects, as it could hurt the open-source ecosystem eventually, especially, when most of the open-source maintainers are unpaid.

![][17]

Furthermore, it is important to support projects that make a "real" difference, rather than just the ones slapping AI and open-source to get attention.

Sure, PearAI got all the media coverage, and attention, which is good in a way. But, its history will never change, which is why founders need to change their way to approach launch projects if they don't want controversies to be associated with their products.

_💬 What do you think about this whole ordeal? Let me know your thoughts in the comments!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/pearai-controversy/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://github.com/microsoft/vscode
[4]: https://github.com/continuedev/continue
[5]: https://twitter.com/not_nang?ref_src=twsrc%5Etfw
[6]: https://t.co/nYeycRKRHm
[7]: https://twitter.com/CodeFryingPan/status/1840203597478539477?ref_src=twsrc%5Etfw
[8]: https://x.com/CodeFryingPan/status/1840831339337302204
[9]: https://news.itsfoss.com/content/images/2024/10/pear-ai-old-license.png
[10]: https://news.itsfoss.com/content/images/2024/10/chatgptd-license.jpg
[11]: https://news.itsfoss.com/content/images/2024/10/rename-continue-pear-ai.png
[12]: https://github.com/trypear/pearai-submodule/commit/12882703d31efe323591db8cebcb4dbe392adebc
[13]: https://t.co/XcEVmv2vVT
[14]: https://t.co/hlGFFB5OsP
[15]: https://twitter.com/gautam_at/status/1840455030551257284?ref_src=twsrc%5Etfw
[16]: https://digitalpress.fra1.cdn.digitaloceanspaces.com/ekvtmdn/2024/01/e9a18237-584f-4ea3-b3e0-9694b6045451_1280x1280.png
[17]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
