[#]: subject: "Using On-Screen Keyboard in Raspberry Pi OS"
[#]: via: "https://itsfoss.com/raspberry-pi-os-onscreen-keyboard/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Using On-Screen Keyboard in Raspberry Pi OS
======

[![Warp Terminal][1]][2]

From Kiosk projects to [homelab dashboards][3], there are numerous usage of a touch screen display with Raspberry Pi.

And it makes total sense to use the on-screen keyboard on the touch device rather than plugging in a keyboard and mouse.

Thankfully, the latest versions of Raspberry Pi OS provide a simple way to install and use the on-screen keyboard.

![On-screen keyboard on Raspberry Pi][4]

Let me show how you can install the on-screen keyboard support on Raspberry Pi OS.

📋

I am using the [DIY Touchscreen by SunFounder][5] (partner link). It's an interesting display that is also compatible with [other SBCs][6]. I'll be doing its full review next week. The steps should also work on other touch screens, too.

![Partner Link][7]

### Just check if you already have the on-screen keyboard support

Raspberry Pi OS Bookworm and later versions include the Squeekboard software for the on-screen keyboard feature.

Now, this package may already be installed by default. If you open a terminal and touch the interface and it brings the keyboard, you have everything set already.

It is also possible that it is installed but not enabled.

Go to the menu, then Preferences and open Raspberry Pi config tool. In the display tab, see if you can change the settings for the on-screen keyboard.

![On-screen keyboard support already installed on Raspberry Pi][8]

If you tap the on-screen keyboard settings and it says, "A virtual keyboard is not installed", you will have to install the software first. The next section details the steps.

![Virtual Keyboard is not installed][9]

### Getting on-screen keyboard in Raspberry Pi OS Bookworm

🚧

You'll need a physical keyboard and mouse for installing the required package If you cannot connect one, you could [try to SSH into the Pi][10].

Update the package cache of your Raspberry Pi first:

```

    sudo apt update

```

The `squeekboard` package provides the virtual keyboard in Debian. Install it using the command below:

```

    sudo apt install squeekboard

```

Once installed, click on the menu and start Raspberry Pi Configuration from the Preferences.

![Access Raspberry Pi Configuration][11]

In the Raspberry Pi Configuration tool, go to the Display tab and touch it.

![][12]

You'll see three options:

  * Enabled always: The on-screen keyboard will be always accessible through the top panel, whether you are using touchscreen or not.
  * Enabled if touchscreen found: The on-screen keyboard is only accessible when it detects a touchscreen.
  * Disabled: Virtual keyboard won't be accessible at all.



Out of these three, you'll be tempted to go for the 'Enabled if touchscreen found'.

However, it didn't work for me. **I opted for Enabled always** instead.

But not all applications will automatically bring up the on-screen keyboard. In my case, Chromium didn't play well. Thankfully, the on-screen keyboard icon at top panel lets you access it at will.

![Virtual keyboard comes up for supported application but it is also accessible from top panel][13]

And this way, you can enjoy the keyboard on a touchscreen.

### Conclusion

For older versions of Raspberry Pi OS, you could also go with the `matchbox-keyboard` package.

```

    sudo apt install matchbox-keyboard

```

Since Squeekboard is for Wayland, perhaps Matchbox will work on Xorg [display server][14].

The [official documents of SunFounder's Touchscreen mentions][15] that Squeekboard is installed by default in Raspberry Pi OS but that was not the case for me.

Installing it was matter of one command and then the virtual keyboard was up and running. This is tested on Raspberry Pi OS but since [Squeekboard][16] is available for Wayland in general, it might work on other operating systems, too.

💬 _Did it work for you? If yes, a simple 'thank you' will encourage me. If not, please provide the details and I'll try to help you._

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-os-onscreen-keyboard/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/homelab-dashboard/
[4]: https://itsfoss.com/content/images/2025/03/raspberry-pi-with-on-screen-keyboard.webp
[5]: https://www.sunfounder.com/collections/1-raspberry-pi-5-collection/products/10inch-touchscreen-for-raspberrypi?ref=itsfoss
[6]: https://itsfoss.com/raspberry-pi-alternatives/
[7]: https://itsfoss.com/content/images/icon/logo2_88e63a14-d758-4866-8135-8596b1337d33_96x96-3.png
[8]: https://itsfoss.com/content/images/2025/03/raspberry-pi-os-enabled-on-screen-keyboard.webp
[9]: https://itsfoss.com/content/images/2025/03/raspberry-pi-os-disabled-on-screen-keyboard.webp
[10]: https://itsfoss.com/ssh-into-raspberry/
[11]: https://itsfoss.com/content/images/2025/03/raspberry-pi-config-1.webp
[12]: https://itsfoss.com/content/images/2025/03/enable-virtual-keyboard-raspberry-pi-1.webp
[13]: https://itsfoss.com/content/images/2025/03/raspberry-pi-with-virtual-keyboard-on-touchscreen-1.webp
[14]: https://itsfoss.com/display-server/
[15]: https://docs.sunfounder.com/projects/ts-10/en/latest/resolution_orientation.html#using-an-on-screen-keyboard
[16]: https://gitlab.gnome.org/World/Phosh/squeekboard
