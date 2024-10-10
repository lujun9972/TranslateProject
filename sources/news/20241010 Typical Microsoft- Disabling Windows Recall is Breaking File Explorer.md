[#]: subject: "Typical Microsoft! Disabling Windows Recall is Breaking File Explorer"
[#]: via: "https://news.itsfoss.com/microsoft-windows-recall/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Typical Microsoft! Disabling Windows Recall is Breaking File Explorer
======
This is what some users have spotted and I am not surprised.
[![][1]][2]

Earlier this year, we were caught off-guard by [Microsoft][3] when they came up with a [creepy move][4] to spy on users with a new AI-powered feature called [Recall][5].

When active, **the feature takes snapshots of the screen a user is working on** , to then catalog it, and serve for later fetching as a scrollable timeline. It was supposed to be disabled by default, but, [it appears][6], Microsoft has gone back to enabling it by default.

The [24H2 release][7] **installs Recall on all PCs** , not just Copilot+ PCs. But, that's not all. Recall also breaks an important Windows feature if someone tries to remove it.

### Disabling Recall Breaks Important Functionality

![Source: InvisibleRasta][8]

Even though there is now [a way][9] to uninstall Recall from Windows 11 PCs, Microsoft doesn't seem to have any plans to make the process an easy one.

Spotted by [Chris Titus][10] on a project he works on, a person [posted][11] their plight on the GitHub repo of [Windows Utility][12] ( _winutil_ ). They explained how a Windows Pro 24H2 ISO created using MicroWin was downgrading the [File Explorer][13] to an older one.

If you didn't know, Windows Utility is a handy tool that **helps people get rid of the unnecessary bloatware and features** that a Windows release usually ships with. Similarly, MicroWin is used to create custom Windows images with tweaks according to one's preferences.

After some back and forth between the original poster and some contributors, it was found that **Recall and Copilot were required to run the new File Explorer**. Before you ask, the new one is the one that provides multi-tab functionality, and Copilot is an [important component][14] of Recall.

This was not the case with the [23H2 release][15], as Chris points out in his [video][16]. **Microsoft has made this change in a very sneaky manner** ; the release blog for 24H2 ( _linked above_ ) doesn't mention a single word about this.

To address the issue with File Explorer when using winutil or MicroWin, a contributor, [CodingWonders][17], made some [fixes][18], where the Recall components were kept intact and were disabled only after a user logged in.

But, for other users, **this is something to be concerned about**. If Microsoft is keeping Recall tied to an essential service like File Explorer, that too without talking about it anywhere, what else are they baking Recall into?

**Suggested Read** 📖

![][19]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/microsoft-windows-recall/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.microsoft.com/
[4]: https://news.itsfoss.com/microsoft-windows-creepy-ai-move/
[5]: https://support.microsoft.com/en-us/windows/retrace-your-steps-with-recall-aa03f8a0-a78b-4b3e-b0a1-2eb8ac48701c
[6]: https://x.com/christitustech/status/1844020075915096169
[7]: https://blogs.windows.com/windowsexperience/2024/10/01/how-to-get-new-experiences-for-windows-11/
[8]: https://news.itsfoss.com/content/images/2024/10/Scummy_Microsoft.png
[9]: https://www.windowscentral.com/software-apps/windows-11/how-to-disable-windows-recall#:~:text=HOW%20TO%20DISABLE%20WINDOWS%20RECALL
[10]: https://christitus.com/
[11]: https://github.com/ChrisTitusTech/winutil/issues/2697
[12]: https://github.com/ChrisTitusTech/winutil
[13]: https://www.microsoft.com/en-us/windows/tips/file-explorer
[14]: https://learn.microsoft.com/en-us/windows/ai/apis/recall
[15]: https://blogs.windows.com/windowsexperience/2023/10/31/how-to-get-the-windows-11-2023-update/
[16]: https://www.youtube.com/watch?v=G9FRadIkkE0&t=225s
[17]: https://github.com/CodingWonders
[18]: https://github.com/ChrisTitusTech/winutil/pull/2853/commits/775e9c704ba4467dbc4af3f3b05a4708966dd3f1
[19]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
