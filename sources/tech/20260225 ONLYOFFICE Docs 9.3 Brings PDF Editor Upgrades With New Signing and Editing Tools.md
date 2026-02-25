[#]: subject: "ONLYOFFICE Docs 9.3 Brings PDF Editor Upgrades With New Signing and Editing Tools"
[#]: via: "https://itsfoss.com/news/onlyoffice-docs-9-3-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ONLYOFFICE Docs 9.3 Brings PDF Editor Upgrades With New Signing and Editing Tools
======

[![Warp Terminal][1]][2]

[ONLYOFFICE][3] is an open source office suite that holds its own against the likes of Microsoft Office, with some decent document format compatibility and a self-hosting option for those who prefer to keep their data in-house.

The [previous point release][4] brought AI-powered grammar checks, macro recording, and customizable keyboard shortcuts.

Now, the developers have pushed out [ONLYOFFICE Docs 9.3][5], and it is a fairly substantial update.

## 🆕 ONLYOFFICE Docs 9.3: What's New?

Starting with the **Document Editor** , you can now use Multipage View to display pages side by side, which makes reviewing layouts in documents a lot more practical.

Comments also got a small but useful upgrade. Now, each user gets a unique color, and the exact start and end points of the comments are shown, so you always know what is being discussed.

The **Spreadsheet Editor** gets a handful of welcome additions too. The new _Solver_ tool lets you tackle linear optimization problems using the [Simplex][6] method. It is accessible from the _Data_ tab.

Three regex functions have been added to the formula library: `REGEXTEST`, `REGEXREPLACE`, and `REGEXEXTRACT`, which should make handling complex text data substantially less painful.

There is also support for dynamic arrays, where a formula can spill results into neighboring cells automatically. Performance-wise, the initial load time for large spreadsheets ( _over 3 MB_ ) has been improved.

![From left to right, the editors are: Document, Spreadsheet, and Presentation.][7]

For **Presentations** , the editor now supports GIF animations in slideshow mode, so you no longer need to rely on video files or external links for showcasing your cat memes and brainrot content.

The **PDF Editor** sees the most attention in this release. You can now unlock and edit password-protected PDFs directly, provided you have the password. Link management has been added, letting you insert and edit links to external resources or internal pages, with those links staying active even in the commenting mode.

Signature options in PDF forms have expanded too. On top of uploading an image ( _now with a background removal option_ ), users can type a signature using a stylized font or draw one directly on screen using a mouse or touch input.

Enterprise users get an additional option to upload a signing certificate through the [Admin Panel][8], enabling trusted digital signatures on submitted forms.

![From left to right, the PDF editor and Admin Panel.][9]

Speaking of enterprise, the **Admin Panel** has picked up several new tools. You can now complete final server configuration from a dedicated window, obtain an HTTPS certificate via script, manage and upload custom fonts, upload a license file, and access per-organization metrics from the _Statistics_ tab.

Across all editors, you can now add hyperlinks to images, shapes, and groups in both documents and spreadsheets. Files can also be saved in the `.md` format, and TSV files can now be opened for viewing.

## 📥 Download ONLYOFFICE Docs 9.3

As always, self-hosting users can grab this release from the [official website][10], and for the rest of us, the [desktop editors][11] should be a good download. Just keep in mind that new releases take some time before they are made available.

The [changelog][12] summarizes all the changes introduced with ONLYOFFICE Docs 9.3.

[ONLYOFFICE Docs 9.3][10]

* * *

**Suggested Read 📖:** [_6 Best Open Source Alternatives to Microsoft Office for Linux_][13]

![][14]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/onlyoffice-docs-9-3-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.onlyoffice.com/
[4]: https://itsfoss.com/news/onlyoffice-docs-9-2-release/
[5]: https://www.onlyoffice.com/blog/2026/02/onlyoffice-docs-9-3
[6]: https://en.wikipedia.org/wiki/Simplex_algorithm
[7]: https://itsfoss.com/content/images/2026/02/onlyoffice-docs-9-3-document-comments.png
[8]: https://helpcenter.onlyoffice.com/docs/installation/docs-cloud-admin-panel.aspx
[9]: https://itsfoss.com/content/images/2026/02/onlyoffice-docs-9-3-pdf-signatures.png
[10]: https://www.onlyoffice.com/download
[11]: https://www.onlyoffice.com/desktop
[12]: https://github.com/ONLYOFFICE/DocumentServer/blob/master/CHANGELOG.md#930
[13]: https://itsfoss.com/best-free-open-source-alternatives-microsoft-office/
[14]: https://itsfoss.com/content/images/icon/android-chrome-512x512-299.png
