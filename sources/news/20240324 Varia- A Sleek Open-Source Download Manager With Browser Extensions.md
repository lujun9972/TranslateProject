[#]: subject: "Varia: A Sleek Open-Source Download Manager With Browser Extensions"
[#]: via: "https://news.itsfoss.com/varia-download-manager/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Varia: A Sleek Open-Source Download Manager With Browser Extensions
======
Take a look at this interesting download manager!
Thanks to an increase in internet speeds around the globe, we can download files in a matter of minutes or even seconds; depending on the size of the file. So, not everyone cares about the download manager being used.

However, in the past, download managers were crucial if you had a slow internet connection, because of features like download speed control, the ability to pause, queue, etc.

Guess what, download managers still make a difference! 😎

In my case, for instance, when I use [Vivaldi][1]'s built-in downloader, it works fine for smaller files such as images and GIFs, but for larger files like ISOs, it starts to slow down considerably. That is where one of the [best download managers for Linux][2], Motrix usually comes handy for me.

But, being the app hopper I am, I often try to find new apps, even if my existing apps work fine.

That is when I came across **Varia** , an open-source download manager for Linux based on [aria2][3], a lightweight command-line download utility.

Let's take a look at it.

**Suggested Read** 📖

![][4]

### Varia: Overview ⭐

![][5]

Written primarily in the Python programming language, Varia takes its name from aria2, and provides many useful features that make it a solid download manager choice.

The **key highlights** of Varia include:

  * **Libadwaita Design**
  * **Browser Extension Available**
  * **Support for Multiple Downloads**



#### Initial Impressions 👨‍💻

When I started researching about Varia, I found out that it is from the same developer as [Flatsweep][6]; which I use regularly to keep my system clean of leftover data from Flatpaks.

When I started up Varia, there was an empty screen with a few options around. I used the URL box towards the left to manually add download URLs for different types of files.

![][7]

After I was done adding, there were handy controls to pause or remove downloads near each download entry. Then there was a sidebar that let me sort through downloads that were in progress, and those that were completed.

The header bar housed the preferences' menu, a three-ribbon menu ( _more on that below_ ), the current download speed for all the files combined, a button to pause all downloads, and the usual window controls.

Strangely enough, **when I tried pausing downloads, Varia would just continue downloading them silently** , but when I restarted the app, the pause buttons would work fine. I am not sure what happened. Probably a temporary bug.

![][8]

The three-ribbon menu had options to run Varia in the background, cancelling all downloads, opening the download folder, and an option to access the about page.

![][9]

As for **the preferences menu** , Varia lets you pick the download directory, set a download speed limit, an option related to authentication, and the ability to change the number of simultaneous downloads Varia could do.

There was also a “ **Remote Mode** ” option for remote control via an RPC interface to control the aria2 backend. It supports _JSON-RPC_ , and _XML-RPC_.

![][10]

And, that's not it. As illustrated by the screenshot above, there's also a browser extension for Varia 🤯

![][11]

And, when you install and enable that for [Firefox][12] or [Chrome][13], Varia can take over the downloading duties from the browser.

When I tested it with Chrome, **there was no consistency in the extension's behavior** ; it would sometimes take over the download, sometimes not. As I see it, manually pasting the download link into Varia is a more reliable approach.

However, it is still good to see an extension trying to make things easy! If it works better for you, that should be wonderful! 😃

If you ask me, Varia still needs some work before I can comfortably switch to it. But, if it gets the job done for you, it is a simple, elegant, and flexible download manager overall!

### 📥 Get Varia

To take advantage of what Varia has to offer, you can grab the latest release from its [official website][14]. You can also head over to the [Flatpak store][15] and [AUR][16] (unofficial) for the same.

[Varia (Flathub)][15]

If you are interested in the source code, then you can visit its [GitHub repo][17].

_💬 Do let me know your experience if you try it on your system!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/varia-download-manager/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://vivaldi.com/
[2]: https://itsfoss.com/best-download-managers-linux/
[3]: https://aria2.github.io/
[4]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[5]: https://news.itsfoss.com/content/images/2024/03/Varia_a.png
[6]: https://github.com/giantpinkrobots/flatsweep
[7]: https://news.itsfoss.com/content/images/2024/03/Varia_b.png
[8]: https://news.itsfoss.com/content/images/2024/03/Varia_c.png
[9]: https://news.itsfoss.com/content/images/2024/03/Varia_d.png
[10]: https://news.itsfoss.com/content/images/2024/03/Varia_e.png
[11]: https://news.itsfoss.com/content/images/2024/03/Varia_f.png
[12]: https://addons.mozilla.org/en-US/firefox/addon/varia-integrator/
[13]: https://chromewebstore.google.com/detail/varia-integrator/dacakhfljjhgdfdlgjpabkkjhbpcmiff
[14]: https://giantpinkrobots.github.io/varia/
[15]: https://flathub.org/apps/io.github.giantpinkrobots.varia
[16]: https://aur.archlinux.org/packages/varia
[17]: https://github.com/giantpinkrobots/varia
