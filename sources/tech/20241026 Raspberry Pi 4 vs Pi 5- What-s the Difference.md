[#]: subject: "Raspberry Pi 4 vs Pi 5: What's the Difference?"
[#]: via: "https://itsfoss.com/raspberry-pi-4-vs-5/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Raspberry Pi 4 vs Pi 5: What's the Difference?
======

[![Warp Terminal][1]][2]

When it comes to picking between the Raspberry Pi 4 and newer Pi 5, there’s no wrong choice, both are fantastic single board computers (SBCs).

But let's not sugarcoat it: **while the Pi 4 pushed the boundaries of what SBCs could do, the Pi 5 takes things to another level**.

With updated hardware like a faster CPU, better GPU, and enhanced I/O, the Pi 5 packs more power and versatility than its predecessor. And, it is a significant update in many ways 😄

It’s a leap that’s hard to ignore. So, how much of an upgrade are we talking about? Does it matter to you? Let’s dive in and see.

### Hardware specs

Let's start by taking a closer look at the hardware of both Raspberry Pi 4 and Pi 5 to see how they stack up.

Hardware Specs | Raspberry Pi 4 | Raspberry Pi 5
---|---|---
Processor | Quad-core Cortex-A72, 1.5 GHz | Quad-core Cortex-A76, 2.4 GHz
RAM | 1GB, 2GB, 4GB, 8GB LPDDR4 | 2GB, 4GB, 8GB LPDDR4X
GPU | VideoCore VI, 500 MHz, OpenGL ES 3.1, Vulkan 1.0 | VideoCore VII, 800 MHz, OpenGL ES 3.1, Vulkan 1.2
Storage | MicroSD, USB 3.0 boot support | MicroSD, PCIe Gen 2 slot, USB 3.0 boot support
USB Ports | 2 × USB 2.0, 2 × USB 3.0 | 2 × USB 2.0, 2 × USB 3.0
Networking | Gigabit Ethernet, 802.11ac Wi-Fi, Bluetooth 5.0 | Gigabit Ethernet, 802.11ac Wi-Fi, Bluetooth 5.0
GPIO | 40-pin GPIO | 40-pin GPIO
Power Supply | 5V/3A USB-C | 5V/5A USB-C
Display | 2 × Micro HDMI, up to 4K (Single display) | 2 × Micro HDMI, up to 4K (Dual display), with HDR support
Other | PoE HAT support, MIPI DSI, MIPI CSI | PoE+ HAT support, PCIe 2.0, MIPI DSI, MIPI CSI

### What are the Upgrades?

At first glance, the Raspberry Pi 5 might seem similar to the Pi 4, but several key design changes stand out.

![A side by side hardware comparison between Pi 4 and Pi 5][3]

The major upgrade in the Raspberry Pi 5 is the addition of a PCIe Gen 2 slot, which allows for faster storage and expansion through an adapter.

The display and camera interfaces have been upgraded, with new connectors replacing the older DSI and CSI ports with two four-lane MIPI interfaces, making it easier to attach peripherals.

Additionally, Pi 5 now **features a built-in power button** and a real-time clock (RTC), though you’ll need to add a battery to make the RTC function.

Perhaps most notably, the new **RP1** chip is now dedicated to handling all I/O operations, managing devices like cameras, screens, USB peripherals, and network connectivity, streamlining the board’s performance overall.

### Power requirements

When it comes to power requirements, the Raspberry Pi 4 and Pi 5 have distinct needs. While the performance difference could be obvious, you do not want an incompatible power source.

The Raspberry Pi 4 typically requires a 5V, 3A power supply, which is relatively straightforward and **compatible with a range of power sources.**

In contrast, the Raspberry Pi 5 demands a higher 5V, 5A power supply due to its increased power consumption.

This higher requirement means that to avoid constant undervoltage errors and ensure stable operation, **it’s crucial to use the official Raspberry Pi 5 power supply.**

### Who's the hottest? Temperature check!

When it comes to cooling, the Raspberry Pi 4 and Pi 5 differ significantly.

**The Pi 4, with its lower power demands, can generally manage heat with basic passive cooling solutions** like heat sinks, though active cooling is recommended for more intensive tasks.

However, **the Raspberry Pi 5, with its increased power consumption and upgraded CPU, runs noticeably hotter** , **making adequate cooling a necessity**.

During testing, both my Raspberry Pi 4 and Pi 5 were housed in passive-cooled cases, and there was no thermal throttling observed. However, I did notice that the Pi 5 became quite hot to the touch.

Thus, I would recommend that you invest in an active cooling solutions such as fans or more advanced heat sinks.

You can check out this review of the [Pironman 5 case][4] by Abhishek. This should get you what you need for a cool Raspberry Pi setup.

![][5]

##### Pironman 5 Case With Tower Cooler and Fan

This dope Raspberry Pi 5 case has a tower cooler and dual RGB fans to keep the device cool. It also extends your Pi 5 with M.2 SSD slot and 2 standard HDMI ports.

[Explore Pironman 5][6]

### Performance benchmark: Putting the Silicon to the test

Now that we know that, they have some significant differences. For your use case, you can decide better if you get to see some synthetic test numbers.

Of course, the Raspberry Pi 5 will take the lead, but it is important to see by how much.

Maybe, Raspberry Pi 4 has enough computing power to run what you need? Or, perhaps you need to spend that little extra for a Raspberry Pi 5?

Fret not, **I tested both Raspberry Pi 4 and Pi 5 through their paces using Geekbench and Sysbench**.

[Geekbench][7] numbers provide a clear comparison of CPU and GPU performance and [Sysbench][8] helps gauge multicore efficiency and memory handling, giving us a detailed look at how each Pi manages workloads under stress.

Before we begin, here are the details of the Pi that I'm using:

![Specs of the Raspberry Pi's that I used for testing][9]

##### Geekbench

Let's begin with Geekbench, and as you can see, the single-core and multi-core results clearly show the performance differences between the Raspberry Pi 4 and Pi 5.

![Geekbench single-core and multi-core benchmark between Pi 4 & Pi 5][10]

Diving deeper, based on the Geekbench scores, the Raspberry Pi 5 outperforms the Pi 4 significantly, with improvements such as increase in text compression, in image compression, and a boost in HTML5 performance.

![Geekbench score of both Pi's in other important categories like Text & Image compression, Navigation & HTML5 performance to replicate a more real world scenario][11]

##### Sysbench

In the [Sysbench benchmark][8], Raspberry Pi 5 also performed better than Pi 4, highlighting its superior CPU efficiency.

The Pi 5 achieved 4155 events per second compared to the Pi 4’s 2766 events per second, showcasing a substantial performance boost.

Additionally, the Pi 5 shows lower latency, with an average of 0.96 ms versus the Pi 4’s 1.44 ms, ensuring quicker response times under heavy workloads.

Overall, the Pi 5’s improved architecture leads to better event handling, faster execution, and more consistent performance in resource-demanding tasks.

Here's an image for a side by side comparison:

![Sysbench multicore benchmark between Pi 4 & Pi 5][12]

In terms of memory performance, the Raspberry Pi 5 once again does as expected from a newer hardware.

The **Pi 5 handled 37.1 million operations per second** compared to the **Pi 4’s 25.1 million** , highlighting its significantly faster memory processing capabilities.

The Pi 5 also transferred **3631 MiB/sec** , outperforming the Pi 4’s **2452 MiB/sec** transfer rate.

Even with the increased operations, the Pi 5 maintained consistent latency, showing almost no delays during memory tasks.

This boost in memory throughput and lower latency makes the Pi 5 a better choice for memory-intensive applications and workloads.

![Sysbench Memory speed test \(RAM\) between Pi 4 & Pi 5][13]

###

### How Much Do They Cost?

The Raspberry Pi 4 and Pi 5 offer different price points, reflective of their capabilities.

The Raspberry Pi 4 is typically priced around **$35-$55** , depending on the RAM configuration and the retailer.

On the other hand, the Raspberry Pi 5, with its enhanced features and performance, is priced higher, **generally ranging from $60-$80**.

While the Pi 5’s price is a bit higher, both models provide excellent value for their respective price points, catering to a variety of projects and needs.

It's always a good idea to compare prices from different retailers to get the best deal.

### Conclusion

Benchmarks give us a good idea of how powerful a computer is, but they don't always tell the whole story.

I've used both the Raspberry Pi 4 and Pi 5, and while the benchmarks show the Pi 5 is much faster, it's not always that simple in real life. You need to take all things into account and not just benchmark numbers.

Like during my testing with Raspberry Pi OS Desktop, the most noticeable difference was smoother, lag-free YouTube playback and faster boot times on the Pi 5.

It also felt a bit more polished overall, but that could be because my Pi 5 had 8 GB of RAM compared to my Pi 4's 4 GB memory. Other than these small improvements, most of the experience felt pretty similar to me.

In the end, the Raspberry Pi 5 is a big step up from the Pi 4. It's got a faster processor, better memory, and new features like a dedicated power button and, best of all, a PCI-E interface.

_💬 I leave you to decide which better suits your needs, Pi 4 or a Pi 5? What would you pick and why? Do share your thoughts in the comments below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-4-vs-5/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/09/pi4-and-pi5-1.png
[4]: https://itsfoss.com/pironman-5-review/
[5]: https://itsfoss.com/content/images/2024/06/pironman-5.webp
[6]: https://www.sunfounder.com/products/pironman-5-nvme-m-2-ssd-pcie-mini-pc-case-for-raspberry-pi-5?ref=itsfoss
[7]: https://www.geekbench.com/
[8]: https://github.com/akopytov/sysbench
[9]: https://itsfoss.com/content/images/2024/09/benchmark-sys-info.png
[10]: https://itsfoss.com/content/images/2024/09/pi4-vs-pi5.png
[11]: https://itsfoss.com/content/images/2024/09/geekbench-pi4-vs-pi5-compression-benchmark.png
[12]: https://itsfoss.com/content/images/2024/09/sysbench-cpu-test-comparison-1.png
[13]: https://itsfoss.com/content/images/2024/09/sysbench-mem-test-comparison.png
