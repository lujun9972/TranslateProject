[#]: subject: "This is the Coolest Raspberry Pi 5 Accessory I have Ever Used"
[#]: via: "https://itsfoss.com/pironman-5-review/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This is the Coolest Raspberry Pi 5 Accessory I have Ever Used
======

[![Warp Terminal][1]][2]

I am not exaggerating when I say that this is the coolest Raspberry Pi accessory I ever used or even seen.

That's not because it has a tower cooler with two RGB fans. I mean that's also a factor but not the only factor here.

At first look, [SunFounder's Pironman 5][3] looks like a transparent Raspberry 5 case with an active cooler but it is much more than that. It actually turns your single board computer into a mini PC.

Let me share more details about this awesome gadget and my experience with it.

### Pironman 5 Features: More than just a Raspberry Pi case

Let's see its features and specifications first.

The Pironman 5 has a part aluminum, part acrylic casing that gives it the feel of a gaming PC in miniature form.

Of course, the tower cooler and the two RGB fans seems the most attractive visible part of it but there is more to it.

But it enhances the capabilities of your Pi 5 by providing two standard HDMI ports (Pi 5 has micro HDMI slots) and adding NVMe M.2 SSD support.

![][4]

On the outer, you have a 0.96" OLED screen that shows the current CPU and RAM usage, CPU temperature, disk storage, and the Pi's IP address. How cool is that 😍

All the ports you get in your Pi remain accessible from outside the case. The TF card slot, GPIO pins, USB ports, power outlet, etc. It also gives you a power button on the front.

Now that you know what it does, let me share my experience with it so far.

### Getting Pironman 5 ready

Like most of their gadgets and accessories, Pironman is also a DIY assembly kit. This means that you'll be getting all the parts and screws and you have to put it together.

![][5]

At the time of writing this article, there is no official video for Pironman 5 assembly. However, the assembly diagram was more than sufficient for me. Considering that I already experienced their [Pi Dog][6] and [Galaxy Rover][7] kit, this assembly was a walk in the park. It took me around 40 minutes to assemble it.

It should not be complicated for most people I believe. If you can assemble Ikea furniture, you could do this one as well. It's similar but tiny.

![][8]

The glass-like transparent display is actually acrylic and I roughed it up a little against the desk and so it has some scratch marks. They are not visible easily but my OCD can spot them from any corner of the room.

Pironman 5 also has a [dedicated document portal][9] which is essential. Why? I tell you in the next section.

### Post assembly setup and configuration

When I turned on the Pi inside the Pironman for the first time, I noticed that the OLED screen was not displaying anything. I started doubting the ability of my fat fingers in successfully assemble the kit.

![The OLED requires additional packages from SunFounder][10]

It was only when I was reading the document portal that I realized that a couple of software setups remained.

SunFounder provides a [pironman Python module][11] that helps you get the stats on the OLED.

![Small OLED display to show system resources, CPU temp and IP address][12]

Not only that, you can also configure and control the RGB lighting and fan behavior through it.

By default, there is a blue light in breathing mode. The RGB fans run when the CPU hits 60 degrees Celsius but that was not happening with Tower Cooler doing a good job of reducing the SoC temperature.

So, I changed the config and made the RGB fans run at 50 degrees. They look cool after all. The RGB lighting should be synced between the two fans. However, I noticed a slight delay of a second. I'll see if that can be fixed.

The RGB lighting and OLED remain on when the Pi is shut down. The documentation mentioned additional steps to deactivate the GPIO power to tackle it.

### My experience with the Pironman 5

I was using the official Raspberry Pi 5 active cooler earlier and it did a decent job of keeping the Pi 5 cool.

Although I didn't do any benchmarking tests, I feel that Pironman does a better job of keeping the CPU temperature down. That's the important part, right?

The fan noise is not that noticeable, primarily because the temperature remains well under control, and hence, the fans don't run at full speed.

I have attached an NVMe SSD, which is working as additional storage for now. I will experiment by running the Raspberry Pi OS directly from the SSD.

The small OLED display is also helpful. If you are running a homelab setup where Pi runs without a dedicated monitor, you can easily see what IP it is using and how much system resources are consumed.

The power button on the front needs to be pressed twice in quick succession to initiate an immediate shutdown. Single press brings the shutdown menu.

### Conclusion

I shared teaser videos on social media platforms. Most people liked Pironman. A few people didn't like the concept of turning the Pi into a mini PC like this.

I think that's subjective. Pironman keeps my Raspberry Pi 5 cool and makes it look cool. I like that. The ability to use standard HDMI and SSD is definitely a plus.

Overall, I am liking the enhanced Raspberry Pi 5 experience with the Pironman 5. I highly recommend it if you are planning to use your Raspberry Pi 5 as a desktop and you can afford it.

Pironman 5 is priced at $79.99, which is reasonable for the features it offers. I have seen regular tower cooler cases in a similar price range. This one additionally provides standard HDMI and SSD abilities. **Note that it doesn't include a Pi 5**. You have to own that separately.

[Explore Pironman 5][3]

🚧

There is also a [Pironman 4 for Raspberry Pi 4][13]. It has similar but not exact the same look and features as the Pironman 5. And they are not compatible with each other. So ensure that you are getting the correct Pironman for your Raspberry Pi.

--------------------------------------------------------------------------------

via: https://itsfoss.com/pironman-5-review/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.sunfounder.com/products/pironman-5-nvme-m-2-ssd-pcie-mini-pc-case-for-raspberry-pi-5?ref=itsfoss
[4]: https://itsfoss.com/content/images/2024/06/pironman-5-features.jpg
[5]: https://itsfoss.com/content/images/2024/06/pironman5-assembly-2--1-.jpg
[6]: https://itsfoss.com/raspberry-pi-dog-review/
[7]: https://itsfoss.com/galaxy-rover/
[8]: https://itsfoss.com/content/images/2024/06/pironman5-assembly-11.jpg
[9]: https://docs.sunfounder.com/projects/pironman5/en/latest/index.html
[10]: https://itsfoss.com/content/images/2024/06/pironman-display.jpg
[11]: https://docs.sunfounder.com/projects/pironman5/en/latest/set_up_pironman5.html#downloading-and-installing-the-pironman5-module
[12]: https://itsfoss.com/content/images/2024/06/pironman5-oled-display.webp
[13]: https://www.sunfounder.com/products/raspberry-pi-4-case?ref=itsfoss
