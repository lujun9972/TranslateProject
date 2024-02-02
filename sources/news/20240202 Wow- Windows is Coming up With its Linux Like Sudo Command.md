[#]: subject: "Wow! Windows is Coming up With its Linux Like Sudo Command"
[#]: via: "https://news.itsfoss.com/sudo-on-windows/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Wow! Windows is Coming up With its Linux Like Sudo Command
======
Yes! You read that right. A leak shows a sudo utility for Windows
operating system.
Back when [running Linux Apps in Windows][1] became a reality and Systemd was [made available][2] for WSL, many users were hyped about the possibilities that could come out of such levels of interoperability.

But, that momentum kind of died down over the years. Luckily, that hype train is going to get started real soon thanks to a recent development that shows **sudo being offered on Windows**.

If you are not familiar, [sudo][3] is a command that effectively allows users to run programs with the security clearance of an administrator.

So, let's begin without any further ado!

### Sudo on Windows: What to Expect?

![Pic Credits: Windows Latest][4]

Spotted first by [Windows Latest][5] on a leaked Windows Server preview build that was accidentally pushed to the Windows 11 Update servers last week, there was a dedicated setting called “Enable sudo” in the System settings.

As you can see above, there are **three distinct options available** on how sudo may run apps when you enable it on Windows. The first is to open apps in a new window; most likely a terminal window, the second one is with input disabled; possibly to prevent any unwanted actions during command execution.

And, the third one is to execute a command in the current window; without opening a new window.

![Pic Credits: Windows Latest][6]

If you were to choose any one of those, then a warning would pop up, saying that running sudo can expose your device and personal data to security risks or harm your device.

After enabling, you should be able to run sudo commands from PowerShell, the Command Prompt, or any other terminal emulator for Windows.

**But, there's a catch**. As of writing, we don't really have a concrete date as to when support for sudo will be introduced into the stable builds of Windows, and whether it will be shipped as part of the upcoming [Windows 11 24H2][7] update or not.

Only time will tell how Microsoft intends to implement sudo into Windows, and whether it would be made available for everyone, or will be an opt-in affair.

_💬 Well, I didn't expect this day to come, but, it's coming. Were you expecting this?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/sudo-on-windows/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/run-linux-apps-windows-wsl/
[2]: https://news.itsfoss.com/systemd-wsl/
[3]: https://www.sudo.ws/
[4]: https://news.itsfoss.com/content/images/2024/02/Windows_Sudo_a.jpg
[5]: https://www.windowslatest.com/2024/02/01/first-look-windows-11-is-getting-native-macos-or-linux-like-sudo-command/
[6]: https://news.itsfoss.com/content/images/2024/02/Windows_Sudo_b.jpg
[7]: https://www.windowscentral.com/software-apps/windows-11/windows-11-version-24h1-changelog-release-date-features-ai-2024-update
