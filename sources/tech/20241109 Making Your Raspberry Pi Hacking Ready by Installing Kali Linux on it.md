[#]: subject: "Making Your Raspberry Pi Hacking Ready by Installing Kali Linux on it"
[#]: via: "https://itsfoss.com/kali-linux-raspberry-pi-2/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Making Your Raspberry Pi Hacking Ready by Installing Kali Linux on it
======

[![Warp Terminal][1]][2]

Ever since I got into the world of computers, the idea of hacking my friends’ systems felt like the coolest thing I could do. And, I am sure, it is not just me.

It started as a casual fascination, but then I discovered [Kali Linux][3], and an entire universe of possibilities opened up in front of me!

This is not your average Linux distro for daily use. Kali Linux is built to offer an essential tool set for cybersecurity pros and curious tinkerers.

Not just the concept of penetration testing or hacking, Kali Linux supports running on Raspberry Pi, which happens to be my area of liking!

Of course, I could not get out the thought of having a mini hacking lab (even if I am not an ethical hacker) on my Raspberry Pi. So, naturally, I installed Kali Linux on it 😉

Here, I tell you how you can do it too.

### Installing Kali Linux on Raspberry Pi

First things first: while you can install Kali Linux on any Raspberry Pi model, the Raspberry Pi 5 is currently in beta for Kali (at the time of writing this), meaning it is not fully supported yet.

You can check out their [documentation][4] for the latest updates, but if you’re using a Pi 5, expect a few bumps along the way.

There are **two methods of installing Kali Linux** and we will be exploring both:

#### Method 1: Using Raspberry Pi Imager

**Step 1:** Open the Imager and click on “Choose OS.”

![][5]

**Step 2:** Go to “Other specific-purpose OS” and then select “ **Kali Linux.** ”

![][6]

You can see other options available along with Kali Linux. Our focus here is Kali.

![][7]

**Step 3:** Choose the appropriate version (64-bit is recommended if your Raspberry Pi supports it).

![][8]

**Step 4:** Select your SD card (make sure it is at least 16 GB for Kali).

**Step 5:** Click “Write” and let the magic happen!

![][9]

#### Method 2: Manual Installation

If you want to choose the ISO yourself, you can manually download the [Kali image for ARM devices][10] from Kali’s website as per your Raspberry Pi model.

![][11]

Once you do that, use a tool like Raspberry Pi Imager or [Balena Etcher][12] (if that's what you prefer) to flash the image to your SD card.

![][13]

### First Boot

Once the flashing process is done, eject the SD card, insert it into your Raspberry Pi, and power it on. Kali will boot directly into a login screen.

💡

__Use__ _****kali****_ __as both the username and password initially__.

### Desktop Experience

When you boot into Kali Linux, you will be greeted by a clean and polished [XFCE desktop][14] that stands out with its sleek customization.

In my opinion, it is one of the best desktop experiences I’ve seen on a Raspberry Pi. The layout is intuitive, making it easy for beginners to navigate.

![][15]

Even if you are more accustomed to Windows, you can switch to a full-fledged Windows-like theme from the settings, which might even trick a seasoned Windows user into thinking you are using Windows on Raspberry Pi.

![][16]

By the way, if you are seriously giving that a thought, it is possible to [install Windows on Raspberry][17]:

![][18]

While Kali boots slightly slower than [Raspberry Pi OS][19] particularly on older Pi models, but once you are in, it runs surprisingly smoothly.

In the Applications menu, you will find Kali’s signature pentesting tools, neatly organized under categories like “ _Exploitation Tools_ ” and “ _Sniffing & Spoofing_” making it a highly focused environment for cybersecurity related work.

![][20]

### My thoughts on Kali experience on Pi

If you are new to cybersecurity, and do not have a spare computer (or system resources for Kali Linux VM), Raspberry Pi is a great option for you. You get access to hundreds of pre-installed tools, and the low cost of the hardware makes it a great choice for experimenting without breaking the bank.

However, **there are some limitations**. A [few Kali Linux tools][21], like [**Burp Suite**][22], are not yet supported for the ARM architecture, which might be a dealbreaker for some.

That said, you can still use a lot of other essential tools for wireless testing, network analysis, and more. Overall, if you want to dive into the world of ethical hacking, this is a perfectly affordable setup.

_💭 I would be curious to learn about your experiences with Kali Linux on Raspberry! Let me know your thoughts in the comments below! Happy hacking!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/kali-linux-raspberry-pi-2/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.kali.org/
[4]: https://www.kali.org/docs/arm/raspberry-pi-5/
[5]: https://itsfoss.com/content/images/2024/10/rpi-imager-choose-os-1.png
[6]: https://itsfoss.com/content/images/2024/10/rpi-imager-specific-os-prompt-2.png
[7]: https://itsfoss.com/content/images/2024/10/rpi-imager-select-kali.png
[8]: https://itsfoss.com/content/images/2024/10/rpi-imager-select-kali-version-1.png
[9]: https://itsfoss.com/content/images/2024/10/rpi-imager-progress.png
[10]: https://www.kali.org/get-kali/#kali-arm
[11]: https://itsfoss.com/content/images/2024/10/kali-arm-downloads.png
[12]: https://etcher.balena.io/#download-etcher
[13]: https://itsfoss.com/content/images/2024/10/balena-etcher.png
[14]: https://xfce.org/
[15]: https://itsfoss.com/content/images/2024/10/kali-linux-home.png
[16]: https://itsfoss.com/content/images/2024/10/kali-in-windows-apperance.png
[17]: https://itsfoss.com/windows-raspberry-pi/
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[19]: https://www.raspberrypi.com/software/operating-systems/
[20]: https://itsfoss.com/content/images/2024/10/kali-linux-app.png
[21]: https://itsfoss.com/best-kali-linux-tools/
[22]: https://portswigger.net/burp
