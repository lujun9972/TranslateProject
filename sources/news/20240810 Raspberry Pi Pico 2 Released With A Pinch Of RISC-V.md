[#]: subject: "Raspberry Pi Pico 2 Released With A Pinch Of RISC-V"
[#]: via: "https://news.itsfoss.com/raspberry-pi-pico-2/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Raspberry Pi Pico 2 Released With A Pinch Of RISC-V
======
The Raspberry Pi Pico 2 is available for just $5!
[![][1]][2]

Generally speaking, [Single-board computers][3] (SBC) like the [Raspberry Pi 5][4] usually steal the limelight when it comes to compact computing. However, those who want something more simple, and less-powered, typically opt for a [single-board microcontroller][5] like the [Arduino Nano][6].

If you were wondering about **the difference between an SBC and a single-board microcontroller** , well, one can run an operating system and is powerful. Whereas, the other is meant for less complex tasks like running just a single program.

In both those areas, [Raspberry Pi][7] is a well-established name, known for their vast range of products that cater to a wide range of use cases.

In a [recent announcement][8], they have introduced a new microcontroller board, the **Raspberry Pi Pico 2** , which incorporates a new chip, and is a successor to [the Pico][9], which was introduced back in 2021.

### Raspberry Pi Pico 2: What to Expect?

![][10]

At the heart of the Pico 2 is a [RP2350][11] microcontroller, which has been derived off the earlier [RP2040][12] chip used on the first Pico.

The board that was used to house the chip features **4 MB of external QSPI flash RAM** , which is both form-factor and electrically compatible with the OG Pico, and features a familiar button to activate USB mass storage mode.

Some **key specs** of the microcontroller include:

  * 2x Arm [Cortex-M33][13] cores running @150 MHz.
  * Support for floating point and DSP.
  * 12 upgraded PIO state machines.
  * Robust security architecture.
  * 520 KB of on-chip SRAM.



During the launch, Raspberry Pi stated that:

> The development of Pico 2 and RP2350 has been an epic, multi-year effort: it is comfortably the second-largest engineering programme we’ve undertaken, behind only Raspberry Pi 5.
>
> Its success is a testament to the incredible talents of the team here, and to the world-class partners who have joined us on the journey.

Moving on, there's another interesting thing in the spec sheet that will catch many people's attention, **the RP2350 comes with two RISC-V cores** that can be used instead of the Cortex-M33 cores during boot time.

The cores are open-source [Hazard3][14] ones, which were developed by a Raspberry Pi Engineer, [Luke Wren][15], in his spare time, and made available under the Apache-2.0 license.

When someone on Reddit [asked][16] **why there was a need for two different types of cores** , another Redditor, _hellotanjent_ replied that:

> The RISC-V cores are relatively small compared to everything else on the chip and they require no licensing fee unlike the ARM cores.
>
> There is some speculation that the inclusion of the RISC-V cores is to help encourage the migration of the existing Pico codebases over to RISC-V so that the Pico 3 (whenever it comes out) can be RISC-V only and remove the ARM licensing fees entirely.

If what they said comes to be, then the cost of future Pico's could go down considerably, as Raspberry Pi won't have to pay [ARM][17] licensing fees, in turn potentially transferring the savings onto their customers.

On the **security side of things** , the RP2350 features a signed boot security model, where booting the binary is only allowed if it has been signed using a private key, with a corresponding public key stored in OTP. This prevents an attacker from running arbitrary code.

But, wait, there's more: the chip also employs additional techniques like a redundancy coprocessor and hardware fast glitch detectors to further deter wrongdoers.

**Raspberry Pi expects there to be issues** with their security measures, and are ready to fix them as they pop up.

To improve bug detection, they are commissioning two third-party firms to audit their security architecture, and are offering **a $10,000 bounty** for the first confirmed break of their signed boot process.

#### 💰 Pricing and Availability

With manufacturing being handled by Sony, the **Pico 2 is available for $5**. You can source it through the many authorized reseller partners, who can be found on the [official website][18].

Additionally, many **partner products based on the RP2350 chip** have also been announced, with options from the likes of [Adafruit][19], [Cytron][20], [Hellbender][21], [Seeed][22], and [Wiznet][23] to name a few.

[Raspberry Pi Pico 2][18]

There are also **plans to introduce a wireless-capable Pico 2 W** by the end of the year, which would be using the same Infineon 43439 modem found on the [Pico W][24].

_💬 Are you going to grab one for a DIY project? Have something more large scale in mind?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/raspberry-pi-pico-2/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Single-board_computer
[4]: https://news.itsfoss.com/raspberry-pi-5/
[5]: https://en.wikipedia.org/wiki/Single-board_microcontroller
[6]: https://store.arduino.cc/products/arduino-nano
[7]: https://www.raspberrypi.org/
[8]: https://www.raspberrypi.com/news/raspberry-pi-pico-2-our-new-5-microcontroller-board-on-sale-now/
[9]: https://news.itsfoss.com/raspberry-pi-pico/
[10]: https://news.itsfoss.com/content/images/2024/08/Raspberry_Pi_Pico_2.jpg
[11]: https://www.raspberrypi.com/products/rp2350/
[12]: https://www.raspberrypi.com/products/rp2040/
[13]: https://developer.arm.com/Processors/Cortex-M33
[14]: https://github.com/Wren6991/Hazard3
[15]: https://www.linkedin.com/in/luke-wren-53590012a/
[16]: https://www.reddit.com/r/embedded/comments/1eniy7m/rp2350_m33_and_ricev/
[17]: https://www.arm.com/
[18]: https://www.raspberrypi.com/products/raspberry-pi-pico-2/
[19]: https://www.adafruit.com/product/6000
[20]: https://www.cytron.io/
[21]: https://www.hellbender.com/
[22]: https://www.seeedstudio.com/Seeed-XIAO-RP2350-p-5944.html
[23]: https://wiznet.io/
[24]: https://www.raspberrypi.com/products/raspberry-pi-pico/
