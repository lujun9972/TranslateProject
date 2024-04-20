[#]: subject: "Switcheroo: Convert Your Images With This Open-Source App for Linux!"
[#]: via: "https://news.itsfoss.com/switcheroo/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Switcheroo: Convert Your Images With This Open-Source App for Linux!
======
Easily convert images using this free and open-source Linux app!
If you are like me, you have to deal with plenty of image files that are not necessarily in the correct format for your use case. I usually use the proprietary [XnConvert][1] app to get the job done, but, for me, the need for an open-source image converter app remains.

Luckily, I have found **a great open-source image converter app for Linux** that gets the job done. It's called “Switcheroo”, and you might find it familiar. Let's dive in!

### Switcheroo: Overview ⭐

![][2]

Formerly known as [Converter][3], Switcheroo is a neat image conversion app that has been written almost completely in the Rust programming language, and is part of the [GNOME circle][4].

It **supports a wide range of image formats** that include, _JPEG_ , _PNG_ , _WebP_ , _AVIF_ , _BMP_ , _HEIF_ , _JXL_ , _TIFF_ , and more.

Other than that, here are its **key highlights** :

  * **Open-Source**
  * **Fast Conversions**
  * **Minimal User Interface**



#### Initial Impressions 👨‍💻

The installation went smoothly thanks to the official Flatpak package, and I added a PNG file for conversion by clicking on the “ _Open Images…_ ” button. I tried dragging and dropping images into Switcheroo, but the app just crashed; more on that later.

![][5]

Switcheroo allowed me to convert images into formats like _JPG_ , _HEIF_ , _AVIF_ , _WebP_ , etc. with **options to tweak the quality of the output** , **setting the background color** for converting transparent images, **ability to resize** them, and **set a resize algorithm**.

![][6]

I could also **convert multiple images at a time** by adding them using the “ _Plus_ ” button on the top-left of the app.

![][7]

The preferences' menu had many options, such as pasting from the clipboard, opening a new window, clearing the existing window, enabling more file formats, etc.

![][8]

Overall, I will say that **Switcheroo does what it's advertised to do**. However, on my GNOME 42.9-equipped system, I encountered random bugs while opening files and dragging/dropping images into the app.

Interestingly, it worked just fine when I tested it on a GNOME 46-equipped system, so I would suggest you run Switcheroo on newer GNOME releases to avoid the above-mentioned issues.

### 📥 Get Switcheroo

You can find Switcheroo on the [Flathub store][9], or if you are up for an adventure, then you can visit its [GitLab repo][10].

[Switcheroo (Flathub Store)][9]

You can also run the following command to get it installed on your Flatpak-equipped system:

```

    flatpak install flathub io.gitlab.adhami3310.Converter

```

_💬 Did you like what Switcheroo has to offer? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/switcheroo/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.xnview.com/en/xnconvert/
[2]: https://news.itsfoss.com/content/images/2024/04/Switcheroo_a.png
[3]: https://itsfoss.com/converter-tool/
[4]: https://circle.gnome.org/
[5]: https://news.itsfoss.com/content/images/2024/04/Switcheroo_b.png
[6]: https://news.itsfoss.com/content/images/2024/04/Switcheroo_c.png
[7]: https://news.itsfoss.com/content/images/2024/04/Switcheroo_d.png
[8]: https://news.itsfoss.com/content/images/2024/04/Switcheroo_e.png
[9]: https://flathub.org/apps/io.gitlab.adhami3310.Converter
[10]: https://gitlab.com/adhami3310/Switcheroo
