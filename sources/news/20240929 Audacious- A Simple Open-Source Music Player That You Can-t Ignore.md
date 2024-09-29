[#]: subject: "Audacious: A Simple Open-Source Music Player That You Can't Ignore"
[#]: via: "https://news.itsfoss.com/audacious/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Audacious: A Simple Open-Source Music Player That You Can't Ignore
======
This music player is straightforward to use, and yet versatile.
[![][1]][2]

If you have been around for a longtime, you probably have seen how audio players have evolved over the years, some have stuck to the old 90s approach, some have gone for a more [minimal approach][3].

Irrespective of the style you prefer, you want an audio player that works, doesn't mess up big playlists, and is, in general, free to get your hands on.

[Audacious][4] is one such option, which, we think, is worthy of being the [App Of The Week][5]. So, join me as I show you around this open-source audio player for Linux.

### Audacious: Audio Player For Pros

![][6]

As an audio player that identifies itself as being the descendant of [XMMS][7], Audacious is a **C++-based** piece of software which was first introduced back in October 2005;

That's over 18 years now! 🤯

Needless to say, it has evolved over the years, with useful improvements and features being implemented frequently, and an active community backing it.

#### ⭐ Key Features

Being a feature-packed audio player, Audacious has a long list of features, some key ones include:

  * Support for both X11 and Wayland sessions on Linux.
  * Choice to switch between Qt 6 and GTK 3, Qt is the default.
  * Cross-platform app, available for Linux, Windows, and macOS (via [Homebrew][8]).



#### 💻 User Experience

Initially, when I started Audacious up on my Ubuntu 22.04.4 laptop, **there was no audio output from the speakers**. To fix that, I had to go into the settings and change the output plugin setting to use _PulseAudio Output_ , as my setup was using PulseAudio on [PipeWire][9].

Just a little troubleshooting tip there if you face the same 💡

Moving on, I added a free album by [50 Cent][10] to the app, with the process for adding it being pretty straightforward. I just clicked on the folder button to add a folder containing all the songs.

Likewise, I could also add individual files by clicking on the green + button.

![][11]

When the songs started playing, the progress bar started up, showing, well, the progress of course, I was able to control playback by using the various controls near it.

The song list was easy to understand, and the album art was shown in the lower part of the app, alongside a small blue-colored visualizer. At the very bottom of the interface were some important details related to the file being played.

![Important Menus of Audacious][12]

At the top of the main interface were all the usual menu options like _File_ , _Playback_ , and _Playlist_ that let me add new files/folders/URLs, control the music, manage the playlist, check the song info, etc.

![Song Info & Audio Settings][13]

The information about a song was in line with what the file had on it, and the settings menu was a loaded one with many options to tweak the appearance, audio, network, playlists, and plugins.

When I was done setting it all up, Audacious looked something like this. 👇

![][14]

The **support for multiple floating windows was the highlight of Audacious for me** 🤩

I was able to open up one for album art, another for checking out the plugins' settings, drag/drop the VU Meter into the main window, pop out a blur scope visualizer, with the freedom to do much more 🤯

**To wrap this up** , I will say that, people who want more features and control than a typical audio player should absolutely give Audacious a try.

It's open-source, it's free, what more do you want? 🤔

**Suggested Read** 📖

![][15]

### ⚙️ Installing Audacious on Linux

The most simple way of getting the latest release of Audacious is to get it from the [Flathub store][16]. You can also get it from the [official website][17], but you will have to manually install the _tar.bz2_ packages.

If you are new to Linux, follow our [Flatpak guide][18] for help.

[Audacious (Flathub)][16]

If interested in the source code, or want to contribute to the development of Audacious, then visit the project's [GitHub][19] repo.

_💬 Know of any other feature-rich audio players for Linux? Feel free to add them in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/audacious/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/decibels/
[4]: https://audacious-media-player.org/
[5]: https://news.itsfoss.com/tag/app-of-the-week/
[6]: https://news.itsfoss.com/content/images/2024/08/Audacious_a.png
[7]: https://en.wikipedia.org/wiki/XMMS
[8]: https://brew.sh/
[9]: https://pipewire.org/
[10]: https://en.wikipedia.org/wiki/50_Cent
[11]: https://news.itsfoss.com/content/images/2024/08/Audacious_b.png
[12]: https://news.itsfoss.com/content/images/2024/08/Audacious_c.png
[13]: https://news.itsfoss.com/content/images/2024/08/Audacious_f.png
[14]: https://news.itsfoss.com/content/images/2024/08/Audacious_h.png
[15]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[16]: https://flathub.org/apps/org.atheme.audacious
[17]: https://audacious-media-player.org/download
[18]: https://itsfoss.com/flatpak-guide/
[19]: https://github.com/audacious-media-player/audacious
