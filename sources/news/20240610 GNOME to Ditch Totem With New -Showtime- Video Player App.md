[#]: subject: "GNOME to Ditch Totem With New 'Showtime' Video Player App"
[#]: via: "https://news.itsfoss.com/gnome-showtime/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

GNOME to Ditch Totem With New 'Showtime' Video Player App
======
It's time for a modern video player app on GNOME.
[![][1]][2]

Even with the advent of online streaming, use of [video players on Linux][3] is still a common sight to see, with many going for options like VLC, MPV player, SMPlayer, etc.

On GNOME, alongside other useful core apps, there is usually the video player called “Totem”, commonly known as “[GNOME Videos][4]”, which has been around for quite some time.

However, this one is being replaced with a newer one, called “ **Showtime** ”, which aims to offer its users a watching experience without distractions.

Let's see what it has to offer.

### Showtime: What to Expect?

![][5]

Inducted into the GNOME [Incubator][6] program, Showtime is a new video player app that has been **primarily written in the Python programming language** , and uses the [GStreamer][7] framework to provide audio/video playback functionality.

While the incubator repo is meant for apps proposed to become a core GNOME app, it has to fulfill a [set of criteria][8], conforming to which will ensure it being included in a GNOME release.

Showtime joins another app called “[Decibels][9]”, which is a minimal player, but for audio. You can also expect it to debut as a core GNOME app in the future.

![][10]

If you were wondering: **Totem was bound to be replaced** , owing to slow maintenance, and being a [GTK3][11] app, which GNOME has been in the process of replacing across their application stack, in favor of [GTK4][12] \+ [Libadwaita][13].

Some keen-eyed among you might've noticed the stripes in the app's header bar in the screenshot above, well, that denotes that it is **an under-development, nightly build of a GNOME app.**

**I tested out the nightly build of Showtime** , and I must say, it didn't disappoint. The user interface was extremely minimal, with all the controls right where I expected them to be.

![][14]

I was able to control the playback using the slider, there were controls to change the volume, go forward/backward 10 seconds in the video, play/pause, and the cogwheel had options to change the playback speed, language, and subtitles.

There were various options when right-clicking on the video to take a screenshot, show its storage location, mute/unmute it and more.

### Want to Try it Out?

The upcoming **GNOME 47 release will most likely feature this** video player **if Showtime achieves the required level of maturity**.

But, if you can't wait, then you can run the following commands to get **a nightly build of Showtime**.

First, ensure that you have [configured][15] the nightly repository on a Flatpak-equipped system:

```

    flatpak remote-add --if-not-exists gnome-nightly https://nightly.gnome.org/gnome-nightly.flatpakrepo

```

Then, run this command to install a nightly build of Showtime:

```

    flatpak install gnome-nightly org.gnome.Showtime.Devel

```

Thereafter, you can launch Showtime from the app launcher, or by running this command:

```

    flatpak run org.gnome.Showtime.Devel

```

If you would like to learn more about this app, head to its [official website][16], and, if you are interested in the source code, then its [GitLab][17] repo is the place to be.

**Suggested Read** 📖

![][18]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/gnome-showtime/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/video-players-linux/
[4]: https://flathub.org/apps/org.gnome.Totem
[5]: https://news.itsfoss.com/content/images/2024/06/Showtime_a.png
[6]: https://gitlab.gnome.org/GNOME/Incubator
[7]: https://gstreamer.freedesktop.org/
[8]: https://gitlab.gnome.org/Teams/Releng/AppOrganization/-/blob/main/OfficialAppDefinition.md
[9]: https://news.itsfoss.com/decibels/
[10]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[11]: https://docs.gtk.org/gtk3/
[12]: https://docs.gtk.org/gtk4/
[13]: https://gitlab.gnome.org/GNOME/libadwaita
[14]: https://news.itsfoss.com/content/images/2024/06/Showtime_b.png
[15]: https://nightly.gnome.org/
[16]: https://apps.gnome.org/Showtime/
[17]: https://gitlab.gnome.org/GNOME/Incubator/showtime
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
