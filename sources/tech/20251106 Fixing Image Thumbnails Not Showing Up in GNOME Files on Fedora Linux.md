[#]: subject: "Fixing Image Thumbnails Not Showing Up in GNOME Files on Fedora Linux"
[#]: via: "https://itsfoss.com/image-thumbnails-missing-gnome/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fixing Image Thumbnails Not Showing Up in GNOME Files on Fedora Linux
======

[![Warp Terminal][1]][2]

I recently [upgraded to Fedora 43][3] and one thing I noticed was that image thumbnails were not showing up in the Nautilus files manager. Not just the recent file [formats like webp][4] or [AVIF][5], it was not even showing up for classic image file formats like png and jpeg.

![Image thumbnails not showing up][6]

As you can see in the screenshot above, thumbnails for video files were displayed properly. Even PDF and EPUB files displayed thumbnails.

Actually, the behvaior was weirdly inconsistent, as it did show thumbnails for some of the older images, and I am these thumbnails were there before I upgraded to Fedora 43 from version 42.

![Thumbnails displayed for some images but not for all][7]

**🔑 The one line solution** : I fixed the issue to display image previews in the file explorer again with one line of command:

```

    sudo dnf install glycin-thumbnailer

```

If you are facing the same issue in Fedora, you can try that and get on with your life. But if you are curious, read on why the issue occurred in the first place and how the command above fixed it. Knowing these little things add to your knowledge and help you improve as a Linux user.

### The mystery of the missing thumbnails

I looked for clues in Fedora forum, the obvious hunting ground for such issues. There were advices to clear the thumbnail cache and restart the Nautilus. My gray cells were hinting that that it was a futile exercise, and it indeed was. It changed nothing.

![][8]

Cleaning the thumbnail cache resulted into losing all image preview. This gave me a hint that _**something did change between Fedora 42 and Fedora 43,**_ as the images from the Fedora 42 time were displaying thumbnails earlier.

#### No thumbnailer for images

I checked the thumbnailer to see what kind of thumbnailers were in use on my system:

```

    ls /usr/share/thumbnailers/

```

And it showed me six thumbnailers and none of them were meant to work with images.

![Various thumbnailers present on my system, none for images][9]

Evince is for documents, gnome-epub for EPUB files, totem for video files, and few more for fonts, .mobi files and office files.

Most distributions use the [pixbuf library][10] for image files and clearly, there were no thumbnailer from gdk-pixbuf2 in my system.

```

    abhishek@fedora:~$ ls /usr/share/thumbnailers/
    evince.thumbnailer                  gnome-font-viewer.thumbnailer       gsf-office.thumbnailer
    gnome-epub-thumbnailer.thumbnailer  gnome-mobi-thumbnailer.thumbnailer  totem.thumbnailer

```

I found it weird because I checked and saw that was properly installed and yet there were no thumbnailers installed from it.

I did reinstall `gdk-pixbuf2`:

```

    sudo dnf reinstall gdk-pixbuf2

```

But even then, it didn't install the thumbnailer:

```

    abhishek@fedora:~$ dnf list --installed | grep -i thumbnailer
    evince-thumbnailer.x86_64                            48.1-1.fc43                          <unknown>
    gnome-epub-thumbnailer.x86_64                        1.8-3.fc43                           <unknown>
    totem-video-thumbnailer.x86_64                       1:43.2-6.fc43                        <unknown>

```

I was tempted to explicitly install `gdk-pixbuf2-thumbnailer` but then I thought to investigate further on why it was gone missing in the first place. Thankfully, this investigation yielded the correct result.

#### Fedora 43 switched to a new image loader

I came [across this discussion][11] that hinted that **Fedora is now moving towards** [**glycin**][12], a Rust-based, sandboxed, and extendable image loading framework. Actually, it is GNOME behind this switch with GNOME version 49.

Interesting but when I checked the installed DNF packages, it showed me a few glycin packages but no thumbnailers.

```

    dnf list --installed | grep -i glycin
    glycin-libs.i686                                     2.0.4-1.fc43                         <unknown>
    glycin-libs.x86_64                                   2.0.4-1.fc43                         <unknown>
    glycin-loaders.i686                                  2.0.4-1.fc43                         <unknown>
    glycin-loaders.x86_64                                2.0.4-1.fc43                         <unknown>

```

And thus I decided to install `glycin-thumbnailer`:

```

    sudo dnf install glycin-thumbnailer

```

![][13]

And this move solved the case of missing image previews. Closed the file manager and opened it again, and voila! All the thumbnails came back to life, even for WebP and AVIF files.

![Image thumbnails now properly displayed][14]

Personally, I feel that glycin is a bit slow in generating thumbnails. I hope I am wrong about that.

📋

If you want to display thumbnails for RAW image files, you need to install `libopenraw` first.

I hope this case file helps you investigate and solve the mystery of missing image previews on your system as well. The solution is a single command, a missing package, but how I arrived at that conclusion is the real fun, just like reading an Agatha Christie novel 🕵️

--------------------------------------------------------------------------------

via: https://itsfoss.com/image-thumbnails-missing-gnome/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/upgrade-fedora-version/
[4]: https://itsfoss.com/webp-ubuntu-linux/
[5]: https://itsfoss.com/view-avif-images-linux/
[6]: https://itsfoss.com/content/images/2025/11/image-thumbnails-not-showing-fedora-gnome-1.png
[7]: https://itsfoss.com/content/images/2025/11/image-thumbnails-displayed-for-some-images-1.webp
[8]: https://itsfoss.com/content/images/2025/11/fedora-image-thumbnail-cache.png
[9]: https://itsfoss.com/content/images/2025/11/fedora-thumbnailers.png
[10]: https://docs.gtk.org/gdk-pixbuf/class.Pixbuf.html
[11]: https://discourse.gnome.org/t/prioritize-glycin-and-papers-thumbnailers-on-gnome-49/31965
[12]: https://gitlab.gnome.org/GNOME/glycin
[13]: https://itsfoss.com/content/images/2025/11/install-glycin-thumbnailer-fedora.png
[14]: https://itsfoss.com/content/images/2025/11/image-thumbnail-displayed-again-fedora.webp
