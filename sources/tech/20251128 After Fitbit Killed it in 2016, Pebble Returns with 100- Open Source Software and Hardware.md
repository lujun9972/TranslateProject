[#]: subject: "After Fitbit Killed it in 2016, Pebble Returns with 100% Open Source Software and Hardware"
[#]: via: "https://itsfoss.com/news/pebble-returns-as-open-source/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

After Fitbit Killed it in 2016, Pebble Returns with 100% Open Source Software and Hardware
======

[![Warp Terminal][1]][2]

[Pebble][3], the e-paper smartwatch that first launched on [Kickstarter][4] in 2012, gained a cult-like following for its innovative approach to wearable tech. Sadly, Fitbit acquired and shut it down in 2016, taking with it the [intellectual property][5] (IP) of the brand.

The IP eventually landed with Google after their [Fitbit acquisition in 2021][6].

Earlier this year, the original creator, [Eric Migicovsky][7], relaunched Pebble through Core Devices LLC, a self-funded company operating via the [rePebble][8] consumer brand. This resurrection became possible after [Google open-sourced PebbleOS][9] in January 2025.

Now, Core Devices has [announced something significant][10] for the Pebble community.

### Great News for Pebble Enthusiasts

![A screenshot from the demo in this YouTube video][11]

**The complete Pebble software stack is now open source**. Everything you need to operate a Pebble watch is now available on [GitHub][12]. All of this didn't just materialize overnight; Core Devices has been improving [PebbleOS][13] since its open-sourcing and has been pushing those to the public repository.

The [rebuilt mobile companion apps][14] for Android and iOS just got released as [open source][15] too. Without these apps, a Pebble watch is basically a paperweight. These are built on `libpebble3`, a Kotlin multiplatform library for interacting with Pebble devices.

Similarly, the developer tools have been completely overhauled, with the old Ubuntu VirtualBox VM-based workflow being replaced with a modern browser-based one that allows anyone to [develop Pebble apps in a web browser][16].

__The Pebble Time 2 is very close to coming to market!__

**Hardware schematics are public as well**. The complete electrical and mechanical design files for the [Pebble 2 Duo][17] are now available with [KiCad][18] project files included. You could literally build your own Pebble-compatible device from these files.

**There are some non-free components still in the mix**. The heart rate sensor library for the Pebble Time 2, [Memfault][19] crash reporting, and [Wispr Flow][20] speech recognition all use proprietary code. But, fret not, **these are all optional**. You can compile and run the core Pebble software without touching any of them.

Core Devices also launched two major software systems alongside the open source releases. **The Pebble mobile app now supports multiple app store feeds** that anyone can create and operate.

This works similar to Linux package managers such as [APT][21] or [AUR][22]. Here, users can subscribe to different feeds and browse apps from multiple sources instead of relying on a single centralized server.

Core Devices already operates its own feed at [appstore-api.repebble.com][23]. This feed backs up to the [Internet Archive][24], preserving community-created watchfaces and apps that have been around over the years.

Plus, developers can upload new or existing apps through the new [Developer Dashboard][25]. Monetization remains possible through services like [KiezelPay][26], so creators can still get paid for their hard work.

### Why Open Source Everything?

Migicovsky learned some painful lessons from Pebble's first shutdown. When Fitbit killed the project in 2016, the community was left scrambling with limited options.

The gap between 95% and 100% open source turned out to matter more than anyone expected. Android users couldn't easily get the companion app. Many iOS users faced the same problem.

" _This made it very hard for the Pebble community to make improvements to their watches after the company behind Pebble shut down_ ," Eric explained in his blog post.

The reasoning behind this open source push is straightforward. If Core Devices disappears tomorrow, **the community has everything they need to keep their watches running**. No dependencies, no single point of failure.

Apart from that, **these new Pebble devices will focus on reparability** , with the upcoming [Pebble Time 2][27] ( _expected March-April 2026_ ) featuring a screwed-in back cover, allowing users to replace the battery themselves instead of needing to buy a new device when the battery gives out.

💬 _What are your thoughts on Pebble's comeback? I certainly look forward to new launches by them!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/pebble-returns-as-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://en.wikipedia.org/wiki/Pebble_(watch)
[4]: https://www.kickstarter.com/projects/getpebble/pebble-e-paper-watch-for-iphone-and-android
[5]: https://en.wikipedia.org/wiki/Intellectual_property
[6]: https://blog.google/products/platforms-devices/fitbit-acquisition/
[7]: https://ericmigi.com/
[8]: https://repebble.com/
[9]: https://opensource.googleblog.com/2025/01/see-code-that-powered-pebble-smartwatches.html
[10]: https://ericmigi.com/blog/pebble-watch-software-is-now-100percent-open-source
[11]: https://itsfoss.com/content/images/2025/11/pebble-reborn-demo.webp
[12]: https://github.com/coredevices/pebbleos
[13]: https://pebbleos-core.readthedocs.io/en/latest/
[14]: https://repebble.com/app
[15]: https://github.com/coredevices/mobileapp
[16]: https://developer.repebble.com/sdk/cloud
[17]: https://github.com/coredevices/hardware
[18]: https://www.kicad.org/
[19]: https://memfault.com/
[20]: https://wisprflow.ai/
[21]: https://itsfoss.com/apt-command-guide/
[22]: https://itsfoss.com/aur-arch-linux/
[23]: https://appstore-api.repebble.com/
[24]: https://archive.org/
[25]: https://appstore-api.repebble.com/dashboard
[26]: https://kiezelpay.com/
[27]: https://store.repebble.com/
