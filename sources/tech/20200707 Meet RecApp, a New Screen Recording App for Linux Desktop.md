[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Meet RecApp, a New Screen Recording App for Linux Desktop)
[#]: via: (https://itsfoss.com/recapp/)
[#]: author: (Ankush Das https://itsfoss.com/author/ankush/)

Meet RecApp, a New Screen Recording App for Linux Desktop
======

_**Brief: RecApp is a simple open-source screen recorder tool. It doesn’t boast of huge features but gives you enough to record your screen with a simple user interface.**_

We have plenty of [screen recorders available for Linux][1]. Abhishek prefers to [use Kazam][2] while I like [using SimpleScreenrecorder][3]. Neither of us use the [GNOME’s built-in screen recorder][4].

Recently we were contacted by the developer of RecApp, a new screen recording tool. Since I like experimenting with different applications, I took it upon myself to cover RecApp as this week’s open source software highlight.

### RecApp: A fairly simple screen recorder for Linux desktop

![][5]

[RecApp][6] is an interesting open-source screen recorder tool that does not depend on [FFmpeg][7] and utilizes free [GStreamer modules][8]. If you’re curious, it’s written in GTK.

If you were looking for a simple and open-source solution to record your desktop screen, RecApp could be a solution.

### Features of RecApp

![][9]

Even though RecApp doesn’t offer a lot, it does have the necessary features to record a desktop screen. Here’s what it lets you do:

  * Tweak frames per second settings
  * Add a delay to the recording
  * Select the screen region to record
  * Toggle between high quality and compressed quality.
  * Ability to record audio from apps
  * Toggle to record the cursor or not
  * Choose the folder for saving the video
  * Supports mp4, webm, and mkv formats



The best thing about RecApp is that you don’t have a separate preference box to tweak settings., which makes things less confusing. You get everything in just a single screen and that’s all you have to follow.

### Installing RecApp on Linux

Primarily, it offers a [Flatpack package][10]. So, you can simply refer to It’s FOSS guide on [using Flatpak][11] to install it.

For Fedora, you can utilize the terminal and type in the command to install it:

```
sudo dnf install recapp
```

[Download RecApp][6]

### Conclusion

Though RecApp is a fairly new project but it worked mostly fine in my usage on [Pop OS 20.04][12]. So, take that with a pinch of salt.

RecApp has a simple interface and is easy to use. However, the aspect ratio of the video recorded wasn’t perfect in my case. It was not completely 1080p and I couldn’t find a way to change that. Other than that, I didn’t have any other issues recording my screen.

What do you think about RecApp? What screen recorder do you use to capture your desktop?

--------------------------------------------------------------------------------

via: https://itsfoss.com/recapp/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/best-linux-screen-recorders/
[2]: https://itsfoss.com/kazam-screen-recorder/
[3]: https://itsfoss.com/record-screen-ubuntu-simplescreenrecorder/
[4]: https://itsfoss.com/gnome-screen-recorder/
[5]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/recapp-screenshot.png?ssl=1
[6]: https://github.com/amikha1lov/RecApp
[7]: https://itsfoss.com/ffmpeg/
[8]: https://gstreamer.freedesktop.org/
[9]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/recapp-screenshot-1.png?ssl=1
[10]: https://flathub.org/apps/details/com.github.amikha1lov.RecApp
[11]: https://itsfoss.com/flatpak-guide/
[12]: https://itsfoss.com/pop-os-20-04-review/
