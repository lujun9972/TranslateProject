[#]: subject: "The Tor Project is Making a Switch to Rust, Ditches C"
[#]: via: "https://itsfoss.com/news/tor-rust-rewrite-progress/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Tor Project is Making a Switch to Rust, Ditches C
======

[![Warp Terminal][1]][2]

The [Tor Project][3] has been busy with the rustification of their offering for quite some time now.

If you have used Tor Browser, you know what it does. Anonymous browsing through encrypted relay chains. The network itself has been running since the early 2000s. All of it is built on [C][4].

**But that C codebase is an issue**. It is known to have buffer overflows, use-after-free bugs, and memory corruption vulnerabilities. That is why they introduced **Arti** , a [Rust][5] rewrite of Tor that [tackles these flaws][6] by leveraging the memory safety of the programming language.

A [new release of Arti][7] just dropped last week, so let's check it out!

### Arti 1.8.0: What's New?

![Source: The Tor Project][8]

We begin with the main highlight of this release, the rollout of the **circuit timeout rework** that was laid out in [proposal 368][9]. Tor currently uses something called _Circuit Dirty Timeout_ (CDT). It is a single timer that controls when your connection circuits become unavailable and when they close down.

Unfortunately, it is predictable. Someone monitoring traffic can spot these patterns and potentially track your activity. Arti 1.8.0 fixes this by implementing usage-based timeouts with separate timers. One handles when circuits accept new connections. Another closes idle circuits at random times instead of fixed intervals.

This should reduce the risk of [fingerprinting][10] from predictable timeout behavior.

Next up is the new experimental `arti hsc ctor-migrate` command that lets onion service operators migrate their restricted discovery keys from the C-based Tor to Arti's keystore.

These keys handle client authorization for [onion services][11]. The command transfers them over without requiring operators to do the manual legwork. The release also delivers improvements for routing architecture, protocol implementation, directory cache support, and OR port listener configuration.

You can go through [the changelog][12] to learn more about the Arti 1.8.0 release.

Via: [Sam Bent][13]

**Suggested Read 📖** : Is Helium [the Browser Brave Was Meant to Be][14]?

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/tor-rust-rewrite-progress/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.torproject.org/
[4]: https://www.c-language.org/
[5]: https://rust-lang.org/
[6]: https://blog.torproject.org/announcing-arti/
[7]: https://blog.torproject.org/arti_1_8_0_released/
[8]: https://itsfoss.com/content/images/2025/12/tor-arti-banner.jpeg
[9]: https://spec.torproject.org/proposals/368-cdt-rethink.html
[10]: https://en.wikipedia.org/wiki/Device_fingerprint
[11]: https://support.torproject.org/tor-browser/features/onion-services/
[12]: https://gitlab.torproject.org/tpo/core/arti/-/blob/main/CHANGELOG.md#arti-180--1-december-2025
[13]: https://www.sambent.com/tor-ditches-c-for-rust-and-your-privacy-benefits/
[14]: https://itsfoss.com/helium-browser/
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-107.png
