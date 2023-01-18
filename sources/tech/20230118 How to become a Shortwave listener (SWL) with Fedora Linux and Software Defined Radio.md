[#]: subject: "How to become a Shortwave listener (SWL) with Fedora Linux and Software Defined Radio"
[#]: via: "https://fedoramagazine.org/how-to-become-a-shortwave-listener-swl-with-fedora-linux-and-software-defined-radio/"
[#]: author: "Bogomil Shopov https://fedoramagazine.org/author/bogomil/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to become a Shortwave listener (SWL) with Fedora Linux and Software Defined Radio
======

![][1]

Image by [John DiLiberto][2] from [Pixabay][3]

Catching signals from others is how we have started communicating as human beings. It all started, of course, with our vocal cords. Then we moved to[ smoke signals][4] for long-distance communication. At some point, we discovered radio waves and are still using them for contact. This article will describe how you can tune in using Fedora Linux and an SDR dongle.

## **My journey**

I got interested in radio communication as a hobby when I was a kid, while my local club, LZ2KRS, was still a thing. I was so excited to be able to listen and communicate with people worldwide. It opened a whole new world for me. I was living in a communist country back then and this was a way to escape just for a bit. It also taught me about ethics and technology.  

Year after year my hobby grew and now, in the Internet era with all the cool devices you can use, it’s getting even more exciting. So I want to show you how to do it with Fedora Linux and a hardware dongle.

## **What is Ham Radio**

Amateur Radio (ham radio) is a popular hobby and service that brings people, electronics, and communication together. People use ham radio to talk across town, worldwide, or even into space, without the Internet or cell phones. 

## **What’s SWLing?**

To broadcast with your ham radio or SDR system, you need to obtain a license from a governmental body. But to intercept signals and listen to the open communication between two amateur radio stations, you don’t need one.

The term SWLing comes from the abbreviation of Short Wave Listener, where you listen to stations communicating in the shortwave bands between 3 and 30 MHz. This can be used for long-distance communication using the [ionosphere][5], a layer of the Earth’s atmosphere. 

To get started, you don’t need a license. Still, I recommend getting yourself an SWL sign to identify yourself in a listening contest. These are competitions for categories like who will discover the most connections in a month or who can listen to contacts from each country in the world. 

### **How to get an SWL Sign?**

There are two options:

  * Contact your national radio club and ask them to issue one for you. I got my Czech one, OK1-36568, after a few weeks.
  * Join the [Short Wave Amateur Radio Listening][6] community and request a sign there.



You will get more information and help from either of these locations if you get stuck in some fashion! 

### **QSL Cards**

You can also use your sign to send QSL cards via post or electronically. This is a great way to communicate with people worldwide and make friends.

Per Wikipedia, *A ****QSL card**** is a written confirmation of either a two-way radio communication between two amateur radio or citizens band stations; a one-way reception of a signal from an AM radio, FM radio, television, or shortwave broadcasting station; or the reception of a two-way radio communication by a third party listener (in our case). *

A typical QSL card is the same size and made from the same material as a regular postcard; most are sent through snail mail. 

# **Replace the radio receiver with your Fedora Linux.**

The focal point of the ham radio hobby is the radio transmitter/receiver. Most of the time, enthusiasts build their radio from scratch, but this differs from what I will write about here. 

## **SDR**

A software-defined radio (SDR) system is a radio communication system that uses software for the modulation and demodulation of radio signals. In other words, a piece of hardware and software takes the place of a radio transmitter/receiver. This helps you discover more in a way that you are familiar with – a User Interface with built-in functions instead of the limited interface of a radio receiver. 

My explanation oversimplifies things, so if you want to go deep and read more about SDR, [here is an excellent start.][7]

## **SDR Set Up under Fedora Linux**

### Choosing the proper hardware

If you search the Internet for an SDR dongle, you’ll find tons of ideas depending on your budget. In this tutorial, I’ll work with the one I have, which works well under Fedora 37 – it is available from [Nooelec][8].

A note: The dongle covers frequencies from 25MHz to 1750MHz, which doesn’t cover the Short Wave bands. You would need an additional device to listen to them. This is included in the package I linked above. Some other hardware providers offer all-in-one products.

### **Check if the dongle is visible**

Before installing anything, detect whether Fedora Linux recognizes your USB dongle. I hope you didn’t buy a fake one :-). Use the following command to list the USB devices on your system.

```

    lsusb

```

One of the output lines (in the case of Nooelec) should be

_Realtek Semiconductor Corp. RTL2838 DVB-T_

![][9]

### **Now proceed by installing the software you need**

Fedora offers a set of tools and [drivers packaged as a group][10]. Even though you would not use all the components in this package from the beginning, I recommend installing it. You’ll have more software to play with.

```

    sudo dnf group install 'Electronic Lab'

```

I advise you to explore what’s in the group by running this command:

```

    sudo dnf group info 'Electronic Lab'

```

Now check if you have everything set up correctly by running:

```

    rtl_test

```

You should see something like this:

![][11]

Do not forget to kill this process because the device will be busy and cannot be used in the next step. A simple Ctrl + c works.

## **Gqrx**

You have the dongle already in your device’s USB port and all the software you need to get started. 

 Now it’s time to intercept your first signal. Start the program called [Gqrx][12]. Don’t be alarmed by the strange interface. You’ll get used to it. 

### **Configure the I/O Device Screen**

![][13]

From the “Device” Dropdown, select the ‘**RealtekRTL2838..**.’

Leave the rest untouched for the moment.

If you don’t see your device there, click the “**Device Scan**” button at the bottom of the screen.

When your device is selected, click “OK” and the dialogue will close.

### **Configure the frequency screen**

Before you start intercepting signals, ensure there is something out there that proves that everything works correctly. Since the dongle covers the FM radio band as well, do this:

  * Locate your favorite radio station’s frequency. Mine is 105MHZ


  * Set it in the Frequency field


  * Select WFM (stereo) in the “Mode” dropdown. If you don’t do this, you will **not** hear a sound.



![][14]

### **Play**

And now, you need to start the reception by clicking the “play button” in your main menu. You will see the frequency visualized like this:

![][15]

If you hear a sound, everything is ready to move to the next step.

If you don’t hear anything, check if everything is set up correctly. You may ask a questions in the comments for this article; I can direct you to the proper forum to solve this.

Feel free to play with some more FM broadcasts. You have the antenna for it in your pack.

## **Let’s go Short Wave**

In the case of the Nooelec, you need to add one more device to the USB dongle and turn it on. Instructions on how to do that are included in the package you receive.  

In short, you plug the “[Up Converter][16]” into your USB dongle and make sure the switch is in the “convert” position. Some videos are available on how to do it if you get stuck.

![][17]

### **You will need an antenna and a good location**

Now things get trickier. If you live in an area where you don’t see an open space out your window or other buildings surround your building, you might have trouble catching a Short Wave radio amateur signal. 

### **Let’s try this to see if it works**

Try to be in the open. I usually listen from my terrace, which could be better but works under particular conditions.

Apart from the hardware, you would need a long wire to act as your antenna. Try the antenna that comes with the hardware initially – the telescoping one from [Nooelec][8], but it will catch only powerful signals.

### **Let’s go back to Gqrx**

Now with the converter, you need to make some changes to your device screen:

![][18]

Please note the –**125Mhz** for the **LNB LO field**. This is required for the Up Converter to work.

Tune your frequency to 14.100 Mhz and make sure your Mode is [USB][19] (standing for **Upper sideband**) because this is this band’s main demodulation option.

Then go to your **FFT Settings** screen, use the zoom slider, and set it to see about **100 kHz**. In our case, you should have between 14.05 to 14.15 Mhz on your screen.

Also, click the “**Enable Band Plan**” to see the information about the SW bands you are exploring.

Then hit the play button and start exploring the space between 14.0 and 14.3 Mhz to get any amateur radio transmission.

![][20]

When intercepting a transmission, [adjust your settings][12] to improve your listening experience. It’s a journey that you have already started.

Most probably, you will hear something like this:

> “CQ CQ CQ this is ..(followed by the radio license number spelled with the [ham radio phonetic alphabet][21]). 

Listen very carefully, and by the call sign, you will be able to determine the location of the [radio amateurs’ country][22].

You can visit the [QRZCQ website][23] to learn more about them and even send them a QSL card confirming their connection.

## **Keep the momentum going**.

Now you have some tools and ideas for starting Short Wave Listening. 

This is the first step of an incredible and exciting journey you can have together with your Fedora Linux OS. 

You will discover the pleasure of [building your antenna for the specific band][24], reading more about [how the ionosphere helps][5], how to be a part of a listening competition, and what [those Q-codes][25] mean.

73

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-to-become-a-shortwave-listener-swl-with-fedora-linux-and-software-defined-radio/

作者：[Bogomil Shopov][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/bogomil/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/01/SWL_with_SDR-816x345.jpg
[2]: https://pixabay.com/users/johndiliberto-760933/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=1503297
[3]: https://pixabay.com//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=1503297
[4]: https://en.wikipedia.org/wiki/Smoke_signal
[5]: https://newhams.info/2019/02/20/why-hams-care-about-the-ionosphere/
[6]: https://swarl.org/callsigns
[7]: https://en.wikipedia.org/wiki/Software-defined_radio
[8]: https://www.nooelec.com/store/nesdr-smart-hf-bundle.html
[9]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-11-07-29-03.png
[10]: https://fedoraproject.org/wiki/SDR
[11]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-11-07-34-35.png
[12]: https://gqrx.dk/doc/practical-tricks-and-tips
[13]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-11-07-41-14.png
[14]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-11-07-58-42.png
[15]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-11-08-00-55.png
[16]: https://support.nooelec.com/hc/en-us/articles/360005812474-Ham-It-Up-Upconverter
[17]: https://fedoramagazine.org/wp-content/uploads/2023/01/20230113_102025-576x1024.jpg
[18]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-13-03-41-15.png
[19]: https://www.mdarc.org/operating-aids/lsb-or-usb
[20]: https://fedoramagazine.org/wp-content/uploads/2023/01/Screenshot-from-2023-01-13-03-48-59-1024x287.png
[21]: https://portablehamradio.com/phonetic-alphabet/
[22]: http://on4sh.be/ham/prefix.htm
[23]: https://www.qrzcq.com/
[24]: https://www.ciphermachinesandcryptology.com/en/swl.htm
[25]: https://portablehamradio.com/ham-radio-terms-q/
