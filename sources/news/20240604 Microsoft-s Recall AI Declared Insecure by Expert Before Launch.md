[#]: subject: "Microsoft's Recall AI Declared Insecure by Expert Before Launch"
[#]: via: "https://news.itsfoss.com/microsofts-recall-ai-insecure/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft's Recall AI Declared Insecure by Expert Before Launch
======
Uh-Oh, Microsoft, it doesn't look like you will be able to earn user's
trust with things like this.
[![][1]][2]

As expected, Microsoft's [creepy move to spy on everything][3] you do on your PC with Copilot+ [Recall][4] has backfired with widespread criticism over the potential privacy issues it could cause.

And, to add fuel to the fire, we now have a more disturbing development that could allow hackers to easily take advantage of a user's Recall data. This is thanks to some key weaknesses that were discovered by [Kevin Beaumont][5], an experienced cybersecurity researcher.

### Why is Microsoft Shooting Itself in The Foot?

A video of Recall for reference.

In his [detailed blog][6], Kevin found out that even though all the data is processed locally, when Azure AI automatically [OCR][7]s ( _extracts text from images_ ) the user's screen, it is stored in an SQLite database in the user's folder under a new “ _CoreAIPlatform_ ” folder inside “ _AppData_ ”.

That is where the problem lies, Microsoft is banking on the encryption already present on a user's device, and is of the belief that a malicious actor would need physical access to a user's device to compromise Recall data.

But, the thing is, **all that data is stored in plain text** and a simple InfoStealer [Trojan][8] could easily make short work of that, stealing all the information that Recall has collected, with the user being unaware of it.

If you were wondering **what kind of information, Recall collects**. Well, you already know that it is **enabled by default and takes screenshots** every few seconds.

So, any app you open, be it a chat application, a browser, the settings app, your password manager, games, and really anything that you have not manually excluded from its settings would be captured.

Not to forget, **Recall doesn't censor sensitive information** like passwords, financial information, government-issued identification numbers, and more.

Even deleted messages on chat applications like Signal, WhatsApp, Telegram are not safe, as Recall will regrettably be able to “recall” those messages.

Sure, one needs an “Admin” account to access the AppData folder, but, as things stand, that covers the majority of the user accounts that many people use, and access to it is just a matter of a few clicks.

As for how the data looks like, Kevin shared it on [X][9], where you can see that it has the name of the app, and some important attributes related to it.

Of course, this screenshot does not show too much, you will understand why soon.

> Microsoft told media outlets a hacker cannot exfiltrate Copilot+ Recall activity remotely.
>
> Reality: how do you think hackers will exfiltrate this plain text database of everything the user has ever viewed on their PC? Very easily, I have it automated.
>
> HT detective [pic.twitter.com/Njv2C9myxQ][10]
>
> — Kevin Beaumont (@GossiTheDog) [May 30, 2024][11]

He also pointed out that **hackers could easily modify existing malware to automatically scrape Recall data** , with him having already built a website where one could upload a Recall database to instantly search it.

Being a sensible cybersecurity professional, he has held back on the technical details on it and a few other findings, until Microsoft actually launches the Recall feature, giving them time to address these glaring issues.

In the end, it is the user who is at risk, as not everyone takes [steps to secure their privacy][12], and many just go along with what's already configured by their providers ( _read as the default settings of Windows_ ).

_💬 Your thoughts? Is having Recall on your PC a good idea? Let me know below._

**Suggested Read** 📖

![][13]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/microsofts-recall-ai-insecure/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/microsoft-windows-creepy-ai-move/
[4]: https://support.microsoft.com/en-us/windows/retrace-your-steps-with-recall-aa03f8a0-a78b-4b3e-b0a1-2eb8ac48701c
[5]: https://www.linkedin.com/in/kevin-beaumont-security/
[6]: https://doublepulsar.com/recall-stealing-everything-youve-ever-typed-or-viewed-on-your-own-windows-pc-is-now-possible-da3e12e9465e
[7]: https://en.wikipedia.org/wiki/Optical_character_recognition
[8]: https://en.wikipedia.org/wiki/Trojan_horse_(computing)
[9]: https://x.com/GossiTheDog/status/1796218726808748367
[10]: https://t.co/Njv2C9myxQ
[11]: https://twitter.com/GossiTheDog/status/1796218726808748367?ref_src=twsrc%5Etfw
[12]: https://itsfoss.com/improve-privacy/
[13]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
