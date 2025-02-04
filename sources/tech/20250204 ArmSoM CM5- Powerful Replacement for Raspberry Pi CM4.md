[#]: subject: "ArmSoM CM5: Powerful Replacement for Raspberry Pi CM4"
[#]: via: "https://itsfoss.com/armsom-cm5/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ArmSoM CM5: Powerful Replacement for Raspberry Pi CM4
======

[![Warp Terminal][1]][2]

From the title, you might be thinking: yet another clickbait post. But I mean it when I say this, ArmSoM has truly delivered something special.

[ArmSoM][3], yet again, has sent us their [Compute Module][4] 5 (CM5) with its [IO board][5] for review. Last time, I tested and reviewed their AIM7 board, and my head was blown by its sheer performance. With an [RK3588 SoC][6], 8GB of RAM, and 32GB of storage, it was a beast.

This time around, we’re looking at the [CM5][7], powered by the [RK3576][8], a slight step down from the RK3588 but still impressive.

It comes with 8 GB of RAM (though a 16 GB version is available) and 64 GB of onboard eMMC storage. On paper, it’s shaping up to be a serious contender in the world of compute modules.

In this review, I’ll walk you through its hardware specifications, software support, benchmarks, AI capabilities, and my personal thoughts.

Let’s dive in!

### CM5 Specifications

![Source: ArmSoM][9]

The ArmSoM Compute Module 5 is a compact powerhouse built around the RK3576 SoC, an octa-core processor that’s both fast and efficient.

With support up to 16GB of LPDDR5 RAM and up to 128GB of onboard eMMC storage, it offers twice the memory and storage options of the Raspberry Pi CM4.

**What makes it even better?** It uses the same 100-pin connector as the CM4, making it compatible with Raspberry Pi IO boards.

Plus, it supports 4K@120fps video output, giving you ultra-smooth visuals for high-resolution displays.

Specification | ArmSoM CM5
---|---
Processor | RK3576 SoC
CPU Architecture | Quad-core ARM Cortex-A72 & Quad-core Cortex-A53
GPU | ARM Mali G52 MC3 GPU
Memory | Up to 16GB LPDDR5
Storage | eMMC storage (optional capacities)
Display Output | 1x HDMI 2.1, 1x DP
Video Resolution | Supports 4K@120fps
Network Interface | 1x Gigabit Ethernet port
USB Ports | 1x USB3.0，1x USB2.0
GPIO | 40-pin GPIO
Expandability | 2x PCIe/SATA/USB 3.0 SS
Camera Interface | 1x 4-lane MIPI CSI, 1x 2-lane MIPI CSI
Display Interface | 1x 4-lane MIPI DSI
Power Input | 5V
Dimensions | 55mm x 40mm
Operating System Support | Debian, Android, Ubuntu, etc.

### CM5-IO board Specifications

![Source: ArmSoM][10]

The CM5-IO board is designed to make the most of the CM5 module. It features an HDMI output for 4K displays, four USB 3.0 ports for peripherals, and a Gigabit Ethernet port with PoE support.

There’s also an SD Card slot and an M.2 slot for adding fast storage or PCIe devices.

With dual MIPI CSI camera interfaces and a 40-pin GPIO header, it’s perfect for projects that demand flexibility.

It’s compact, functional, and pairs seamlessly with the CM5 module to deliver a complete development platform.

Specifications
---
1x HDMI output
4x USB 3.0 Type-A
Gigabit Ethernet RJ45 with PoE support
Firmware flashing and device mode via USB Type-C
GPIO: 40-PIN header
Power connector: DC Barrel jack for 12V power input
Expansion: M.2 (M-key, supports PCIe), microSD
MIPI DSI: 1x 4-lane MIPI DSI, supports up to 4K@60fps (x4)
MIPI CSI0: 1x 4-lane MIPI CSI, each lane up to 2.5Gbps
MIPI CSI1: 1x 2-lane MIPI CSI, each lane up to 2.5Gbps
Others: HPOUT, FAN, VRTC
Dimensions: 100 x 80 x 29 mm (3.94 x 3.15 x 1.14 inches)

### Unboxing and first impression

The CM5 and its IO board arrived fully assembled, tucked neatly inside a sturdy, no-nonsense package. While the box wasn’t flashy, it did its job well, everything was secure and free of unnecessary fluff.

![Sorry for the potato looking image quality][11]

The first thing I noticed was the compactness of the CM5 module. It’s small, yet it feels solid in hand, like it means business. Looking closely, you can immediately spot the essentials: the RK3576 SoC sitting at the heart of the module, flanked by the eMMC storage chip and LPDDR5 RAM.

![][12]

The layout is efficient and clean, with every component neatly placed. Even the tiny antenna connectors for Bluetooth and WiFi are exposed, ready to connect to external antennas for better wireless performance.

Flipping it over, the 100-pin connector on the back stands out.

![][13]

The CM5 is designed to work seamlessly with Raspberry Pi IO boards, making it an excellent choice for anyone looking to upgrade their Pi-based projects.

![ArmSoM CM5 supports Raspberry Pi IO board | Source: ArmSoM][14]

The IO board, which came paired with the module, is equally impressive. It’s larger than the CM5 itself but just as well-built.

![][15]

Ports and connectors are thoughtfully arranged, from the HDMI output and USB 3.0 ports and 40-pin GPIO header.

![][16]

and don't forget that this IO board also has an M.2 slot unlike [Raspberry Pi 500, which came in news with its unpopulated M.2 slot][17].

![][18]

### Setting it up

Getting started with the CM5 was refreshingly simple. The module slid perfectly into the IO board, just look for the markings on the board.

![][19]

And to my surprise, this time I didn't have to rely on other sources, as ArmSoM has provided a great [documentation for setup][20] and links to all the OS images.

![][21]

### OS Installation & first boot

If you are coming from Raspberry Pi ecosystem, you might find it difficult to flash OS images into CM5 but during my experience with AIM7, it was an ease for me.

![][22]

[RKDevTool][23] is required to flash an OS image in Rockchip devices.

![Flashing Android 14 image to CM5 using RKDevTool][24]

##### Debian

The CM5 came pre-installed with ArmSoM’s custom Debian image, which saved me the hassle of flashing an OS right out of the box.

When I powered it on, the board booted into Debian in under 30 seconds, thanks to the onboard eMMC storage.

![][25]

However, there was a small hiccup: the default locale was set to Chinese. While this threw me off for a moment, Google Translate came to the rescue. I’ve covered a detailed guide on [how to change locales in Debian][26].

Once the language barrier was out of the way, everything ran smoothly. The system felt responsive, and the ArmSoM image came with just the right balance of pre-installed utilities to get started without feeling bloated.

##### Android 14

ArmSoM doesn’t just stop at Debian; they also provide an Android 14 image for the CM5, and I couldn’t resist the idea of running Android on this tiny yet powerful board.

Installing it was straightforward, though slightly different from the usual process. Instead of burning the image to an SD card or eMMC, you need to flash it as firmware using the **RKDevTool** utility.

The process was smooth, and once the flashing was complete, I rebooted the system.

I was greeted with the Android boot animation, and in no time, the familiar Android home screen appeared. Interestingly, the display was in portrait mode, which felt a bit odd on my monitor but didn’t hinder functionality.

The Android image was barebones - just the essentials, nothing more. I scrolled through the settings, checked out the "About" section, and explored the file manager. It felt snappy and responsive, but that was about it.

One noticeable omission was the absence of the Google Play Store. If you’re keen on having it, you can install it using [**Open GApps Project**][27].

However, since I was pressed for time, I skipped that step and instead sideloaded Geekbench for Android from [APKMirror][28] to get straight to benchmarking.

### Performance testing

Now comes the most awaited section, the benchmarks!

It’s one thing to talk about specs on paper, but how does the CM5 actually perform in real-world tests? To keep things simple, here’s what I tested:

  * **Geekbench Performance** : Evaluating CPU and overall system power.
  * **AI Capabilities** : Testing the NPU for AI-related workloads.
  * **YouTube Playback** : Checking video performance and hardware acceleration.



📋

The Geekbench test was conducted using the Geekbench Android app. For AI testing, I used the pre-installed Debian image. YouTube performance was tested in the Chromium browser inside Debian as well, with hardware acceleration enabled.

#### Geekbench results

The Geekbench results gave us a good glimpse of the CM5's raw power. With a **Single-Core Score of 321** and a **Multi-Core Score of 1261** , the CM5 delivers solid performance.

![][29]

The single-core score of **321** might seem modest, but it’s adequate for basic tasks like file compression ( **54.9 MB/sec** ) and lightweight navigation ( **2.34 routes/sec** ).

![][30]

If you’re planning to use the CM5 for simple applications, like hosting a lightweight server or running scripts, this score is sufficient.

However, for tasks that demand high single-threaded performance like intensive image processing or compiling large programs, you might notice some lag.

![][31]

The multi-core score of **1261** is where the RK3576 shines. This score reflects the strength of its eight cores working together, making it ideal for multitasking and workloads that can leverage parallel processing.

#### AI workload

The CM5’s 6 TOPS NPU is designed to handle AI inference efficiently, just like its big sibling, the AIM7.

It supports **RKNN-LLM** , a toolkit that enables deploying lightweight language models on Rockchip hardware with optimized performance.

![Source: RKNN-LLM][32]

To test its capabilities, I ran the **TinyLLAMA model with 1.1 billion parameters** , and the results were consistent with the AIM7.

The NPU achieved a throughput of **13 or 14 tokens /second** , showcasing its ability to handle lightweight AI workloads with ease.

![][33]

With NPU handling AI tasks, the GPU stays free for other workloads. This makes CM5 ideal for edge AI projects where efficient resource use is key.

#### YouTube playback

YouTube playback is my favorite test for any SBC because it’s where many boards, including the Raspberry Pi (even the Pi 5), still stumble.

Playing 1080p consistently is a challenge for most, and 4K? Forget about it. But the CM5 completely shattered my expectations.

Running Chromium on Debian with hardware acceleration enabled, I tested videos at 1080p, 1440p, and 4K. The CM5 didn’t just handle it, it crushed it.

Even at 4K resolution, the playback was smooth, with less than 10 dropped frames throughout the video. That’s right, 4K on an SBC, and it worked beautifully.

What’s more impressive is how efficiently it handled the load. Thanks to hardware decoding, CPU usage stayed low, leaving the board cool and responsive.

I even recorded a video of the CM5 playing a 4K YouTube video to showcase its capabilities.

If you’re considering the CM5 for a media server or as a replacement for your Android TV box, this performance makes it an easy choice. It’s rare to see this level of multimedia smoothness on an SBC, and the CM5 delivers it effortlessly.

### What about Raspberry Pi CM5?

I don't want to sugarcoat it, the Raspberry Pi CM5 outperforms the ArmSoM CM5 in raw processing power, and the benchmarks make that crystal clear.

![][34]

In single-core performance, the Raspberry Pi CM5 delivers a stellar 804 compared to the ArmSoM CM5’s modest 321. That’s a difference of 39.9%, and it’s noticeable in tasks that rely on single-threaded performance, like browsing, lightweight applications, or running certain server processes.

The gap widens further in multi-core performance, where the Pi CM5 scores an impressive 1651, leaving the ArmSoM CM5 trailing at 1261 a 76.4% lead that makes the Pi CM5 the clear choice for CPU-intensive tasks.

That said, the ArmSoM CM5 isn’t trying to play the same game. It’s built with a different focus, and its strengths lie elsewhere.

The 6 TOPS NPU on the ArmSoM CM5 is a game-changer for AI workloads, allowing it to handle tasks like language models or image recognition with ease, something the Raspberry Pi CM5 lacks entirely.

### Final thoughts

After spending time with the ArmSoM CM5, it’s clear that this little board has carved out its niche.

It may not outshine the Raspberry Pi CM5 in raw CPU benchmarks, but it brings its own strengths to the table.

The built-in NPU, seamless 4K playback, and thoughtful design make it a compelling choice for AI-driven edge projects, media servers, or even as a replacement for an Android TV box.

What impressed me most was its support for Raspberry Pi IO boards.

I feel that, the ArmSoM CM5 isn’t trying to be a Raspberry Pi killer. Instead, it’s a specialist board that excels in areas where the Pi falters.

As I wrap up this review, I'm also thinking about running some emulators on the CM5 to dive deeper into its GPU performance and for the fun of it.

Recently, many retro game emulation videos have been popping up in my feed, and they’re tempting me to dip my toes in.

If you want to see that, let me know in the comments section! 🕹️

--------------------------------------------------------------------------------

via: https://itsfoss.com/armsom-cm5/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.armsom.org/
[4]: https://itsfoss.com/compute-module/
[5]: https://docs.armsom.org/armsom-cm5-io
[6]: https://www.rock-chips.com/a/en/products/RK35_Series/2022/0926/1660.html
[7]: https://www.armsom.org/cm5
[8]: https://www.rock-chips.com/a/en/products/RK35_Series/2024/1212/2033.html
[9]: https://itsfoss.com/content/images/2025/01/armsom-cm5.jpg
[10]: https://itsfoss.com/content/images/2025/01/cm5-io-layout.png
[11]: https://itsfoss.com/content/images/2025/01/cm5-unboxing.jpg
[12]: https://itsfoss.com/content/images/2025/01/cm5-front-side.jpg
[13]: https://itsfoss.com/content/images/2025/01/cm5-back-side.jpg
[14]: https://itsfoss.com/content/images/2025/01/cm5-on-rpi-cm4-io.png
[15]: https://itsfoss.com/content/images/2025/01/cm5-top-view.jpg
[16]: https://itsfoss.com/content/images/2025/01/cm5-io-front-view.jpg
[17]: https://www.jeffgeerling.com/blog/2024/pi-500-much-faster-lacks-m2
[18]: https://itsfoss.com/content/images/2025/01/cm5-io-back-side-1.jpg
[19]: https://itsfoss.com/content/images/2025/01/cm5-slot-alignment-with-io-1.jpg
[20]: https://docs.armsom.org/armsom-cm5
[21]: https://itsfoss.com/content/images/2025/01/cm5-os-images-download.png
[22]: https://itsfoss.com/content/images/2025/01/flashing-os-in-cm5.jpg
[23]: https://dl.radxa.com/tools/windows/RKDevTool_Release_v2.96_zh.zip
[24]: https://itsfoss.com/content/images/2025/01/cm5-rkdevtool.png
[25]: https://itsfoss.com/content/images/2025/01/running-debian-in-cm5.jpg
[26]: https://itsfoss.com/p/e019c28b-ba2c-4df6-8019-db2e517baada/
[27]: https://opengapps.org
[28]: https://www.apkmirror.com
[29]: https://itsfoss.com/content/images/2025/01/geekbench-results-all.png
[30]: https://itsfoss.com/content/images/2025/01/cm5-single-core.png
[31]: https://itsfoss.com/content/images/2025/01/cm5-multicore-result.png
[32]: https://itsfoss.com/content/images/2025/01/rkllm-framework-1.jpg
[33]: https://itsfoss.com/content/images/2025/01/tinyllama-cm5-rknn-llm-1.png
[34]: https://itsfoss.com/content/images/2025/01/rpi-cm5-vs-armsom-cm5-geekbench.png
