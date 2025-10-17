[#]: subject: "Looking for Open Source Kindle Alternatives? Build it Yourself"
[#]: via: "https://itsfoss.com/open-source-ebook-readers-options/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Looking for Open Source Kindle Alternatives? Build it Yourself
======

[![Warp Terminal][1]][2]

The e-ink display technology arrived on the scene as the answer for a long list of issues and desires people had with digital book reading. The strain on the eyes, the distractions, the low battery life—all of it fixed in one swoop.

While the most popular option that remains in the category is an Amazon Kindle, not everyone of us would want a DRM-restricted Big Tech ecosystem.

As a Linux user and open source enthusiast, I wanted something more 'open' and thus I scoured the World Wide Web and came up with a few interesting options.

I have put them into two categories:

  * DIY: You use a board like Raspberry Pi Pico and you build it yourself thanks to the blueprint provided by the project developer. This is for hardware tinkerers.
  * A couple of non-DIY options that may be considered here.



Needless to say, you should not expect a polished, out of the box eBook experience like Amazon Kindle but that's not what we are aiming for here, are we?

Also, I have not tested these projects on my own. As much as I would like to, I don't have enough money to get all of them and experiment with them.

### 1\. The Open Book

The Open Book project is the definitively DIY ebook reader project. It is based on the **Raspberry Pi Pico** , and makes a point of having to buy a minimum number of components. The pins on the Pico make it easy to control all necessary actions including button controls, power controls, etc. The firmware is called _libros,_ which needs to be flashed onto the Pico. It also uses a library called Babel that gives it the ability to display the text of all languages in the world, which is a major advantage.

![][3]

  * **Display:** 4.2" GDEW042T2 display, designed for fast refreshing
  * **Formats supported:** Plain UTF-8 text, TXT files (a converter is given by the creator)
  * **Battery:** 2 AAA batteries
  * **Cost:** Can differ depending on the cost of the hardware you decide to go with, but a decent build can be made at about $130.



The PCB for the main board as well as the e-paper driver are easily printable because the schematics are [given by the creator][4]. The instructions for setting up the device and getting books ready to be read on the device are given very clearly and concisely on the website.

### 2\. ZEReader

[ZEReader][5] is a device inspired by The Open Book, making another iteration of the **Raspberry Pi Pico** based e-ink device. This project is relatively more convenient as it provides a USB-C port for charging. The convenience is not only limited to the usage, but also the assembly. The software is based on [Zephyr Real-Time OS][6], which makes it easier for the software to be adapted to other hardware boards as well.

![][7]

  * **Display:** 7.5" Waveshare ePaper display
  * **Formats supported:** EPUB, very basic HTML parsing
  * **Battery:** LiPo battery
  * **Cost:** Unknown



For navigation, there are 4 buttons designed on the casing. The board is printable with [schematics available online][8], and the parts can be gathered as the user pleases according to the requirements. There's a micro SD card necessary for storage of files. The instructions can all be found on the [GitHub page][9], along with the information of the parts and software commands. Get more information on our [news article][10] about the device.

### 3\. Dual-Screen E-Reader

The big idea behind this project is getting back to the feeling of reading a two-paged book instead of a single-page pamphlet-like structure like a Kindle provides. A button press to change the page moves both the pages ahead, making it feel more natural, similar to an actual book.

Instead of a full single-board computer like a Raspberry Pi, this uses a SoC, **ESP32-S3**. This provides a significant edge to the power consumption, drawing very low power as it is in the reading mode, but in the deep sleep mode, which occurs after 10 minutes of inactivity, it reduces power consumption even more dramatically, basically never needing to be turned off.

![][11]

  * **Display:** 2 x 4.2" panels
  * **Formats supported:** EPUB, basic HTML
  * **Battery:** 2 x 1300 mAh batteries
  * **Cost:** Original creator's estimate is a little over $80.



The parts are all laid out in a very concise list on the originating [Reddit post][12] with all the relevant information linked there effectively. The project is posted on [Yanko Design][13] as well in a well written post.

### 4\. piEreader

The piEreader aims for a fully open approach, that includes the hardware, software, and even a server to host a library. The heart of the device is a [**Raspberry Pi Compute Module**][14], giving it more capabilities than an average microcontroller.

The display on the build has a touch-screen as well as a backlight. The software revolves around MuPDF, which is a very well known popular e-book reader on the Linux platform.

![][15]

  * **Display:** [4.2" e-paper display][16]
  * **Formats supported:** EPUB, MOBI, CBZ, PDF, etc.
  * **Battery:** Lithium battery
  * **Cost:** Unknown



The [Hackaday page][17] contains all the necessary information, and the [GitLab page][18] hosts all the necessary code. It is worth noting that the creator has been able to successfully try out the software on other boards like PINE64-LTS, SOQUARTZ, etc. as well. Read more about this device in our [news article][19].

### 5\. TurtleBook

Taking an extremely practical approach, the creator of TurtleBook made some really innovative choices.

First, and as they mention, most e-book readers have a lot of unnecessary features when mostly all that is needed is turning a page. As such, the reader doesn't have any physical buttons. It works on gestures, which can be used to switch pages, open menus and adjust brightness, among other things.

Also since e-ink technology doesn't require a lot of power, the power setup is solar with hybrid capacitors, making it truly autonomous and one-of-a-kind. The device is based on an **Arduino MEGA2560 board**.

![][20]

  * **Display:** Waveshare 5.3" e-ink display, and a small OLED panel for easily accessing the menu options
  * **Formats supported:** CB files (custom formatting website is given by the creator)
  * **Battery:** Hybrid capacitors
  * **Cost:** $80-$120



All the necessary parts and the links to them are provided by the creator in a list on the [GitHub page][21], as well as the schematics for the PCBs and 3D-printable casing. There are two options, one with SRAM, a charger and WiFI capabilities and the other one with no charger or WiFi. The [Instructables][22] page for the device has very detailed instructions for the entire process, making it one of the most friendly options on this list.

### 6\. EPub-InkPlate

![][23]

[Inkplate 6][24] from Soldred Electronics is basically an ESP-32 based e-Paper display. Inkplate uses recycled screens from old, discarded e-Book readers. Excellent intiative.

The project is open source both software and hardware wise. While you can build a lot of cool devices on top of it, the [EPub-InkPlate project][25] allows you to convert it into an eBook reader.

Although, the GitHub repo doesn't seen any new updates since 2022, it could be worth giving a shot if you already have an InkPlate display.

### 7\. PineNote (not DIY)

While not DIY like the other projects on the list, [PineNote][26] is from the company Pine64, which has been one of the most actively pro-open source companies in recent times.

Since it is pre-built by a proper manufacturer, it can provide a lot of stable features that the DIY projects might lack. To start with, it is immensely powerful and has a Linux-based OS. It has a 128 GB eMMC storage, 4 GB RAM, and am ARM processor.

![][27]

  * **Display:** 10.3" multi-touch e-ink panel with frontlighting and an optional Wacom EMR pen
  * **Formats supported:** PDF, MOBI, CBZ, TXT, etc. virtually any format
  * **Battery:** 4000 mAh lithium battery
  * **Cost:** $400 (I know but it's not just an e-Book reader)



It also is charged by USB-C and can be expanded into different sorts of projects, not just an e-book reader since it is based on an unrestricted Linux OS.

### Special Mention: paper 7

Don't confuse this paper 7 with the [Paper 7 e-ink tablet from Harbor Innovations][28]. That is also an excellent device but not open source.

Yes. [paper 7][29] is an open source device, or at [least it is in the process][30]. It is developed by a company called [paperless paper][31] based in Leipzig, Germany. It has been designed mainly as a photo frame, but I think it can be repurposed into an e-book reader.

Presently, the [official integration][32] shows that you can save and read webpages on it. Adding the ability to read PDF and ePUB files would be wonderful.

![][33]

[paper 7][29]

### Conclusion

There are a lot of options to choose from, each with something more distinct than the last. The extent of the open-source philosophy, the amount of effort it might require, the extra features the devices have are some of the factors that might influence your decision when choosing the right device for yourself.

Whatever your choice may be, you might find yourself with a new device as well as a new interest, perhaps, after dabbling into the DIY side of open technology. We wish you the very best for it. Let us know what you think about it in the comments. Cheers!

--------------------------------------------------------------------------------

via: https://itsfoss.com/open-source-ebook-readers-options/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://t43217012.p.clickup-attachments.com/t43217012/5c5eb5bd-4e18-4e48-82ef-1283f04f3b98/The%20Open%20Book.jpg
[4]: https://www.oddlyspecificobjects.com/projects/openbook/
[5]: https://marx.engineer/zereader/
[6]: https://www.zephyrproject.org/
[7]: https://t43217012.p.clickup-attachments.com/t43217012/95d67151-622b-4a3d-981a-c26d8bf11bd8/zereader.jpg
[8]: https://github.com/Allegra42/ZEReader-KiCad
[9]: https://github.com/Allegra42/ZEReader
[10]: https://news.itsfoss.com/zereader-open-source-epub-reader/
[11]: https://t43217012.p.clickup-attachments.com/t43217012/e2d8d078-ced5-4540-b140-6273ae15af0e/dualscreenereader.jpeg
[12]: https://www.reddit.com/r/esp32/comments/1mi8tb4/i_made_a_diy_esp32s3based_dualscreen_ereader/
[13]: https://www.yankodesign.com/2025/08/08/this-genius-dual-screen-e-reader-feels-like-actually-reading-a-book/
[14]: https://itsfoss.com/compute-module/
[15]: https://t43217012.p.clickup-attachments.com/t43217012/bcc0eb63-56eb-492a-b473-9bfb6393b126/piereader.jpg
[16]: https://www.good-display.com/product/617.html
[17]: https://hackaday.com/2024/07/17/free-and-open-e-reader-from-the-ground-up/
[18]: https://gitlab.com/guyjeangilles/piereader
[19]: https://news.itsfoss.com/raspberry-pi-to-ebook-reader/
[20]: https://t43217012.p.clickup-attachments.com/t43217012/ef4562e0-324d-44f1-8189-1266cd05d228/turtlereader.jpg
[21]: https://github.com/fel88/TurtleBook
[22]: https://www.instructables.com/Solar-Powered-Zero-Buttons-E-book-Reader/
[23]: https://t43217012.p.clickup-attachments.com/t43217012/3f32bb79-b671-4f1e-bcda-58b54176f217/inkplate6.jpg
[24]: https://soldered.com/product/inkplate-6-6-e-paper-board/
[25]: https://github.com/turgu1/EPub-InkPlate
[26]: https://pine64.org/devices/pinenote/
[27]: https://t43217012.p.clickup-attachments.com/t43217012/b6ff308a-190f-48bf-b09e-d8ba20dfe737/pinenote.jpg
[28]: https://amzn.to/4qaSzq9
[29]: https://paperlesspaper.de/en/buy-7-inch-epaper-picture-frame
[30]: https://github.com/paperlesspaper/
[31]: https://paperlesspaper.de/en
[32]: https://paperlesspaper.de/en/integrations
[33]: https://t43217012.p.clickup-attachments.com/t43217012/fab02e83-e143-44dc-b04e-9f3d78026d14/paper7.jpg
