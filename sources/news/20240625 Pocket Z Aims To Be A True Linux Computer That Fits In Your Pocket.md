[#]: subject: "Pocket Z Aims To Be A True Linux Computer That Fits In Your Pocket!"
[#]: via: "https://news.itsfoss.com/pocket-z-linux-pc/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Pocket Z Aims To Be A True Linux Computer That Fits In Your Pocket!
======
A Linux computer in our pockets? Well, why not!
[![][1]][2]

[Ultra-mobile PCs][3] (UMPC) were all the rage back in the mid-2000s, with many people flaunting their devices as a matter of pride, showing off their multitasking prowess, and what not.

However, the advent of smartphones put a massive dent in their adoption, which has just about made such devices irrelevant in today's time.

That is why I was surprised to see that someone trying to engineer a new line of UMPCs under the “ **Pocket Z** ” name. This is an interesting project that I truly hope catches on.

Allow me to show you what it's all about.

### Pocket Z: What's to Expect?

The project's tagline says, “ _Bring back the PDAs & UMPCs_”, which is being spearheaded by [Patrick Trillsam][4], a professional developer also known as Icepat on the internet who wants to accomplish the following:

> The goal of this project is to create a high quality device good enough to be produced, powerful enough to run a Linux Desktop Environment while being super portable with the lowest price tag possible.

Some other goals of this project also include things like it being pocketable, featuring a decent display, USB-C charging, a keyboard, and a few other things.

Icepat also mentions that **they will be taking inspiration from older pocket computers** like the HP Jornada 720, Psion 5Mx, Psion 3a, and more notably the Sharp Zaurus SL-C700 and 750 as those are their favorites.

The initial iteration of the Pocket Z is powered by a [Raspberry Pi Zero 2W][5], which the project lead admits is not the fastest SBC around.

**Suggested Read** 📖

![][6]

But, they mention that it has some really nifty advantages, such as being cheap, having a low-power draw, being capable enough to run a Linux distro, and featuring a DPI RGB interface for handling the display duties.

Icepat shared an up-close look of the first prototype a few days back.

It features a 7-inch display, a membrane keyboard without keycaps, a Raspberry Pi Zero 2W, space for a Li-Po battery, many connectors, and a PCB to bring them all together.

📋

There are also ****plans for a second set of prototypes**** featuring 5-inch and 7-inch displays, respectively.

As illustrated by the pictures below, everything is exposed. For the display, **the prototype sports a 24-bit DPI RGB 7-inch capacitive touch panel** with a resolution of 1024×600.

![Source: Icepat][7]

The keyboard uses part of the [Ti-92][8] layout for providing a usable keyboard interface, and is powered by an [Atmega32U4][9], which is a cheap/reliable keyboard controller with support for USB HID.

There are **two USB connectors** too, one is a USB-A for connecting commonly used accessories, and the other is a USB-C for powering the entire thing. The Li-Po battery can be charged using that port, with three distinct modes available: _Power_ , _Boost_ , and _Protect_.

They also showcased the Pocket Z prototype running a modified version of Raspberry Pi OS Lite with Xfce and [Conky][10]. There are also **plans to develop a dedicated Linux distribution** for the Pocket Z line of devices, too.

![Source: Icepat][11]

The project lead also mentions a few things that would be nice to have, such as additional GPIOs for expansion boards, a high-quality keyboard, and wireless charging.

Overall, it sounds great, but we have to wait to see the final product, and when it does launch, its future depends on how well it does in terms of consumer demand and sales.

### Want to check it out?

If this project piqued your interest, I highly suggest you head to its Hackaday [project page][12] for learning more about it.

After the second set of prototypes are out, they intend to finalize the keyboard, and an outer shell so that they can **** launch **an initial batch of 50–100 devices which would be priced modestly**.

Doing so allows them to share their work with the community, while also gathering feedback, ideas, and gauging demand.

The project lead is actively looking for other contributors to join in and share their knowledge so that this could one day be a mass production product.

[Pocket Z (Hackaday)][12]

_💬 Projects like these are something that continue to catch my attention. What about you?_

Via: [Tom's Hardware][13]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/pocket-z-linux-pc/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Ultra-mobile_PC
[4]: https://au.linkedin.com/in/patricktrillsam
[5]: https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/
[6]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[7]: https://news.itsfoss.com/content/images/2024/06/Pocket_Z_a-1.jpg
[8]: https://en.wikipedia.org/wiki/TI-92_series
[9]: https://www.microchip.com/en-us/product/atmega32u4
[10]: https://github.com/brndnmtthws/conky
[11]: https://news.itsfoss.com/content/images/2024/06/Pocket_Z_d.png
[12]: https://hackaday.io/project/196625-pocket-z-bring-back-the-pdas-amp-umpcs
[13]: https://www.tomshardware.com/raspberry-pi/raspberry-pi-projects/pocket-z-project-hopes-to-rekindle-pocket-pc-form-factor-with-a-raspberry-pi-zero-2w-inside
