[#]: subject: "LibreOffice 26.2 is a Maintenance Release That Feels Like a Stable One"
[#]: via: "https://itsfoss.com/news/libreoffice-26-2-release/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

LibreOffice 26.2 is a Maintenance Release That Feels Like a Stable One
======

[![Warp Terminal][1]][2]

People who aren't fans of their office suite handing over data to feed some deluded AI system opt for [open source alternatives][3] with comparable functionality and no snooping to worry about.

[LibreOffice][4] is one of those options that has proven itself time and again with its versatility and easy-to-use interface. Heck, it's so good governmental agencies [have been switching to it][5] and [saving some good money][6] as a result.

A new point release, [LibreOffice 26.2][7], has been announced by The Document Foundation that focuses on delivering upgrades across all editors. The folks from [Collabora Productivity][8] have contributed over 2,000 commits to this release too.

### 🆕 LibreOffice 26.2: What's New?

![][9]

**Writer** gets several pagination and tracking improvements. Floating tables now behave properly with _keep-with-next_ and _don't split_ paragraph attributes, avoiding awkward page breaks.

Similarly, the editor can now split floating tables for better DOCX export, partly deleted paragraphs in _Track Changes_ don't clutter numbering list, and auto-caption insertion now works when pasting single images if you have configured it via the AutoCaption Images setting.

![][10]

Then there are the new " _Start_ " and " _End_ " paragraph alignments that automatically adapt to text direction. This should be useful for documents that combine left-to-right and right-to-left text.

**Calc** has received major performance and format upgrades. Pasting content from Excel is better now thanks to [BIFF12][11] clipboard format support, and scrolling in sheets with many hidden columns is noticeably faster too.

![][12]

Connector shapes are a new addition that help with diagram work within spreadsheets, and the _Remove Duplicates_ function and _Reject All Changes_ operations both run faster.

Additionally, the Excel 2010-365 format is now the default when saving XLSX files.

**Impress** adds better audio/video support on Windows, using the [Microsoft Media Foundation][13] integration for providing native playback of common codecs.

The _Layouts_ panel and _Theme_ dialog now use IconView widgets for a cleaner experience.

### Miscellaneous Changes

3D chart performance issues have been fixed, Google Drive authentication has been improved on Windows, and EPUB exports are significantly faster, with a helpful progress bar now being shown.

For those who work with _.md_ files, **the import and export of Markdown content is now possible** , including clipboard support and the ability to use _ODT_ / _DOCX_ templates when importing.

Graphics and core improvements round out the release. [Skia][14] rendering is now the standard on Windows and macOS. SVG files with pattern fills render faster on Linux thanks to backend optimizations.

#### ⚙️ How to Install/Upgrade?

For most Linux users, [Flathub][15] supplies this LibreOffice release for quick installations. Those on other platforms can get the appropriate files from the [official website][16].

[LibreOffice 26.2][16]

Existing Linux desktop users can wait for the upgrade to be delivered by their distribution or [manually install the tar package][17].

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/libreoffice-26-2-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/best-free-open-source-alternatives-microsoft-office/
[4]: https://www.libreoffice.org/
[5]: https://itsfoss.com/news/denmark-set-to-replace-microsoft/
[6]: https://itsfoss.com/news/german-state-ditch-microsoft/
[7]: https://wiki.documentfoundation.org/ReleaseNotes/26.2
[8]: https://www.collaboraonline.com/
[9]: https://itsfoss.com/content/images/2026/02/libreoffice-26-2.png
[10]: https://itsfoss.com/content/images/2026/02/libreoffice-26-2-paragraph-properties-dialog.png
[11]: https://support.microsoft.com/en-us/office/file-formats-that-are-supported-in-excel-0943ff2c-6014-4e8d-aaea-b83d51d46247#:~:text=The%20binary%20file%20format%20(BIFF12,Excel%202010%20and%20Excel%202007.
[12]: https://itsfoss.com/content/images/2026/02/libreoffice-26-2-calc-connectors.png
[13]: https://learn.microsoft.com/en-us/windows/win32/medfound/microsoft-media-foundation-sdk
[14]: https://skia.org/
[15]: https://flathub.org/en/apps/org.libreoffice.LibreOffice
[16]: https://www.libreoffice.org/download/download-libreoffice/
[17]: https://www.libreoffice.org/download/download-libreoffice/#:~:text=need%20another%20language%3F-,SDK%20and%20Sourcecode,-Download%20the%20SDK
