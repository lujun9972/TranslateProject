[#]: subject: "Openreads: An Open Source Mobile App To Keep Track of Your Books"
[#]: via: "https://news.itsfoss.com/openreads/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Openreads: An Open Source Mobile App To Keep Track of Your Books
======
You can keep track of your book progresses using the Openreads app.
Here's how.
[![][1]][2]

Reading books, digital or a physical copy, is one of the best things one can do for fostering personal growth, knowledge, ideas, and experiences. In the fast-moving digital world of 15-second short videos, **I have been slowly but steadily warming up to the habit of reading books**.

I have discovered that I feel a sense of peace when I immerse myself deeply into a book, undeterred by distractions—just me and the book. As I progress through various books, keeping track of my previous reads is becoming a challenging task. Typically, I store my reading list on a [note-taking app][3].

But, having a dedicated application for this wouldn't hurt, so I searched around for one, and that is when my search led to **Openreads** , an open source book tracker that has an **intuitive user interface** and **no ads**.

Join me as I share my experience of it with you. 😃

### Openreads: Tracking Books Made Simple

![The onboarding flow of Openreads at first launch; I have omitted a few steps.][4]

Completely built using [Flutter][5], Openreads is [GPL 2.0][6]-licensed software that is the work of over 50 contributors, with [Mateusz Bąk][7], the lead developer, doing most of the heavy lifting.

When I first launched the app, I was taken through an onboarding flow that showed what Openreads is about, with a handy menu for restoring any past backups or importing CSV files from Openreads, [Goodreads][8], and [BookWyrm][9].

![Openreads provides many options for adding books.][10]

**For adding books, there are three main ways**. The first is adding a book manually and filling out the relevant details like its name, subtitle, author, cover image, etc. with additional options to set a reading status/list for it.

These are self-explanatory, like _Finished_ , _In progress_ , _For later_ , and _Unfinished_.

![Adding a book \(The Body Keeps the Score\) to Openreads by using Open Library.][11]

The second and most straightforward way for adding books is by searching for them in the [Open Library][12]. As you can see above, I found my current read, [The Body Keeps the Score][13], without any issues.

**Openreads filled out the book entry with useful information** like the author name, the description of the book, and its [ISBN][14] code, with fields to add a personal review and note on it. I gave it the _In progress_ status to track it properly and selected the book type as _E-book_.

I then added some _For later_ books when **I noticed the search function being a bit slow at times** , but it was fine. The added books were [How Linux Works][15], [Pro Git][16], and **** manga and comics like [One-Punch Man][17] and [Ultimate Spider-Man][18].

![Openreads lists out added books neatly, with the settings menu featuring useful appearance and book import/export settings.][19]

All the added books could be found on their respective pages on the home screen of Openreads, where they can either be shown as a list, or as a grid. During my testing, I found that **the list view was more appropriate for smaller screens**. If you have a larger screen, then the grid view is nice to have.

For accessing any unfinished books, I had to go into a separate section inside the three-dot menu at the top right of the app. Similarly, the settings menu houses many useful controls.

The **Appearance submenu provided extensive control over the app’s theming** , while the Backup menu offered handy options for backing up and restoring books. Additionally, **I could also add custom tags to books** , making sorting and organization more efficient.

Before you ask, _what about the barcode scanning feature?_ Well, I didn't get to test it out, as I don't own any physical books. ☠️ I still checked to see if it could be used, and after granting Openreads camera permission, the app was ready to scan for barcodes.

### Install Openreads

You can find the latest release of Openreads on [F-Droid][20] and the [Play Store][21]. If you want to build from source or sideload the APK, head to the project's [GitHub][22] repo.

[Openreads][21]

**P.S:** _There's even an_ [_iOS app_][23] _for those trapped in the walled garden._ 😆

**Suggested Read** 📖

![][24]

* * *

[Get It's FOSS Plus Membership][25]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/openreads/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/note-taking-apps-linux/
[4]: https://news.itsfoss.com/content/images/2024/11/Openreads_a.jpg
[5]: https://flutter.dev/
[6]: https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html
[7]: https://github.com/mateusz-bak
[8]: https://www.goodreads.com/
[9]: https://joinbookwyrm.com/
[10]: https://news.itsfoss.com/content/images/2024/11/Openreads_d.jpg
[11]: https://news.itsfoss.com/content/images/2024/11/Openreads_f.jpg
[12]: https://openlibrary.org/
[13]: https://openlibrary.org/works/OL18147687W/The_Body_Keeps_the_Score
[14]: https://en.wikipedia.org/wiki/ISBN
[15]: https://nostarch.com/howlinuxworks3
[16]: https://git-scm.com/book/en/v2
[17]: https://en.wikipedia.org/wiki/One-Punch_Man
[18]: https://en.wikipedia.org/wiki/Ultimate_Spider-Man
[19]: https://news.itsfoss.com/content/images/2024/11/Openreads_j.jpg
[20]: https://f-droid.org/en/packages/software.mdev.bookstracker/
[21]: https://play.google.com/store/apps/details?id=software.mdev.bookstracker
[22]: https://github.com/mateusz-bak/openreads
[23]: https://apps.apple.com/us/app/openreads/id6476542305
[24]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[25]: https://itsfoss.com/#/portal/signup
