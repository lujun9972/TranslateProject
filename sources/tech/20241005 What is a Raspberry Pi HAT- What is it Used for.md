[#]: subject: "What is a Raspberry Pi HAT? What is it Used for?"
[#]: via: "https://itsfoss.com/raspberry-pi-hat/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What is a Raspberry Pi HAT? What is it Used for?
======

[![Warp Terminal][1]][2]

When you first get your Raspberry Pi, you essentially have a powerful little computer with the basics needed to operate.

But what if you want to expand its potential?

That’s where HATs come in.

### What's a HAT?

HAT stands for **Hardware Attached on Top** , and it's an add-on board designed to sit perfectly on top of your Raspberry Pi.

HATs provide a neat, standardized way to expand your Raspberry Pi’s capabilities with things like displays, sensors, audio controllers, and even NVMe storage on Pi 5.

They were created to solve that problem by offering a standardized solution that makes hardware tinkering as accessible as software development. **Think of them as equivalent to browser plugins or GNOME extensions**.

The introduction of HATs allowed people to focus more on the fun part like building projects, rather than spending time on tedious setups.

You want to use Pi as NAS? Get a [SATA HAT][3] and focus on getting your NAS ready instead of figuring out how you will connect four SATA HDDs to the Pi.

![][4]

We [reviewed a Raspberry Pi-based dog kit earlier][5]. That, too, was using a custom HAT developed by the kit maker.

Raspberry Pi HATs are also electrically safe, meaning they come with an [EEPROM][6] chip that tells your Pi what hardware is connected, reducing the chances of frying your board accidentally.

### Assembly?

**Putting your HAT on your Raspberry Pi is as easy as pie!** ;)

Just align the pins on the HAT with the ones on your Pi, gently press them together, and that's it! It's like snapping a puzzle piece into place.

No soldering or complicated wiring required. Once it's connected, your Pi will automatically recognize the HAT and you're ready to start exploring its new functionalities.

![Apologies for the cringe-worthy image, but it was necessary to illustrate the point][7]

### Official Raspberry Pi HATs

Here are a few HATs Raspberry Pi have launched:

#### [Raspberry Pi M.2 HAT+][8]

![Source: Raspberry Pi][9]

The Raspberry Pi M.2 HAT+ allows you to connect M.2 peripherals like **NVMe drives** and **AI accelerators** to your Raspberry Pi 5.

This enables fast data transfer speeds of up to 500 MB/s. It supports devices with the M key edge connector in the **2230** and **2242** form factors.

The HAT can provide up to 3A of power to connected devices. It is auto detected by the latest Raspberry Pi software/firmware and can be easily installed using the provided stacking header and threaded spacers.

##### [PoE+ HAT][10]

![Source: Raspberry Pi][11]

The Raspberry Pi PoE HAT enables your Raspberry Pi to receive power through its Ethernet port, eliminating the need for a separate power supply.

It is compatible with Raspberry Pi 4 and Raspberry Pi 3B+. You'll need a PoE+ power-sourcing equipment to use this HAT.

📋

While there isn't an official Raspberry Pi PoE HAT for the Raspberry Pi 5 yet, you might consider the [****Waveshare PoE HAT****][12] as a potential alternative.

##### [Sense HAT][13]

![Source: Raspberry Pi][14]

The Sense HAT is an add-on board that provides your Raspberry Pi with sensors for monitoring pressure, humidity, temperature, color, orientation, and movement.

It also features an LED matrix for visualizing data and a joystick for user interaction.

##### [Raspberry Pi DAC+][15]

![Source: Raspberry Pi][16]

The Raspberry Pi DAC+ is a high-quality audio HAT that connects directly to your Raspberry Pi's GPIO header.

It provides stereo analog audio output and is compatible with all Raspberry Pi models with a 40-pin GPIO header.

### Unofficial Raspberry Pi HATs

Let me list some other HATs that are not developed by Raspberry Pi but you can use them with your Pi devices.

##### [Inventor HAT Mini][17]

![Image Source: PIMORONI][18]

Inventor HAT Mini is a versatile expansion board for your Raspberry Pi. It simplifies the process of adding motors, servos, sensors, and LEDs to your projects.

With its pre-soldered headers, Qw/ST connector, and Python library, you can quickly and easily create interactive and engaging projects.

Whether you're building a robot, a kinetic sculpture, or a custom automation, Inventor HAT Mini provides the necessary tools to bring your ideas to life.

##### [Picade X HAT USB-C][19]

![Image Source: PIMORONI][20]

It transforms your Raspberry Pi into a retro gaming console. With built-in joystick and button inputs, a 3W I2S DAC/amplifier, and a soft power switch, it's the perfect solution for DIY arcade cabinet builds.

It's Raspberry Pi 4 and features a convenient USB-C power connector.

Simply plug in your power supply, connect your controls, and install our driver to start enjoying classic games on your Raspberry Pi.

##### [Adafruit BrainCraft HAT - Machine Learning for Raspberry Pi 4][21]

![Image Source: Adafruit][22]

The BrainCraft HAT for Raspberry Pi is designed for building edge-based machine learning projects with microcontrollers and microcomputers.

It features a 240×240 TFT IPS display for inference results, a camera connector for imaging projects, dual microphones, stereo audio output, and a joystick for input control.

With its DotStar RGB LEDs, STEMMA connectors for servos or NeoPixels, and a fan for cooling during intensive tasks, it's ideal for audio/video AI projects.

##### [Google Voice Kit (V1)][23]

![Image Source: Google][24]

The Google Voice Kit v1 allows you to create a natural language recognizer and connect it to Google Assistant using the AIY Projects voice kit.

With this kit, you can add custom question-and-answer interactions alongside everything Google Assistant already offers, all packed into a neat cardboard cube powered by Raspberry Pi.

The kit includes a Voice HAT board, a microphone board, a speaker, an arcade-style push button, and essential cables, making it easy to build your own voice-controlled assistant.

If you don't have the kit, you can still integrate Google Assistant using the [official SDK][25].

##### Cooling HAT with OLED Display

![][26]

Available for Pi 4 and Pi 3, this cooling fan HAT comes with OLED display to show the CPU and RAM usage and CPU temperature. This increases the usability in my opinion.

[Cooling HAT with OLED display][27]

More than just a HAT. Pironman is an awe-inspiring case of your Raspberry Pi. You get NVMe SSD slot, proper HDMI slots and more.

![][28]

##### Pironman 5 Case With Tower Cooler and Fan

This dope Raspberry Pi 5 case has a tower cooler and dual RGB fans to keep the device cool. It also extends your Pi 5 with M.2 SSD slot and 2 standard HDMI ports.

[Explore Pironman 5][29]

### Final Thoughts

HATs are a fantastic way to expand your Raspberry Pi's capabilities, but they're not a one-size-fits-all solution.

Before adding a HAT to your setup, carefully consider your project's specific requirements, the compatibility of the HAT with your Pi model, and the potential trade-offs in terms of power consumption and physical size.

The possibilities are endless with HATs. So, what will you create next?

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-hat/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://radxa.com/products/accessories/penta-sata-hat/
[4]: https://itsfoss.com/content/images/2024/09/radaxa-sata-hat-raspberry-pi.webp
[5]: https://itsfoss.com/raspberry-pi-dog-review/
[6]: https://en.wikipedia.org/wiki/EEPROM
[7]: https://itsfoss.com/content/images/2024/09/rpi-hat-explain-3.png
[8]: https://www.raspberrypi.com/products/m2-hat-plus/
[9]: https://itsfoss.com/content/images/2024/09/pi-m2-hat-1.webp
[10]: https://www.raspberrypi.com/products/poe-plus-hat/
[11]: https://itsfoss.com/content/images/2024/09/poe-hat.webp
[12]: https://www.waveshare.com/poe-hat-f.htm
[13]: https://www.raspberrypi.com/products/sense-hat/
[14]: https://itsfoss.com/content/images/2024/09/pi-sense-hat.webp
[15]: https://www.raspberrypi.com/products/dac-plus/
[16]: https://itsfoss.com/content/images/2024/09/hifi-dac-hat.webp
[17]: https://shop.pimoroni.com/products/inventor-hat-mini?variant=40588023464019
[18]: https://itsfoss.com/content/images/2024/09/pimoroni-inventor-hat-mini.webp
[19]: https://shop.pimoroni.com/products/picade-x-hat-usb-c?variant=29156918558803
[20]: https://itsfoss.com/content/images/2024/09/picade-hat-usb-c-1.jpg
[21]: https://www.adafruit.com/product/4374
[22]: https://itsfoss.com/content/images/2024/09/braincraft-hat-ml.jpg
[23]: https://aiyprojects.withgoogle.com/voice-v1/
[24]: https://itsfoss.com/content/images/2024/09/google-voice-kit-v1.jpg
[25]: https://developers.google.com/assistant/sdk
[26]: https://itsfoss.com/content/images/2024/09/raspberry-pi-cooling-hat-with-oled-display.webp
[27]: https://www.sunfounder.com/products/cooling-fan-hat-with-oled?ref=itsfoss
[28]: https://itsfoss.com/content/images/2024/06/pironman-5.webp
[29]: https://www.sunfounder.com/products/pironman-5-nvme-m-2-ssd-pcie-mini-pc-case-for-raspberry-pi-5?ref=itsfoss
