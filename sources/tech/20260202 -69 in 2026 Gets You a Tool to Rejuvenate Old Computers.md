[#]: subject: "$69 in 2026 Gets You a Tool to Rejuvenate Old Computers"
[#]: via: "https://itsfoss.com/news/picoide-crowdfunding-campaign/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

$69 in 2026 Gets You a Tool to Rejuvenate Old Computers
======

[![Warp Terminal][1]][2]

If you have been warming up to the idea of owning [physical media][3] or preserving your existing collection before it fades away, then **PicoIDE** should interest you.

The work of [Polpotronics][4], this is **an open source IDE/ATAPI emulator** meant to replace aging tech like CD-ROM drives and hard disks. If you don't know what those are, you probably weren't around back then. ☠️

The job of the PicoIDE is quite simple; it can take in disk images ( _e.g., ISO, .bin/.cue, .vhd_ ) from microSD cards and present them to your vintage computer as real IDE hard drives or ATAPI CD-ROM drives.

### PicoIDE: Physical Media FTW

The [PicoIDE][5] is powered by a [Raspberry Pi RP2350][6] microcontroller and fits into a standard 3.5-inch drive bay found on most old hardware. It uses a regular 40-pin IDE connector and gets power through the standard 4-pin Molex connector.

For storage, it reads disk images off microSD cards formatted in FAT32 or exFAT. There are **two variants** for it; the _**Base**_ one handles image switching through a DOS utility or by swapping the microSD card.

The _**Deluxe**_ version adds an OLED display and physical buttons so you can browse and switch images directly on the device. It also has WiFi for managing images through a web interface.

The device supports PIO modes 0-4 and multi-word DMA modes 0-2 for data transfer. It also has a proper audio setup with a [TI PCM5100A DAC][7] that outputs high quality analog CD audio through both an MPC-2 header and a 3.5mm line-out jack.

You can also create or modify disk images using emulators like [86Box][8] or [WinUAE][9] ( _the name is unrelated to a certain soulless regime_ ).

As for why anyone would need such a device, the [Crowdsupply][10] page for the project gives a fine example. Load your entire CD game library onto one microSD card, organize it, and switch between titles using the front panel or DOS utility.

The CD audio output **even works with mixed-mode discs** that have [redbook][11] audio tracks, which software emulators can't handle, they add.

### 💰 Funding the PicoIDE

![][12]

As of writing this, the PicoIDE had **reached its funding goal of $35,000** and was going strong at $100,339 raised.

If you want to get your hands on it, then you can pitch in a minimum of **$69** for the _**Base**_ variant, which gets you a fully assembled PicoIDE board along with its enclosure.

If you can go the extra mile, then **$110** gets you the _**Deluxe**_ variant, which is the same thing but with two color options and more bits, as mentioned earlier.

[PicoIDE][10]

You should also keep an eye on PicoIDE's [GitHub][13] repo. The design files and source code will go live there before units start shipping.

* * *

**Suggested Read 📖:** [_These Linux Distros Turn Your PC into a Retro Gaming Console_][14]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/picoide-crowdfunding-campaign/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://en.wikipedia.org/wiki/Physical_media
[4]: https://polpotronics.com/
[5]: https://picoide.com/
[6]: https://www.raspberrypi.com/products/rp2350/
[7]: https://www.ti.com/product/PCM5100A
[8]: https://86box.net/
[9]: https://github.com/tonioni/WinUAE
[10]: https://www.crowdsupply.com/polpotronics/picoide
[11]: https://en.wikipedia.org/wiki/Rainbow_Books#Red_Book_(1980)
[12]: https://itsfoss.com/content/images/2026/02/picoide-pcb-front-back-views.jpg
[13]: https://github.com/polpo/picoide/tree/main/docs
[14]: https://itsfoss.com/retro-gaming-console-linux-distros/
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-254.png
