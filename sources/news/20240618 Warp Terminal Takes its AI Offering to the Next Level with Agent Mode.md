[#]: subject: "Warp Terminal Takes its AI Offering to the Next Level with Agent Mode"
[#]: via: "https://news.itsfoss.com/warp-ai-agent-mode/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Warp Terminal Takes its AI Offering to the Next Level with Agent Mode
======
Rust-based AI terminal gets a superpower with this new feature!
[![][1]][2]

Warp is a Rust-based, cross-platform terminal app that tries to “ _reimagine with AI and collaborative tools for better productivity_ ”. Its adoption has been growing consistently, with many users finding its AI-powered features under the _Warp AI_ umbrella useful.

Coming off the introduction of [Warp for ARM][3], the developers have introduced a new feature to Warp AI called “ **Agent Mode** ”, which, they claim, embeds LLM directly into the terminal for “ _multi-step workflows_ ”.

Let's check it out.

🚧

Warp is not FOSS, we cover it because it is available for Linux.

### Agent Mode: What's The Buzz About?

A new way to interact with AI on Warp, Agent Mode, understands plain English text (including commands) to suggest code, give outputs to guide you, autocorrect itself, learn/integrate with any service that hosts public documentation or a help page, and more.

📋

This article includes affiliate links. Refer to our [affiliate link policy][4] to learn more.

Thanks to its natural language prowess, users can simply ask it to do things, similar to having a conversation with a colleague or a [subject-matter expert][5]. It has tight integration with the CLI, enabling it to interface with any service without any extra configuration overhead.

The developers add that:

> If the service has a CLI, an API, or publicly available docs, you can use Agent Mode for the task. Agent Mode has inherent knowledge of most public CLIs, and you can easily teach it how to use internal CLIs by asking it to read their help content.

They also stress that **auto-detection of natural language happens locally** , data is only sent to their servers when you proceed with the request to process the entered data with Warp AI. You can also disable auto-detection, if you'd like, but, it's **enabled by default**.

They clarified that part with an example:

> If Warp AI needs the name of your git branch, it will ask to run git branch and read the output. You will be able to approve or reject the command. We’ve designed Agent Mode so that you know exactly what information is leaving your machine.

Of course, it's no secret that **Warp AI is powered by OpenAI,** so naturally all the input is sent to them, with Warp assuring that OpenAI doesn't train their models on such data. For users who don't prefer that, they could switch their LLM provider by opting for Warp's enterprise plan.

If you were wondering how Agent Mode could help, **here's an example** given by the developers.

![][6]

They illustrate how you can deal with the “ _port 3000 already taken_ ” error.

After attaching context to a query, Users can type something like “fix it”, and Agent Mode will start working on providing solutions 🤯

### Get Warp

If this new feature of Warp interested you, then you can head to its [official website][7], where you will find packages for **Linux** and **macOS** , with the Windows app coming soon.

Users of every plan tier will be able to access this, with the free plan including up to 40 AI requests per month, and users of the paid plans having more.

[Warp][7]

**For existing users** , you will now see the new Agent Mode replacing the first-gen Warp AI chat panel, with the “ _type # to ask Warp AI_ ” feature being retained for the short-term, with plans to retire it in the near future as Agent Mode matures.

If you would like to learn more, the official [announcement blog][8][documentation][9] has further information.

_💬 I know most of you do not like proprietary apps like this. But, if you give Warp a try, do let me know in the comments below._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/warp-ai-agent-mode/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/warp-terminal-linux-arm/
[4]: https://itsfoss.com/affiliate-policy/
[5]: https://en.wikipedia.org/wiki/Subject-matter_expert
[6]: https://news.itsfoss.com/content/images/2024/06/Warp_Agent_Mode.png
[7]: https://app.warp.dev/referral/6N3LPK
[8]: https://www.warp.dev/blog/agent-mode
[9]: https://docs.warp.dev/features/warp-ai/agent-mode
