[#]: subject: "The Affordable Pironman Alternative Mini PC Case for Raspberry Pi 5"
[#]: via: "https://itsfoss.com/elecrow-raspberry-pi-5-case/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Affordable Pironman Alternative Mini PC Case for Raspberry Pi 5
======

[![Warp Terminal][1]][2]

[SunFounder's Pironman cases for Raspberry Pi][3] are a huge hit. This bestselling device [converts the naked Raspberry Pi board into a miniature tower PC][4]. The RGB lighting, OLED display and glass casing make it look cool. Full HDMI ports, NVMe ports and active-passive cooling options enhance the functionality of the Pi 5.

This great gadget is too expensive for some people to [buy at $76 for the Pironman][3] and $95 for the dual-NVMe [NVMe Pironman Max][5].

SunFounder knows it and that's why they have [introduced Pironman 5 Mini at $45][6] but have removed the OLED display, full HDMI ports and reduced the number of fans. Dealbreaker? Maybe. Maybe not. But I have come across a new case that has most of the features at a much lower price.

### Elecrow's Pitower

![][7]

Like SunFounder, Elecrow's has been offering gadgets and accessories for Raspberry Pi and other embedded devices for years. Their [CrowView Note][8] and [all-in-one starter kits][9] have been popular among SBC enthusiasts.

They have just r[evealed a new product, a mini PC case for your Raspberry Pi 5 and Jetson Orin Nano][10]. Yes, that doubles the excitement.

![][11]

Parameter | Specification
---|---
Compatible Devices | Raspberry Pi 5 / Jetson Orin Nano
Display | 1.3″ OLED Screen
Material | Aluminum Alloy + Acrylic
Cooling System | 3 × Cooling Fans
Power Control | Integrated Power Button
PCIe Interface (Raspberry Pi Version) | PCIe M.2
Supported SSD Sizes | 2230 / 2242 / 2260 / 2280
RTC (Real-Time Clock) Support | Supported (Raspberry Pi Version)
Dimensions | 120 × 120 × 72 mm
Weight | 500 g
Ports | 2 x Full HDMI Ports 4 x USB 1 X Ethernet 1 X Type C for power
Included Accessories | 1 × Case (Unassembled) 1 × PCBA Board 3 × Cooling Fans 1 × Heatsink (for Raspberry Pi) -1 × User Manual

And all this comes at a lower price tag of nearly $40 (more on this later). That sounds tempting, right? Let's see how good this case is.

📋

Elecrow sent me this case for review. The views expressed are my own.

### Features meet affordibility

Let's take a look at the appearance of Elecrow's mini PC case. It is slightly bigger than the Pironman cases and has a more boxy looks somehow.

The OLED display and power button are at the top. The micro SD card outlet is at the bottom and to accommodate it, the case has taller feet.

There is nothing in the front of the device except a transparent acrylic sheet. The main look of the case comes from the side that gives you a broader look at the circuits. It looks magnificent with the RGB lights. The GPIO pins are accessible from here and they are duly marked.

![Front view][12]

There are three RGB fans here. Two in the back throw air out and one at the top sucks air in. This is done to keep the airflow in circulation inside the case. The official Raspberry Pi Active Cooler is also added to provide some passive cooling.

All the other ports are accessible from the back. In addition to all the usual Raspberry Pi ports, there are two full-HDMI ports replacing the mini HDMI ports.

![Back view][13]

The NVMe board is inside the case and it is better to insert the SSD while assembling the case. Yes, this is also an assembly kit.

📋

I used the case for Raspberry Pi 5 and hence this section focuses on the Pi 5 specific features.

### Assembling the case

![Mini PC case box][14]

Since Elecrow's tower case is clearly inspired from SunFounder's Pironman case, they also have kept the DIY angle here. This simply means that you have to assemble the kit yourself.

It is while assembling that you can decide whether you want to use it for Raspberry Pi 5 or Jetson Orin Nano. Assembling instructions differ slightly for the devices.

There is an official assembly video and you should surely watch it to get a feel of how much effort is required for building this case.

In my case, I was not aware of the assembly video as I was sent this device at the time the product was announced. I used the included paper manual and it took me nearly two hours to complete the assembly. If I had had the help of the video and if I had not encountered a couple of issues, this could have been done within an hour.

![Assembling the case][15]

Did I say issues? Yes, a few. First, the paper manual didn't specifically mention connecting one of the FPC cables. The video mentions it, thankfully.

One major issue was in putting in the power button. It seems to me that while they sized the hole according to the power button, they applied the black coating later on. And this reduced the size of the hole from which the power button passes through.

I don't see the official assembly video mentioning this issue and it could create confusion. The workaround is to simply use an object to remove the coating. I used scissors to scrape it.

Another issue was putting in the tiny screws in even tinier spaces at times. The situation worsened for me as the paper manual suggested joining the main board and all the adapter boards in the initial phases. This made putting the screws in even harder. As the video shows, this could be done in steps.

My magnetic screwdriver helped a great deal in placing the tiny screws in narrow places, and I think Elecrow should have provided a magnetic screwdriver instead of a regular one.

### User experience

To make full use of all the cool features, i.e., OLED display, RGB fans, etc., you need to install a few Python scripts first.

![Scripts to add support for power button actions and OLED screen][16]

And here's the thing that I have noticed with most Elecrow products: they are uncertain about the appropriate location for their documentation.

The paper manual that comes with the package has a QR code that takes you to [this Google Drive][17] that contains various scripts and a readme file. But there is also [an online Wiki page][18] and I think this page should be considered and distributed as the official documentation.

After running 12 or so commands, including a few that allow 777 permissions, the OLED screen started showing system stats such as CPU temperature and usage, RAM usage, disk stats, date and time. It would have been nice if it displayed the IP address too.

![Milliseconds of light sync issue which is present in SunFounder cases too][19]

Like Pironman, Elecrow also has RGB lighting of fans out of sync by a few milliseconds. Not an issue unless you have acute OSD. The main issue is that it has three fans and the fans start running as soon as the device is turned on. For such a tiny device, three continuously running fans generate considerable noise.

The problem is that there is no user-facing way of controlling the fans without modifying the scripts themselves.

Another issue is that if you turn off Pi from the operating system, i.e., use the shutdown command or the graphical option of Raspberry Pi OS, the RGB lights and fans stay on. Even the OLED screen keeps on displaying whatever message it had when the system was shut down.

![Top of the case has the OLED display and power button][20]

If you shut down the device by long pressing the power button, everything is turned off normally. This should not be the intended behavior. I have notified Elecrow about it and hopefully their developers will work on fixing their script.

Barring these hiccups, there are plenty of positives. There is an RTC battery to give you correct time between long shutdowns, although it works only with Raspberry Pi OS at the moment. The device stays super cool thanks to three fans maintaining a good airflow and the active cooler adding to the overall cooling. The clear display with RGB lights surely gives it an oomph factor.

![My photography skills don't do justice][21]

### Conclusion

There is room for improvement here, and I hope Elecrow updates their scripts to address these issues in the future:

  * Proper handling of lights/fans shutdown instead of relying on the power button.
  * Provide options to configure the RGB lights and control the fans.
  * Include IP address in OLED display (optional).



Other than that, I have no complaints. The case is visually appealing, the device remains cool, and the price is reasonable in comparison to the [popular Pironman cases][3].

Coming to the pricing. The device costs $32 for the Jetson Nano version and $40 for the Raspberry Pi version. I am guessing this is because the Pi version includes the additional active cooler.

Do note that the pricing displayed on the website DOES NOT include shipping charges and customs duty. Those things will be additional.

Alternatively, at least for our readers in the United States of America, the device is [available on Amazon][22] (partner link) but at a price tag of $59 at the time of writing this review. You don't have to worry about extra shipping or custom duty fee if you order from Amazon.

[Get it from Amazon US (for $59)][22]

[Get it from official website (shipping/customs extra)][10]

--------------------------------------------------------------------------------

via: https://itsfoss.com/elecrow-raspberry-pi-5-case/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.sunfounder.com/products/pironman-5-nvme-m-2-ssd-pcie-mini-pc-case-for-raspberry-pi-5?ref=itsfoss
[4]: https://itsfoss.com/raspberry-pi-5-tower-cases/
[5]: https://itsfoss.com/pironman-5-max-review/
[6]: https://www.sunfounder.com/collections/1-raspberry-pi-5-collection/products/pironman-5-mini-case?ref=itsfoss
[7]: https://itsfoss.com/content/images/2025/10/elecrow-pitpower-case-sideview.webp
[8]: https://itsfoss.com/crowview-note-review/
[9]: https://itsfoss.com/crowpi-3-review/
[10]: https://www.elecrow.com/small-mini-pc-case-with-1-3-oled-screen-for-raspberry-pi-and-jetson-nano.html?idd=6
[11]: https://itsfoss.com/content/images/2025/10/hardware_overview_of_mini_pc_case_for_RPI.webp
[12]: https://itsfoss.com/content/images/2025/10/elecrow-pi-case-1.webp
[13]: https://itsfoss.com/content/images/2025/10/elecrow-mini-pc-case-back.webp
[14]: https://itsfoss.com/content/images/2025/10/elecrow-mini-pc-case-box.webp
[15]: https://itsfoss.com/content/images/2025/10/elecrow-mini-pc-assembly.webp
[16]: https://itsfoss.com/content/images/2025/10/elecrow-scripts-for-pitower-case.webp
[17]: https://drive.google.com/drive/u/1/folders/14QB_eCKqBgupR0OfekWJwF35kZT6SiLa
[18]: https://www.elecrow.com/wiki/mini-pc-case.html
[19]: https://itsfoss.com/content/images/2025/10/elecrow-pi-light-sync-issue.webp
[20]: https://itsfoss.com/content/images/2025/10/elecrow-case-top-view.webp
[21]: https://itsfoss.com/content/images/2025/10/elecrow-pi-case.webp
[22]: https://amzn.to/4o9ARBi
