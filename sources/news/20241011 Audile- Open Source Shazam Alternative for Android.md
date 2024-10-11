[#]: subject: "Audile: Open Source Shazam Alternative for Android"
[#]: via: "https://news.itsfoss.com/audile/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Audile: Open Source Shazam Alternative for Android
======
Can you replace Shazam with this open source app? Let's see!
[![][1]][2]

You know, I'm something of a music aficionado myself ([ _Osborn intensifies_][3]).

I listen to many types of music, be it regional or international, and more often than not, I get to listen to some song or the other when I am out and about in the city. Whenever I listen to a new one I like, I immediately pull out my phone and use [Shazam][4] to see which song that is.

It works quite well, but it is not an open-source app. After searching around for a bit, I found **Audile** , an open-source music recognition app for Android, which looked like a viable alternative.

Join me as I take you through my experience with it. 😃

### Audile: An Alternative To Shazam

![Audile's about page.][5]

Freely offered under the [GPL-3.0 License][6], Audile is **powered by two proprietary services** , [AudD][7] and [ACRCloud][8] that make all the music recognition possible. Other than that, most things related to the app are open-source.

The app was formerly known as _MusicRecognizer._

When first launching the app, Audile took me through a quick setup process, which consisted of me allowing the microphone permission for the app and skipping the request for adding an AudD API token; more on this later.

![Audile's quick setup wizard.][9]

After configuration was complete, I found a familiar button at the center to start recognizing music. I loaded up [Tom's Diner][10] on Spotify and played it via the speakers on my laptop.

![Audile's music recognition in action.][11]

Audile took some time, but was **able to successfully detect the song and provided me with handy links for many popular music streaming websites** hosting the same song. It turns out that Audile uses the [Odesli][12] service to retrieve platform-specific links.

![Audile's track info, sharing options and library grid view.][13]

I could also get access to some track info, which showed me that AudD recognized the song at 04:17 p.m ( _or 16:17 for the 24-hour clock folks_ ) and the date it was last recognized on Audile.

Sharing the song with relevant info and streaming links to any of my contacts was quite straightforward too. It worked across most popular social apps.

Similarly, for getting an overview of the recognized songs, the library is a handy place. I had switched it to the grid view, as I usually use that on my media apps, but the default one, the list view, is good too.

![Audile's library filters, music recognition queue, and preferences menu.][14]

I could also search for any specific song, filter through the library, check the music recognition queue, and tweak the application behavior via the preferences menu.

There are other things too, like the option to add a quick settings tile and a home screen widget to get quick access to Audile; those are helpful when you are on the go.

Coming back to the AudD API thing, during my testing, I found out that **a maximum of five music recognition tasks** could be carried out every 24 hours, which is thanks to the limit set in the API. To have greater access, users will have to opt for [paying AudD][15] according to the number of requests; there is a 14-day free trial available as well.

If you ask me, five requests a day seems fine, unless you are at a place with superb music taste who are always playing some good tunes you didn't know. **I also noticed that Shazam works noticeably faster than Audile** , and that's probably due to their much larger and more refined dataset.

### Install Audile

You can grab the latest Audile release from [F-Droid][16] as well as from the project's GitHub [releases page][17].

[Audile (F-Droid)][16]

If you are searching for the source code, the [GitHub][18] repo is the place to be.

**Suggested Read** 📖

![][19]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/audile/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://tenor.com/view/spider-man-norman-osborn-you-know-im-something-of-a-scientist-myself-smiling-gif-24183196
[4]: https://www.shazam.com/
[5]: https://news.itsfoss.com/content/images/2024/10/Audile_x.png
[6]: https://www.gnu.org/licenses/gpl-3.0.en.html
[7]: https://audd.io/
[8]: https://www.acrcloud.com/
[9]: https://news.itsfoss.com/content/images/2024/10/Audile_a-1.jpg
[10]: https://open.spotify.com/track/0oA9wBGDY4uyILLg4GymWP
[11]: https://news.itsfoss.com/content/images/2024/10/Audile_d-1.jpg
[12]: https://odesli.co/
[13]: https://news.itsfoss.com/content/images/2024/10/Audile_g-1.jpg
[14]: https://news.itsfoss.com/content/images/2024/10/Audile_i-1.jpg
[15]: https://audd.io/#:~:text=Terms%20of%20Service-,PRICING,-0%2B%20requests%20per
[16]: https://f-droid.org/en/packages/com.mrsep.musicrecognizer/index.html
[17]: https://github.com/aleksey-saenko/MusicRecognizer/releases/
[18]: https://github.com/aleksey-saenko/MusicRecognizer
[19]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
