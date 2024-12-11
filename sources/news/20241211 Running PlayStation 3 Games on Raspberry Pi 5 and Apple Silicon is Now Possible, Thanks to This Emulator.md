[#]: subject: "Running PlayStation 3 Games on Raspberry Pi 5 and Apple Silicon is Now Possible, Thanks to This Emulator"
[#]: via: "https://news.itsfoss.com/ps3-games-raspberrypi-5/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Running PlayStation 3 Games on Raspberry Pi 5 and Apple Silicon is Now Possible, Thanks to This Emulator
======
If you have been wanting to emulate PS3 games on your Raspberry Pi, or
Apple Silicon, powered by Linux, now is the time!
[![][1]][2]

In the world of game emulation, [RPCS3][3] is a well-known name that has been around since 2011, allowing gamers to run [PlayStation 3][4] ( _PS3_ ) games on modern hardware. Over the years, it has steadily evolved into a robust emulator capable of running thousands of PS3 titles.

It **works on Linux, Windows, and macOS** , and is supported by an active community of open source developers and end-users. This collaborative effort has ensured that RPCS3 regularly receives updates, new features, and performance upgrades.

Recently, the developers announced the arrival of [Arm64][5] support, marking a significant step towards embracing the increasingly popular CPU architecture.

### RPCS3 Now Supports ARM64: What To Expect?

An overclocked [Raspberry Pi 5][6] running some popular PS3 games.

In the works since 2021, **the development team of RPCS3 had to go through many obstacles to make this happen**. I won't go into the technical details of it, but be assured that they put in a lot of hard work into making this possible.

To showcase their work, they shared some benchmarking numbers and test videos. We start with the assessments for [Raspberry Pi 5][6], where they installed [Arch Linux ARM][7] ( _for its up-to-date packages_ ), and overclocked the board's CPU to 2900 MHz, and the GPU to 1060 MHz.

They initially tested game rendering with [Vulkan][8], but it caused the system to hang after a short period, requiring a [power cycle][9]. As a result, they switched to testing with [OpenGL][10], where Mesa's [V3D][11] implementation for Broadcom GPUs performed well, rendering all tested games correctly without any visual issues.

However, they had to downscale the resolution to 272p ( _38% resolution scale_ ), as **the onboard GPU on the Raspberry Pi 5 was not powerful enough to render at 720p**. The result was that games were running smoothly at up to 30 FPS.

Now that I think about it, the upcoming [Pilet][12] line of handheld computers will greatly benefit from this. They **can be converted into proper handheld gaming consoles** if someone were to install RPCS3 on it and overclock the Raspberry Pi 5 underneath.

Moving on, **the results were much better on Apple Silicon** , where the RPCS3 team was able to get upwards of ~80 FPS on [some titles][13] when running games natively on macOS with an [Apple M1][14] system.

****Left:**** [Rosetta 2][15] x64 → Arm64 translation layer ****Right:**** Native

They even tested running games on an Apple M1 system with [Asahi Linux][16] installed, and the performance was great there too, though not on the same level as on macOS, as shown above.

![RPCS3 Arm64 build running on an Apple M1 system with Asahi Linux installed. \(Source: RPCS3\)][17]

If you were wondering **what happened to Windows Arm64 support** , well, due to not having access to Arm64 devices that could run Windows, the RPCS3 team had to use an Arm64 [virtual machine][18] to carry out testing.

They faced some issues, but after debugging, they got RPCS3 running on Arm64 Windows. However, due to a lack of testing hardware, only a few sample games were tested. While homebrew games should work, they mention that commercial titles are likely to encounter problems.

Similarly, **for mobile platforms like Android and iOS** , the developers have stated that they have no plans to port RPCS3, citing harassment from users within the mobile emulation community, and issues with the redistribution of modified or malicious builds.

You can find the technical details of this newly added support in the official [announcement blog][19].

### Get RPCS3 for ARM64

The latest Arm64 builds of RPCS3 for **Linux** ( _AppImage_ ) and **macOS** ( _.app_ ) can be downloaded from the [official website][20]. Those **looking to run it on FreeBSD or Windows** will have to build [from source][21].

[RPCS3][20]

**Suggested Read** 📖

![][22]

* * *

[Get It's FOSS Plus Membership][23]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ps3-games-raspberrypi-5/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://rpcs3.net/
[4]: https://en.wikipedia.org/wiki/PlayStation_3
[5]: https://en.wikipedia.org/wiki/AArch64
[6]: https://news.itsfoss.com/raspberry-pi-5/
[7]: https://archlinuxarm.org/
[8]: https://www.vulkan.org/
[9]: https://en.wikipedia.org/wiki/Power_cycling
[10]: https://www.opengl.org/
[11]: https://docs.mesa3d.org/drivers/v3d.html
[12]: https://news.itsfoss.com/pilet-handeld/
[13]: https://www.youtube.com/watch?v=QyeXbg7kXMQ
[14]: https://en.wikipedia.org/wiki/Apple_M1
[15]: https://en.wikipedia.org/wiki/Rosetta_(software)#Rosetta_2
[16]: https://asahilinux.org/
[17]: https://news.itsfoss.com/content/images/2024/12/RPCS3_ARM64_Apple_Silicon_Asahi_Linux.jpg
[18]: https://itsfoss.com/virtual-machine/
[19]: https://rpcs3.net/blog/2024/12/09/introducing-rpcs3-for-arm64/
[20]: https://rpcs3.net/download
[21]: https://github.com/rpcs3
[22]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[23]: https://itsfoss.com/#/portal/signup
