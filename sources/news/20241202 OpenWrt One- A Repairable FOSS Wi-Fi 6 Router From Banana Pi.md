[#]: subject: "OpenWrt One: A Repairable FOSS Wi-Fi 6 Router From Banana Pi"
[#]: via: "https://news.itsfoss.com/openwrt-one/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

OpenWrt One: A Repairable FOSS Wi-Fi 6 Router From Banana Pi
======
If you love open source hardware or the ones that give you full rights
to do your own thing, this is one of them!
[![][1]][2]

Taking note of what networking gear you are running is important, as that could make or break your network, be it the sophisticated setups found in data centers, or even the basic one at your home.

For the latter, we usually rely on our [ISP][3] to provide us with the necessary hardware like a modem and router, which usually come combined in a single box. This allows us to connect to their network and, by extension, to the internet.

Sadly, **such devices come preloaded with proprietary firmware and web interfaces** that don't really allow the user to do much if something were to go wrong, limiting their right to repair.

This is where projects like [OpenWrt][4] come in, allowing people to replace the proprietary device firmware with **a Linux-based operating system** that opens up a wide range of possibilities.

Now, the same project has launched **OpenWrt One** , a new Wi-Fi 6 router that combines the principles of software freedom and the right to repair.

### OpenWrt One: What To Expect?

![Source: OpenWrt][5]

OpenWrt, in collaboration with the Software Freedom Conservancy (SFC), [recently announced][6] the launch of OpenWrt One, where they shared some key details of the router.

Built with user control in mind, **the OpenWrt One is designed to be open and unbrickable** , with a switch to separately flash the NOR and NAND portions of the flash memory. This allows anyone to recover their router quickly, even if one of the firmware partitions is corrupted, enabling easy flashes and unmatched customization potential.

In addition, its creators have ensured that it complies with the U.S. FCC's [equipment authorization][7] standards and Europe's [EC/RoHS][8].

The **key specs** of the OpenWrt One include:

  * **SoC:** MediaTek MT7981B ( _Filogic 820_ )
  * **RAM:** 1 GB DDR4
  * **NOR:** 16 MB ( _SPI_ )
  * **NAND:** 128 MB ( _SPI_ )
  * **Wi-Fi:** MediaTek MT7976C ( _Wi-Fi 6_ ) ( _2×2 2.4 GHz + 3×3 5Ghz_ )
  * **Ports:** 1x M.2 2242/2230, 1x 2.5 GbE RJ45 ( _PoE_ ), 1x Gigabit Ethernet RJ45 port, 1x USB-C ( _Serial_ ), 1x USB-C ( _PD15V_ ), and 1x USB 2.0.



**An overview of the OpenWrt One board.** 👇

![Source: Banana Pi][9]

You should also know that [Banana Pi][10] is handling the manufacturing and distribution of the router, with OpenWrt being a frequent collaborator of theirs. Plus, **for each router sold, $10 will go towards the OpenWrt fund at SFC** , helping the project cover hosting expenses and possibly **an OpenWrt summit** in the near future.

### Get OpenWrt One

The variant with the OpenWrt One board, case, 3x 3dB antennas and a 12v power supply cost **$89** for US-based customers ( _excl shipping_ ) on [AliExpress][11]. There is also [a bare-bones kit][12] with just the OpenWrt One board that costs **$68.42** for UK-based customers ( _excl shipping_ ), with the product not being available for US-based customers on AliExpress.

You can alternatively find these on other China-based online marketplaces if you are looking to compare prices or want greater shipping coverage. If you want to learn more about this router, then you can refer to the [official wiki][13] and the Banana Pi [documentation][14].

[OpenWrt One][15]

For the schematics, you can visit the official OpenWrt One [hardware index][16] that lists KiCad files for all the relevant parts and handy instruction guides.

**Suggested Read** 📖

![][17]

* * *

[Get It's FOSS Plus Membership][18]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/openwrt-one/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Internet_service_provider
[4]: https://openwrt.org/
[5]: https://news.itsfoss.com/content/images/2024/12/OpenWrt_One_Router.jpg
[6]: https://sfconservancy.org/news/2024/nov/29/openwrt-one-wireless-router-now-ships-black-friday/
[7]: https://www.fcc.gov/engineering-technology/laboratory-division/general/equipment-authorization
[8]: https://environment.ec.europa.eu/topics/waste-and-recycling/rohs-directive_en
[9]: https://news.itsfoss.com/content/images/2024/12/OpenWrt_One_Board.jpg
[10]: https://www.banana-pi.org/
[11]: https://www.aliexpress.us/item/3256807609464530.html?gatewayAdapt=glo2usa4itemAdapt
[12]: https://www.aliexpress.com/item/1005008143000598.html?gatewayAdapt=4itemAdapt
[13]: https://openwrt.org/toh/openwrt/one
[14]: https://docs.banana-pi.org/en/OpenWRT-One/BananaPi_OpenWRT-One
[15]: https://www.aliexpress.com/item/1005007795779282.html
[16]: https://one.openwrt.org/hardware/
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[18]: https://itsfoss.com/#/portal/signup
