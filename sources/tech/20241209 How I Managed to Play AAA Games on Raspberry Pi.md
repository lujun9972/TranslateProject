[#]: subject: "How I Managed to Play AAA Games on Raspberry Pi"
[#]: via: "https://itsfoss.com/raspberry-pi-moonlight-setup/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I Managed to Play AAA Games on Raspberry Pi
======

[![Warp Terminal][1]][2]

Have you ever thought of running high-end AAA games on a Raspberry Pi? Absurd right?

**Spoiler alert** : you can’t. Of course.

But, you may ask — _what about the article's title?_

In fairness, please note that I mentioned "Play" instead of "Run." That is the crucial aspect of my experiment 🤓

**You cannot run the game** , but what you _can_ do is **stream those demanding games from a powerful PC to your Raspberry Pi** using [**Moonlight**][3], and it works like a charm!

![][4]

In this article, I’ll show you how I turned my humble Raspberry Pi 5 into a game-streaming powerhouse.

Stick with me for a breakdown of every step you need to replicate this feat. And don’t worry—I’ll try keeping the technical jargon at bay.

### What is Moonlight?

Picture this: your beastly gaming rig is upstairs, but your comfy couch (and bigger TV) is downstairs.

Instead of running an HDMI cable across the house, you can use [Moonlight][3] to stream your games over your home network. Moonlight uses Nvidia’s [GameStream][5] technology to deliver smooth, high-definition, low-latency gameplay.

The Raspberry Pi, with its small form factor and affordable price, makes the perfect device for this setup.

Whether you’re using a Raspberry Pi 4 or the newer Raspberry Pi 5, Moonlight can help you bring AAA gaming to the comfort of any room.

### What You’ll Need

Here’s the gear that I used for this project:

💡

A wired connection is highly recommended for both your Raspberry Pi and your PC for the best experience.

  * **Raspberry Pi 4/5** (the more powerful, the better)
  * **MicroSD Card** (16 GB or larger, for the OS)
  * **Ethernet Cable** (for low latency)
  * **USB Mouse and Keyboard**
  * **Controller** (Xbox or PlayStation, optional but recommended)
  * **A PC with a Compatible Nvidia GPU** (running [Sunshine][6], an open-source GameStream host)



#### Step 1: Preparing Your Raspberry Pi

📋

You should [install the official Raspberry Pi OS on your Pi][7] first.

Start by making sure your Raspberry Pi is updated. Open the terminal and run these commands:

```

    sudo apt update && sudo apt full-upgrade -y

```

![][8]

You will need `curl` for downloading the repository and `pulseaudio` for audio support. Install them with:

```

    sudo apt install curl pulseaudio

```

![][9]

Set PulseAudio to start automatically when the Pi boots:

```

    sudo systemctl --global enable pulseaudio

```

![][10]

#### Step 2: Installing Moonlight

Run the following command to add the Moonlight package repository:

```

    curl -1sLf 'https://dl.cloudsmith.io/public/moonlight-game-streaming/moonlight-qt/setup.deb.sh' | distro=raspbian codename=$(lsb_release -cs) sudo -E bash

```

![][11]

Once the repository is added, install Moonlight with:

```

    sudo apt install moonlight-qt

```

![][12]

#### Step 3: Configuring Moonlight

Edit the crontab file to launch Moonlight automatically when your Pi starts. This way, you get a seamless experience.

```

    crontab -e

```

![][13]

Add this line at the end of the file:

```

    @reboot moonlight-qt

```

![][14]

Reboot your Pi to apply the changes:

```

    sudo reboot now

```

#### Step 4: Pairing Moonlight with your PC

Download and install [Sunshine][15], an open-source GameStream server, on your PC. This is essential for pairing with Moonlight.

![][16]

Once installed, it will redirect you to a browser window, where you need to set up a user first before you can access anything:

![][17]

Once done, you are ready to launch Moonlight on your Raspberry Pi.

💡

If your PC doesn’t appear automatically, click the ****+**** icon and manually enter your PC’s IP address.

![][18]

You’ll be prompted with a PIN code. Enter this PIN in the Sunshine web interface on your PC to complete the pairing.

![][19]

You need to enter this PIN here in the Sunshine web UI:

![][20]

Sunshine should automatically add the desktop to stream, but you can manually use Sunshine’s web interface to add specific applications, the desktop, or games to the list of streamable apps.

![][21]

#### Step 5: Start Streaming!

With everything set up, you can now stream games to your Raspberry Pi. Connect your controller, choose a game from the Moonlight interface, and enjoy the magic of high-performance gaming on your Pi.

If you are wondering the input lag and poor framerate, that's all because I tested this whole setup on Wi-Fi just for the tutorial. Unlike me, you are smart and will use a wired connection.

### Final Thoughts

Running AAA games directly on a Raspberry Pi is not an ideal thought because of what it's built for. Thanks to Moonlight, you can stream games effortlessly on your Raspberry Pi, so it is always useful in one way or the other.

With a bit of preparation, your Raspberry Pi can transform into a versatile gaming client, letting you enjoy PC-quality gaming anywhere in your home.

_💭 Have questions or tips of your own? Drop them in the comments below, I’d love to hear from you!_

Happy streaming! 🎮

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-moonlight-setup/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://moonlight-stream.org
[4]: https://itsfoss.com/content/images/2024/11/steam-game-library-inside-moonlight.jpg
[5]: https://www.nvidia.com/en-us/support/gamestream/gamestream-pc-setup/
[6]: https://github.com/LizardByte/Sunshine
[7]: https://itsfoss.com/tutorial-how-to-install-raspberry-pi-os-raspbian-wheezy/
[8]: https://itsfoss.com/content/images/2024/11/updating-rpi.png
[9]: https://itsfoss.com/content/images/2024/11/installing-curl-and-pulseaudio.png
[10]: https://itsfoss.com/content/images/2024/11/enabling-pulseaudio-at-startup.png
[11]: https://itsfoss.com/content/images/2024/11/adding-moonlight-repo.png
[12]: https://itsfoss.com/content/images/2024/11/installing-moonlight.png
[13]: https://itsfoss.com/content/images/2024/11/editing-crontab-2.png
[14]: https://itsfoss.com/content/images/2024/11/crontab-adding-reboot-tag.png
[15]: https://app.lizardbyte.dev/Sunshine/?lng=en
[16]: https://itsfoss.com/content/images/2024/11/sunshine-github-release.png
[17]: https://itsfoss.com/content/images/2024/11/sunshine-setting-up-user.png
[18]: https://itsfoss.com/content/images/2024/11/launching-moonlight-first-time-1.png
[19]: https://itsfoss.com/content/images/2024/11/moonlight-pin.png
[20]: https://itsfoss.com/content/images/2024/11/sunshine-adding-pin.png
[21]: https://itsfoss.com/content/images/2024/11/sunshine-device-functionality.png
