[#]: subject: "LibreOffice 24.8 Release Adds a New Privacy Feature"
[#]: via: "https://news.itsfoss.com/libreoffice-24-8-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

LibreOffice 24.8 Release Adds a New Privacy Feature
======
LibreOffice 24.8 is getting better with meaningful improvements.
[![][1]][2]

Many of you may be familiar with [LibreOffice][3], the open-source office suite which is a safe haven for those moving away from the hold of Microsoft Office, a proprietary piece of software.

No doubt, a large chunk of the global population knows and uses MS Office. But, open options such as LibreOffice, ONLYOFFICE, OpenOffice, etc. make it easier for people to access a fully fledged office suite with all the essential features.

After switching to a new version naming scheme earlier this year, LibreOffice now has a new release with important upgrades, including a privacy-focused one.

So, let's check it out. 😃

## 🆕 LibreOffice 24.8: What's New?

The new features in this release were made possible due to **the work of 171 contributors** , with 57% of code commits coming from 49 developers who work for companies on The Document Foundation [advisory board][4].

We start with the **new privacy-focused feature** that allows personal information like author names, timestamps, printer names, editing duration, and configuration to be removed whenever a draft is saved.

![][5]

But, it is **disabled by default**. You can enable it by going into _Tools_ > _Options_ > _LibreOffice_ > _Security_ > _Security Options_ > _Remove personal information on saving_. This should be a great feature for situations where you don't want such details out in public.

On the **editor side of things** , Writer now has a new “Find” deck in the sidebar that allows for easy viewing of quick searches. It can be brought up by using the default _Alt_ \+ _9_ keyboard shortcut.

![][6]

There's also improved support for multi-page floating tables, better rendering of text in CJK writing systems with font fallback, and a fix for an issue with shape positioning in DOCX imports for RTL paragraphs.

After that, there are the **improvements to Calc** , which include things like the newly added support for importing/exporting OOXML pivot table format definitions, better localization of the status bar, and the ability to delete comments using right-click menu.

![][7]

Moreover, you get **new functions** like LET, XLOOKUP, and XMATCH, with better threaded calculation performance, and more flexible choices for comparison operators, as shown above.

**Impress also received many upgrades** , with some interesting ones including a new “Notes Pane” for notes, which, when enabled, will show a collapsible pane just under the slide. It can be enabled from the “ _View_ ” menu.

![][8]

And, lastly, the included bundled templates from the Indonesian community now feature localized placeholders instead of the generic lorem ipsum text, and opening custom shape-heavy PPTX files is now faster.

### 🛠️ Other Changes and Improvements

Then there are the rest of the changes, with some notable ones including:

  * New chart types, “ _Pie-of-Pie_ ” and “ _Bar-of-Pie_ ”.
  * An official package for ARM-based Windows PCs.
  * Support for adding tiling patterns in imported PDF files on Draw.
  * Introduction of a high performing password-based ODF encryption.
  * Chinese and Japanese word selection in Math now being based on [ICU][9] rules.



For more details, you can give the official [release notes][10] a read.

**Suggested Read** 📖

![][11]

### ⚙️ How to Install/Upgrade?

The most straightforward way for getting this release on Linux is to install it from the [Flathub store][12]. For other packages, the [official website][13] is the place to go.

[LibreOffice 24.8][13]

**For existing users** , if you are running the Flatpak, then you can update it from your app store or by running the following command:

```

    flatpak update org.libreoffice.LibreOffice

```

If you went for the _tar.gz_ package, then you should refer to the upgrade instructions mentioned in my [coverage][14] of the earlier LibreOffice 24.2 release.

_💬 Do you like using LibreOffice? Use some other open-source office suite? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/libreoffice-24-8-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.libreoffice.org/
[4]: https://www.documentfoundation.org/advisory-board/
[5]: https://news.itsfoss.com/content/images/2024/08/LibreOffice_24.8_a.png
[6]: https://news.itsfoss.com/content/images/2024/08/LibreOffice_24.8_b.png
[7]: https://news.itsfoss.com/content/images/2024/08/LibreOffice_24.8_c.png
[8]: https://news.itsfoss.com/content/images/2024/08/LibreOffice_24.8_d.png
[9]: https://icu.unicode.org/home
[10]: https://wiki.documentfoundation.org/ReleaseNotes/24.8
[11]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[12]: https://flathub.org/apps/org.libreoffice.LibreOffice
[13]: https://www.libreoffice.org/download/download-libreoffice/
[14]: https://news.itsfoss.com/libreoffice-24-2-is-here/
