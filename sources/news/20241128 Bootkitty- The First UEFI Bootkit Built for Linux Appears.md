[#]: subject: "Bootkitty: The First UEFI Bootkit Built for Linux Appears!"
[#]: via: "https://news.itsfoss.com/bootkitty-linux/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Bootkitty: The First UEFI Bootkit Built for Linux Appears!
======
Nothing is bulletproof. However, it is still not a concern for panic.
Just follow the best practices, and you should be fine.
[![][1]][2]

If you own a computer, it is imperative that you take care of its security by investing time and resources in safeguarding it. [Threat actors][3] across the world are constantly working on undermining the security measures of computers. It doesn't matter whether you are an individual or a big corporation raking in millions in revenue; you should be on guard.

There used to be a time when operating systems like Windows and macOS were **the most bountiful targets** for such perpetrators, but they are not the only prey now.

Thanks to an increase in both personal and enterprise usage, Linux distributions are slowly but surely becoming the next big thing to crack. And guess what? A new threat called “ **Bootkitty** ” has recently been [uncovered][4] that targets UEFI-equipped Linux systems.

### Bootkitty: Should Linux Users Be Worried?

![Source: ESET][5]

Known for their cybersecurity expertise, ESET's researchers first stumbled across this on [VirusTotal][6] where it was uploaded anonymously as an unknown [UEFI][7] application named “ _bootkit.efi_ ”.

After analyzing it, the ESET team found that it was **a UEFI bootkit for Linux, which targeted specific versions of Ubuntu**.

If you didn't know, a [bootkit][8] is a type of rootkit that is specifically designed to infect a computer's boot process. These allow an attacker to carry out a range of malicious actions while staying hidden from conventional malware removal methods.

The researchers deduced that Bootkitty's main goal was to:

> Disable the kernel’s signature verification feature and to preload two as yet unknown ELF binaries via the Linux init process.

As it stands, **Bootkitty can affect UEFI systems with secure boot enabled** only if the attacker has successfully installed malicious certificates, and also in cases where secure boot is not enabled.

The researchers found many [artifacts][9] that aided them in understanding what this bootkit was all about. They found two unused functions that were capable of printing special [strings][10] during execution.

The first was the ASCII art you saw above, which led ESET to believe that Bootkitty is what the bootkit is called.

![Source: ESET][11]

The second was the printing of a list of potential Bootkitty authors ( _redacted by ESET_ ) and other people related to the malware, with another set of strings being printed out on every boot containing the following text:

> Bootkitty's Bootkit
>  \- Developed By BlackCat

ESET clarifies that they don't believe this is related to the notorious [BlackCat][12] ransomware group, as that group primarily develops Rust-based malware, while Bootkitty was developed using C.

Currently, many in the cybersecurity space consider Bootkitty to be **an initial proof-of-concept bootkit** , with ESET explaining that according to their data, it has not yet been used in the outside world.

So, for now, there is no need to panic. 🤓

Nevertheless, **taking some preventative measures will go a long way** in securing your Linux system. You can learn about some of those by reading on.

**Don't Miss The Deals** 🕐

![][13]

### What Steps To Take?

For starters, **keep secure boot enabled** , as it is highly unlikely that your system has been affected by the Bootkitty attackers' malicious UEFI certificates. Then comes the most obvious one: **Keep your Linux distros updated with the most recent patches** ; upgrade if you are running something ancient/unsupported.

Additionally, ESET mentions to always **keep your** [**UEFI revocations list**][14] **updated** to prevent malicious bootloaders from loading and compromising your system. You could also follow some tips mentioned in our article to [improve the security of your Linux system][15].

If you are interested in learning more about the inner workings of Bootkitty, I highly suggest you read [ESET's deep dive blog][4].

For samples and the indicators of compromise ( _IoCs_ ), you can visit ESET's [GitHub][16] repo.

**Suggested Read** 📖

![][13]

* * *

[Get It's FOSS Plus Membership][17]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/bootkitty-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Threat_actor
[4]: https://www.welivesecurity.com/en/eset-research/bootkitty-analyzing-first-uefi-bootkit-linux/
[5]: https://news.itsfoss.com/content/images/2024/11/Bootkitty_a-1.png
[6]: https://www.virustotal.com/gui/file/f1f84819bdf395d42c36adb36ded0e7de338e2036e174716b5de71abc56f5d40
[7]: https://en.wikipedia.org/wiki/UEFI
[8]: https://en.wikipedia.org/wiki/Rootkit#bootkit
[9]: https://www.sciencedirect.com/topics/computer-science/malware-artifact
[10]: https://en.wikipedia.org/wiki/String_(computer_science)
[11]: https://news.itsfoss.com/content/images/2024/11/Bootkitty_b.png
[12]: https://en.wikipedia.org/wiki/BlackCat_(cyber_gang)
[13]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[14]: https://uefi.org/revocationlistfile
[15]: https://itsfoss.com/improve-security-linux/
[16]: https://github.com/eset/malware-ioc/tree/master/bootkitty
[17]: https://itsfoss.com/#/portal/signup
