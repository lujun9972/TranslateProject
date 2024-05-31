[#]: subject: "Microsoft Makes Windows Subsystem for Linux Easy With These Updates"
[#]: via: "https://news.itsfoss.com/wsl-upgrades/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft Makes Windows Subsystem for Linux Easy With These Updates
======
More added convenience to WSL.
[![][1]][2]

Fresh off their [creepy move to spy][3] on everything users do, in a recent blog post, Microsoft revealed information on how they intend to take WSL forward in 2024.

For those not familiar, [Windows Subsystem for Linux][4] (WSL) is a feature that allows users to run a Linux environment inside a Windows-equipped system while also doing away with the need to configure a separate virtual machine or dual-boot setup.

Ever since its launch back in 2016, WSL has grown considerably, with it being able to garner the interest of many users, including individual developers and enterprises.

Let's see what they have planned for WSL in 2024.

### Significant Upgrades in Store for WSL

Announced during this year's [Build Conference][5], Microsoft has laid out plans for WSL that feature many interesting improvements.

We start off with a **new GUI settings application for WSL** , which will let users customize their WSL instance. There are options to change the logical processor count, the available memory, the swap size, and the swap file location.

Just like a [virtualization software][6] lets us do.

![][7]

When introduced, there won't be a need to edit the _.wslconfig_ file to manage WSL settings; doing so also **prevents any potential breakage** that could be caused by misconfiguration.

Of course, the config file is not going anywhere; users can use both the GUI app and the config file to make tweaks to their WSL setup.

Then there's the various upcoming upgrades, like the automatic release of stored memory in WSL back to Windows, better networking, and management of WSL in [Dev Home][8].

On the security side of things, there's support for WSL 2 on [Microsoft Defender for Endpoint][9], many new [Intune][10] features, and integration with [Microsoft Entra ID][11].

All these improvements ought to make WSL more user-friendly and capable for both new users and experienced users alike.

If you would like to learn more about the upcoming improvements to WSL, you can refer to the official [Windows Command Line][12] blog.

**Suggested Read** 📖

![][13]

_What do you think of these changes? Let me know your thoughts!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/wsl-upgrades/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/microsoft-windows-creepy-ai-move/
[4]: https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux
[5]: https://build.microsoft.com/en-US/home
[6]: https://itsfoss.com/virtualization-software-linux/
[7]: https://news.itsfoss.com/content/images/2024/05/WSL_GUI_Settings.jpg
[8]: https://github.com/microsoft/devhome
[9]: https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint
[10]: https://www.microsoft.com/security/business/microsoft-intune
[11]: https://www.microsoft.com/security/business/identity-access/microsoft-entra-id
[12]: https://devblogs.microsoft.com/commandline/whats-new-in-the-windows-subsystem-for-linux-in-may-2024/
[13]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
