[#]: subject: "Fedora 44 is Replacing Decades-Old Kernel Console with Safer, Modern Alternative"
[#]: via: "https://itsfoss.com/news/fedora-replacing-kernel-console/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora 44 is Replacing Decades-Old Kernel Console with Safer, Modern Alternative
======

[![Warp Terminal][1]][2]

[Fedora][3] is known for pushing boundaries when it comes to adopting new tech, almost always staying near the bleeding edge of what's currently available. The project doesn't really wait around for things to become " _accepted_ " before jumping in.

That approach now continues as the Fedora Engineering Steering Committee (FESCo) [just gave the green light][4] to replace a very old system component with something more modern.

### What's Happening?

Fedora 44 is ditching [fbcon][5], the kernel framebuffer console, in favor of [kmscon][6], a more modern userspace console based on [Kernel Mode Setting][7] (KMS).

If you have ever pressed `Ctrl+Alt+F2` on your Linux computer and seen a full-screen text interface, that's what we are talking about. It is also the same text-only screen that shows up when you boot up your system.

Currently, **the old console runs inside the kernel itself**. The new approach moves it to [userspace][8], where regular programs live instead of deep in the sensitive core.

### Why the Change?

[Jocelyn Falempe][9], who came up with [this proposal][10], laid out some very good reasons for this. The first one is obvious, **fbcon is showing its age**. It lost scrolling support years ago when developers had to yank the feature due to a security bug.

It still relies on `fbdev` emulation, even though modern GPU drivers moved to the newer [DRM][11] interface. This creates an unnecessary component that shouldn't be there.

Then there is **the security issue**. fbcon runs in kernel space, so when it crashes, your whole system goes down with a [kernel panic][12]. This makes recovering a system painful.

### What to Expect?

kmscon brings back what fbcon left out. Scrolling works again. Keyboard handling is considerably better with [xkbcommon][13] support. Multiple layouts, proper shortcuts, and more are included.

There is also **the ability to change fonts, use more Unicode characters** , and the keyboard layout is mirrored with what a user has on their graphical environment.

Don't worry about things breaking. If kmscon gives out, your system falls back to the old [Getty][14]/fbcon setup automatically. You can switch back yourself too if needed.

The end game is to eventually do away with both fbcon and fbdev emulation completely. If Fedora pulls this off without issues, other distros could probably follow along soon.

You can go through the conversation surrounding this change on [Fedora Discussion][15].

Via: [Phoronix][16]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/fedora-replacing-kernel-console/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.fedoraproject.org/
[4]: https://pagure.io/fesco/issue/3513
[5]: https://docs.kernel.org/fb/fbcon.html
[6]: https://github.com/kmscon/kmscon
[7]: https://www.kernel.org/doc/html/v4.15/gpu/drm-kms.html
[8]: https://en.wikipedia.org/wiki/User_space_and_kernel_space
[9]: https://gitlab.com/kdj0c
[10]: https://fedoraproject.org/wiki/Changes/UseKmsconVTConsole
[11]: https://en.wikipedia.org/wiki/Direct_Rendering_Manager
[12]: https://en.wikipedia.org/wiki/Kernel_panic
[13]: https://xkbcommon.org/
[14]: https://en.wikipedia.org/wiki/Getty_(software)
[15]: https://discussion.fedoraproject.org/t/f44-change-proposal-usekmsconvtconsole-systemwide/172602
[16]: https://www.phoronix.com/news/Fedora-44-Approved-KMSCON
