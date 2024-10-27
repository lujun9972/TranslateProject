[#]: subject: "PeaZip: A Versatile Open Source File Archiver and Encryption Utility"
[#]: via: "https://news.itsfoss.com/peazip/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

PeaZip: A Versatile Open Source File Archiver and Encryption Utility
======
A free and open source file archiver with various useful abilities.
[![][1]][2]

File archiving is an efficient way to store files and folders in a reliable and compact manner, which can significantly save storage space, depending on the archive format used. I have used many file-archiving apps over the years, including the infamous [WinRAR][3] back in the day.

But, subsequently, I switched to the open source [7-Zip][4] on my Windows machine and used the default file manager ( _usually Nautilus_ ) on my Linux machine to handle file archives.

That lasted until I learned of PeaZip, a cross-platform, open source file archiver utility that offered more features and file format support.

Join me as I take you through it. 😃

### PeaZip: For Your File Archiving Needs

![][5]

Offered under the [LGPL 3.0][6] license, PeaZip is a file archiving application that aims to provide a GUI frontend for popular open source file archiving tools like 7-Zip,Brotli, Zstd, FreeArc, and more.

Primarily written using [Lazarus][7]/[FreePascal][8], the project is actively maintained, with new releases being rolled out regularly.

#### ⭐ Key Features

In a long list of features like being CLI-friendly, allowing file management, supporting multiple interface modes, and more. PeaZip has the following key points of interest:

  * **Encryption and 2FA are available.**
  * **Extensible via plugins and themes.**
  * **Support for over 200 archive formats.**



#### 💻 User Experience

Using the official PeaZip Flatpak on my [Fedora 40][9]-equipped system has been a great experience so far. It lets me browse my files, and creating new archives is just a matter of a few clicks.

![PeaZip showing the Downloads directory.][10]

When creating a new archive, I can set the output location and choose which file format I want it to be. There are many options to pick from, such as _7Z_ , _TAR_ , _ZIP_ , _Zstd_ , _Brotli_ , _GZip_ , _PEA_ , etc.

![PeaZip archive file compression controls.][11]

Depending on the archive format used, there are **many compression levels to choose from** , with options like “ _Store_ ” for just storing the files without any compression and “ _Ultra_ ” for the maximum level of compression.

There are many handy presets for splitting the archive too, with options for floppy disks, CDs, DVDs, and Blu-rays.

![PeaZip file compression progress dialog.][12]

During file compression operations, a handy progress dialog appears with useful menu items at the top, and a progress bar, and controls to cancel or pause the operation at the bottom.

![][13]

Extracting files is also a similar affair, with similar controls and dialogs being shown during extraction operations.

If needed, there is also the **capability to add passwords to archives** to secure them against unauthorized access during transmission. PeaZip relies on tech like [AES][14], [Twofish][15] and [Serpent][16] to achieve that.

![PeaZip archive file password protection controls.][17]

Similarly, PeaZip features something called “[Secure Delete][18]”, which enables permanent deletion of files and folders by overwriting disk sectors over and over to ensure that data cannot be recovered.

![PeaZip secure delete feature in action.][19]

PeaZip also features **a password manager with strong encryption** that locally stores passwords, with a master password or [keyfile][20] acting as an additional layer of security to secure this sensitive information from prying eyes.

![PeaZip password manager in action.][21]

For a file-archiving app, PeaZip sure offers many features on top of the usual archiving ones. So far, it has **proven itself to be a versatile and reliable tool**. Whether you need to archive large files, protect sensitive data, or simply reduce file sizes, PeaZip has you covered.

### ⚙️ Installing PeaZip on Linux

You can get the latest release of PeaZip from the [official website][22], which also lists packages for BSD, Windows, and macOS.

For Linux, there's also the option to get it from the [Flathub store][23]. If that doesn't suit you, then you can get packages directly from the [releases section][24] in the project's [GitHub repo][25].

[PeaZip (Flathub)][23]

_💬 Know of any other file-archiving apps? Let me know below!_

* * *

[Get It's FOSS Plus Membership][26]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/peazip/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.win-rar.com/
[4]: https://www.7-zip.org/
[5]: https://news.itsfoss.com/content/images/2024/10/PeaZip_a.png
[6]: https://www.gnu.org/licenses/lgpl-3.0.en.html
[7]: https://www.lazarus-ide.org/
[8]: https://www.freepascal.org/
[9]: https://news.itsfoss.com/fedora-40-release/
[10]: https://news.itsfoss.com/content/images/2024/10/PeaZip_b-1.png
[11]: https://news.itsfoss.com/content/images/2024/10/PeaZip_c-1.png
[12]: https://news.itsfoss.com/content/images/2024/10/PeaZip_g.png
[13]: https://news.itsfoss.com/content/images/2024/10/PeaZip_h.png
[14]: https://en.wikipedia.org/wiki/Advanced_Encryption_Standard
[15]: https://en.wikipedia.org/wiki/Twofish
[16]: https://en.wikipedia.org/wiki/Serpent_(cipher)
[17]: https://news.itsfoss.com/content/images/2024/10/PeaZip_j.png
[18]: https://peazip.github.io/secure-delete.html
[19]: https://news.itsfoss.com/content/images/2024/10/PeaZip_k.png
[20]: https://en.wikipedia.org/wiki/Keyfile
[21]: https://news.itsfoss.com/content/images/2024/10/PeaZip_m.png
[22]: https://peazip.github.io/
[23]: https://flathub.org/apps/io.github.peazip.PeaZip
[24]: https://github.com/peazip/PeaZip/releases
[25]: https://github.com/peazip/PeaZip
[26]: https://itsfoss.com/#/portal/signup
