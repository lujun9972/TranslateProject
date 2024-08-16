[#]: subject: "I Discovered This Tiny Feature in Ubuntu 24.04 and I Love it"
[#]: via: "https://itsfoss.com/ubuntu-bluetooth-battery-status/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Discovered This Tiny Feature in Ubuntu 24.04 and I Love it
======

[![Warp Terminal][1]][2]

Bluetooth headphones, Bluetooth mouse, Bluetooth keyboard. Bluetooth is part of our wireless computing life.

There is one problem, though. It is not always easy to know when the Bluetooth devices needs to be charged or its battery should be changed.

Headphones usually announce their battery state when you power them on but once connected, there is no easy way of knowing it again in most devices.

This is why I was pleasantly surprised to discover that Ubuntu 24.04 displayed the battery status of the connected Bluetooth devices.

![Battery status of connected Bluetooth devices in Ubuntu 24.04][3]

As you can see in the screenshot above, my Sony headphone has 70% battery remaining and my Asus mouse is at 50%.

📋

It is highly likely that this feature was already available in older versions of GNOME and Ubuntu but I discovered it only recently. If that's the case, please ignore my ignorance and enthusiasm 😉

### Checking the battery status of connected Bluetooth devices

Please [check your desktop environment][4]. This tutorial is only valid for GNOME desktop users.

Open the Settings application.

![Open Settings app][5]

In here, go to the Power settings from the left sidebar and you should see the battery status of the connected Bluetooth devices on the right pane.

![][6]

As you can see, it shows the battery status of your laptop (if you are using it) and the battery status of any Bluetooth devices connected to your system.

That's super! Isn't it?

✋

Please note that not every Bluetooth device advertises its battery state and thus you may not see battery status for all the Bluetooth devices connected to your system. Most new Bluetooth devices should have this feature but it's not a guarantee.

### Get Bluetooth battery status in the system tray

Don't like going into power settings to check the battery status? How about displaying them in the system tray or the top panel?

There are a couple of GNOME Extensions that enable this functionality.

  * [Bluetooth Battery Indicator][7]: Shows the battery status in the top panel
  * [Bluetooth Battery Meter][8]: Shows the battery status in the system tray



Please read our [guide on using GNOME Extensions][9].

![][10]

### Conclusion

This is a handy feature. It allows me to charge my devices timely. Of course, this is a GNOME desktop feature. Other desktop environments may or may not have this handy feature.

Out of the two devices I used, my Sony headset is rechargeable via USB-C. The Asus mouse uses a single AA alkaline battery. While both devices showed their battery status, not all devices may do the same.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-bluetooth-battery-status/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/08/bluetooth-battery-status-show-ubuntu.png
[4]: https://itsfoss.com/find-desktop-environment/
[5]: https://itsfoss.com/content/images/wordpress/2022/12/open-settings-from-activities-overview.png
[6]: https://itsfoss.com/content/images/2024/08/bluetooth-battery-status-ubuntu.png
[7]: https://extensions.gnome.org/extension/3991/bluetooth-battery/
[8]: https://extensions.gnome.org/extension/6670/bluetooth-battery-meter/
[9]: https://itsfoss.com/gnome-shell-extensions/
[10]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
