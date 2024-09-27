[#]: subject: "Aria2App is a Super Fast Versatile Open-Source Download Manager for Android"
[#]: via: "https://news.itsfoss.com/aria2app/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Aria2App is a Super Fast Versatile Open-Source Download Manager for Android
======
A useful open-source download manager for Android
[![][1]][2]

Using a [download manager][3], besides the one on your web browser, is a handy trick that helps with effortless file downloads. Personally speaking, I have used quite a few over the years, with [Motrix][4] being my current daily driver on Fedora.

But, on Android, I had never used one, and that got me thinking: Is there a download manager for Android? It turns out there are quite a few, and that is when I found **Aria2App**.

Join me as I take you through this handy FOSS app. 😃

### Aria2App: Reliable Downloads For Android

![][5]

Offered freely under the [GPL-3.0 License][6], Aria2App is **a Java-based download manager for Android** that is powered by the popular [aria2][7] utility. It is supported by many, with [Gianluca Altomani][8] being the project lead.

At first launch, you will be prompted to select a profile, where there is already a pre-configured one set up, go with that if you don't want to fiddle around. On the main screen, you will find controls to search for downloads, filter through them, and add new downloads via the plus symbol button at the bottom.

Thanks to aria2, Aria2App supports downloading _Torrents_ , _Metalinks_ , _HTTP(S)_ , _FTP_ , and _SFTP_. When downloads are in progress, there is **a togglable network activity chart** at the top, which gets updated in real-time, with buttons to pause, stop, or remove any downloads below each entry.

You can also directly download files from a website by going into the “WebView” option from the add download (+) button. Just enter the URL of a website, then navigate to the download button/link to get the files via Aria2App.

![][9]

I tested out how **downloading Torrent files** worked on Aria2App by downloading ISO files for [GhostBSD][10] and [Zorin OS 17.2][11] from [FOSS Torrents][12].

The app is snappy, and offers so many features (if you want to use them).

As you can see above, Aria2App delivered. It enabled me to see all the relevant information, like the status of the peers, the file size, the download progress, and more.

The developers also mention that it is **possible to manage aria2 instances running on servers** with the help of a JSON-RPC interface, which is interesting 🤯

### Install Aria2App

This app is available on [F-Droid][13] and the [Play Store][14], with the former having the option to download an APK. After installation, Aria2App is simple to get used to; just go with the default profile if you would rather not get into the more advanced aspects of the application.

[Aria2App][14]

In case you are curious about the source code, you can always visit the project's [GitHub][15] repo.

**Suggested Read** 📖

![][16]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/aria2app/

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
[4]: https://motrix.app/
[5]: https://news.itsfoss.com/content/images/2024/09/Aria2App_a.png
[6]: https://www.gnu.org/licenses/gpl-3.0.en.html
[7]: https://github.com/aria2/aria2
[8]: https://www.linkedin.com/in/devgianlu/
[9]: https://news.itsfoss.com/content/images/2024/09/Aria2App_c.png
[10]: https://ghostbsd.org/
[11]: https://news.itsfoss.com/zorin-os-17-2/
[12]: https://fosstorrents.com/
[13]: https://f-droid.org/packages/com.gianlu.aria2app/
[14]: https://play.google.com/store/apps/details?id=com.gianlu.aria2app
[15]: https://github.com/devgianlu/Aria2App
[16]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
