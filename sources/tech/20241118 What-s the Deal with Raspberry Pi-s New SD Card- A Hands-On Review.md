[#]: subject: "What's the Deal with Raspberry Pi's New SD Card? A Hands-On Review"
[#]: via: "https://itsfoss.com/raspberry-pi-sd-card/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What's the Deal with Raspberry Pi's New SD Card? A Hands-On Review
======

[![Warp Terminal][1]][2]

The [Raspberry Pi Foundation][3] recently introduced a new [microSD card][4] specifically designed for their beloved range of single-board computers.

As an essential component for Raspberry Pi enthusiasts, the microSD card plays a vital role in ensuring smooth operation, quick access to data, and stability for various projects.

This launch aims to enhance user experience, but how does it really stack up? In this review,

I’ll dive into its features, capabilities, and real-world performance compared to industry heavyweights like Samsung, WD, and HP.

### Specifications

  * A2 microSD cards with support for DDR50 and SDR104 bus speeds and command queueing (CQ) extension
  * Speed Class: C10, U3, V30, A2
  * Random 4 KB read performance: 3,200 IOPS (Raspberry Pi 4, DDR50) 5,000 IOPS (Raspberry Pi 5, SDR104)
  * Random 4K write performance: 1,200 IOPS (Raspberry Pi 4, DDR50) 2,000 IOPS (Raspberry Pi 5, SDR104)
  * Shock-proof, X-ray–proof, and magnet-proof
  * 32 GB32 GB, 64 GB, or 128 GB capacity
  * Available unprogrammed or pre-programmed with Raspberry Pi OS.
  * microSDHC / microSDXC formats
  * Compatible with microSDHC- and microSDXC-supporting host devices



### Key features and capabilities

The new [Raspberry Pi microSD card][4], developed in partnership with [Longsys][5] (the same company behind [Amazon Basics SD cards][6]), promises a significant boost in performance, especially when paired with [Raspberry Pi’s Operating System][7].

This is largely due to the implementation of [**Command Queuing**][8] in the OS, which is said to streamline tasks and enhance read/write speeds.

Raspberry Pi offers these cards in several capacities (32 GB, 64 GB, and 128 GB), aiming to cater to a wide range of users, from casual tinkerers to professional developers.

What sets these cards apart, at least on paper, is the claimed optimization for the Raspberry Pi ecosystem.

But before we get into the performance side of things, let's decode some of the cryptic symbols and terms you might find on your typical SD card.

### A2, UHS, and Speed Classes: What are they?

When shopping for SD cards, you’ve likely noticed terms like **A2** , **UHS-1** , and **U3**.

These aren’t just marketing fluff but provide valuable insights into a card’s performance capabilities.

  * **A2** (Application Performance Class 2): SD cards with an A2 rating are optimized for running apps, meaning faster random read/write speeds—crucial for Pi users running lightweight applications or databases.
  * **UHS (Ultra High Speed)** : UHS-1, UHS-2, and UHS-3 refer to the card’s bus speed. UHS-1 can theoretically hit 104 MB/s, while UHS-3 is significantly faster, but only certain devices can leverage this speed.
  * **Speed Class** : This is often denoted by a number inside a circle or a U-shaped symbol (e.g., Class 10 or U1). Class 10 or U1 cards guarantee a minimum write speed of 10 MB/s, essential for recording HD videos or handling large data files.



The new Raspberry Pi microSD card falls under the A2 and UHS-1 categories, meaning it should handle both general file operations and some light app hosting without much fuss.

But how does it perform in the real world?

### Performance: Raspberry Pi SD card vs. the competition

🚧

The performance of SD cards can vary depending on the device, environment, and testing setup used. For the purpose of this article, all SD cards have been tested using the Raspberry Pi's inbuilt card reader to ensure consistent results across the board. However, real-world performance may differ slightly based on your setup or if using an external card reader.

I ran a series of tests to gauge how the official Raspberry Pi SD card compares to industry leaders like **Samsung** , **Western Digital** , **Sandisk & HP.**

![][9]

Using the [**fio**][10] tool for benchmarking, I measured **sequential read/write speeds** , which are essential metrics for evaluating performance in Raspberry Pi setups.

Here’s how the 64 GB Raspberry Pi card stacked up:

💡

All the 16 GB cards are a decade old from my old camcorder, I just tested them for fun.

![Command Queuing was turned On at the time of testing][11]

and here's the data for Random read/ write performance:

![Command Queuing was turned On at the time of testing][12]

#### Command queuing advantage?

While most cards performed similarly in sequential operations, the Raspberry Pi microSD card’s advantage became apparent in random operations, thanks to **Command Queuing**.

This feature significantly boosted random read/write speeds, especially in the 32 GB and 64 GB variants, offering up to **3x** the performance boost compared to alternatives like the Samsung EVO Plus and WD Purple.

### Summary of the benchmark tests

Based on these benchmarks, the new Raspberry Pi microSD card is clearly optimized for its target hardware, excelling in random read/write speeds where it matters most for Raspberry Pi users running complex workloads or multiple apps.

But does that mean you should rush out to buy one?

#### Pros

  * **Optimized for Raspberry Pi OS** : The card works best with the OS it was designed for, offering clear performance advantages.
  * **Command Queuing** : This feature sets it apart from the competition in specific use cases like random operations.
  * **Value in Certain Markets** : In the EU, these cards are priced competitively, often undercutting brands like Samsung and Amazon Basics.



#### Cons

  * **Availability and Pricing** : In some regions, like the US, the card is priced at a premium. You may find better value in alternatives like Samsung or Western Digital for similar sequential performance.
  * **Performance Plateau** : The performance gains taper off at higher capacities, making the card less appealing for users needing 128 GB or larger storage.



### Verdict: Should you buy?

This decision comes down to **price** and **specific needs**. If the card is priced reasonably in your region, and you’re after those random performance boosts, it’s worth considering.

Otherwise, plenty of alternatives can provide the same speed without the extra markup.

### Conclusion

Raspberry Pi’s official microSD card delivers on its promise of enhanced performance, especially when paired with the Raspberry Pi OS and its unique Command Queuing feature.

It’s a solid choice for those looking to maximize their Pi’s potential, but depending on where you are and how you use your Pi, it might not always be the best bang for your buck.

Evaluate your needs, check the pricing in your region, and make an informed decision that works best for you.

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-sd-card/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.raspberrypi.com
[4]: https://www.raspberrypi.com/products/sd-cards/
[5]: https://www.longsys.com
[6]: https://www.amazon.com/Amazon-Basics-microSDXC-Memory-Adapter/dp/B08TJRVWV1?th=1
[7]: https://www.raspberrypi.com/software/
[8]: https://datasheets.raspberrypi.com/sd-card/sd-card-product-brief.pdf
[9]: https://itsfoss.com/content/images/2024/10/RPi-SD-Card-testing.jpg
[10]: https://fio.readthedocs.io/en/latest/fio_doc.html
[11]: https://itsfoss.com/content/images/2024/10/rpi-microsd-seq-read-and-write-1.png
[12]: https://itsfoss.com/content/images/2024/10/rpi-microsd-random-read-and-write.png
