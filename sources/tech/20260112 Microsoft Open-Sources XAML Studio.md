[#]: subject: "Microsoft Open-Sources XAML Studio"
[#]: via: "https://itsfoss.com/news/microsoft-open-sources-xaml-studio/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft Open-Sources XAML Studio
======

[![Warp Terminal][1]][2]

Microsoft has [open-sourced XAML Studio][3], a visual development tool for building Windows application interfaces. The project is now available on [GitHub][4] under **the MIT license** and has joined the [.NET Foundation][5] as a seed project.

It is a rapid prototyping tool that lets developers design and test Windows app interfaces using [XAML][6], the markup language for WinUI, before they integrate the work into [Visual Studio][7].

Think of it like [Qt Design Studio][8] for Qt applications, but specifically for Windows apps. It provides live editing, meaning you can see your interface changes in real time without needing to recompile your application.

**As for what you can expect** , XAML Studio 1.1 is available on the [Microsoft Store][9] right now with goodies like a binding debugger, [IntelliSense][10] for code completions, a data context editor, auto-save and restore document functionality, and alignment guides.

But beyond that, the developers have **a 2.0 release in the works** that can be built from source on GitHub right now.

![The upcoming V2 interface for XAML Studio as shared by the developers.][11]

This is **a complete interface overhaul** using [Fluent UI][12]. The redesign makes the tool look and feel more modern, matching the current Windows design language. The layout has been restructured to accommodate new panels and tools.

On the features side, XAML Studio 2.0 adds a properties panel that brings together the visual tree navigation, visual state management, and property editing in one place. There is also something called [Adorners][13] that lets you highlight element boundaries and work on precise layouts.

There is some work pending too. Many of **the 2.0 features are still experimental** and early in their development cycle. The developers are looking to improve these and stabilize the code, with some larger changes still needed to fully support the new features as well as WinUI 3.

Once everything is ready, they plan to push an official stable release of 2.0 to the Microsoft Store sometime later in 2026. And, to wrap this up, according to [Michael Hawker][14], the project lead for XAML Studio, **the tool was meant to be open source from the beginning**.

_Better late than never, I guess._ 😅

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/microsoft-open-sources-xaml-studio/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://devblogs.microsoft.com/ifdef-windows/xaml-studio-is-now-open-sourced/
[4]: https://github.com/dotnet/XAMLStudio
[5]: https://dotnetfoundation.org/
[6]: https://learn.microsoft.com/en-us/dotnet/desktop/wpf/xaml/
[7]: https://visualstudio.microsoft.com/
[8]: https://www.qt.io/development/ui-design-tools
[9]: https://apps.microsoft.com/detail/9ntls214tkmq
[10]: https://code.visualstudio.com/docs/editing/intellisense
[11]: https://itsfoss.com/content/images/2026/01/xaml-studio-2-0-pre-release.png
[12]: https://developer.microsoft.com/en-us/fluentui
[13]: https://github.com/CommunityToolkit/Labs-Windows/pull/760
[14]: https://www.linkedin.com/in/michaelahawker/
