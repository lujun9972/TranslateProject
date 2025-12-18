[#]: subject: "The First Rust CVE in Linux Kernel Only Makes Your System Crash"
[#]: via: "https://itsfoss.com/news/first-linux-kernel-rust-cve/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The First Rust CVE in Linux Kernel Only Makes Your System Crash
======

[![Warp Terminal][1]][2]

So what happened is, [CVE-2025-68260][3] affects the [Android Binder][4] driver, which was rewritten in [Rust][5] for Linux 6.18 and newer. The driver handles communication between different parts of Android.

The bug happens when different parts of the code try to access the same list at the same time ( _the technical term is "_[ _a data race_][6] _"_ ). This creates a timing issue that messes things up, and the system crashes.

But here's the thing: **it only causes crashes**. It does not let attackers take over your system, steal data, or run malicious code. That is very different from typical memory bugs found in [C][7] code, which could allow those things.

In a post on [social.kernel.org][8], Greg put it like this:

> Rust is is not a "silver bullet" that can solve all security problems, but it sure helps out a lot and will cut out huge swatches of Linux kernel vulnerabilities as it gets used more widely in our codebase.
>
> That being said, we just assigned our first CVE for some Rust code in the kernel: [https://lore.kernel.org/all/2025121614-CVE-2025-68260-558d@gregkh/][9] where the offending issue just causes a crash, not the ability to take advantage of the memory corruption, a much better thing overall.
>
> Note the other 159 kernel CVEs issued today for fixes in the C portion of the codebase, so as always, everyone should be upgrading to newer kernels to remain secure overall.

_You see what he's saying?_ 🤔

On the same day this Rust CVE was announced, **159 other CVEs were issued for the C portions of the kernel**. Greg's message is clear: Rust isn't perfect, but it's helping.

**The fix is already available**. If you are running Linux 6.18, then update to 6.18.1 or later, and the same is already live in 6.19-RC1. The Linux kernel CVE team recommends updating to the latest stable version rather than trying to cherry-pick individual patches.

Of course this CVE is sure to ruffle some feathers because it is related to Rust. But beyond that, it's good to see the kernel team continuing to deliver patches consistently, regardless of which language the bugs are in. That's what matters at the end of the day.

Via: [Phoronix][10]

**Suggested Read 📖:** [The Tor Project is Making a Switch to Rust, Ditches C][11]

![][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/first-linux-kernel-rust-cve/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://lore.kernel.org/linux-cve-announce/2025121614-CVE-2025-68260-558d@gregkh/
[4]: https://www.phoronix.com/news/Rust-Binder-For-Linux-6.18
[5]: https://rust-lang.org/
[6]: https://doc.rust-lang.org/nomicon/races.html
[7]: https://www.c-language.org/
[8]: https://social.kernel.org/notice/B1JLrtkxEBazCPQHDM
[9]: https://lore.kernel.org/all/2025121614-CVE-2025-68260-558d@gregkh/
[10]: https://www.phoronix.com/news/First-Linux-Rust-CVE
[11]: https://itsfoss.com/news/tor-rust-rewrite-progress/
[12]: https://itsfoss.com/content/images/icon/android-chrome-512x512-136.png
