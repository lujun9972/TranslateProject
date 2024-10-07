[#]: subject: "Converting Raspberry Pi into an eBook Reader? Yes, you can do that!"
[#]: via: "https://news.itsfoss.com/raspberry-pi-to-ebook-reader/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Converting Raspberry Pi into an eBook Reader? Yes, you can do that!
======
An interesting project to make an open-source Amazon Kindle-like device.
[![][1]][2]

[eBooks][3] have revolutionized how we consume books in today's digital age, they have made way for storing enormous amounts of books on compact devices and storage mediums, allowing for unmatched portability, when compared to physical books.

On Linux, there are plenty of [good eBook reader apps][4]. But, many people prefer consuming eBooks on dedicated devices called [e-readers][5], which usually come equipped with [electronic paper][6] ( _e-paper_ ) displays that are easy on the eyes.

However, some of **the most popular ones are those that are proprietary**. You have device families such as the [Amazon Kindle][7], the [Kobo][8], and the [PocketBook][9] in this segment.

But, what if I told you that you could build one for yourself? That too, by taking advantage of open-source resources?

### piEreader: Something For The DIYers

![piEreader v5 with some other piEreader boards.][10]

Meant to be a proof-of-concept, the piEreader is an open-source project by [Guyrandy Jean-Gilles][11] for building **Raspberry Pi-based e-readers** that support a range of file formats like _EPUB_ , _MOBI_ , _PDF_ , _CBZ_ , and more.

The project has been made freely available under the [AGPL v3.0][12] License, with **the main goal being to create an open-source, self-hostable eBook reading platform** that anyone can deploy and tweak to their liking.

Powered by Raspberry Pi hardware such as the [Compute Module 4][13], there have been **five distinct versions** of the piEreader so far:

  * [piEreader v1][14], which was the first one, acting as the [MVP][15].
  * [piEreader v2][16], which features a dedicated PCB that follows the [Raspberry Pi HAT][17] spec.
  * [piEreader v3][18], which brought about the [LVGL][19] port of the GUI, alongside server syncing with [Calibre][20].
  * [piEreader v4][21], which saw the addition of a custom carrier board made to match the Compute Module 4 form factor.
  * [piEreader v5][22], the most advanced one with a touchscreen, front-light, and battery power.



📋

You can see v1 in action over on Jean-Gilles' [Instagram][23].

**Suggested Read** 📖

![][24]

All of those have a long list of hardware and software components that make the project possible, and Jean-Gilles thanks [The Open Book][25] project, on which the piEreader relies on for the e-reader software. Similarly, [MuPDF][26] is used to manage the books.

For the display, piEreader uses an e-ink one _(a popular e-paper display brand_ ) manufactured by [Good Display][27], and the firmware for that is from [Waveshare][28].

On the repo for the v5 board, I noticed there were some pending tasks that would definitely make it a more complete version than any of the ones that came before.

There are planned tasks like adding a virtual keyboard, support for entering Wi-Fi credentials, URL input from the graphical user interface (GUI), a device enclosure, and the possibility of going for a 6-inch e-paper display.

**Support for more hardware platforms** based on the 2×20 pin header form factor, like the ones found on the Pine [A64-LTS][29], Pine [SOQUARTZ][30], and [Core3566][31], is also planned for introduction in the future.

#### Want To Build Your Own?

If you are someone who knows their way around Raspberry Pi-based DIY projects, then you can give piEreader's [GitLab][32] repo a visit. It contains information such as the fabrication files, the bill of materials, and the software required to make it all happen.

[piEreader][32]

The different variants have folders in their respective branches, so you can focus on whichever variant you want to put together.

_💬 Are you going to build a piEreader? Let me know in the comments below!_

**Via:** [XDA][33]

**Suggested Read** 📖

![][24]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/raspberry-pi-to-ebook-reader/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Ebook
[4]: https://itsfoss.com/best-ebook-readers-linux/
[5]: https://en.wikipedia.org/wiki/E-reader
[6]: https://en.wikipedia.org/wiki/Electronic_paper
[7]: https://www.amazon.com/Amazon-Kindle-Ereader-Family/b?ie=UTF8&node=6669702011
[8]: https://gl.kobobooks.com/collections/ereaders
[9]: https://pocketbook.ch/en-ch/catalog
[10]: https://news.itsfoss.com/content/images/2024/10/piEreader_v5.jpg
[11]: https://www.linkedin.com/in/guyrandy/
[12]: https://www.gnu.org/licenses/agpl-3.0.en.html
[13]: https://www.raspberrypi.com/products/compute-module-4/?variant=raspberry-pi-cm4001000
[14]: https://gitlab.com/guyjeangilles/piereader/-/tree/v1
[15]: https://en.wikipedia.org/wiki/Minimum_viable_product
[16]: https://gitlab.com/guyjeangilles/piereader/-/tree/v2
[17]: https://itsfoss.com/raspberry-pi-hat/
[18]: https://gitlab.com/guyjeangilles/piereader/-/tree/v3
[19]: https://lvgl.io/
[20]: https://manual.calibre-ebook.com/server.html
[21]: https://gitlab.com/guyjeangilles/piereader/-/tree/v4
[22]: https://gitlab.com/guyjeangilles/piereader/-/tree/v5
[23]: https://www.instagram.com/p/CpthhhAjAM9/
[24]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[25]: https://github.com/joeycastillo/The-Open-Book
[26]: https://mupdf.com/
[27]: https://www.good-display.com/
[28]: https://www.waveshare.com/
[29]: https://pine64.com/product/pine-a64-lts/
[30]: https://pine64.com/product/soquartz-2gb-compute-module-w/
[31]: https://www.waveshare.com/core3566.htm
[32]: https://gitlab.com/guyjeangilles/piereader/
[33]: https://www.xda-developers.com/piereader-project-build-open-source-ereader-raspberry-pi/
