[#]: subject: "Thorium: The Fastest Open Source Chromium-based Browser?"
[#]: via: "https://news.itsfoss.com/thorium/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Thorium: The Fastest Open Source Chromium-based Browser?
======
Fast like Lightning McQueen?
After taking a look at [Floorp Browser][1], I was left wondering whether there was a Chromium-based web browser that was as good, or even better than Chrome. That is when I came across Thorium, a web-browser that claims to be the “ _ **the fastest browser on Earth**_ ”.

So, join me as I check out this interesting browser with this first look.

**Suggested Read** 📖

![][2]

### Thorium: Overview ⭐

![][3]

Named after the radioactive metal, [Thorium][4], it is a Chromium-based browser whose big claim is backed by a myriad of tweaks that include, compiler optimizations for _SSE4.2_ , _AVS_ , _AES_ , various mods to _CFLAGS_ , _LDFLAGS_ , thinLTO flags, and [more][5].

The developer shares [performance stats][6] using popular benchmarking tools, and that definitely shows!

![Google Chrome vs. Thorium \(Speedometer test with 38% performance gain\)][7]

I tested it using [Speedometer 3.0 benchmark][8] on **Fedora 39** and compared it to Brave, and the scores were:

```

    Thorium: 19.2; Brave: 19.5

```

So, it may not be the “fastest” always, probably one of the fastest, that comes close to Brave or sometimes even beats it (depends on the version you tested it and your system).

Alexander Frick, the lead developer, also [insists on][9] providing support for older operating systems such as [Windows 7][10] so that its user base can use a capable modern browser without much fuss.

Some **key highlights** of Thorium include:

  * **Open-Source**
  * **Cross-Platform**
  * **Performance-Focused**



### Initial Impressions 👨‍💻

Installation on my Ubuntu 22.04 LTS system went by quite smoothly thanks to the provided _DEB_ package. At first launch, Thorium prompted me to sign in into my Google account.

![][11]

After I signed in, I was able to sync my Google Account content without any issues.

![][12]

When the sync setup was done, Thorium greeted me with a welcome page that was still under construction, and synced all my settings such as the theme, my bookmarks, the extensions, etc.

After browsing around a bit, I realized that the browsing experience was just what you would expect from a modern web browser.

![][13]

During all that, I noticed a slightly different looking three-ribbon menu that housed all the usual options to open a new tab, access the history, bookmarks, etc.

![][14]

On the extensions' menu, I saw a few pre-installed extensions that I couldn't disable, but could remove. The syncing also brought in [uBlock Origin][15] from my Google Account, but, Thorium already came pre-installed with a development build of the same.

![][16]

My passwords were also synced properly; Even though I don't really use Google's password manager anymore, it was nice to have.

![][17]

Overall, **I can confidently say that it is a web browser I could daily drive** , if I were to ditch Chrome completely. It gels in quite well with the Google ecosystem and has a familiar user interface that doesn't get in the way.

Plus the technical benefits that come along, makes it for a snappier experience.

## 📥 Get Thorium

As Thorium is **a cross-platform web browser** , you can find packages for a wide range of platforms that such as **Linux** , **Raspberry Pi** , **Windows** , **Android** , **macOS** , and more.

Just head over to the [official website][18] to get stared with the package of your choice, where the developer also lists some of their created Chrome extensions and a few Apps for [ThoriumOS][19], a fork of [ChromiumOS][20].

[Thorium][18]

You can also check out its [GitHub repo][21] for the source code if it interests you.

_💬 Would you ditch Chrome for Thorium or any other non-Chromium web browsers?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/thorium/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/floorp-firefox/
[2]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[3]: https://news.itsfoss.com/content/images/2024/03/Thorium_a-1.png
[4]: https://en.wikipedia.org/wiki/Thorium
[5]: https://thorium.rocks/optimizations
[6]: https://thorium.rocks/performance
[7]: https://news.itsfoss.com/content/images/2024/03/performance-gains-thorium.jpg
[8]: https://browserbench.org/Speedometer3.0/
[9]: https://thorium.rocks/win7
[10]: https://en.wikipedia.org/wiki/Windows_7
[11]: https://news.itsfoss.com/content/images/2024/03/Thorium_b.png
[12]: https://news.itsfoss.com/content/images/2024/03/Thorium_c.png
[13]: https://news.itsfoss.com/content/images/2024/03/Thorium_d.png
[14]: https://news.itsfoss.com/content/images/2024/03/Thorium_g.png
[15]: https://ublockorigin.com/
[16]: https://news.itsfoss.com/content/images/2024/03/Thorium_e.png
[17]: https://news.itsfoss.com/content/images/2024/03/Thorium_f.png
[18]: https://thorium.rocks/
[19]: https://github.com/Alex313031/ThoriumOS/
[20]: https://www.chromium.org/chromium-os/
[21]: https://github.com/Alex313031/thorium
