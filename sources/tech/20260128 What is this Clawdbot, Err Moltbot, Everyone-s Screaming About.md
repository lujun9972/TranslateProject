[#]: subject: "What is this Clawdbot, Err Moltbot, Everyone's Screaming About?"
[#]: via: "https://itsfoss.com/news/clawdbot-fiasco-explained/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What is this Clawdbot, Err Moltbot, Everyone's Screaming About?
======

[![Warp Terminal][1]][2]

Late last year, [Peter Steinberger][3] launched [Clawdbot][4], an open source AI assistant that **runs locally on a user's hardware** and executes tasks instead of just chatting about them.

You message it through WhatsApp, Telegram, Slack, Discord, or iMessage, and it handles tasks across your digital life. It reads and responds to emails, manages your calendar, controls your browser, runs shell commands, and remembers everything through persistent memory stored locally on your machine.

Heck, Clawdbot even got people buying [Mac mini][5] devices in droves just so they could get their hands on its capabilities.

Like most viral projects, Clawdbot got served " _a polite email asking for a name change_ " [by Anthropic][6], the company behind Claude AI. Following a 5 AM community voting session on Discord, the project decided on the new [Moltbot][7] name.

Their branding, [X handle][8], documentation, etc. have all been changed accordingly.

The project's woes didn't stop there, as Peter [tweeted yesterday][9] that his [GitHub][10] account's username was stolen by [crypto scammers][11]. The issue was a combination of him messing up the renaming of his account in a panic induced by the _@clawdbot_ handle getting taken over by a crypto-flavored squatter and zealous malicious actors pouncing on the username.

Luckily, the fix came quickly in the form of the rebrand and Peter regaining access to his GitHub username. And, if you think things are calming down, I wouldn't hold my breath.

### A Banquet of Security Holes

Rahul Sood, a known name in entrepreneurial circles, posted [an article][12] on X a few days ago, where he pointed out the issues with Moltbot. His main concern was [prompt injection attacks][13].

Malicious PDFs or emails could trick the AI underneath into executing hidden commands. Since Moltbot connects to WhatsApp, Telegram, and Discord, any message, document, or webpage could become a potential [attack vector][14].

Similar concerns [were raised][15] by another person, to which Peter replied with a list of existing safeguards that included things like enabling sandbox mode, using allowlists for commands, and running the built-in security audit tool.

If you think Rahul's word is not authoritative enough for you, then the folks over at [InfoStealers][16] have laid out how Moltbot stores sensitive information like user profiles, memories, and authentication tokens **in plaintext files** that any malware can read.

They coin it as " _Cognitive Context Theft_ " because hackers get access not only to passwords but also to a user's entire workflow, routines, and who they talk to. Further adding that major [Malware-as-a-Service][17] (MaaS) families like _**Vidar**_ , _**RedLine** ,_ and _**Lumma**_ are already adapting to target it.

* * *

**Suggested Read 📖:** [_Ubuntu's Snap Store is Under Siege from Scammers_][11]

![][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/clawdbot-fiasco-explained/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://steipete.me/
[4]: https://clawd.bot/
[5]: https://www.apple.com/mac-mini/
[6]: https://docs.molt.bot/start/lore#:~:text=For%20a%20while%2C%20the%20lobster%20was%20called%20Clawd%2C%20living%20in%20a%20Clawdbot.%20But%20in%20January%202026%2C%20Anthropic%20sent%20a%20polite%20email%20asking%20for%20a%20name%20change%20(trademark%20stuff).%20And%20so%20the%20lobster%20did%20what%20lobsters%20do%20best%3A
[7]: https://www.molt.bot/
[8]: https://x.com/moltbot/status/2016058924403753024
[9]: https://x.com/steipete/status/2016073406840476131
[10]: https://github.com/steipete
[11]: https://itsfoss.com/news/snap-store-under-siege/
[12]: https://x.com/rahulsood/status/2015397582105969106
[13]: https://en.wikipedia.org/wiki/Prompt_injection
[14]: https://www.cloudflare.com/learning/security/glossary/attack-vector/
[15]: https://x.com/steipete/status/2015266538371125727
[16]: https://www.infostealers.com/article/clawdbot-the-new-primary-target-for-infostealers-in-the-ai-era/
[17]: https://encyclopedia.kaspersky.com/glossary/malware-as-a-service-maas/
[18]: https://itsfoss.com/content/images/icon/android-chrome-512x512-238.png
