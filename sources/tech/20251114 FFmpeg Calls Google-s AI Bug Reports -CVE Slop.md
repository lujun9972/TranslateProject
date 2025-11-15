[#]: subject: "FFmpeg Calls Google's AI Bug Reports "CVE Slop""
[#]: via: "https://itsfoss.com/news/ffmpeg-google-fiasco/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

FFmpeg Calls Google's AI Bug Reports "CVE Slop"
======

[![Warp Terminal][1]][2]

[FFmpeg][3] maintainers have publicly criticized Google after its AI tool reported a security bug in code for a 1995 video game.

The maintainers called the finding "[CVE slop][4]" and questioned whether trillion-dollar corporations should use AI to find security issues in volunteer code without providing fixes.

### Unchecked Automation is Not an Answer

> Patch to fix an issue with decoding LucasArts Smush codec, specifically the first 10-20 frames of Rebel Assault 2, a game from 1995.
>
> FFmpeg aims to play every video file ever made. [pic.twitter.com/9WryDgDpER][5]
>
> — FFmpeg (@FFmpeg) [October 30, 2025][6]

**So what happened is** , Google's AI agent Big Sleep found [a bug][7] in FFmpeg's code for decoding LucasArts Smush codec. The issue affected the first 10-20 frames of [Rebel Assault II][8], a game from 1995.

If you didn't know, [Big Sleep][9] is Google's AI-powered vulnerability detection tool developed by its Project Zero and DeepMind divisions. It is supposed to find security vulnerabilities in software before attackers can exploit them.

But there's an issue here: under Google's "[Reporting Transparency][10]" policy, the tech giant publicly announces it has found a vulnerability within one week of reporting it. A 90-day disclosure clock then starts regardless of whether a patch is available.

_You see the problem now?_ 🤔

FFmpeg developers patched the bug but weren't happy about it. They tweeted in [late October][11] that " _We take security very seriously but at the same time is it really fair that trillion-dollar corporations run AI to find security issues in people's hobby code? Then expect volunteers to fix_."

Beyond that, you have to understand that **FFmpeg is an important piece of digital infrastructure** that is used in Google Chrome, Firefox, YouTube, VLC, Kodi, and many other platforms.

The project is written almost exclusively by volunteers. Much of the code is in [assembly language][12], which is difficult to work with. This situation basically highlights [the ongoing tensions][13] over how corporations use volunteer-maintained open source software that powers their commercial products and expect them to fix any obscure issues that crop up.

Via: [The New Stack][14]

**Suggested Reads 📖**

![][15]

![][16]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ffmpeg-google-fiasco/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.ffmpeg.org/
[4]: https://x.com/ffmpeg/status/1984207514389586050
[5]: https://t.co/9WryDgDpER
[6]: https://twitter.com/FFmpeg/status/1983949866725437791?ref_src=twsrc%5Etfw
[7]: https://x.com/FFmpeg/status/1983949866725437791
[8]: https://en.wikipedia.org/wiki/Star_Wars:_Rebel_Assault_II:_The_Hidden_Empire
[9]: https://googleprojectzero.blogspot.com/2024/10/from-naptime-to-big-sleep.html
[10]: https://googleprojectzero.blogspot.com/2025/07/reporting-transparency.html
[11]: https://x.com/FFmpeg/status/1984178359354483058
[12]: https://en.wikipedia.org/wiki/Assembly_language
[13]: https://itsfoss.com/news/open-source-infrastructure-is-breaking-down/
[14]: https://thenewstack.io/ffmpeg-to-google-fund-us-or-stop-sending-bugs/
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-20.png
[16]: https://itsfoss.com/content/images/icon/android-chrome-512x512-19.png
