[#]: subject: "LibreOffice 24.2 is Here!"
[#]: via: "https://news.itsfoss.com/libreoffice-24-2-is-here/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

LibreOffice 24.2 is Here!
======
A packed LibreOffice upgrade has arrived with a new version naming
scheme.
LibreOffice, the [best open source alternative to Microsoft Office][1], has announced a new release with a change in how the versions are named.

Going forward, they will now **follow a calendar-based version numbering scheme** , with the “ _YY.M_ ” format; So, in line with that, the new release is called **LibreOffice 24.2,** where 24 denotes the year 2024, and 2 denotes the month, February.

The last release that followed the older naming scheme was [LibreOffice 7.6][2].

Of course, the new version numbering is not the only change with this release, join me as I take you through this release, and what it has to offer.

**Suggested Read** 📖

![][3]

### LibreOffice 7.6: What's New?

With **over 160 contributors** working on the new features of LibreOffice 24.2, this release is extensive with many improvements.

Some **key highlights** include:

  * **Improved Security**
  * **Editor Improvements**
  * **Better Compatibility with MS Office**



#### Improved Security

![][4]

When adding passwords to documents, **the password dialog now shows a password strength meter** that uses [zxcvbn-c][5] to show the strength of an entered password.

Then there's **a new password-based ODF encryption** that works faster, hides metadata better, and has been hardened to better resist brute force attacks and tampering.

![][6]

#### Editor Improvements

![][7]

**In the case of Writer** , the word processor for LibreOffice, **you can now use styles with comments** that make it easier to distinguish multiple comments, with the Comment paragraph style being the default one.

There are **updates to the multipage floating table support** too, with improvements to overlap control, footnotes, borders, nesting, and more.

![][8]

**In the case of Calc** , the spreadsheets app for LibreOffice, you can now highlight the Row and Column for the active cell for better pinpointing a piece of data in a sea of cells.

There is also **a new search field** in the Functions sidebar deck for quick access to the various functions on Calc, and **support for the scientific number format** that can be saved in ODF.

![][9]

**In the case of Impress** , the presentation app for LibreOffice, **support for** [**small caps**][10] **has been added** , this will be handy for those who prefer using such characters in their text.

Additionally, the settings for Presenter Console and Remote Control have been moved to _Slideshow > Slide Show Settings_, with tweaks done to the labelling and dialog layout.

#### Better Compatibility with MS Office

With LibreOffice 24.2, **users can take advantage of improved compatibility with the Microsoft Office suit**. ****

You can expect things such as improvements to first page headers/footers [OOXML][11] import in Writer, optimized templates for Japanese text, support for the SVG OOXML extension, and more.

#### 🛠️ Other Changes and Improvements

As for the rest, here are some other changes worth noting:

  * Improvements to how mouse positions are handled.
  * Saving AutoRecovery information is now enabled by default.
  * Better status bars in dialog menus that now report the correct accessible role for better screen reader support.
  * Various fixes to the NotebookBar options, that include menu improvements, better radio buttons, better print preview support, etc.



The LibreOffice 24.2 release comes close on the heels of the recently released [ONLYOFFICE Docs 8.0][12], and is a packed one at that. You can go through the official [announcement blog][13] to learn more about it.

#### ⚙️ How to Install/Upgrade?

You can get the latest release of LibreOffice from the [official website][14] or the [Flathub store][15].

[LibreOffice 24.2][14]

**For upgrading** , usually, LibreOffice is preinstalled on most major Linux distributions, you can just wait for your distro to provide the upgrade from its repository, the official LibreOffice PPA, or Flathub.

However, if you can't wait, then uninstall your existing LibreOffice installation and download the _tar_ package (DEB or RPM) from the official website linked above, then extract the package to a directory.

Now, head into the folder named “ _DEBS_ ” or “ _RPMS_ ” depending on the _tar_ you downloaded and use the right-click menu to open it in the terminal.

![][16]

Then, type in one of the following commands according to the package you downloaded to install (Fedora or Debian-based distros):

```

    sudo dnf install *.rpm

    sudo dpkg -i *.deb

```

And that's it, you have successfully installed the latest LibreOffice release.

_💬 What do you think of this release? Let me know of your thoughts below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/libreoffice-24-2-is-here/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/best-free-open-source-alternatives-microsoft-office/
[2]: https://news.itsfoss.com/libreoffice-7-6/
[3]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[4]: https://news.itsfoss.com/content/images/2024/02/LibreOffice_24.2_a.png
[5]: https://github.com/tsyrogit/zxcvbn-c
[6]: https://news.itsfoss.com/content/images/2023/04/Follow-us-on-Google-News.png
[7]: https://news.itsfoss.com/content/images/2024/02/LibreOffice_24.2_b.png
[8]: https://news.itsfoss.com/content/images/2024/02/LibreOffice_24.2_c.png
[9]: https://news.itsfoss.com/content/images/2024/02/LibreOffice_24.2_d.png
[10]: https://en.wikipedia.org/wiki/Small_caps
[11]: https://en.wikipedia.org/wiki/Office_Open_XML
[12]: https://news.itsfoss.com/onlyoffice-8-0-release/
[13]: https://blog.documentfoundation.org/blog/2024/01/31/libreoffice-24-2/
[14]: https://www.libreoffice.org/download/download-libreoffice/
[15]: https://flathub.org/apps/org.libreoffice.LibreOffice
[16]: https://news.itsfoss.com/content/images/2024/02/LibreOffice_24.2_e.png
