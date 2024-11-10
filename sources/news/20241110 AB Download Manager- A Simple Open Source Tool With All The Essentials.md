[#]: subject: "AB Download Manager: A Simple Open Source Tool With All The Essentials"
[#]: via: "https://news.itsfoss.com/ab-download-manager/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

AB Download Manager: A Simple Open Source Tool With All The Essentials
======
Want to try a different download manager for a change? Try AB download
manager!
[![][1]][2]

[Download managers on Linux][3] are aplenty, with each option being different from the other in how it handles downloads and the user interface itself. Usually, many of those are based on [aria2][4], the popular download utility.

Here, we have the AB Download Manager, which does not use aria2, but is a great choice for hassle-free file downloads on the Linux desktop.

🚧

This is still under development, so you may encounter bugs from time to time.

### AB Download Manager: Speedy File Downloads

![][5]

Written in [Kotlin][6], AB Download Manager is the work of two developers, [AmirHossein Abdolmotallebi][7] and [Dagim G. Astatkie][8] who have made it freely available under the Apache 2.0 License.

#### ⭐ Key Features

Even though the function of this app is pretty straightforward, here are some notable features to keep you hooked:

  * **Cross-Platform**
  * **Batch Downloads**
  * **Actively Developed**



#### 💻 User Experience

Installing it on [Linux Mint 22][9] using the provided DEB file worked as expected. I started a download for Lubuntu 24.04.1 and copied over the download link from the web browser to AB Download Manager.

It showed me a dialog with all the relevant information, like the download link, the path, the file size, and controls to limit the download speed.

![][10]

After the download began, another smaller dialog popped up, showing me the download progress, with important details related to the file, including information on whether resuming this download was possible.

Below it, there was a handy status window, which showed me all the parts of the file AB Download Manager was downloading.

![][11]

There was also a settings page in the dialog where I could set the download speed limit and tweak the thread count to adjust the download behavior.

I then queued up some downloads to check out the **download queuing functionality** , and it worked as expected when I clicked on “ _Start Queue_ ”.

![][12]

The default queue was called “ _main_ ”, but when I navigated into the “ _Open Queues_ ” menu, I could add any number of download queues to better organize the downloads.

There were more advanced controls in this menu, allowing me to enable a scheduler, set the maximum number of concurrent downloads, and configuring the auto-stop behavior.

![AB Download Manager Open Queues menu.][13]

The global settings menu for AB Download Manager was quite useful too, letting me change the default download folder, change the speed display options, switch between light/dark themes, and more.

![][14]

As I was wrapping up my use, I noticed that there were **browser extensions** for AB Download Manager that work with [Firefox][15] and [Chrome][16].

![][17]

I tested it on Firefox, and it worked flawlessly. As soon as I clicked on a download button, AB Download Manager would capture the download from the browser. It showed me the usual dialogs to start a new download and monitor progress.

### ⚙️ Installing AB Download Manager

You can get AB Download Manager for Linux and Windows from the [official website][18] or the GitHub [releases][19] section of the project. There are only two package choices for Linux, either _.deb_ or _.tar.gz_ , unless you want to build it from source.

To explore the source code, you can check out its [GitHub][20] repo.

[AB Download Manager][18]

**Suggested Read** 📖

![][21]

* * *

[Get It's FOSS Plus Membership][22]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ab-download-manager/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/best-download-managers-linux/
[4]: https://aria2.github.io/
[5]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_a.png
[6]: https://kotlinlang.org/
[7]: https://www.amirab.ir/?lang=en
[8]: https://dagimg-dot.netlify.app/
[9]: https://news.itsfoss.com/linux-mint-22-release/
[10]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_b.png
[11]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_c.png
[12]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_e.png
[13]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_f.png
[14]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_h.png
[15]: https://addons.mozilla.org/en-US/firefox/addon/ab-download-manager/
[16]: https://chromewebstore.google.com/detail/ab-download-manager-brows/bbobopahenonfdgjgaleledndnnfhooj
[17]: https://news.itsfoss.com/content/images/2024/09/AB_Download_Manager_i.png
[18]: https://abdownloadmanager.com/
[19]: https://github.com/amir1376/ab-download-manager/releases
[20]: https://github.com/amir1376/ab-download-manager
[21]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[22]: https://itsfoss.com/#/portal/signup
