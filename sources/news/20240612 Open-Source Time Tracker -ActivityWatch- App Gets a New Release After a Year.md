[#]: subject: "Open-Source Time Tracker 'ActivityWatch' App Gets a New Release After a Year"
[#]: via: "https://news.itsfoss.com/activitywatch-0-13-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Open-Source Time Tracker 'ActivityWatch' App Gets a New Release After a Year
======
ActivityWatch's new update makes me want to use it to track my screen
time!
[![][1]][2]

You don't really come across many utilities on Linux that can help you track what you do on your PC, helping you see whether you are being productive, or are wasting time on unnecessary things.

[ActivityWatch][3] is one such app that got our attention way back in 2019 for its cross-platform, open-source nature that offers plenty of useful features to go along with it.

The [last stable release][4] dropped back on March 22, 2023, we didn't get to see a new major release since, but a number of intermediary beta releases ( _about 19_ ).

Luckily, that has now changed 👇

### ActivityWatch 0.13.0: Slow and Steady

![][5]

ActivityWatch follows a steady approach to new updates, over pushing new upgrades quickly.

Hence, it is easy to miss out on their major releases when it arrives. Luckily, I came across their announcement [X][6] for the latest release, which was the result of months of development with over 25+ contributors making it all happen.

Taking a look at some key highlights of this release, we have: **Improvements to the dark theme** , **categories and other settings are now carried across browsers** , and a **fix for X11 sessions** where the _aw-watcher-window_ was getting stuck in a loop.

Then there's the new 'app' and 'title' fields for CSV exports when exporting events data and **new modules which are not enabled by default** , but can extend functionality when enabled. Among them:

  * **aw-notify** is a module for sending you useful notifications related to your activity.
  * **aw-watcher-input** which will collect more detailed input activity like mouse clicks, key presses, and more.
  * **aw-sync** which is used to sync your local data with a sync folder to be used with services like Syncthing, Dropbox, etc.



And, to wrap this up, there's a new **productivity score feature** for categories, **redesigned timeline filter** settings, better timeline tooltip, a bucket merge tool, and improved time formatting.

If you want to dive into the technical changes, go through the release notes for [_0.13.0_][7] and ** [_0.13.1_][8] _._

### Get ActivityWatch

For getting started with this release, you can head over to the [official website][9] where you will find various packages for **Linux** , **Windows** , **macOS** , and **Android** ( _beta build_ ).

[ActivityWatch][9]

For those interested in the source code, they can make their way to the project's [GitHub][10] repo.

If you are not sure how to use it, then [our guide][11] on ActivityWatch is a must-read. It is a bit older but hold true for the most part. We'll be updating that soon:

![][12]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/activitywatch-0-13-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://activitywatch.net/
[4]: https://github.com/ActivityWatch/activitywatch/releases/tag/v0.12.2
[5]: https://news.itsfoss.com/content/images/2024/06/ActivityWatch-1.png
[6]: https://x.com/ActivityWatchIt/status/1800455076420669673
[7]: https://github.com/ActivityWatch/activitywatch/releases/tag/v0.13.0
[8]: https://github.com/ActivityWatch/activitywatch/releases/tag/v0.13.1
[9]: https://activitywatch.net/downloads/
[10]: https://github.com/ActivityWatch/activitywatch
[11]: https://itsfoss.com/activitywatch/
[12]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
