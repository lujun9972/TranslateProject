[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Convert Video to GIF in Linux [Terminal and GUI Methods])
[#]: via: (https://itsfoss.com/convert-video-gif-linux/)
[#]: author: (Dimitrios Savvopoulos https://itsfoss.com/author/dimitrios/)

How to Convert Video to GIF in Linux [Terminal and GUI Methods]
======

Animated GIFs are everywhere on the internet. From blog posts to social media, GIFs can be used in a humorous as well as explanatory way.

Even on It’s FOSS, we use GIFs to show a certain step in action. It is better than still images and shorter than loading a video.

In this tutorial, I will show you how to convert a video clip to GIF. I’ll discuss both:

  * Command line way to convert video to GIF
  * GUI tool for converting video to GIF



### Method 1: Create GIF from Video using ffmpeg in command line

![][1]

[FFmpeg][2] is a video and audio converter that can also grab from a live audio/video source. It can also resize video on the fly without compromising the quality.

FFmpeg is a powerful tool and can be used for various scenarios, if you are curious here is the [official documentation][3]. We also have a good [collection of ffmpge usage examples][4].

In this example, I will use the [Linux Mint 20][5] new feature presentation video. I [downloaded the video from YouTube using youtube-dl][6] and then I [trimmed][7] the video to get the first 5 seconds.

Make sure to install ffmpeg using your distribution’s package manager:

```
sudo apt install ffmpeg
```

Once you have selected the video that you want to convert, open your terminal and change directory where your video is saved. Below is a general principle, where input is the actual name of the video, following by the video format and the name that you want your gif to be.

**The output name can be something totally different to the input name**, but I tend to use something similar, as it helps to identify it when you have a folder full of files.

```
ffmpeg -i input_video_file output.gif
```

![][8]

Press the enter key to execute the command and your gif will be ready shortly.

![][9]

You should find the GIF file in the same folder as your video file unless you specified some other path for the output file).

![][10]

### Method 2: Converting video to GIF using Gifcurry GUI application

[Gifcurry][11] is an open-source, easy-to-use app GIF maker app.

It uses ffmpeg and [imagemagick][12] to process video and convert to GIF. It can be used both in command-line and the graphical user interface, although this tutorial will only cover the GUI part.

It can be installed using [snap][13] and other package managers, but I recommend using the [AppImage][14] because I found some issue with other packages.

Before you attempt to open gifcurry, you need to make sure that the required dependencies are already installed.

  * [GTK+ &gt;= 3.10][15]
  * [FFmpeg &gt;= 2.8.15][16]
  * [GStreamer &gt;= 1.0][17]
    * [GStreamer Plugins][18]
  * [ImageMagick &gt;= 6][19]



#### Open and use gifcurry

To make an Appimage executable is very straight forward and you grant the permission at the file properties as following:

![][20]

When you open Gifcurry you will be prompted to navigate to the file that you want to convert and at this example I will use again the initial video. As ffmpeg, Gifcurry is not limited to purely converting videos to gif and vice versa. Some of the features are listed.

#### A few other Gifcurry Features

  * **Add text to gif**
  * **Choose starting time**
  * **Set duration**
  * **Adjust gif width **
  * **Adjust Quality**



![][21]

At the last step, you have to choose the file name, the file format and click save.

![][22]

The final result is here:

![][23]

#### Conclusion

Either you choose the command line or the graphical user interface, your job will get done lightning fast both ways.

Let me know which way you prefer and feel free to request any further explanation at the comments section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/convert-video-gif-linux/

作者：[Dimitrios Savvopoulos][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/dimitrios/
[b]: https://github.com/lujun9972
[1]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/08/Convert-Video-to-gif-in-linux.jpg?ssl=1
[2]: https://ffmpeg.org/
[3]: https://ffmpeg.org/ffmpeg.html
[4]: https://itsfoss.com/ffmpeg/
[5]: https://www.youtube.com/watch?v=7knHfN-NUZk
[6]: https://itsfoss.com/download-youtube-linux/
[7]: https://itsfoss.com/video-trimmer/
[8]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/1-e1596944469134.png?ssl=1
[9]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/2-1.png?ssl=1
[10]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/3-2.png?ssl=1
[11]: https://github.com/lettier/gifcurry
[12]: https://imagemagick.org/index.php
[13]: https://itsfoss.com/use-snap-packages-ubuntu-16-04/
[14]: https://github.com/lettier/gifcurry/releases/tag/6.0.0.0
[15]: https://www.gtk.org/docs/installations/linux/
[16]: https://www.ffmpeg.org/download.html
[17]: https://gstreamer.freedesktop.org/download/
[18]: https://gstreamer.freedesktop.org/modules/
[19]: http://www.imagemagick.org/script/download.php
[20]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/4-1.png?ssl=1
[21]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/5-1.png?ssl=1
[22]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/6-3.png?ssl=1
[23]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/gifcurry.gif?ssl=1
