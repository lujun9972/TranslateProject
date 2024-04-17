[#]: subject: "Obfuscate: The Open-Source Privacy Tool You Need!"
[#]: via: "https://news.itsfoss.com/obfuscate/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Obfuscate: The Open-Source Privacy Tool You Need!
======
Take a step back, use this tool before you share any image online!
Every so often, there are situations where you need to hide some sensitive information from the images you intend to share publicly, or even with a few select individuals or groups.

Maybe you work for a highly secretive organization that deals with classified information and want to maintain the highest standards of [OPSEC][1].

Or perhaps, you are just an individual who does not let sensitive data such as contact details, addresses, or your Social Security number be out in the open when sharing images.

You could manually edit the images, but that would take some time to pull off, more so if you have to deal with numerous images.

What if I told you there's a much simpler way to do that? Yes! Obfuscate is an app to help you with the job.

### Obfuscate: Overview ⭐

![][2]

Primarily written in the Rust programming language, Obfuscate is **free and** **an open-source app that lets users censor private information from images** with the help of some handy tools.

Some **key highlights** of Obfuscate include:

  * **Easy Redactions**
  * **Low Storage Footprint**
  * **Minimal User Interface**



#### Initial Impressions 👨‍💻

I loaded up _The GNU C Reference Manual_ on a PDF reader, and took a screenshot. Then, to check out the abilities of the Obfuscate app, I loaded that image up on the app.

I noticed that the user interface was quite minimal, with **two redaction modes** in the header bar. I started off with the “ _Fill_ ” redaction mode ( _square symbol_ ).

![][3]

After I finished dragging a box over a piece of text, Obfuscate immediately filled the selected area with a black layer, completely hiding the text underneath.

![][4]

There was another “ _Blur_ ” redaction mode ( _droplet symbol_ ) too, but when I switched to that, **a warning popped up** saying that this tool is not secure.

So, you can use the blur tool to hide certain areas in an image that does not involve sensitive information.

![][5]

I tested it by following the same steps I used with the “ _Fill_ ” redaction tool.

As you can see, the _Blur_ method doesn't really hide the contents all that well, and people with the correct tools can recover the text. So, don't use that redaction mode for highly sensitive stuff.

![][6]

For saving any changes, you can head over to the three-ribbon menu and click on “ _Save_ ”, or use the keyboard shortcut “ _Ctrl+S_ ”, to create a new file with the desired edits.

There is also an option to “ _Copy_ ” which will copy the redacted image to your clipboard for easy sharing. You can also use the keyboard shortcut “ _Ctrl+C_ ” to do the same.

![][7]

To wrap this up, I will say this: **Obfuscate is a no-nonsense redaction tool that's easy to learn and use**. For me, this was just the tool I was looking for to use in tandem with [Metadata Cleaner][8].

### 📥 Get Obfuscate

Head over to the [Flathub store][9] to grab the latest Obfuscate release, and did I say it is part of the [GNOME Circle][10]?

If you have a GNOME-equipped system, expect a very comfortable usage experience.

[Obfuscate (Flathub Store)][9]

You can also check out the source code on its [GitLab repo][11].

**Suggested Read** 📖

![][12]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/obfuscate/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://en.wikipedia.org/wiki/Operations_security
[2]: https://news.itsfoss.com/content/images/2024/04/Obfuscate_a.png
[3]: https://news.itsfoss.com/content/images/2024/04/Obfuscate_b.png
[4]: https://news.itsfoss.com/content/images/2024/04/Obfuscate_c-1.png
[5]: https://news.itsfoss.com/content/images/2024/04/Obfuscate_d-1.png
[6]: https://news.itsfoss.com/content/images/2024/04/Obfuscate_f.png
[7]: https://news.itsfoss.com/content/images/2024/04/Obfuscate_g.png
[8]: https://itsfoss.com/metadata-cleaner/
[9]: https://flathub.org/apps/com.belmoussaoui.Obfuscate
[10]: https://circle.gnome.org/
[11]: https://gitlab.gnome.org/World/obfuscate/
[12]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
