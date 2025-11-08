[#]: subject: "This OpenWrt-Based Router Has Swappable Wi-Fi Modules for Future Upgrades"
[#]: via: "https://itsfoss.com/news/turris-omnia-ng/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This OpenWrt-Based Router Has Swappable Wi-Fi Modules for Future Upgrades
======

[CZ.NIC][1], the organization behind the Czech Republic's national domain registry, has been around since 1998. Beyond managing `.cz` domains, they have built a reputation for doing well in carrying out network security research.

Their [Turris][2] router project started as an internal research effort focused on understanding network threats that has now evolved into offering commercial products with rock-solid security and convenient features.

Now, they have launched the Turris Omnia NG, the next generation of their security-focused router line. Like its predecessors, the router is manufactured in the [Czech Republic][3].

## 📝 Turris Omnia NG: Key Specifications

![The front and back views of the Turris Omnia NG.][4]

The Omnia NG **runs on a quad-core ARMv8 64-bit processor** that operates at 2.2 GHz. Despite the horsepower, CZ.NIC opted for passive cooling only. No fans means silent operation, even under load.

**Wi-Fi 7 support comes standard** , with the 6 GHz band hitting speeds of up to 11,530 Mbps. The 5 GHz band maxes out at 8,647 Mbps and the 2.4 GHz band at 800 Mbps, but here's the clever bit: **the Wi-Fi board isn't soldered on**.

Instead, it's an M.2 card. When Wi-Fi 8 or whatever comes next arrives, you can swap the card rather than replace the entire router to take advantage of newer tech. [Planned obsolescence][5] is crying in the corner, btw.

The WAN port supports 10 Gbps via SFP+, or you can use a standard 2.5 Gbps RJ45 connection. LAN gets one 10 Gbps SFP+ port and four 2.5 Gbps RJ45 ports.

**Wondering about cellular connectivity?** Another M.2 slot handles that. Pop in a 4G or 5G modem card for backup internet or as your primary connection. The router supports up to eight antennas simultaneously.

A 240×240 pixel color display sits on the front panel. It shows network status and router stats without you needing to open the web interface. Navigation happens via a D-pad on the front-right of the device.

### Hungry for More?

![][6]

The Omnia NG runs [Turris OS][7], which is based on [OpenWrt][8]. The entire operating system is open source, with its source code available on [GitLab][9]. That OpenWrt base means package management flexibility and full access to the underlying Linux system. You **are not locked into vendor-specific configurations** or limited extensibility.

With 2 GB of RAM onboard, **the router can be used as a virtualization host**. You can run [LXC][10] containers or even full Linux distributions like Ubuntu or Debian on [virtual machines][11].

**For home users** , the Omnia NG can work as a NAS, VPN gateway, or self-hosted cloud server running Nextcloud. The NVMe slot provides fast storage for media servers or backup solutions.

**Small businesses get enterprise-grade security** without enterprise prices. The passive cooling and rack-mount capability make it suitable for compact server rooms.

## 🛒 Purchasing the Turris Omnia NG

Pricing starts around **€520** , though exact amounts vary across retailers. The [official website][12] lists authorized sellers in different regions. Taxes and shipping costs get calculated at checkout based on your location.

[Turris Omnia NG][12]

**Suggested Read** 📖

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/turris-omnia-ng/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.nic.cz/
[2]: https://www.turris.com/en/
[3]: https://en.wikipedia.org/wiki/Czech_Republic
[4]: https://itsfoss.com/content/images/2025/11/turris-omnia-ng-front-1.png
[5]: https://en.wikipedia.org/wiki/Planned_obsolescence
[6]: https://itsfoss.com/content/images/2025/11/turris-omnia-ng-insides.jpg
[7]: https://www.turris.com/en/turris-os/
[8]: https://openwrt.org/
[9]: https://gitlab.nic.cz/turris/os
[10]: https://linuxcontainers.org/
[11]: https://itsfoss.com/virtual-machine/
[12]: https://www.turris.com/en/products/omnia-NG/
[13]: https://itsfoss.com/content/images/icon/android-chrome-192x192-317.png
