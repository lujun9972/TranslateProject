[#]: subject: "OpenShot: The Underrated Open-Source Video Editor for Linux and Other Platforms"
[#]: via: "https://news.itsfoss.com/openshot/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

OpenShot: The Underrated Open-Source Video Editor for Linux and Other Platforms
======
OpenShot is decently popular, but could use a better spotlight.
[![][1]][2]

If you are into content creation, or even professional video production, **having a good video editor is a must if you want to produce quality results**. For me, I used to run a YouTube channel back in the day, where I used to post videos of my motorcycle riding escapades.

I used to do some basic edits on a Windows machine using Adobe Premiere Pro, and the results used to be tolerable 😝. For a brief period, I experimented with DaVinci Resolve, and that was great too. But, that was around the end of my [motovlogging][3] journey.

Nowadays, I ride a scooter to move around the city. But, that's enough reminiscing. 🤐

On Linux, there are many [great video editors][4] that will make you forget using a Windows machine for simple video editing tasks.

OpenShot is one such option, and our pick for the [App Of The Week][5]. So, let's check it out!

### OpenShot: An Open-Source Video Editor For Everyone

![][6]

Born in a land with no good video editors, [Jonathan Thomas][7] started working on OpenShot at a time ( _2008_ ) when capable video editors for Linux were difficult to come by.

He started [on his own][8], but, along the years, many talented people joined in this endeavor, and now we have an editor that can easily take the fight to other established players in the space.

It is **primarily written using the Python programming language** and is offered under the GNU General Public License (v3.0).

#### ⭐ Key Features

Before we check out what OpenShot can do, here are some key aspects of the editor:

  * **Cross-Platform**
  * **Supports 3D Animations**
  * **Unlimited Tracks/Layers**
  * **Broad File Format Support**



#### 💻 User Experience

I installed OpenShot on an Ubuntu 22.04.4 LTS system to check out what it can do. When I started it up, I could only use the CPU on my Dell G15 5530 laptop for hardware decoding. I tried switching to the on-board NVIDIA GPU, but it didn't work.

So, I proceeded with the CPU, and it fared well for the basic edits I did. For more advanced editing, I suggest using the dedicated GPU on your computer.

A little troubleshooting should help, I had a similar experience for NVIDIA graphics on [Gyroflow][9] last year. Hence, it is safe to say that it is an NVIDIA-specific problem that needs troubleshooting, not OpenShot's fault.

![][10]

I started by creating a new project and adding files to it — a [stock video][11], and a [copyright-free song][12].

I then manually added those to the timeline by dragging and dropping them into Tracks 4 and 5, during which a menu popped up, allowing me to tweak the content before it was put in place.

![][13]

After I was done adding content, the user interface filled up with a video preview being shown on the right of the screen and another window on the left. Do note that I could switch up the layout as I pleased by dragging any of those around.

0:00

/0:36

1×

Adding transitions to a video on OpenShot.

In the lower part, there was **the timeline, with handy controls right above it**. There were tools to add a new track, enable/disable snapping, trim a track, add markers, change the timeline zoom level, and more.

I then started experimenting by adding two transition effects to the video using the “ _Transitions_ ” menu, and, as you can see above, it went as expected.

![][14]

Similarly, **I tried adding a few effects** to the footage; I added a negative filter to the video and a robotic filter to the audio, just to see how those worked. And, I will say, the result was an absolute abomination😂

By no fault of OpenShot, of course, just due to my editing skills and curiosity.

![][15]

I could also **add emojis to the video** , with controls to change its appearance, behavior, etc. Cropping the video and trimming any of the tracks in the timeline was quite straightforward to do as well.

![The video export process in OpenShot.][16]

When I was done, **I went ahead to export the video**. The exporter let me select a video profile, tweak the quality, set the file format, give it a name, and select the folder path.

In the end, [the result][17] speaks for itself. With the basic edits I carried out with the help of OpenShot, nowhere did I feel lost, the user interface was easy to get the hang of, and the application never crashed or acted out.

### ⚙️ Installing OpenShot on Linux

You can grab the latest AppImage for Linux on the [official website][18], which also lists installation packages for ChromeOS, Windows, and macOS. If you are unsure how to use an AppImage, refer to [our guide][19].

[OpenShot][18]

If building from source is your thing, you can head to OpenShot's [GitHub][20] repo to get started. The official [user guide][21] is also a handy resource to learn your way around this video editor.

_💬 Have you used OpenShot to edit videos before? How did your experience go?_

**Suggested Read** 📖

![][22]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/openshot/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Motovlog
[4]: https://itsfoss.com/best-video-editing-software-linux/
[5]: https://news.itsfoss.com/tag/app-of-the-week/
[6]: https://news.itsfoss.com/content/images/2024/08/OpenShot_a.png
[7]: https://www.linkedin.com/in/jonoomph/
[8]: https://www.openshot.org/story/
[9]: https://news.itsfoss.com/gyroflow/
[10]: https://news.itsfoss.com/content/images/2024/08/OpenShot_b.png
[11]: https://www.pexels.com/video/cloudy-mountains-27607601/
[12]: https://ncs.io/onandon
[13]: https://news.itsfoss.com/content/images/2024/08/OpenShot_b2.png
[14]: https://news.itsfoss.com/content/images/2024/08/OpenShot_d.png
[15]: https://news.itsfoss.com/content/images/2024/08/OpenShot_e.png
[16]: https://news.itsfoss.com/content/images/2024/08/OpenShot_j-1.png
[17]: https://imgur.com/a/iowKVZY
[18]: https://www.openshot.org/download/
[19]: https://itsfoss.com/use-appimage-linux/
[20]: https://github.com/OpenShot/openshot-qt/
[21]: https://www.openshot.org/user-guide/
[22]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
