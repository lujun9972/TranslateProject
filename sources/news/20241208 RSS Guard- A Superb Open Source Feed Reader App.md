[#]: subject: "RSS Guard: A Superb Open Source Feed Reader App"
[#]: via: "https://news.itsfoss.com/rss-guard/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

RSS Guard: A Superb Open Source Feed Reader App
======
A cross-platform open source feed reader that gets the job done.
[![][1]][2]

📜

Must-Know Bits 👇
— It is open source and cross-platform.
— Supports RSS, RDF, Atom, and JSON feeds.
— Offers plenty of cool features that a user might need.

* * *

[RSS][3] and [Atom][4] feeds are a really nifty way of keeping track of web resources like blogs and news articles, allowing easy access to subscribed content. I use such feeds to keep track of news in the tech world as well as the real world.

Earlier, I used to use [Omnivore][5] for my feed and newsletter needs, but that platform is no more thanks to a change in ownership. I have had to switch to the proprietary [Feedly][6] for keeping track of my feeds.

However, that is just a temporary solution for me, and I am looking to switch to an open source option. There are many great ones out there, and I will be checking out one of them with this article.

### RSS Guard: Manage Your Feeds Easily

![][7]

The brainchild of [Martin Rotter][8], RSS Guard is **an open source desktop feed reader and podcast player** that is written primarily using C++. It can be used to fetch feeds in the RSS, [RDF][9], Atom, and [JSON][10] formats.

#### ⭐ Key Features

Among the list of useful features like an internal browser, an [ad blocker][11], a [CLI version][12], and an advanced [website scraper][13], here are some of RSS Guard's most notable talking points:

  * **Cross-Platform**
  * **Actively Developed**
  * **Minimal User Interface**



#### 💻 User Experience

During my testing on Fedora 40, I focused on handling RSS and Atom feeds, skipping the JSON feed and [podcast player][14] functionalities.

On first launch, the app nudges you to go through **account setup** , with conventional options to manually add feeds or sync from other apps/services like [Tiny Tiny RSS][15], Feedly, Gmail, [Nextcloud News][16], and a few more.

![RSS Guard's new account creation process.][17]

I went the manual way, as **Feedly was asking me to pay for a Pro subscription for access to their developer tools**. So, for that, I created an account with the default name, and RSS Guard filled it up with a default set of feeds, which, to my surprise, had [It's FOSS][18] under the _Technology_ category!

📋

It would be cool to see It's FOSS News on there too! 😁

![][19]

Subsequently, **I started organizing my feed** by deleting some existing feeds and feed categories. The latter of which are folders that contain the feed themselves.

The right-click menus for feeds and categories are quite identical, with options to fetch the latest posts, add new items, edit the selected item, controls for sorting them, marking them as read/unread, and a few others.

![RSS Guard's category and feed related controls.][20]

**Adding a new category is quite straightforward** ; just right-click on an account or existing category, then choose “Add new category”. A small dialog will pop up asking you to enter the relevant details, like its location, title, description, and icon.

![][21]

Similarly, **adding new feeds is easy** ; just enter the URL for the feed of a website and correctly select which feeds you want access to, then click “ _Import checked feeds_ ”.

If you want more control, then you could switch to “ _advanced mode_ ”.

![RSS Guard's advanced mode new feed creation process.][22]

As you can see above, I was able to manually add the RSS feed for [It's FOSS News][23] and the Atom feed for [The Register][24] by uploading the _.rss_ and _.atom_ files for these.

For adding details about the feed, I used the “ _Fetch metadata_ ” option to make RSS Guard grab relevant details like the site name, the caption, and the icon ( _usually a website's_ [_favicon_][25]).

![][26]

By now, you might be curious to see **how the feed-reading experience is** , and I must say, it is quite nice. The internal browser does an impressive job of showing content from the various feeds.

![RSS Guard's internal browser in action.][27]

If you click on the full-screen mode button at the bottom-left of the app, a new tab opens up showing the content in a new tab, with options to open the featured image of an article and the original content.

Of course, this functionality depends on the website. **Some websites don't show all the information** , so the user has to visit the website themselves.

![][28]

Around the end of my testing, I noticed that **RSS Guard was showing status notifications of the fetched articles** in the notification panel on my GNOME 46-equipped system. I really liked that.

**Suggested Read** 📖

![][29]

### ⚙️ Installing RSS Guard

Linux users can get RSS Guard from [Flathub][30], with the [GitHub][31] repo hosting the source code and additional packages in its _releases sectio,_ for **Linux** , **BSD** , **OS/2** , **Windows** , and **macOS**.

[RSS Guard (Flathub)][30]

There is also a [lite version of RSS Guard][32], which offers a safer, simpler, and more memory-efficient internal browser devoid of JavaScript support. The [documentation][33] is a handy resource if you want to dive deeper into this app.

**Suggested Read** 📖

![][34]

* * *

[Get It's FOSS Plus Membership][35]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/rss-guard/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/RSS
[4]: https://en.wikipedia.org/wiki/Atom_(web_standard)
[5]: https://news.itsfoss.com/omnivore/
[6]: https://feedly.com/
[7]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_a.png
[8]: https://martinrotter.github.io/
[9]: https://en.wikipedia.org/wiki/Resource_Description_Framework
[10]: https://en.wikipedia.org/wiki/JSON
[11]: https://rssguard.readthedocs.io/en/stable/features/browseradblock.html
[12]: https://rssguard.readthedocs.io/en/stable/features/cli.html
[13]: https://rssguard.readthedocs.io/en/stable/features/scraping.html
[14]: https://rssguard.readthedocs.io/en/stable/features/mediaplayer.html
[15]: https://tt-rss.org/
[16]: https://apps.nextcloud.com/apps/news
[17]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_b.png
[18]: https://itsfoss.com/
[19]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_e.png
[20]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_f.png
[21]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_h.png
[22]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_j-1.png
[23]: https://news.itsfoss.com/latest/rss/
[24]: https://www.theregister.com/Design/page/feeds.html
[25]: https://en.wikipedia.org/wiki/Favicon
[26]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_l.png
[27]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard_m.png
[28]: https://news.itsfoss.com/content/images/2024/11/RSS_Guard.png
[29]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[30]: https://flathub.org/apps/io.github.martinrotter.rssguard
[31]: https://github.com/martinrotter/rssguard
[32]: https://flathub.org/apps/io.github.martinrotter.rssguardlite
[33]: https://rssguard.readthedocs.io/en/stable/index.html
[34]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[35]: https://itsfoss.com/#/portal/signup
