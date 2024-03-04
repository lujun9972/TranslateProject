[#]: subject: "Privacy-Focused Google Photos Alternative 'Ente' is Now Open-Source"
[#]: via: "https://news.itsfoss.com/ente-open-source/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Privacy-Focused Google Photos Alternative 'Ente' is Now Open-Source
======
A new open-source alternative to Google Photos, sounds awesome!
There are plenty of photo services around the web that offer to store your images on their cloud infrastructure; for a fee, of course. But, not all provide an end-to-end encrypted experience, ensuring that no one else besides you can see the contents of your stored files.

I know that is quite subjective in this age of [mass surveillance][1], but it is better than having no encryption, isn't it? That is where a service like [Ente][2] comes in, it is **a cloud storage service geared towards storing photos** that offers end-to-end encryption out of the box.

And with a recent announcement, **Ente is fully embracing the essence of open-source**. So, join me as I take you through this interesting development.

### Ente: What to Expect?

![][3]

You see, Ente's various applications were already open-source, but the server side of things were not. But, that has changed now.

**The developers have completely open-sourced their server source code** for everyone to access.

Doing that also resulted in merging all of Ente's code into a single repository that **can be cloned to develop robust alternatives** to the likes of Google Photos and Apple iCloud.

The developers share that this is the same code that they work with to provide their cloud service that has been proven in production environments, and that others can expect continuous updates to it.

They also state that:

> Our real aim behind open sourcing our servers is to offer yet another reason for Ente customers to feel proud that by choosing Ente, they’ve made the right choice.

That does sound very assuring, if only more organizations opted to open-source their products; I am looking at you, Microsoft. 😑

Moving on, the developers mention that **they intended to open-source their server component sooner** , but they were unable to do so due to being caught up working on Ente.

Before they could even open-source it, they hired a firm to run an audit of the server code to ensure that it was not keeping any doors open unintentionally. The [report][4] took some time, but they passed it with a few suggestions from the auditor to fix the code.

The changes took some time, but they eventually got there. When developing a new feature for implementing [Passkeys][5] ( _TBA_ ), they were able to shift their focus towards the server code, and got around to open-source it too.

#### Want to check it out?

If you are interested in taking a peek at the source code or contributing to it, then you can visit Ente's [GitHub repo][6].

[Ente (GitHub)][6]

Head to the [official website][2] to get started with Ente if you like it.

_💬 Have you used Ente before? Let me know in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ente-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://en.wikipedia.org/wiki/Mass_surveillance
[2]: https://ente.io/
[3]: https://news.itsfoss.com/content/images/2024/03/Ente.png
[4]: https://ente.io/reports/Fallible-Audit-Report-19-04-2023.pdf
[5]: https://safety.google/authentication/passkey/
[6]: https://github.com/ente-io/ente
