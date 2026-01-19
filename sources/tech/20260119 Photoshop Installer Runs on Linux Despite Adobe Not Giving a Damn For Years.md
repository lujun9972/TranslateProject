[#]: subject: "Photoshop Installer Runs on Linux Despite Adobe Not Giving a Damn For Years"
[#]: via: "https://itsfoss.com/news/photoshop-installer-runs-on-linux/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Photoshop Installer Runs on Linux Despite Adobe Not Giving a Damn For Years
======

[![Warp Terminal][1]][2]

Creatives on Linux have just [a handful of Adobe Photoshop alternatives][3] to pick from, and while they are good, most people just can't move away from Adobe's [Creative Cloud][4] (CC).

I say this with confidence because whenever we post a Linux-focused QnA or " _switch to Linux today_ " type of post [on our socials][5], we see people complaining how Adobe's software doesn't run on the platform. This is their main justification for sticking with Windows or macOS, btw.

Sadly, there's not much anyone other than [Adobe][6] can do on this matter, or so we thought.

### What's Happening?

0:00

/0:47

1×

__Source:__ [__PhialsBasement__][7] __(the video is very lossy).__

A developer who goes by the username [PhialsBasement][8] has [made patches for Wine][7] that address the issue of Adobe CC not working on Linux. Basically, he fixed how [Wine][9] handles some JavaScript and XML code that Adobe's installers use.

This has been tested with the installers for Photoshop 2021 and 2025, with these patches being submitted to Valve's [bleeding-edge fork of Wine][10]. But, as Valve's Kisak [points out][11], **these changes first need to be submitted to Wine** [upstream][12], and if it is accepted there, it could be backported to [Proton][13].

Posting [an update][14] to the above, the developer has revealed that he also got Adobe's Collection installer running via their Wine patch. **Most Adobe apps can be installed now** , with Adobe [XD][15] and [Fresco][16] being the only ones that don't work since they are [UWP][17] apps.

If you want to try this, you will have to grab the pre-built binaries from the developer's [GitHub][18]. Also, the installation experience is one thing, but running the apps themselves is another, so keep that in mind.

And while **it's still early to say whether this will make it into Wine officially** , this should rekindle some hope for Linux users and users-to-be who have been missing Adobe's creative suite on the platform.

* * *

**Suggested Read 📖:** [_Free and Open Source Alternatives to Adobe Photoshop_][3]

![][19]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/photoshop-installer-runs-on-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/open-source-photoshop-alternatives/
[4]: https://www.adobe.com/creativecloud.html
[5]: https://itsfoss.com/#:~:text=Guides%20%F0%9F%93%92-,Social,-Facebook
[6]: https://www.adobe.com/
[7]: https://www.reddit.com/r/linux_gaming/comments/1qdgd73/i_made_adobe_cc_installers_work_on_linux_pr_in/
[8]: https://github.com/PhialsBasement
[9]: https://www.winehq.org/
[10]: https://github.com/ValveSoftware/wine/pull/310
[11]: https://github.com/ValveSoftware/wine/pull/310#issuecomment-3754971501
[12]: https://gitlab.winehq.org/wine/wine
[13]: https://github.com/ValveSoftware/Proton
[14]: https://www.reddit.com/r/linux_gaming/comments/1qgybfy/update_on_the_adobe_cc_installers_patch_now_the/
[15]: https://en.wikipedia.org/wiki/Adobe_XD
[16]: https://www.adobe.com/products/fresco.html
[17]: https://learn.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide
[18]: https://github.com/PhialsBasement/wine-adobe-installers/
[19]: https://itsfoss.com/content/images/icon/android-chrome-512x512-226.png
