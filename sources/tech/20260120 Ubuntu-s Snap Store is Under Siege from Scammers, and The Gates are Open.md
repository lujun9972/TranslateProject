[#]: subject: "Ubuntu's Snap Store is Under Siege from Scammers, and The Gates are Open"
[#]: via: "https://itsfoss.com/news/snap-store-under-siege/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ubuntu's Snap Store is Under Siege from Scammers, and The Gates are Open
======

[![Warp Terminal][1]][2]

Malicious actors are doing everything at their disposal to undermine modern IT infrastructure. Some are motivated by the usual monetary gains, while others have more sinister intents.

Canonical's [Snap Store][3] is the latest in line, with the platform facing increasingly sophisticated attacks, and [a recent development][4] makes things look particularly bleak.

Before we go ahead, keep in mind that **the backend tech for the Snap Store is proprietary** , and many people tend to confuse this with [Snaps][5] themselves being some mysterious concoction ( _read: closed-source_ ).

### The Snap Store is Due For a Clean-Up

![][6]

📋

The picture above shows the search results when searching for the term "[ _ _Crypto Wallet__][7]." Imagine how easy it would be to install a malicious one by mistake.

[Alan Pope][8], a former Canonical employee who worked there from 2011 to 2021, has been documenting this mess since early 2024, where fake cryptocurrency wallet applications have been flooding the store.

Such scams have led to confirmed losses, including one case where [$490,000 was stolen from a single victim][9].

This goes without saying, but these aren't just annoying adware-ridden apps. They are outright thieving tools. The scammers publish malware disguised as legitimate crypto wallets like [Exodus][10], [Trust Wallet][11], or [Ledger][12]. When users install these fake apps and enter their wallet recovery phrases, the credentials get delivered straight to the criminals.

The tactics have evolved over time. Initially, scammers just published authentic-looking apps with plausible screenshots. When Canonical added text filters, they started using Unicode lookalike characters from other alphabets to bypass detection.

Then arrived **the bait-and-switch approach** : publish something harmless like a game under a random name, get it approved, then push a second version containing the harmful [malware][13].

_But their latest tactic is utter mischief and absolute deceit._ 😑

The scammers **have started monitoring the Snap Store for applications whose publishers' domain registrations have expired**. When a domain, let's say `coolproject.tech`, is abandoned, these wannabe vultures swoop in to register it in their name and trigger a password reset on [the Snap Store account][14].

By doing this, they gain control of a legitimate, trusted publisher account with an established history.

Alan was reminded of this long-standing issue when he started monitoring the Snap Store using his [SnapScope][15] tool. Though he remains sympathetic to the people working at Canonical and is not angry at the engineers. But he does want the problem fixed.

### What Can Be Done?

Well, much of the matter would've been tackled if domain names were bound to their original owners ( _with the option to transfer them to others_ ) and weren't left to the bandits once some time limit was up. But that isn't feasible in today's time.

The next best and obvious bet would be **for Canonical to step up their game** and do something about this issue. They already have [a manual review process][16] for new Snap name registrations, but that [isn't sufficient][17] to handle this particular loophole those sneaky scammers are using, is it?

_If they don't do anything about this, then they are knowingly endangering their users, both private and commercial, you know._ 🙃

* * *

**Suggested Read 📖:** [_Check Your Snap Packages for Vulnerabilities_][15]

![][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/snap-store-under-siege/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://snapcraft.io/
[4]: https://blog.popey.com/2026/01/malware-purveyors-taking-over-published-snap-email-domains/
[5]: https://github.com/canonical/snapd
[6]: https://itsfoss.com/content/images/2026/01/snap-store-crypto-wallet-query.png
[7]: https://snapcraft.io/store?q=Crypto+Wallet
[8]: https://www.linkedin.com/in/alan-pope-uk/
[9]: https://blog.popey.com/2024/02/exodus-bitcoin-wallet-490k-swindle/
[10]: https://www.exodus.com/
[11]: https://trustwallet.com/
[12]: https://www.ledger.com/
[13]: https://www.malwarebytes.com/malware
[14]: https://dashboard.snapcraft.io/stores/snaps/
[15]: https://itsfoss.com/news/check-snap-packages-vulnerabilities/
[16]: https://forum.snapcraft.io/t/manual-review-of-all-new-snap-name-registrations/39440
[17]: https://forum.snapcraft.io/t/report-of-fake-crypto-wallet-exodus-snap-s/49161
[18]: https://itsfoss.com/content/images/icon/android-chrome-512x512-227.png
