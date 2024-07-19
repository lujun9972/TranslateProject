[#]: subject: "Open-Source Battery Saver App for Android With Fine Controls"
[#]: via: "https://news.itsfoss.com/savertuner/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Open-Source Battery Saver App for Android With Fine Controls
======
Your phone's battery juice should last longer with these tweaks.
[![][1]][2]

With all the advancements to the Android operating system, we do not need third-party battery saving applications for the most part.

If you have been using Android for a while, you will get the reference to all the crazy battery focused applications we have had, which used to drain more battery than actually save it 😄

Fret not, I have come across a useful open-source Android app that my colleague, Shivam, suggested, that actually makes sense to keep.

📋

It is geared towards specific users who want all that control, and are willing to enable some advanced settings for it to work.

### SaverTuner: If You Think You Need It

![][3]

SaverTuner is not magic, it helps you toggle fine-grained controls that translate to a better battery life. It is based on [Buoy][4], meant to act as an extension to the built-in Android battery saver. Unlike some dubious “battery booster” applications, it works as you expect it to, depending on your customized settings.

Considering you have it set up, you get various options to choose from, unlike the default battery saving options in most devices.

You can enable the battery saving settings to be _extreme, high, moderate, light_ , or just keep using the defaults of your device.

While these are the easy toggle options, you can go further by **forcing apps to sleep** , **dialing down the screen brightness** to its minimum (sometimes lower than what manufacturer allows). Also, a useful option to enable “ **quick doze** ” that enables deep sleep as soon as you turn off the screen, increasing the standby time.

![][5]

You also get other controls like:

  * Enable/Disable Vibrations
  * Show power saving mode to applications without actually enabling it
  * Import/Export settings
  * Enable firewall for security



To get started, you need to install it, and then enable a specific permission using ADB (via Debugging) or you can decide to root your device if you like. It does not need a rooted device to work, so it is up to you the method you decide for it to work.

You may follow our tutorial on installing ADB if it is your first time:

![][6]

🚧

Before you uninstall the app, make sure to revert to the default profile to reset the configuration.

### Install SaverTuner

SaverTuner is available on [F-Droid][7]. You can also install the APK directly from its [Codeberg source code page][8].

[SaverTuner][9]

_💬 What do you think about it? Let me know in the thoughts!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/savertuner/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/content/images/2024/07/saver-tuner-foss-1-1.jpg
[4]: https://github.com/tytydraco/Buoy
[5]: https://news.itsfoss.com/content/images/2024/07/saver-tuner-foss-2.jpg
[6]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[7]: https://f-droid.org/en/packages/s1m.savertuner/
[8]: https://codeberg.org/s1m/savertuner
[9]: https://f-droid.org/packages/s1m.savertuner/
