[#]: subject: "freeDictionaryApp: Open Source Android App That Helps You Get Information on a Word"
[#]: via: "https://news.itsfoss.com/freedictionaryapp/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

freeDictionaryApp: Open Source Android App That Helps You Get Information on a Word
======
An easy way to get additional information about a word!
[![][1]][2]

Every so often, while [reading a book][3], I come across unfamiliar words that I need to look up online to understand. Occasionally, I even forget the meanings of words I once knew.

I usually do a Google search for understanding a word, and more often than not, I end up on [Merriam-Webster][4], as Google's [Knowledge Graph][5] results have become worse over the past few months.

However, the need for an offline, ad-free, and tracker-free solution has been constantly on my mind. As it happens, my search has led me to freeDictionaryApp, **a FOSS dictionary app for Android**.

Let’s jump right in and see what we find! 📖 📱

### freeDictionaryApp: Words Unpacked

![][6]

Written using Kotlin, freeDictionaryApp is the work of [Yamin Siahmargooei][7], who describes this app as a reincarnation of [Owl2][8], but with a [Free Dictionary API][9] implementation.

Even though **the development of the API seems to have stopped two years ago** , freeDictionaryApp seems to be functioning just fine. I tested it on my Android 12 smartphone, and the experience was seamless.

There is a search bar at the bottom of the app to search for words, and on successful word searches, the page fills up with the word type and multiple definitions and examples. I could also use **the text-to-speech feature** by clicking on the pronunciation mentioned below the word.

![][10]

There is also a neat **favorite words feature** that lets me save any important words for later use so that I wouldn't have to search for those manually again. If you want to save a word, just click on the heart icon beside a word.

To access your saved words, you can go to the header menu and tap on the heart icon. The same region also has other useful options like **search history** , **a die roll for showing random words** , **the settings menu** , and an **information page** with the license details ([ _GPL 3.0_][11]).

I could also **easily share any searched words** by using the share button on the app, which opened up Android's sharing menu with all the relevant communication apps. When sharing a word, freeDictionaryApp attaches a detailed excerpt with links to it and the API at the end.

As I used it more, **I noticed that freeDictionaryApp could only handle single words** , not multi-word queries like “ _open source_ ”. This is most likely a limitation of the API underneath and not the app itself, but it is fine for now. I hope the developer considers adding support for multi-word queries in future updates by using a more powerful API to power the app.

### Install freeDictionaryApp

You can install this on your Android smartphone by downloading the latest release from [F-Droid][12]. You can also visit the project's [GitHub][13] repo for alternative downloads or the source code.

[freeDictionaryApp][12]

**Suggested Read** 📖

![][14]

* * *

[Get It's FOSS Plus Membership][15]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/freedictionaryapp/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/openreads/
[4]: https://www.merriam-webster.com/
[5]: https://en.wikipedia.org/wiki/Google_Knowledge_Graph
[6]: https://news.itsfoss.com/content/images/2024/12/freeDictionaryApp_a.png
[7]: https://github.com/yamin8000
[8]: https://github.com/yamin8000/Owl2
[9]: https://dictionaryapi.dev/
[10]: https://news.itsfoss.com/content/images/2024/12/freeDictionaryApp_b.png
[11]: https://www.gnu.org/licenses/gpl-3.0.en.html
[12]: https://f-droid.org/en/packages/io.github.yamin8000.owl/index.html
[13]: https://github.com/yamin8000/freeDictionaryApp
[14]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[15]: https://itsfoss.com/#/portal/signup
