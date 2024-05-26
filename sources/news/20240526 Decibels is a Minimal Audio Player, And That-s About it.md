[#]: subject: "Decibels is a Minimal Audio Player, And That's About it!"
[#]: via: "https://news.itsfoss.com/decibels/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Decibels is a Minimal Audio Player, And That's About it!
======
A focused audio player to play what you need for the moment.
[![][1]][2]

We Linux users have plenty of audio players to choose from, but, there's always some new option that aims to offer something different. I know it's challenging to develop one, but many still give it a shot.

One such option that I recently came across was “ **Decibels** ”, a minimal audio player app for Linux that doesn't come on too strong at first glance. So, let's check it out!

📋

Psst, a gentle reminder, we recently started a dedicated [Android series][3] where we cover FOSS Android apps.

### Decibels: Overview ⭐

![][4]

Written primarily using TypeScript, Decibels is an audio player that was recently accepted into the [GNOME Incubator][5], where apps land when they are being considered to be included into the GNOME desktop environment.

The lead developer, [Angelo Verlain][6], worked on this to make it a reality, while also taking many cues from a [couple of mockups][7] that Allan Day from GNOME shared a few months ago.

Some **key highlights** of the app include:

  * **Minimal User Interface**
  * **Intuitive Audio Controls**
  * **Support for Many File Formats**



#### Initial Impressions 👨‍💻

I tested the official Flatpak package on an Ubuntu 22.04 LTS installation, where I added an audio file to Decibels by using the “Open…” option.

When the file loaded, a neat-looking waveform animation started playing in sync with the audio, which could be dragged forward or backward to change the timestamp of the audio being played.

![][8]

The **audio controls were useful too** ; there was the usual playback slide control, a dedicated option to change the speed of playback, options to move 10s forward/backward, a pause/play button, and the volume slider.

You can also use keyboard shortcuts to control the Decibels app. For that, you can refer to the three-ribbon menu on the top-left of the app to get started.

![][9]

And that's all there is to the app, a focused media playing experience.

If you ask me, **Decibels is a great match for you if you want to play single audio files** , such as an audiobook or a podcast. However, if you were looking for features like audio queuing and playlists, this is not the one for you.

You can try other [music players available for Linux][10]:

![][11]

### 📥 Get Decibels

For getting the latest Decibels release, the [Flathub store][12] is your friend.

[Decibels (Flathub Store)][12]

You can also run the following command to get it installed on your Flatpak-equipped system:

```

      flatpak install flathub org.gnome.Decibels

```

Then, to run it, either launch it from the app launcher or run this command:

```

    flatpak run org.gnome.Decibels

```

If you are interested in the source code, or want to contribute to it, head to Decibels' [GitLab repo][13].

_💬 Did this app pique your interest? Do you have some other app in mind? Feel free to add your thoughts below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/decibels/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/tag/android/
[4]: https://news.itsfoss.com/content/images/2024/04/Decibels_a.png
[5]: https://gitlab.gnome.org/GNOME/Incubator
[6]: https://www.vixalien.com/
[7]: https://gitlab.gnome.org/Teams/Design/app-mockups/-/blob/master/audio-player/audio-player.png
[8]: https://news.itsfoss.com/content/images/2024/04/Decibels_b.png
[9]: https://news.itsfoss.com/content/images/2024/04/Decibels_c.png
[10]: https://itsfoss.com/best-music-players-linux/
[11]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[12]: https://flathub.org/apps/org.gnome.Decibels
[13]: https://gitlab.gnome.org/GNOME/Incubator/decibels
