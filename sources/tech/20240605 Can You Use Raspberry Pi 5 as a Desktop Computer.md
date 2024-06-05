[#]: subject: "Can You Use Raspberry Pi 5 as a Desktop Computer?"
[#]: via: "https://itsfoss.com/raspberry-pi-5-review/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Can You Use Raspberry Pi 5 as a Desktop Computer?
======

[![Warp Terminal][1]][2]

It's been several months since Raspberry Pi 5 was first released. I wanted to try it then but getting the latest version of Raspberry Pi has always been tricky.

So, I shared this problem with Raspberry Pi folks and they were kind enough to send me one.

But I didn't start writing a review immediately. I prefer using the devices for a considerable time before sharing my opinion on it.

And I wanted to use the device as a regular desktop for some time. I mean the Raspberry Pi is not necessarily a low-end device anymore. So why not use it as your regular PC?

Here's what I feel about using Pi 5 as a regular computer for the past two months.

### Raspberry Pi 5 hardware

The Raspberry Pi 5 Kit I received had the following:

  * Raspberry Pi 5 8 GB model
  * Raspberry Pi keyboard and mouse
  * Official power adapter
  * Micro HDMI to HDMI cable
  * MicroSD card loaded with Raspberry Pi OS
  * Official Active Cooler (heatsink and fan)



#### Official keyboard and mouse (not needed)

While the official keyboard and mouse look cute and blend well with the Raspberry Pi's red and white branding, I am not a fan of the keyboard.

![][3]

Don't get me wrong. It's a decent keyboard for the price tag, but I use a Keychron V6, and it is difficult to have the same feel with non-mechanical keyboards.

Even if I don't compare it with a mechanical keyboard, it feels short compared to my Dell keyboard.

But again, it's an inexpensive keyboard and doesn't always come with Pi 5. If you have a regular keyboard at home, you can skip getting the official one.

#### Official power adapter (must have)

I usually don't care much about the power adapter with SBCs. They usually work fine with mini-USB or USB-C power adapters that come with smartphones and other devices. My [Sige7][4] is a beast in specification and works fine with my Galaxy S23 charger.

But the Pi 5 doesn't play well with the regular smartphone power adapters. I used my fast charger and Pi 5 started complaining about it.

![][5]

It's a good thing that I got the official power adapter. You should get one, too.

#### Keeping the temperature in control (must have)

Though I had received the Active Cooler in the package, I started using Pi 5 without it. From my past experience with Pi devices, I knew that it is always better to keep the device cool, one way or another.

The device heats up quickly, even with a couple of browser tabs open. A heated chip will impact performance and you know it.

To use the Pi 5 as a desktop, you need to keep the temperature in check. This is where the Active Cooler helped me.

I [enabled temperature monitoring on my Pi 5 device][6] and I noticed that the cooler brought the CPU temperature down from 69 degree centigrades to 53 degrees within seconds. I'll share a video on YouTube about it.

With the hardware setup done, let's see how it worked as a regular personal computer.

### Experiencing the Pi 5 as a desktop computer

![][7]

Once I had taken care of the heating issue, the next challenge came in the form of browsing the internet.

Both Firefox and Chromium felt bulky and sluggish. This was especially true with websites with advertisements. With ad-blocker, this issue was mostly solved.

The default Raspberry Pi OS uses a lightweight PIXEL desktop environment based on LXDE and it does a fair job at that.

It doesn't have all the graphical effects you get in GNOME and I feel that it looks a bit outdated but that's by design. You sacrifice the looks for performance.

From the alt-tab switcher to pressing the super keys, I missed many GNOME features that I take for granted.

I used Raspberry Pi for browsing the internet, writing articles and some coding with VS Code. I also added [Coral TPU][8] (partner link) to have some fun with beginner-level AI projects.

I did notice that the WiFi was a little slow when compared to my TUXEDO or Dell laptops. While I got around 75 Mbps on Pi 5, the other laptops showed over 120 Mbps. It's not a deal breaker, for sure.

### Conclusion

To conclude, you can use the 8 GB RAM version of Raspberry Pi as a regular desktop computer and use it for browsing the internet, doing some coding, watching online videos and other usual stuff you do on your PC.

You cannot get the performance of a high-end computer but it gives you a fairly decent experience that can be compared to a i3 processor, mid-end laptop.

But in any case, you must use a fan and heat sink. Without that, you'll have a difficult time using the Pi 5 even for simple, less resource-consuming tasks.

The official Active Cooler is a decent choice. If you can afford $79, you can opt for a better one like Pironman 5. It is super cool 😍

![][9]

##### Pironman 5 Case With Tower Cooler and Fan

This dope Raspberry Pi 5 case has a tower cooler and dual RGB fans to keep the device cool. It also extends your Pi 5 with M.2 SSD slot and 2 standard HDMI ports.

[Explore Pironman 5][10]

🗨️ Do you use a Raspberry Pi 5? How's your experience with it?

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-5-review/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/06/raspberry-pi-5-keyboard.webp
[4]: https://www.armsom.org/sige7
[5]: https://itsfoss.com/content/images/2024/06/raspberry-pi-5-power-adapter-issue.png
[6]: https://itsfoss.com/raspberry-pi-cpu-gpu-temperature/
[7]: https://itsfoss.com/content/images/2024/06/pi-5-desktop.webp
[8]: https://www.seeedstudio.com/Coral-USB-Accelerator-p-2899.html?sensecap_affiliate=YtQVXkS&referring_service=link
[9]: https://itsfoss.com/content/images/2024/06/pironman-5.webp
[10]: https://www.sunfounder.com/products/pironman-5-nvme-m-2-ssd-pcie-mini-pc-case-for-raspberry-pi-5?ref=itsfoss
