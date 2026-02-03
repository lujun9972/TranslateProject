[#]: subject: "Oh Dear! Notepad++ Was Quietly Compromised for Six Months (But Don't Panic Just Yet)"
[#]: via: "https://itsfoss.com/news/notepad-plus-plus-compromised/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Oh Dear! Notepad++ Was Quietly Compromised for Six Months (But Don't Panic Just Yet)
======

[![Warp Terminal][1]][2]

[Notepad++][3] has been around for quite some time now, and for good reason. It is a free ( _as in freedom_ ) and open source text editor that's lightweight in nature. Developers, sysadmins, and anyone else who works with code or plain text on Windows has most likely used it at some point.

I say Windows because **it is still not available on Linux** , even after 22 years since its initial release, though [you can run it via an unofficial Snap][4] that uses Wine under the hood.

Unfortunately, there's [some concerning news][5] that you should take note of if you have it installed.

### What's Happened?

The update infrastructure of Notepad++ was compromised.

The attack did not come from a flaw in Notepad++ itself. It started with the hosting provider, who ran the server handling Notepad++'s update system ( _WinGup_ ).

Back in June 2025, attackers broke into that shared hosting server and got themselves inside the update infrastructure. From there, they could intercept update requests and quietly redirect users to their own servers.

This went on for months, but the attackers lost direct access to the server in early September after a routine maintenance update kicked them out. But they had already grabbed credentials to the hosting provider's internal services and used those to keep the redirection going all the way until December 2, 2025.

**The targeting was not random either**. Many security researchers [have traced the attack][6] to what they believe is a Chinese state-sponsored group. Moreover, only certain users were deliberately targeted.

The attack has since been effectively shut down, with the hosting provider patching the vulnerabilities, changing out all the compromised credentials, and Notepad++ moving to a new hosting provider.

### The Fix

It is quite simple, actually. If you are an existing user, then you can download [Notepad++ v8.9.1][7] ( _or later_ ), which **includes the necessary security fixes**. You will have to manually update though.

That release comes with many other improvements too, like macro and search bug fixes, better syntax highlighting for Perl, new _Function List_ support for Nim, and a better _Find_ dialog that now flags invisible characters.

[Notepad++ v8.9.1][7]

* * *

**Suggested Read 📖:** [_Best Notepad++ Alternatives For Linux_][8]

![][9]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/notepad-plus-plus-compromised/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://notepad-plus-plus.org/
[4]: https://itsfoss.com/notepad-plus-plus-linux/
[5]: https://notepad-plus-plus.org/news/hijacked-incident-info-update/
[6]: https://www.rapid7.com/blog/post/tr-chrysalis-backdoor-dive-into-lotus-blossoms-toolkit/
[7]: https://notepad-plus-plus.org/downloads/v8.9.1/
[8]: https://itsfoss.com/notepad-alternatives-for-linux/
[9]: https://itsfoss.com/content/images/icon/android-chrome-512x512-257.png
