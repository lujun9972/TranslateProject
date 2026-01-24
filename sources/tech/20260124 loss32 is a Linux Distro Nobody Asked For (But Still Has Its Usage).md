[#]: subject: "loss32 is a Linux Distro Nobody Asked For (But Still Has Its Usage)"
[#]: via: "https://itsfoss.com/loss32-distro/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

loss32 is a Linux Distro Nobody Asked For (But Still Has Its Usage)
======

[![Warp Terminal][1]][2]

loss32, or, as it is called by its creator, _Win32 plus Linux_ , is an upcoming Linux distribution where the entire desktop environment is [Win32 software][3] that runs under [Wine][4].

It sounds absurd on paper but seems to be following a very different approach than usual, where **a fully functional desktop with the Windows Classic theme** runs on [Debian 13][5]. As you can see in the screenshot below, loss32 appears to be able to run a _Paint_ application, a file explorer, a terminal, and a taskbar.

![Original screenshot courtesy of hikari_no_yume.][6]

The project makes it a point to differentiate itself from others like [ReactOS][7], which, as the developer notes, tries to reimplement the [Windows NT][8] kernel and has struggled with hardware compatibility and stability.

But **loss32 does take some components from ReactOS** , most notably the [user space][9] ones, to achieve a similar desktop experience while making use of a more practical foundation comprised of Linux and Wine to bring it all together.

This is the brainchild of [hikari_no_yume][10], who wants to preserve the late 90s to early 2010s PC desktop experience that was beloved by power users.

She also argues that a desktop environment where everything runs inside Wine **would create strong incentives to improve Wine for everyone** , addressing the rough edges people currently tolerate only as a last resort.

The most interesting ( _albeit a bit spicy_ ) motivation the dev shares is that **Win32 is the stable Linux ABI**. By which she means that there are over three decades of Win32 software that can still run in Wine or on Windows, with no other [ABI][11] matching such compatibility standards.

Before you dive in, know that **the developer is still working on shipping an initial proof-of-concept**. They had mentioned a release timeline of January 2026, so there's only a few more days to go.

Once ready, loss32 is meant to be very easy to install through a package repository. From there, you can download and run `.exe` files directly. In the meantime, you can keep an eye out on the [project homepage][12] for updates on the initial release of loss32.

[loss32][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/loss32-distro/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://learn.microsoft.com/en-us/windows/win32/
[4]: https://www.winehq.org/
[5]: https://itsfoss.com/news/debian-13-release/
[6]: https://itsfoss.com/content/images/2026/01/loss32.png
[7]: https://reactos.org/
[8]: https://en.wikipedia.org/wiki/Windows_NT
[9]: https://en.wikipedia.org/wiki/User_space_and_kernel_space
[10]: https://hikari.noyu.me/
[11]: https://en.wikipedia.org/wiki/Application_binary_interface
[12]: https://loss32.org/
