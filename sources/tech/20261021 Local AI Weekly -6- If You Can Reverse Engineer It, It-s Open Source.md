[#]: subject: "Local AI Weekly #6: If You Can Reverse Engineer It, It's Open Source!"
[#]: via: "https://itsfoss.com/newsletter/local-ai-weekly-6/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Local AI Weekly #6: If You Can Reverse Engineer It, It's Open Source!
======

[![Warp Terminal][1]][2]

What I realized in the past week or so is that if you can reverse engineer it, any software is open source software.

Not in the license sense, of course. But AI agents are getting good at reading binaries, tracing what an app does and rebuilding it. Last issue, we had the Craft tools cloning Microsoft Office. This week, there are more office clones, a viral repo that reverse engineers "anything", and people taking back control of their smart TVs with the help of AI.

The source code is no longer the wall it used to be. Whether that's a good thing depends a lot on which side you are on.

## 🧪 On my desk

I have enjoyed using Myna for voice based input on Ubuntu 26.04 (yes, it can be installed on 26.04). The performance is surprising good. Next, I will be trying a few more such voice input tools, starting with [SpeakoFlow][3].

## 🔍 Discover AI tools

[REA (Reverse Engineer Anything)][4] is the repo of the week. It's an MIT-licensed MCP server that lets AI agents inspect native binaries, Electron apps, Android APKs, firmware and more. Deep native analysis needs proper reverse engineering tools like [Ghidra][5]. Analysis runs locally, but your agent's model provider still sees what it finds. Also, fake REA repos are already serving malware, so install it only from the official repo or npm package.

[Graphify][6] is reverse engineering for your own code. It turns a codebase, docs and PDFs into a knowledge graph your coding agent can query. Code is parsed locally with tree-sitter, and `GRAPHIFY_BACKEND=ollama` keeps the rest local too.

[It's a Plan][7] is a self-hosted Linear/Jira alternative where AI agents get a role and pick up issues like any team member. External agents run on your machine and hand tasks to Claude Code, Codex or opencode. In early stages for now.

## 🏢 The office clone wars

Mandrake Linux creator Gaël Duval is behind [ElixirOffice][8], a Microsoft Office look-alike built on Euro-Office components. The code was written by LLM agents, with tests and reviews on every change. It's AGPL-3.0 and in beta.

Then there is [Ely Office][9], six offline desktop apps for documents, sheets, slides, PDF, Git and Markdown.

And [BetterOffice][10], which we covered last week, now has its Apache-2.0 source under the openooxml org on GitHub.

Meanwhile, Perplexity added REA to its Computer agent as a `/reverse-engineer` command, free until 31 October. Its demo clones included Photopea, Audacity and... LibreOffice Calc. Yes, reverse engineering an app that is already open source (LOL).

## 📺 Your TV, your rules

My favorite story of the week. Android TV owners are using AI to [debloat their smart TVs][11]. The agent connects over ADB, lists installed packages and disables ads, telemetry and preinstalled junk. People report faster TVs. A related project does the same for Fire TV.

This is the "reverse engineering" idea at its most useful. You don't need to be an Android developer anymore to fix the device you paid for.

## 📡 Open Model News

Meta released [Muse Spark Open][12], an 816B model with 42B active parameters and a 1M-token context. The headline says it "runs on Macs". But that actually means two Mac Studios with 512 GB each. Not the kind of hardware normies like me can afford.

Also note the licence. It's the "Muse Model License" with limited commercial terms. Open weights, yes. Open source, no.

## 👀 Big Tech Watch

[NVIDIA RTX Spark laptops][13] went on sale on 16 October, starting at $2,599, from ASUS, Dell, HP, Lenovo, Microsoft and MSI. The chip pairs a Blackwell GPU with a Grace Arm CPU and up to 128GB of unified memory, enough for bigger local models on a laptop. Two catches. The 128GB is only on the top configuration, and the lower tier tops out at 32GB. And these are Windows on Arm machines, with no word on native Linux support (yet).

Google Research open sourced [Harness²][14], a framework that improves the harness around a model (prompts, tools, memory, skills) without touching its weights. It's Apache-2.0 and uses OpenCode by default. Model runs are configured for Vertex AI, and I see no documented local model path yet.

[Anthropic says Claude Code now gzips the conversation][15] it sends on every turn, and cloud sessions start as soon as you begin typing. It reports up to 3x faster time to first token for local Claude Code sessions, compared with August. The billion-dollar AI speedup came from gzip, a free and open source software tool from 1992.

## 🗂 AI Jargon: Clean-room design

How do you copy software legally? Clean-room design.

One team studies the original app and writes down only what it does: the behavior, the file formats, the interfaces. A second team, which has never seen the original code, builds a new app from that description. That separation is what protects the clone from copyright claims. It's how the PC BIOS was cloned in the 1980s and that's how Compaq became a popular PC brand.

AI agents blur this neatly. The same agent that reads the binary often writes the new code. Whether that still counts as a clean room is a question lawyers will be busy with for a while.

## 😂 Meme

![][16]

## ⚡ Quick Tip: Back up before an agent touches your TV

Before you get too excited and let an agent debloat your Android TV, save the package list first:

```

    adb shell pm list packages > tv-packages.txt

```

Ask the agent to use `pm disable-user` instead of uninstalling. A disabled package comes back with `adb shell pm enable <package-name>`. And turn off USB or wireless debugging when you are done. An open ADB port on your home network is not something you want to leave lying around.

And if you must use cloud AI for something sensitive, Maple has a [sensible guide to using AI privately][17]. Maple sells a private AI service, so keep that in mind. The thing is that privacy settings alone don't stop a provider from reading your chats. Running models locally is still the only option that keeps your words off someone else's server.

Keep on exploring AI (locally).

If this helped you, consider supporting It's FOSS

It's FOSS has been helping people use Linux for the past 14 years. Help us stay independent from big tech. Become a Plus member, enjoy ad-free reading and get 5 eBooks.

Plus yearly

Ad-free, FREE ebooks

[Join yearly][18]

Best value

Plus lifetime

Pay once, Enjoy forever

[Go lifetime][19]

Buy us a coffee

Any amount, no commitment

[Support on Ko-fi][20]

Skip the AI slop and SEO spam in your Google results

Tell Google you prefer It's FOSS, and it will show our Linux news and tutorials, created by experienced Linux users, more often when you search. It takes just a click.

[Set as preferred source][21]

--------------------------------------------------------------------------------

via: https://itsfoss.com/newsletter/local-ai-weekly-6/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/AbhishekBarali/SpeakoFlow
[4]: https://github.com/morluto/rea
[5]: https://itsfoss.com/nsa-ghidra-open-source/
[6]: https://github.com/Graphify-Labs/graphify
[7]: https://github.com/croffasia/itsaplan
[8]: https://itsfoss.com/news/elixiroffice-euro-office-fork/
[9]: https://office.elygpui.com/
[10]: https://github.com/openooxml/betteroffice
[11]: https://itsfoss.com/news/debloat-smart-tv/
[12]: https://research.meta.ai/blog/muse-spark-open
[13]: https://nvidianews.nvidia.com/news/nvidia-rtx-spark-pcs-available-today-a-new-beginning-for-windows-pcs
[14]: https://github.com/google-research/harness2
[15]: https://x.com/ClaudeDevs/status/2111209208012210409
[16]: https://itsfoss.com/content/images/2026/10/GZJF7z5WcAA5NUb.jpeg
[17]: https://maple.ai/blog/how-to-use-ai-privately
[18]: https://itsfoss.com/#/portal/signup
[19]: https://itsfoss.com/lifetime-membership/
[20]: https://ko-fi.com/itsfoss
[21]: https://www.google.com/preferences/source?q=itsfoss.com
