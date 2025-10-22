[#]: subject: "Arduino Alternative Microcontroller Boards for Your DIY Projects in the Post-Qualcomm Era"
[#]: via: "https://itsfoss.com/arduino-alternative-microcontroller-boards/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Arduino Alternative Microcontroller Boards for Your DIY Projects in the Post-Qualcomm Era
======

[![Warp Terminal][1]][2]

Arduino has been the cornerstone of embedded electronics projects for a while now. Be it DIY remote-controlled vehicles, binary clocks, [power laces][3], or as is relevant to the month of publishing, [flamethrowing Jack-O'-Lanterns][4]! The versatility and affordability of the board has been uniquely unparalleled.

But now that [Qualcomm has acquired Arduino][5] projecting more AI-forward features with more powerful hardware, there might be some changes around the corner. Perhaps I am reading too much between the lines but not all of us have favorable views about Big Tech and corporate greed. We thought it might be a good time to look at some alternatives.

Since Arduino has a lot of different models with different features, we will not draw a comparison between Arduino and other boards, but just highlight the unique features these alternative boards have.

### 1\. Raspberry Pi Pico

![][6]

Raspberry Pi needs no introduction, it being the one company besides Arduino that has always been the favorite of tinkerers. While Raspberry Pi is known for its full fledged single-board-computers, the [Pico][7] is a development board for programming dedicated tasks like the Arduino boards.

There are two releases of the Pico at the time of writing this article, 1 and 2. The major upgrade being the processor. There are certain prefixes which denote model features, "W" denoting wireless capabilities, "H" denoting pre-soldered headers. Here, I describe the cutting-edge model, the [**Pico 2 W with Headers**][8].

  * **Processors:** Dual Cortex-M33 (ARM) upto 133 MHz and optional Hazard3 processors (RISC-V)
  * **Memory:** 520 KB on-chip SRAM
  * **Input-Output:** 26 GPIO pins
  * **Connectivity:** Optionally 2.4 GHz Wi-Fi and Bluetooth 5.2 on the W model
  * **Power:** Micro-USB
  * **Programming Software or Language:** MicroPython or C/C++
  * **Price:** $8
  * **Extra Features:** Temperature sensor



The greatest advantage of Raspberry Pi is the huge userbase, second probably only to Arduino. Besides that, the GPIO pins make projects easier to construct, and the optional RISC-V processors give it an open-source experimental edge that many long for.

### 2\. ESP32

ESP32 is a SoC that has soared in popularity in the past decade, and for all the right reasons. It comes in very cheap, screaming "hobbyist" and is committed to good documentation and an open SDK (software development kit). It came as a successor to the already very successful and still relevant [ESP8266 SoC][9].

The categorization is a little to get a hang of because of the sheer number of boards available. The original ESP32 SoC boards come with dual-core Xtensa LX6 processors that go up to 240 MHz, and they come with Wi-Fi + Bluetooth classic/LE built-in. The ESP32-S series are a little enhanced, with more GPIO pins for connectivity. Now the ESP32-C series transitioned to RISC-V chips, and finally the ESP32-H series are designed for ultra low-power IoT applications. If the board name has WROOM, it belongs to the original basic family but the ones with WROVER indicate modules with PSRAM and more memory in general. You can find all the "DevKits" [here][10].

Getting over the whole naming culture, I will directly describe one board here that might fulfill your Arduino-alternative needs, [ESP32-DevKitC-VE][11]:

![][12]

  * **Processors:** Dual-core 32-bit LX6 upto 240 MHz
  * **Memory:** 8 MB
  * **Input-Output:** 34 programmable GPIOs
  * **Connectivity:** 802.11 Wi-Fi, Bluetooth 4.2 with BLE
  * **Power:** Micro-USB
  * **Programming Software or Language:** Arduino IDE, PlatformIO IDE (VS Code), LUA, MicroPython, Espressif IDF (IoT Development Framework), JavaScript
  * **Price:** $11
  * **Extra Features:** Breadboard friendly, rich set of peripheral interfaces



I encourage you to do your own research based on your needs of the board and choose one, as the support and hardware is rock solid but the sheer number of options can be a little tricky to figure out.

### 3\. Adafruit Feather

![][13]

[Adafruit Feather][14] isn't a single board, but a [category of hardware boards][15] that come with all sorts of different features and processors each. The idea is getting a "feather", which is the board, and then getting "wings" which are hats/shields, basically extending the features and abilities of the board, and there are a huge number of them. This extensible versatility is the most attractive features of the boards but also the reason why I cannot describe one board that best suits the needs of any user. I can, however, tell you what options they provide.

#### All Feathers

  * Can be programmed with Arduino IDE
  * Come with Micro-USB or USB-C
  * Are 0.9" long and breadboard-compatible
  * Can be run with either USB power or a LiPo battery



#### Processors

The boards are available with several different processors, such as:

  * Atmel ATmega32u4 and ATmega 328P - 8 bit AVR
  * Atmel ATSAMD21 - 32 bit ARM Cortex M0+
  * Atmel ATSAMD51 - 32-bit ARM Cortex M4
  * Broadcom/Cypress WICED - STM32 with WiFi
  * Espressif ESP8266 and ESP32 - Tensilica with WiFi/BT
  * Freescale MK20 - ARM Cortex M4, as the Teensy 3.2 Feather Adapter
  * Nordic nRF52832 and nRF32840 - ARM Cortex & Bluetooth LE
  * Packet radio modules featuring SemTech SX1231
  * LoRa radio modules featuring SemTech SX127x



A good model to look into for an Arduino alternative is [Adafruit ESP32 Feather V2][16].

#### Connectivity and wings

The "feathers" have different categories based on their connectivity. The categories include:

  * Basic Feathers
  * Wi-Fi Feathers
  * Bluetooth Feathers
  * Cellular Feathers
  * LoRa and Radio Feathers



This doesn't mean that these connectivity features are mutually exclusive, there are several boards which have more than one of theses connectivity options.

[The Wings][17] add all the functionality to the boards, and the number of options are immense. I cannot possibly list them here.

### 4\. Seeeduino

As Arduino alternatives go, this board seems to be one of the most worthy of holding that title. It looks like an Arduino, works with the software that Arduino is compatible with, and even supports the shields made for UNO-R3. Here is the description of the most recent model at the time of writing this, [Seeeduino V4.3][18]:

![][19]

  * **Processors:** ATmega328
  * **Memory:** 2 KB RAM, 1 KB EEPROM and 32 KB Flash Memory
  * **Input-Output:** 14 digial IO pins, 6 analog inputs
  * **Power:** Micro-USB, DC Input Jack
  * **Programming Software or Language:** Arduino IDE
  * **Price:** $7.6



If you need a no-brainer Arduino alternative that delivers what it does with stability and efficiency, this should be your go-to choice.

### 5\. STM32 Nucleo Boards

STM32 offers a [very, very wide range of development boards][20], among which the [Nucleo boards][21] seem like the best alternatives for Arduino. They come in three series as well: Nucleo-32, Nucleo-64 and Nucleo-144, the numbers at the end of which denote the number of connectivity pins that the board offers. Every single series has a number of models within, again. Here, I will describe the one most appropriate as an Arduino alternative:

#### [STM32 Nucleo-F103RB][22]

![][23]

  * **Microcontroller:** STM32
  * **Input-Output:** 64 IO pins; Arduino shield-compatible
  * **Connectivity:** Arduino Uno V3 expansion connector
  * **Power:** Micro-USB
  * **Programming Software or Language:** IAR Embedded Workbench, MDK-ARM, STM32CubeIDE, etc.
  * **Price:** $10.81
  * **Extra Features:** 1 programmable LED, 1 programmable button, 1 reset button
  * **Optional Features:** Second user LED, cryptography, USB-C, etc.



STM32 provides great hardware abstraction, ease of development, GUI based initialization, good resources and more. If that is the kind of thing you need, then this should probably be your choice.

### 6\. micro:bit

[micro:bit boards][24] are designed mostly for younger students and kids to learn programming, but offer some really interesting features that can help anyone make a project without buying many extra parts. In fact, this is one of the [ideal tools for introducing STEM education to young children][25].

![][26]

Here are the details of the most recent version at the time of writing, micro:bit v2:

  * **Processors:** Nordic Semiconductor nRF52833
  * **Memory:** 128 KB RAM, 512 KB Flash Memory
  * **Input-Output:** 25 pins (4 dedicated GPIO, PWM, I2C, SPI)
  * **Connectivity:** Bluetooth 5.0, radio
  * **Power:** Micro-USB
  * **Programming Software or Language:**
  * **Price:** $17.95 ([other more expensive bundles with extra hardware are also available][27])



The extra built-in features of the board include:

  * 2 built in buttons that can be programmed in different ways
  * Touch sensor on the logo, temperature sensor
  * Built-in speaker and microphone
  * 25 programmable LEDs
  * Accelerometer and compass
  * Reset and power button



If a plethora of extra hardware features capable of executing almost anything you might want, or if you want a development board with extensive documentation for younger audiences, this should be your go to choice. The company doesn't only make great boards, but also supports inclusive technological education for children of all abilities, and sustainability, which is admirable.

### 7\. Particle Photon 2

[The Particle Photon 2][28] is a board designed with ease of prototyping in mind. It enables IoT projects, giving broad customization options to both hardware and software. The Photon is also Feather-compatible (from Adafruit), giving the ability to attach Wings to extend the features.

![][29]

  * **Processors:** ARM Cortex M33, upto 200 MHz
  * **Memory:** 3MB RAM, 2MB Flash **** Memory
  * **Input-Output:** 16 GPIO pins
  * **Connectivity:** Dual-band Wi-Fi and BLE 5.3
  * **Power:** Micro-USB
  * **Programming Software or Language:** VSC plug-in
  * **Price:** $17.95



The Photon also has a built-in programmable LED. Particle also provides a Wi-Fi antenna add-on component if your project requires that. If building new product ideas is your need, this might just be what you're looking for.

### 8\. Teensy Development Boards

[The Teensy board series][30], as the name suggests, aims for a small board with a minimal footprint with a lot of power packed at an affordable price. There have been several releases of the board, with the most recent one at the time of writing being [Teensy 4.1][31]:

![][32]

  * **Processors:** ARM Cortex-M7 at 600 MHz
  * **Memory:** 1024K RAM**,** 8MB Flash Memory
  * **Input-Output:** 55 digital IO pins, 18 analog input pins
  * **Power:** Micro-USB,
  * **Programming Software or Language:** Arduino IDE + Teensyduino, Visual Micro, PlatformIO, CircuitPython, command line
  * **Price:** [$31.50][33]
  * **Extra Features:** Onboard Micro SD card



If you need a stable base for your project that just works, this might be your choice. It is worth noting that the Teensy boards have excellent audio libraries and offer a lot of processing power.

### 9\. PineCone

[PineCone][34] is a development board from one of the foremost open source companies, Pine64. It provides amazing features and connectivity, making it ideal for a lot of tinkering purposes.

![][35]

  * **Processors:** 32-bit RV32IMAFC RISC-V “SiFive E24 Core”
  * **Memory:** 2 MB Flash Memory
  * **Input-Output:** 18 GPIO pins
  * **Connectivity:** Wi-Fi, BLE 5.0, Radio
  * **Power:** USB-C
  * **Programming Software or Language:** Rust
  * **Price:** $3.99
  * **Extra Features:** 3 on-board LEDs



The RISC-V processor capability gives it the open-source hardware edge that many other boards lack. That makes it quite good for IoT prototyping into devices and technologies that might be very new and untapped.

### 10\. Sparkfun Development Boards

Sparkfun has a whole range of boards on their website, out of which the two most notable series are the "RedBoard" series and the "Thing" series. A big part of some of these boards is the [Qwiic ecosystem][36], in which I2C sensors, actuators, shields, etc. can be connected to the board with the same 4-pin connector. Not only that, but you can daisy-chain the boards in one string, making it more convenient and less prone to errors. [Here's][37] a great article to learn about the Qwiic ecosystem.

#### [Sparkfun RedBoard Qwiic][38]

This is another board that is a perfect alternative to Arduino with extra features because it was designed to be so. It is an Arduino-compatible board, supporting the software, shields, etc.

![][39]

  * **Microcontroller:** ATmega328 with UNO's Optiboot Bootloader
  * **Input-Output:** 20 Digital IO pins, 1 Qwiic connector
  * **Connectivity:** 20 Digital I/O pins with 6 PWM pins
  * **Power:** Micro-USB, Pin input
  * **Programming Software or Language:** Arduino IDE
  * **Price:** $21.95



#### Sparkfun Thing Plus Series

The Sparkfun Thing Plus series comes in with sorts of different processors and connection abilities like RP2040, RP2350, nRF9160, ARM Cortex-M4, ESP32-based, STM32-based, etc. We've chosen to describe one of the most popular models here, [SparkFun Thing Plus - ESP32 WROOM (USB-C)][40].

![][41]

  * **Microcontroller:** ESP32-WROOM Module
  * **Input-Output:** 21 Multifunctional GPIO
  * **Connectivity:** Wi-Fi 2.4GHz, dual integrated Bluetooth (classic and BLE)
  * **Power:** USB-C, Qwiic connector
  * **Programming Software or Language:** Arduino IDE
  * **Price:** $33.73
  * **Extra Features:** RGB status LED, built-in SD card slot, Adafruit Feather compatible (you can attach the "Wings")



Sparkfun offers a lot of options, especially based on the form-factor. They not only provide /new unique features of their own, but also utilize the open technologies provided by other companies very well, as you can see.

### Conclusion

The Arduino boards clearly have a lot of alternatives, varying in size, features and practicality. If Arduino being acquired puts a bad taste in your mouth, or even if you just want to explore what the alternatives offer, I hope this article has been helpful for you. Please let us know in the comments if we missed your favorite one. Cheers!

--------------------------------------------------------------------------------

via: https://itsfoss.com/arduino-alternative-microcontroller-boards/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.instructables.com/Power-Laces-the-Auto-lacing-shoe/
[4]: https://www.instructables.com/Flamethrowing-Jack-O-Lantern/
[5]: https://www.arduino.cc/qualcomm
[6]: https://itsfoss.com/content/images/2025/10/raspberry-pi-pico.webp
[7]: https://www.raspberrypi.com/documentation/microcontrollers/pico-series.html
[8]: https://www.pishop.us/product/raspberry-pi-pico-2w-with-header/
[9]: https://www.mouser.com/ProductDetail/Espressif-Systems/ESP8266-DevKitC-02U-F?qs=qSfuJ%252Bfl/d6KCnDPGU%252BMZA%3D%3D
[10]: https://www.espressif.com/en/products/devkits
[11]: https://www.amazon.com/Espressif-ESP32-DevKitC-VE-Development-Board/dp/B087TNPQCV?th=1
[12]: https://itsfoss.com/content/images/2025/10/esp32-2.jpg
[13]: https://itsfoss.com/content/images/2025/10/AdafruitFeather.jpg
[14]: https://learn.adafruit.com/adafruit-feather/feathers
[15]: https://www.adafruit.com/category/946
[16]: https://www.adafruit.com/product/5900
[17]: https://www.adafruit.com/category/814
[18]: https://www.seeedstudio.com/Seeeduino-V4-2-p-2517.html
[19]: https://itsfoss.com/content/images/2025/10/seeeduino.jpg
[20]: https://www.digikey.com/en/product-highlight/s/stmicroelectronics/stm32-kits
[21]: https://www.st.com/en/evaluation-tools/stm32-nucleo-boards.html
[22]: https://www.st.com/en/evaluation-tools/nucleo-f103rb.html
[23]: https://itsfoss.com/content/images/2025/10/stm32nucleo.jpg
[24]: https://microbit.org/get-started/what-is-the-microbit/
[25]: https://itsfoss.com/ways-kids-learn-code/
[26]: https://itsfoss.com/content/images/2025/10/microbitv2.jpg
[27]: https://microbit.org/buy/
[28]: https://store.particle.io/products/photon-2?_fid=6d0f69df9&_pos=2&_ss=c
[29]: https://itsfoss.com/content/images/2025/10/Particle-Photon.jpg
[30]: https://www.pjrc.com/teensy/
[31]: https://www.pjrc.com/store/teensy41.html
[32]: https://itsfoss.com/content/images/2025/10/teensy41_4.jpg
[33]: https://www.sparkfun.com/teensy-4-1.html
[34]: https://pine64.com/product/pinecone-bl602-evaluation-board/
[35]: https://itsfoss.com/content/images/2025/10/Pinecone.jpg
[36]: https://www.sparkfun.com/qwiic
[37]: https://www.smart-prototyping.com/Qwiic.html
[38]: https://www.sparkfun.com/sparkfun-redboard-qwiic.html
[39]: https://itsfoss.com/content/images/2025/10/SparkfunReadBoard.jpg
[40]: https://www.sparkfun.com/sparkfun-thing-plus-esp32-wroom-usb-c.html
[41]: https://itsfoss.com/content/images/2025/10/20168Diagonal.webp
