[#]: subject: "This Patch Boosts Linux Gaming Performance By 50% and More"
[#]: via: "https://news.itsfoss.com/linux-gaming-boost-driver/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Patch Boosts Linux Gaming Performance By 50% and More
======
This should help the Linux gaming experience thrive.
Back in 2021, a contributor to the [Wine][1] project started out to [build something][2] that would allow for the implementation of the Windows NT synchronization object API into the Linux kernel.

Doing that improved performance for Windows apps on Linux when using Wine or Valve's [Proton][3] that is based on the former. But, progress on that kind of slowed down along the years.

Enter 2024, where that has gotten a major boost by the same person who kick-started it all.

**Elizabeth Figura** who now works for [CodeWeavers][4], posted a patch with “request for comments” (RFC) label in the Linux kernel mailing lists around the end of January. And, this was to introduce a new driver for implementing **Windows NT synchronization primitive** (NTSYNC) directly into the Linux kernel.

She also shared some helpful benchmarks that show **games running better with average improvement rates ranging from 50% to 150%** when using the new driver compared to not using it.

So, let's dive in see and what's in store! 😃

### Windows NTSYNC Primitive: What to Expect?

The need for such a driver arose when it was found that the NT synchronization primitives, a key part of the Windows API emulated by Wine performed **horribly on heavy multithreaded tasks** when an [RPC][5] was made to [_wineserver_][6].

This resulted in a bottleneck that caused many apps and games to not run to their full potential, causing a wide variety of slowdowns, bugs and what not.

![An image of a game launcher on Linux][7]

On an older kernel mailing list post, Elizabeth mentioned that:

> In recent years applications, especially high-performance games, have made heavy use of multiple threads, and consequently heavy use of these synchronization primitives.

> The RPC to the wineserver has become not just a bottleneck, but a heavy bottleneck. It's particularly a problem because the server is single-threaded and can only service one request at a time.

The issue of the NT synchronization APIs was it being tricky to implement on top of the existing primitives “ _without sacrificing correctness_ ”. So, a solution to resolve the issue was the need of the hour.

She also clarified the technical bits for developers:

> _Operations like NtPulseEvent() or the “wait-for-all” mode of NtWaitForMultipleObjects() would require better control to work properly, and that is not possible without a solution._

That is where the Windows NTSYNC primitive driver aims to deliver by acting as a new character device for implementing “ _problematic interfaces_ ” directly into the Linux kernel.

I promise I won't go more into the tech bits meant for developers 😅

So, here are **some benchmarking numbers** that ought to make it simpler for you. These tests were done on various hardware running games, both old and new, with and without the new driver being active.

The results look quite promising if you ask me:

![][8]

If these numbers are any indication, then **Windows-only apps and games should run better than ever before when using Wine** or other Wine-based derivatives.

I can't wait to see when this is implemented into the Linux kernel. But, after reading all that, you're maybe wondering; **when will this become a reality?**

Well, it will take some time as this is **still subject to approval from the maintainers and Linus Torvalds himself** ; if he chooses to look at it more closely.

For now, you can only wait and see whether this change is approved in time for any of the upcoming Linux kernel releases.

For staying up to date with the status and to learn more about the Windows NTSYNC primitive driver, you can refer to the [mailing list][9].

_💬 What do you think of the new driver? Share your thoughts!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-gaming-boost-driver/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.winehq.org/
[2]: https://lore.kernel.org/lkml/f4cc1a38-1441-62f8-47e4-0c67f5ad1d43@codeweavers.com/
[3]: https://itsfoss.com/steam-play-proton/
[4]: https://www.codeweavers.com/
[5]: https://en.wikipedia.org/wiki/Remote_procedure_call
[6]: https://wiki.winehq.org/Wineserver
[7]: https://news.itsfoss.com/content/images/2024/02/bottles-next-ui.jpg
[8]: https://news.itsfoss.com/content/images/2024/02/NTSYNC_Benchmarks.png
[9]: https://lore.kernel.org/lkml/20240219223833.95710-1-zfigura@codeweavers.com/
