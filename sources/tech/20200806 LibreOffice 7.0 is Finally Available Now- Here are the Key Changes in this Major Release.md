[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (LibreOffice 7.0 is Finally Available Now! Here are the Key Changes in this Major Release)
[#]: via: (https://itsfoss.com/libreoffice-7-release/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

LibreOffice 7.0 is Finally Available Now! Here are the Key Changes in this Major Release
======

LibreOffice 7.0 is the latest major release after version 6.4. There are plenty of additions to improve the LibreOffice experience.

In this article, I’ll share some details on the key changes on LibreOffice 7 and how to get it.

![][1]

### LibreOffice 7: Key Changes

As mentioned, LibreOffice 7 does not introduce major new features but several improvements contributing to a major release. Here, I’ve highlighted the features that I think are important:

#### Visual Changes

![][2]

Don’t expect an overhaul — but you will find the addition of a new icon theme **Sukapura**. It looks similar to Apple’s color palette in macOS.

So, if you’re using LibreOffice in macOS or just want that look and feel, you can utilize this new theme.

You may also observe some new icons and banners when installing LibreOffice (depending on the platform you’re using it).

#### Changes to LibreOffice Calc

It’s good to see new spreadsheet functions “**RAND.NV()**” and “**RANDBETWEEN.NV()**” which are non-volatile random number generating functions that does not get affected by updates on other cell. Previously, RAND/RANDBETWEEN functions were being re-calculated whenever a new value was added to any other cell — which was not convenient.

Some of the spreadsheet functions like TEXT() and OFFSET() had issues with how it worked. The TEXT() function now allows the second argument to be an empty string and the OFFSET() function now has a rule of allowing value greater than 0 for width &amp; height parameter.

Even though these are minor improvements, it fixes a lot of issues for the users who rely on these functions.

#### Changes in LibreOffice Writer

The added support for padded numbering, improvements to the auto-correct feature, and support for semi-transparent texts are some of the key highlights for the changes coming to LibreOffice Writer.

You will also find some minor improvements like highlighting the invisible fields with gray area for better visibility when editing.

Not to forget, the [Navigator][3] also received a couple of improvements to make it more useful and accurate.

#### Changes to LibreOffice Impress &amp; Draw

You now have the support for semi-transparent texts on Draw/Impress. Also, Draw supports page sizes larger than 200″ (508 cm) when exporting a PDF, they’ve removed the limit.

There are also performance improvements here when you work with animations, table editing mode, and PPT file load speed.

#### Accessibility Improvements

![][4]

An accessibility check tool has been introduced to make sure that the documents are more accessible before exporting it.

#### Vulkan Support

The switch from [Cairo library][5] for rendering to [Skia graphics library][6] now allows optional GPU-based Vulkan acceleration support which should improve the performance as well.

#### ODF 1.3 Support

With the latest release, you can now export to new versions of [ODF][7] that includes ODF 1.3 as well. You can also find the previous versions — but it’s recommended to use ODF 1.3

#### Improvements to DOCX Export

To improve compatibility for users with files from different versions of Microsoft Office, DOCX now saves in 2013/2016/2019 mode instead of the 2007 compatibility mode. Also, the support for glow effects on objects and some other minor improvements should make the experience better when working with DOCX files.

#### Help Page improvements

No major overhaul here — but you will find some basic syntax diagrams (more than ever) and the help pages have different colors for modules.

Help page is not something everyone cares about, but updating the accuracy of it and adding more information is always a good thing.

#### Other Improvements

You will find improvements to proof-reading tools, language support, scripting, configuration options, and several other stuff.

To get all the details for what has changed, you can refer to the [official release notes of LibreOffice 7.0.][8]

### Download LibreOffice 7.0

Your Linux distributions may take some time to provide you the latest LibreOffice 7 version.

For Ubuntu-based distributions, there is an official PPA but version 7.0 is not available via this PPA yet. I’ll update the article with the instructions when it is available.

For now, if you really want to use it, you can download the DEB/RPM installer files from the official download page.

[Download LibreOffice 7.0][9]

I am glad that [LibreOffice removed the ‘Personal Edition’ labelling][10] it was bound to create controversy.

What do you think of the changes in LibreOffice 7.0? Let me know your thoughts in the comments below!

--------------------------------------------------------------------------------

via: https://itsfoss.com/libreoffice-7-release/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/libreoffice-7.png?ssl=1
[2]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/libreoffice-sukapura-theme.png?ssl=1
[3]: https://help.libreoffice.org/6.4/en-US/text/scalc/01/02110000.html?DbPAR=CALC
[4]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/libreoffice-accessibility.png?ssl=1
[5]: https://wiki.documentfoundation.org/ReleaseNotes/7.0#Writer
[6]: https://skia.org/
[7]: https://en.wikipedia.org/wiki/OpenDocument
[8]: https://wiki.documentfoundation.org/ReleaseNotes/7.0#Impress_.26_Draw
[9]: https://www.libreoffice.org/download/download/
[10]: https://itsfoss.com/libreoffice-personal-edition-issue/
