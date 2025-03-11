[#]: subject: "Prolong Laptop Battery Life in Linux by Limiting Charging Levels"
[#]: via: "https://itsfoss.com/limit-battery-charging-linux/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Prolong Laptop Battery Life in Linux by Limiting Charging Levels
======

[![Warp Terminal][1]][2]

In case you didn't know it already, regularly charging the battery to 100% or fully discharging it puts your battery at stress and may lead to poor battery life in long run.

I am not making claims on my own. This is what the experts and even the computer manufactures tell you.

As you can see in the official Lenovo video above, continuous full charging and discharging accelerate the deterioration of battery health. They also tell you that the optimum battery charging range is 20-80%.

![][3]

Although Lenovo also tells you that battery these days are made to last longer than your computer. Not sure what's their idea of an average computer lifespan, I would prefer to keep the battery life healthy for a longer period and thus extract a good performance from my laptop as long as it lives.

I mean, it's all about following the best practices, right?

Now, you could manually plug and unplug the power cord but it won't work if you are connected to a docking station or use a modern monitor to power your laptop.

What can you do in that case? Well, to control the battery charging on Linux, you have a few options:

  * KDE Plasma has this as an in-built feature. That's why KDE is ❤️
  * GNOME has extensions for this. Typical GNOME thing.
  * There are command line tools to limit battery charging levels. Typical Linux thing 😍



Let's see them one by one.

📋

Please verify [which desktop environment you are using][4] and then follow the appropriate method.

### Limit laptop battery charging in KDE

If you are using KDE Plasma desktop environment, all you have to do is to open the Settings app and go to Power Management. In the Advanced Power Settings, you'll see the battery levels settings.

I like that KDE informs the users about reduced battery life due to overcharging. It even sets the charging levels at 50-90% by default.

![][5]

Of course, you can change the limit to something like 20-80. Although, I am not a fan of the lower 20% limit and I prefer 40-80% instead.

![][6]

That's KDE for you. Always caring for its kusers.

💡

It is possible that the battery charging control feature may need to be enabled from the BIOS. Look for it under power management settings in BIOS.

### Set battery charging limit in GNOME

Like most other things, GNOME users can achieve this by using a GNOME extension.

There is an extension called [ThinkPad Battery Threshold][7] for this purpose. Although it mentions ThinkPad everywhere, you don't need to own a Lenovo ThinkPad to use it.

From what I see, the command it runs should work for most, if not all, laptops from different manufacturers.

I have a detailed tutorial on [using GNOME Extensions][8], so I won't repeat the steps.

Use the [Extension Manager tool][9] to install ThinkPad Battery Threshold extension.

Once the extension is enabled, you can find it in the system tray. On the first run, it shows red exclamation mark because it is not enabled yet.

![][10]

If you click on the Threshold settings, you will be presented with configuration options.

![][11]

Once you have set the desired values, click on apply. Next, you'll have to click Enable thresholds. When you hit that, it will ask for your password.

At this screen, you can have a partial hint about the command it is going to run it.

![][12]

📋

From what I experienced, while it does set an upper limit, it didn't set the lower limit for my Asus Zenbook. I'll check it on my Tuxedo laptop later. Meanwhile, if you try it on some other device, do share if it works for the lower charging limit as well.

### Using command line to set battery charging thresholds

🚧

You must have [basic knowledge of the Linux command line][13]. That's because there are many moving parts and variables for this part.

Here's the thing. For most laptops, there should be file(s) to control battery charging in `/sys/class/power_supply/BAT0/` directory but the file names are not standard. It could be `charge_control_end_threshold` or `charge_stop_threshold` or something similar.

Also, you may have more than one battery. For most laptops, it will be BAT0 that is the main battery but you need to make sure of that.

Install the `upower` CLI tool on your distribution and then use this command:

```

    upower --enumerate

```

It will show all the power devices present on the system:

```

    /org/freedesktop/UPower/devices/battery_BAT0
    /org/freedesktop/UPower/devices/line_power_AC0
    /org/freedesktop/UPower/devices/line_power_ucsi_source_psy_USBC000o001
    /org/freedesktop/UPower/devices/line_power_ucsi_source_psy_USBC000o002
    /org/freedesktop/UPower/devices/headphones_dev_BC_87_FA_23_77_B2
    /org/freedesktop/UPower/devices/DisplayDevice

```

You can find the battery name here.

The next step is to look for the related file in `/sys/class/power_supply/BAT0/` directory.

If you find a file starting with `charge`, note down its name and then add the threshold value to it.

In my case, it is `/sys/class/power_supply/BAT0/charge_control_end_threshold`, so I set an upper threshold of 80 in this way:

```

    echo 80 | sudo tee /sys/class/power_supply/BAT0/charge_control_end_threshold

```

You could also [use nano editor][14] to edit the file but [using tee command][15] is quicker here.

💡

You can also [use tlp][16] for this purpose by editing the `/etc/tlp.conf` file.

### Conclusion

See, if you were getting 10 hours of average battery life on a new laptop, it is normal to expect it to be around 7-8 hours after two years. But if you leave it at full charge all the time, it may come down to 6 hours instead of 7-8 hours. The numbers are for example purpose.

This 20-80% range is what the industry recommends these days. On my Samsung Galaxy smartphone, there is a "Battery protection" setting to stop charging the device after 80% of the charge.

I wish a healthy battery life for your laptop 💻

--------------------------------------------------------------------------------

via: https://itsfoss.com/limit-battery-charging-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/03/Optimum-battery-charge.png
[4]: https://itsfoss.com/find-desktop-environment/
[5]: https://itsfoss.com/content/images/2025/03/battery-charge-setting-kde-1.png
[6]: https://itsfoss.com/content/images/2025/03/battery-charge-80-40.png
[7]: https://extensions.gnome.org/extension/4798/thinkpad-battery-threshold/
[8]: https://itsfoss.com/gnome-shell-extensions/
[9]: https://flathub.org/apps/com.mattjakeman.ExtensionManager
[10]: https://itsfoss.com/content/images/2025/03/thinkpad-battery-threshold-gnome-extension-1.png
[11]: https://itsfoss.com/content/images/2025/03/configure-battery-charging-threshold-gnome.png
[12]: https://itsfoss.com/content/images/2025/03/thinkpad-battery-threshold-extension-script.png
[13]: https://courses.linuxhandbook.com/courses/linux-for-devops/
[14]: https://itsfoss.com/nano-editor-guide/
[15]: https://linuxhandbook.com/tee-command/
[16]: https://linrunner.de/tlp/settings/battery.html
