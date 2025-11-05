[#]: subject: "It's Time to Bring Back GNOME Office (Hope You Remember It)"
[#]: via: "https://itsfoss.com/gnome-office-revival/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

It's Time to Bring Back GNOME Office (Hope You Remember It)
======

[![Warp Terminal][1]][2]

With recent developments, such as the introduction of a [reference operating system][3], the [GNOME project][4] has clearly positioned itself as a full, top-to-bottom computing platform. It has one of the fastest-growing app ecosystems in the Linux and open-source world as a whole and even has an [Incubator][5], providing a path for some apps to join Core via the Release Team. GNOME-adjacent, community-led projects like [Phosh][6] build on this robust ecosystem to deliver their unified vision to other form factors.

Yet, one of the jarringly obvious things the GNOME platform lacks right now is a dedicated office suite that follows its Human Interface Guidelines (HIG) and uses its native technologies. This brings us to the question: Is it time for a resurrection?

### GNOME Office of the past

For those who aren't familiar, it's probably best if we take a step back in history and look at what exactly GNOME Office was — and, technically, still "is" in a loose sense.

![Abiword 3.0.7 editing a .docx file][7]

Back in the days of GNOME 2, circa the early 2000s, there was a loose effort to establish an open-source, GTK-based office suite from the sum of existing parts. **The 1.0 release (September 15, 2003) consisted of** [**AbiWord**][8] **2.0,** [**Gnumeric**][9] **1.2.0, and** [**GNOME-DB**][10] **1.0.** This was a strategy to give the GNOME desktop environment an office suite of its own, easing the transition for users migrating from platforms where the idea of a dedicated office suite was more or less an expectation.

![Gnumeric 1.12.59 with the built-in calendar template][11]

While there was never any subsequent release, in the years that followed, the [GNOME Office wiki][12] (now archived) would come to include other applications under this umbrella, including [Evolution][13] (for mail and groupware), [Evince][14] (for document viewing), [Inkscape][15] (for vector graphics), and [Ease][16] (for presentations, but now abandoned), to name a few.

![Evince the former document viewer for GNOME][17]

All the applications listed there have historically used some version of GTK for their interface and variably used GNOME-associated libraries, such as the [now-deprecated][18] [Clutter][19]. However, none of them were created for inclusion in any official "GNOME Office suite". Rather, they were adopted under this label once it was recognised that they could serve this purpose.

That said, times have changed dramatically since 2003, and with GNOME increasingly pushing for a place among the larger platforms, now might be a great time for a second look. As it stands, two decades later, GNOME has a mature design system ([libadwaita][20]), a clear path for inclusion in the core project, and a solid foundation for a mobile operating system. Yet, except for AbiWord and Gnumeric, which do not fit its current vision, it still lacks robust native applications to fill this niche.

### The case for a revival

Platform coherence is one of the strongest drivers of user loyalty, and a powerful argument for a GNOME-native office suite. Not only would it follow the GNOME HIG and use familiar libadwaita widgets, but it would also integrate with portals and [GNOME Online Accounts][21] (GOA). A native GNOME Office suite would be mobile-ready, able to scale to phones and tablets on Phosh, thereby delivering the same visual language and behaviours as Files, Settings, and the rest of GNOME Core.

This mirrors how macOS has achieved loyalty through consistent UI/UX patterns, despite lacking the broader market dominance of Windows. As GNOME seeks to secure and protect its vision, an initiative of this kind would encourage distro vendors to bundle more tightly integrated, GNOME-native applications in their default application line-ups.

Furthermore, a dedicated office suite would fill the gaps currently existing in this platform. For example, GNOME has [Papers][22] (the replacement for Evince) for _viewing_ documents, and [Document Scanner][23] (formerly Simple Scan) for _scanning_. However, there are no official apps for _editing_ documents.

![Document Scanner \(Simple Scan\)][24]

The situation is even worse for other common office formats like spreadsheets and presentations. Without a third-party suite of applications, there are no official GNOME apps for viewing these documents on a standard GNOME desktop. Most distros resolve this by shipping [LibreOffice][25], which works fine, but is notably heavier and does not fit the GNOME aesthetic.

Sure, users could use AbiWord (which is still maintained, believe it or not), or Gnumeric, but neither of these is aligned to the modern GNOME platform. Both Gnumeric and AbiWord use GTK 3, which is under maintenance, not the modern GTK 4/libadwaita stack. This also doesn't solve the problem of a missing presentation solution. LibreOffice _works_ , but it is not designed to be a "GNOME" application. We'll get into the deeper details of why this matters shortly.

All these things considered, there's great benefit to having a lightweight, native suite that not only _looks_ at home, but plays well with its existing office-related apps, including Calendar, Contacts, Loupe (the image viewer) and Document Scanner.

### Why now?

In the past, the GNOME project was, for the most part, _just_ a desktop environment - a collection of applications and related libraries that provide a defined and reproducible setup for desktop users. Today, the GNOME project is a lot more than this; it prescribes everything from how applications should look and operate to what system libraries and init systems should be used.

There's even an official reference GNOME distribution, GNOME OS, which brings the project from environment to _platform_. At this point, having its own office suite is no longer a fancy "nice-to-have" idea. It's almost essential. An official GNOME reference suite would serve as guidance for other applications looking to target the platform.

### Aren't existing FOSS office suites good enough?

![LibreOffice writer is a powerful, fully-featured document editor, but doesn't fit GNOME's minimalist look][26]

It's only fair to ask this question, and the answer is a mix of yes _and_ no. Both LibreOffice and [ONLYOFFICE][27] provide solid experiences, and the features needed by the average student or professional who may need to do professional work on a modern Linux desktop. Plus, in terms of compatibility with other office suites, like the market-dominant Microsoft Office, both office suites are, for the most part, more than good enough. They are highly compatible with Microsoft's older proprietary formats, and support the ISO open-standard [Office Open XML][28] (OOXML)-based formats. LibreOffice even has (limited) support for Excel macros.

However, both suites are designed independently of the GNOME vision, and as such, do not adhere to its HIG, and do not always play well within the desktop environment. Furthermore, while LibreOffice is the most popular of the two, the user experience with its default interface is, to this day, a matter of controversy. To be fair, the same could be said for ONLYOFFICE, as it follows Microsoft's UI design more closely. It really depends on who you ask.

![ONLYOFFICE is powerful and efficient, but not aligned with GNOME's design][29]

Between the two, LibreOffice is the most widely used across most distros. However, it uses the VCL toolkit for its interface, which has GTK 3/4 backends, but often has notable deficiencies. Work on a GTK 4 plugin for VCL is still ongoing, and the experience using it in GNOME can vary from distro to distro. Furthermore, its interface is admittedly more complex than most GNOME applications and doesn't follow the minimalist guidance that most of them do.

For these reasons, a lightweight, GNOME-focused office suite would actually be better aligned with the project's vision and provide users with a more streamlined experience. It would also allow distributions seeking a purist experience to build upon this vision. For mobile users, it would give them an office suite that's designed for their devices (thanks to libadwaita's strong support for responsive designs). The goal here isn’t to replace LibreOffice or ONLYOFFICE, but rather to _complement_ them with a GNOME-native option that integrates tightly with the platform’s HIG, portals, and mobile ambitions.

### What would it take?

There are two possible avenues for this potential revival, should it ever happen:

  1. **Reviving mature code:** Upgrading AbiWord and Gnumeric to use modern libraries and changing their interfaces to match.
  2. **Using the Incubator:** Creating/adopting new applications to fill these roles within the GNOME project.



Both have their benefits and setbacks, but only one would likely serve the best interests of the project at this time. While converting AbiWord and Gnumeric to GTK4 and libadwaita apps is a possible pathway, the effort involved might be more than it's worth. Not only would both applications need to have their codebases heavily refactored, but their interfaces would need to be changed dramatically. Transitions like these often leave existing users in limbo, and many often don't respond well to removed tools or changed workflows.

This is why the best possible pathway toward a stable GNOME Office platform is to create or adopt new applications into GNOME Core. Under this strategy, a focused trio of applications could enter the GNOME Incubator and, if successful, graduate into the Core with the blessing of the Release Team. Already, there is at least one application that could be a candidate for a future GNOME Office's word processor/document editor: [Letters][30]. Written in Python, this application was [recently released][31] to [Flathub][32], supports the Open Document Text (ODT) format, and follows GNOME's minimalist design.

![Letters is a new, but promising word processor for the GNOME desktop][33]

Like [Calligra Words][34], the word processor from [KDE's office suite][35], it does not support the full gamut of features available with ODT, but for the purpose of providing basic functionality, it's at least sufficient. Also, to be fair, the app is rather new, having been released in October of this year (2025). From a technical standpoint, it uses the Pandoc library, which means it can support a vast array of text documents without any extra dependencies.

![Calligra Words, KDE's word processor][36]

At this time, there seem not to be any equivalent applications for presentations or spreadsheets, but in theory, these applications could be swiftly built on existing libraries. For instance, a presentation editor could be built on GTK4 and libadwaita using odfpy and python-pptx for providing file format support. A spreadsheet editor could be created on top of the same UI libraries and use liborcus and ixion for providing file format support and the underlying logic.

Alternatively, GNOME Office already has useful libraries for building office applications: [libgsf][37] handles structured document I/O (ZIP/OLE2, streams, metadata), while [GOffice][38] provides charting and spreadsheet-oriented utilities (the same stack Gnumeric builds on). Together, they could prove a solid core beneath a GTK4/libadwaita interface.

If these (theoretical) apps were to be written in a popular and accessible language like Python, as with Letters, it's even more likely that the community would be able to take over if, at any time, development were to slow down. Neither app would need to support the full features of their relevant formats. All that the average user needs is to be able to produce simple presentations and spreadsheets with what they have on their system. For those who need full functionality, there's always the option to install and use a fully-featured suite like LibreOffice or ONLYOFFICE.

### Conclusion

Now that GNOME has everything in place to serve as a full platform, it's well-positioned to have first-party answers for documents, spreadsheets, and presentations that fit the GNOME way. A small, native GNOME Office would not replace LibreOffice or ONLYOFFICE. It would sit beside them and cover the basics with a clean, touch-friendly, libadwaita interface that works on laptops, tablets, and phones. The building blocks already exist. At this point, all that is missing is a focused push to turn them into real apps and bring them through the Incubator.

--------------------------------------------------------------------------------

via: https://itsfoss.com/gnome-office-revival/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/gnome-os/
[4]: https://gnome.org
[5]: https://gitlab.gnome.org/GNOME/Incubator
[6]: https://phosh.mobi/about/
[7]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-11-45-39.png
[8]: https://gitlab.gnome.org/World/AbiWord
[9]: https://gnome.pages.gitlab.gnome.org/gnumeric-web/
[10]: https://www.gnome-db.org/
[11]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-11-47-08.png
[12]: https://wiki.gnome.org/Attic/GnomeOffice
[13]: https://gitlab.gnome.org/GNOME/evolution/-/wikis/home
[14]: https://wiki.gnome.org/Apps/Evince
[15]: https://inkscape.org
[16]: https://wiki.gnome.org/Attic(2f)Ease.html
[17]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-11-51-39.png
[18]: https://blogs.gnome.org/clutter/2022/02/16/retiring-clutter/
[19]: https://mutter.gnome.org/clutter/
[20]: https://gitlab.gnome.org/GNOME/libadwaita
[21]: https://gitlab.gnome.org/GNOME/gnome-online-accounts
[22]: https://gitlab.gnome.org/GNOME/papers
[23]: https://gitlab.gnome.org/GNOME/simple-scan
[24]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-11-54-28.png
[25]: https://www.libreoffice.org/
[26]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-11-57-24.png
[27]: https://www.onlyoffice.com/
[28]: https://en.wikipedia.org/wiki/Office_Open_XML
[29]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-12-13-30.png
[30]: https://codeberg.org/eyekay/letters
[31]: https://flathub.org/en/apps/net.codelogistics.letters
[32]: https://flathub.org/en
[33]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-12-05-29.png
[34]: https://calligra.org/components/words/
[35]: https://calligra.org/
[36]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-04-12-08-19.png
[37]: https://gitlab.gnome.org/GNOME/libgsf
[38]: https://gitlab.gnome.org/GNOME/goffice
