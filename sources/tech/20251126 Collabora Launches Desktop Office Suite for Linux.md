[#]: subject: "Collabora Launches Desktop Office Suite for Linux"
[#]: via: "https://itsfoss.com/news/collabora-launches-desktop-office-suite/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Collabora Launches Desktop Office Suite for Linux
======

[![Warp Terminal][1]][2]

[Collabora Productivity][3] is well-known for two of its flagship offerings, [Collabora Online][4], their web-based document editor that powers many organizations, and their LibreOffice-based enterprise suite. That second one just got a makeover and the existing offering was moved to a new name.

They announced [Collabora Office for desktop][5] today. It brings their online editor's interface to local **desktop apps for Linux, Windows, and macOS**. The previous enterprise suite is now called **Collabora Office Classic**.

### Collabora Office: What's Fresh?

![From left to right: Writer, Impress, and Calc. Click to expand.][6]

The new suite covers the basics like word processing, spreadsheets, presentations, and vector graphics. You get **Writer** for documents, **Impress** for presentations, and **Calc** for spreadsheets. But the way it is all put together is quite different.

**Under the hood, it uses LibreOffice's core technology, but the interface is where things get interesting.** Instead of relying on VCL, they built it with JavaScript, CSS, WebGL, and Canvas.

There is **no Java dependency** either. The result is a smaller download that installs cleanly. Everything you need comes in one package.

File compatibility looks good too. Microsoft Office formats like _DOCX_ , _XLSX_ , and _PPTX_ work as expected. [OpenDocument][7] formats are obviously supported as well.

During my brief use of it, the interface felt modern with a familiar tabbed layout and easy-to-use toolbars. The developers mention that **they have simplified the defaults and settings compared to typical desktop office apps**. This should result in less clutter and more productivity for people who use Collabora Office daily.

Speaking on this, [Michael Meeks][8], the CEO of Collabora Productivity, added that:

> We’re excited to bring a first release of Collabora Office to the desktop, letting desktop users work both on-line and off-line in comfort. We look forward to working with and gaining valuable feedback from our partners, customers, users and community.

### Similar to LibreOffice, Yet Different

Both products use the same [LibreOffice][9] foundation. But that's where the similarities end. The new one mimics Collabora Online's web interface using JavaScript and CSS. Classic sticks with the traditional [VCL][10]-based desktop interface that longtime LibreOffice users will know well.

Classic includes the [Base][11] database app with its Java components. The new version skips Base entirely and drops the Java requirement.

Macros work on both, but differently. Classic gives you full editing capabilities with BASIC, Python, and UNO support. The new version just runs macros, no advanced tools.

**For business users** , the support difference will matter the most. Classic has long-term enterprise support available now. The new Collabora Office is a fresh release that isn't yet tailored for enterprise deployment.

Collabora is working on bringing enterprise support to the new suite. They expect to have it ready **sometime in 2026**. Until then, organizations needing production-ready support should stick with Classic.

### Download Collabora Office

You can grab Collabora Office from the [official website][12]. The suite is available as a _Flatpak_ for **Linux** , an _appx_ file for **Windows 11** , and an app bundle for **macOS 15 Sequoia** or later.

If you need help with deployment or documentation, you can check out the [support page][13] for the relevant resources. The source code is available on [GitHub][14].

[Collabora Office][12]

**Suggested Read 📖**

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/collabora-launches-desktop-office-suite/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.collaboraonline.com/
[4]: https://www.collaboraonline.com/collabora-online/
[5]: https://www.collaboraonline.com/blog/press-release-bringing-collabora-online-to-the-desktop/
[6]: https://itsfoss.com/content/images/2025/11/collabora-office-writer.png
[7]: https://itsfoss.com/news/odf-1-4-release/
[8]: https://www.linkedin.com/in/michael-meeks-8a6b2151/
[9]: https://www.libreoffice.org/
[10]: https://docs.libreoffice.org/vcl.html
[11]: https://www.libreoffice.org/discover/base
[12]: https://www.collaboraonline.com/collabora-office/
[13]: https://www.collaboraonline.com/engineering-support/
[14]: https://github.com/CollaboraOnline
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-50.png
