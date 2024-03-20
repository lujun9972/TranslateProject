[#]: subject: "How to Test Webcam on Ubuntu"
[#]: via: "https://itsfoss.com/test-webcam-ubuntu/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Test Webcam on Ubuntu
======

[![Warp Terminal][1]][2]

Considering you have a webcam device connected to your computer or a laptop with webcam, it is a good idea to test if it works before an important video call.

You would rather not troubleshoot when you are in the middle of a video conferencing session, right?

So, how to test the webcam on Ubuntu or your Linux system before the call?

You have a simple solution: **you can use the cheese webcam app on your Ubuntu system.**

### Using Cheese or Snapshot Webcam App on Ubuntu

By default, Ubuntu comes pre-installed with the Cheese webcam app, unless you opted for a minimal installation of Ubuntu.

First, you need to search for the app:

![][3]

And, then launch the app. Upon launching it, your webcam output should be directly visible if there are no configuration errors:

![][4]

You should be good to go for the video call for the most part (considering you have checked the audio side too).

💡

For a laptop, both the audio/video devices should work as expected out of the box on Ubuntu. But, if it is a PC or if you have external devices connected, you need to ensure the devices are selected in the configuration/preferences of the video call app or service to use it.

And, if it's not visible or if you want to check the resolution/change it, you can head to the app preferences using the hamburger menu icon:

![][5]

In my case, I tested it first with a laptop's built-in camera. If you have a separate webcam device connected, you can set it here in the preference, and then test if it is visible to you.

My external webcam device looked like this, with " **HD Camera** " as the name to select:

![][6]

Normally, you should not have an issue with laptops, but you should always check before a video call.

It is also important to keep in mind, your preferences in the Cheese app do not necessarily carry forward to the web app or service you use to make a video call. So, make sure that you check the preferences of the app you use for the video as well.

Fret not, if you do not have a laptop or a separate webcam device, you can also [use your phone as a camera and mic][7]:

![][8]

📋

At the time of writing, Ubuntu 24.04 LTS was yet to be released, which could feature the new GNOME app — Snapshot as a webcam app instead of Cheese. Just keep that in mind when you try Ubuntu 24.04 LTS, we shall update this article as soon that releases.

### Using the CLI

If you want to see if the webcam device is detected on your system using the terminal, you can also do that by typing the following command:

```

    ls -l /dev/video*

```

If you do not have any video devices connected, it will show you the output that says ' _No such file or directory_ '.

If you have any connected devices, the output will look like this:

![][9]

For each device, you get two lines of output. I added an external webcam, and here you can see the output for the same command:

![][10]

_💬 How do you prefer to test your webcam? Do you face issues with an external webcam compared to a laptop's built-in cam? Share your thoughts in the comments below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/test-webcam-ubuntu/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/03/cheese-app-search.png
[4]: https://itsfoss.com/content/images/2024/03/cheese-webcam-active.png
[5]: https://itsfoss.com/content/images/2024/03/cheese-app-preferences.png
[6]: https://itsfoss.com/content/images/2024/03/webcam-change.png
[7]: https://itsfoss.com/ubuntu-phone-camera-mic/
[8]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[9]: https://itsfoss.com/content/images/2024/03/video-devices-connected.png
[10]: https://itsfoss.com/content/images/2024/03/devices-connected-2.png
