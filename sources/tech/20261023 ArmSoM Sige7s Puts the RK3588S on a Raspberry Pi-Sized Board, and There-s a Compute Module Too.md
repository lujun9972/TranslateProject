[#]: subject: "ArmSoM Sige7s Puts the RK3588S on a Raspberry Pi-Sized Board, and There's a Compute Module Too"
[#]: via: "https://itsfoss.com/news/armsom-sige7s/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ArmSoM Sige7s Puts the RK3588S on a Raspberry Pi-Sized Board, and There's a Compute Module Too
======

[![Warp Terminal][1]][2]

If you've followed It's FOSS for a while, you probably have seen our previous coverage of ArmSoM devices. I [reviewed the Sige7][3] a while back and came away impressed (cheeky headline and all). Earlier this year, we also covered the [Sige6][4], the first Sige board to swap Rockchip for Allwinner.

Now the Sige lineup is back on Rockchip with the [Sige7s][5]. So, what's changed?

![][6]

### Key Specifications

  * SoC: Rockchip RK3588S, 8nm, 4x Cortex-A76 @ 2.4GHz + 4x Cortex-A55 @ 1.8GHz
  * AI: 6 TOPS NPU (INT4/INT8/INT16)
  * RAM: up to 32GB LPDDR4/4X
  * Storage: removable eMMC module (16GB to 128GB) + microSD
  * Networking: Wi-Fi 6 + Bluetooth 5.0, Gigabit Ethernet with PoE support (add-on module)
  * 2x USB 3.0 + 2x USB 2.0
  * 1x MIPI CSI (up to 5MP camera)
  * CAN, SPI, PWM, 3x UART, 2x I2C, 6x ADC
  * RTC battery connector
  * Headphone out
  * Power and Maskrom buttons
  * 0°C to 80°C operating temperature
  * Size: 85 x 56 x 17mm, same footprint as a Raspberry Pi



![][7]

The Sige7s starts at $153 on ArmSoM's store.

The "s" in the name comes from the chip. The RK3588S is the trimmed-down version of the RK3588 that powers the Sige7. You get the same CPU, the same Mali-G610 MP4 GPU, and the same 6 TOPS NPU. What you lose is peripheral bandwidth. There is no PCIe 3.0, one HDMI output instead of two, no HDMI input, and only one Gigabit Ethernet controller.

In simpler words, the compute is the focus here, the I/O is not. If you want a Rockchip SBC fast NVMe drive or dual networking, this isn't the board for you. If you want RK3588-class power in a smaller package for less money, it is.

![][8]

There are a few more indirect cost optimizations here for the users. Sige7s accepts a wide 5V to 23V input, so you aren't stuck with a specific USB-C power brick. It also uses a **removable eMMC module** , which means your precious storage isn't stuck to the board if you want to upgrade or reflash it on another machine.

On the display side, there's HDMI 2.1 up to 8K@60fps, a DisplayPort 1.4 over USB-C, and a 2-lane MIPI DSI connector. The hardware video engine decodes 8K@60fps H.265/VP9 and encodes 8K@30fps, so it can double as a serious media box.

![][9]

The **40-pin header is Raspberry Pi compatible** , and ArmSoM says it works with [Pi HATs][10], the Pi 7-inch display, the IMX219-based Pi camera, and Pi 4 cooling solutions. That's a good thing if you already have Pi accessories in your stock or if you want to expand the board.

### Prefer a Compute Module? Meet the CM7s

![][11]

Alongside the Sige7s, ArmSoM also offers the [CM7s][12], a compute module built around the **same RK3588S chip**. I checked both spec pages, and the CPU, GPU, NPU, and video engine are identical. It's just a different form factor.

In case you did not know, the compute module contains just the processor, memory, storage, and power management. There are no standard physical input/output ports like USB, HDMI, and Ethernet. Compute modules are more suitable in cases where they need to be embedded.

The CM7s measures 55 x 40mm, pretty much the same size as the Raspberry Pi CM5. Not sure if you can put it into a CM5 carrier board, though.

It's available with up to 32GB LPDDR4/4X RAM and up to 256GB eMMC. Through the 100-pin connectors, it exposes HDMI 2.1, DP 1.4, MIPI CSI/DSI, USB 3.0, PCIe 2.0/SATA, and the usual GPIO buses. ArmSoM has also committed to producing it until at least August 2034, which is reassuring if you're building a product around it.

To get started, there's the CM7s-IO carrier board. It gives you HDMI, USB-C DisplayPort, 4x USB 3.0, Gigabit Ethernet, a 40-pin header, an M.2 M-key slot for NVMe SSDs, microSD, and MIPI camera and display connectors. Unlike the Sige7s, it runs on a 12V DC barrel jack.

### Pricing and Availability

Both boards are available now from ArmSoM's official store, with AliExpress and Taobao listings as well.

The Sige7s starts at $153. Wi-Fi antennas are sold separately, so add those to your cart.

[ArmSoM Sige7s][13]

The CM7s starts at $179.

[ArmSoM CM7s][12]

If you're in the US, note that ArmSoM collects 25% of the product value as prepaid customs duty at checkout (listed as "sales tax"), so there's no surprise bill on delivery.

If you just want a ready-to-use RK3588S computer, go for the Sige7s. If you're designing your own hardware or want an NVMe slot via the carrier board, the CM7s is the one.

ArmSoM hardware might remind you of Banana Pi boards, that's because the two companies are known to work closely together, and the boards often share the same base.

One more thing worth I have noticed. ArmSoM's documentation has improved considerably since I first tried their boards. That's a positive sign because new SBCs often struggle with the documentation and community.

Enjoyed this update? Support independent Linux news coverage

It's FOSS has been helping people use Linux for the past 14 years. Help us stay independent from big tech. Become a Plus member, enjoy ad-free reading and get 5 eBooks.

Plus yearly

Ad-free, FREE ebooks

[Join yearly][14]

Best value

Plus lifetime

Pay once, Enjoy forever

[Go lifetime][15]

Buy us a coffee

Any amount, no commitment

[Support on Ko-fi][16]

Skip the AI slop and SEO spam in your Google results

Tell Google you prefer It's FOSS, and it will show our Linux news and tutorials, created by experienced Linux users, more often when you search. It takes just a click.

[Set as preferred source][17]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/armsom-sige7s/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/arosom-sige7-review/
[4]: https://itsfoss.com/news/armsom-sige6-launched-with-allwinner-soc/
[5]: https://www.armsom.org/sige7s
[6]: https://itsfoss.com/content/images/2026/10/armsom-sige7s-1.webp
[7]: https://itsfoss.com/content/images/2026/10/Sige7s_interface-1.webp
[8]: https://itsfoss.com/content/images/2026/10/Sige7s_interface-2-1.webp
[9]: https://itsfoss.com/content/images/2026/10/armsom-sige7s-2-1.webp
[10]: https://itsfoss.com/raspberry-pi-hat/
[11]: https://itsfoss.com/content/images/2026/10/ArmSom-Cm7s-2.webp
[12]: https://www.armsom.org/cm7s
[13]: https://www.armsom.org/product-page/sige7s
[14]: https://itsfoss.com/#/portal/signup
[15]: https://itsfoss.com/lifetime-membership/
[16]: https://ko-fi.com/itsfoss
[17]: https://www.google.com/preferences/source?q=itsfoss.com
