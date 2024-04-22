[#]: subject: "Thunderbird Embraces Microsoft Exchange: Relies on Rust to add Support!"
[#]: via: "https://news.itsfoss.com/thunderbird-rust-microsoft-exchange/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Thunderbird Embraces Microsoft Exchange: Relies on Rust to add Support!
======
Thunderbird + Rust, exciting times!
Many users know Thunderbird to be one of the [best email clients for Linux][1], and rightly so. It has been around since 2003, consistently coping with changes in the [Internet mail standards][2] and other trends in the electronic mail world.

Continuing on that lineage, [Thunderbird][3] is now stepping into a new chapter, with [Rust][4] powering it all. Let's see what's going on.

### Thunderbird and Rust: A Good Pairing?

Thunderbird is all set **to provide native support for** [**Microsoft Exchange**][5] via the [Exchange Web Services][6] API ( _EWS_ ).

Doing so **will most likely end the need for a paid add-on** such as [Owl for Exchange][7], which happens to be one of the popular ways of using Exchange with Thunderbird.

![Owl for Exchange][8]

Native support for Exchange is being made possible with the use of Rust. But, seeing that Thunderbird features a lot of old code that dates back to the days of [Netscape Communicator][9], the developers have had to improvise a lot.

#### Why go with Rust?

The developers went with Rust because they wanted something powerful to develop complex features quickly, with long-term maintenance in mind. Rust provides advantages such as **memory safety** , **robust performance** , and a **modular nature** that is **supported by a vast ecosystem of users**.

There's also things like the shared CI infrastructure with [Firefox][10] that supports Rust, a set of powerful tools, support for a wide variety of platforms, and the ability to create modular crates that enable code reusability.

However, **the transition has not been smooth**.

Thanks to Thunderbird's huge codebase, a **lot of existing code doesn't play nice with Rust**. Take, for instance, the build system, which had to be given a tweak where Thunderbird would define its workspace and add its config to [_mach_][11], Mozilla's upstream build tool.

Then there's [_XPCOM_][12], for which Thunderbirds' developers had to implement a bridge to get it working with Rust.

As to **how they intend to implement Exchange support** , they are banking on using the [Necko][13] networking component found on Firefox. But, that is written in C++.

They implemented two key things to overcome the compatibility issues. First, they added support for a native Rust async/await syntax, and the second is that they added an [idiomatic][14] HTTP API to take care of the creation of XPCOM objects and Rustic error handling.

There are a few more things that they did, but I am skipping over those to keep things concise.

After going through the above, naturally, one question comes to mind.

#### When will Thunderbird feature support for Microsoft Exchange?

In the **upcoming ESR release of Thunderbird** , which is scheduled to be released in **July 2024**. As this is a big undertaking, **the developers are only implementing native Exchange support for email** , with calendar and address book support arriving later.

If you have any further questions regarding this, you can refer to the [announcement blog][15].

There's also a [community interaction][16] taking place for the Rust endeavor on Thunderbird. You can refer to the official details on when they share more details through video chat/stream.

**Suggested Read** 📖

![][17]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/thunderbird-rust-microsoft-exchange/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/best-email-clients-linux/
[2]: https://en.wikipedia.org/wiki/Internet_mail_standard
[3]: https://www.thunderbird.net/en-US/
[4]: https://www.rust-lang.org/
[5]: https://www.microsoft.com/en-us/microsoft-365/exchange/email
[6]: https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/ews-managed-api-reference-for-exchange
[7]: https://addons.thunderbird.net/en-us/thunderbird/addon/owl-for-exchange/
[8]: https://news.itsfoss.com/content/images/2024/04/Owl_AddOn_Thunderbird.jpg
[9]: https://en.wikipedia.org/wiki/Netscape_Communicator
[10]: https://www.mozilla.org/en-US/firefox/
[11]: https://firefox-source-docs.mozilla.org/mach/index.html
[12]: https://firefox-source-docs.mozilla.org/xpcom/index.html
[13]: https://firefox-source-docs.mozilla.org/networking/index.html
[14]: https://medium.com/swlh/idiomatic-code-a73f17f0f287
[15]: https://blog.thunderbird.net/2024/04/adventures-in-rust-bringing-exchange-support-to-thunderbird/
[16]: https://blog.thunderbird.net/2024/04/april-2024-community-office-hours-rust-and-exchange-support/
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
