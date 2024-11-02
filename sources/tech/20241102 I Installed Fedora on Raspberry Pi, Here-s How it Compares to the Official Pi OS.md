[#]: subject: "I Installed Fedora on Raspberry Pi, Here's How it Compares to the Official Pi OS"
[#]: via: "https://itsfoss.com/fedora-on-raspberry-pi/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Installed Fedora on Raspberry Pi, Here's How it Compares to the Official Pi OS
======

[![Warp Terminal][1]][2]

Fedora is one of those Linux distributions that tends to fly under the radar for Raspberry Pi users because there's Raspberry Pi OS and [many other distros fit for Raspberry Pi][3].

But with Fedora’s official support for ARM devices, it is definitely worth a closer look, especially if you’re thinking of using your Raspberry Pi as your main PC.

So, we are going to put that theory into the test, and **I will be installing Fedora on my Raspberry Pi 4 with 4 GB of RAM.** If you have some other Raspberry Pi board, the performance/experience can be slightly different.

### Why Fedora?

Undoubtedly, [Fedora][4] has been around for years and is backed by [Red Hat][5], so it is well-maintained and frequently updated.

Fedora is popular for its [GNOME desktop environment][6] and its focus on being up-to-date with the latest technologies.

If you have been using Raspberry Pi OS, Fedora will feel a bit heavier, but it also offers a lot more in terms of features and polish.

So, let us get started... 😊

![][7]

### Installation

✋

At the time of writing this article, Fedora is not officially supported on Raspberry Pi 5. I tried it for fun, but it failed.

##### Step 1: Downloading the right version

To get started, you’ll need the correct version of Fedora. Head over to the [Download's page][8] and grab the **Fedora Workstation** image for ARM (aarch64).

Make sure you are getting the image specifically for ARM devices, as those are built to work with Raspberry Pi hardware.

![][9]

The file you download will be compressed as `.xz`, but you don’t need to extract it. We’ll flash this file directly onto our microSD card.

##### Step 2: Flashing Fedora to a microSD Card

For this guide, I will be using **Raspberry Pi Imager** to write Fedora to the microSD card.

There are third-party tools like Balena Etcher, but Raspberry Pi Imager is simple and gets the job done. You can get it from [Raspberry Pi's download page][10].

![Steps to flash Fedora using Raspberry Pi Imager][11]

  1. Insert your microSD card (at least 16 GB, preferably 32 GB).
  2. Open **Raspberry Pi Imager** on your PC.
  3. Select **"Use Custom"** when choosing the OS and find the Fedora image you just downloaded.
  4. Select the microSD card as the target storage.
  5. Hit **"Write"** and let the tool burn the image to your card.



This process can take a few minutes, depending on the speed of your card. Once done, safely eject the card.

##### Step 3: First Boot

Now comes the exciting part, plug the microSD card into your Raspberry Pi 4, hook it up to your monitor, and power it on.

Apologies for the shaky video experience. I wanted you to see the initial boot time of Fedora, which is significantly slower than Raspberry Pi OS.

On my Raspberry Pi 4 with 4 GB of RAM, it took more than a minute to load up to its home screen.

If you have used GNOME before, this will feel familiar, if not, it is a bit different from the lightweight LXDE desktop you would be used to on Raspberry Pi OS.

### Exploring Fedora's Desktop on Raspberry Pi

Once Fedora is up and running, you will notice that it is a much more feature-rich experience than the Raspberry Pi OS.

The GNOME desktop offers smooth transitions, a dock, and an 'Activities' overview for multitasking. Of course, you probably know this if you have used Fedora or any GNOME-based distribution on your computer.

![Once you are booted, you will see the GNOME desktop environment][12]

![This is fedora's app drawer, looks pretty neat!][13]

However, GNOME is heavier on resources compared to the lightweight desktop environments on Raspberry Pi OS, so it can feel sluggish at times, especially when you start opening multiple apps or browser tabs.

I am guessing you could eliminate some performance issues with an 8 GB RAM Raspberry Pi. You can try 😉

##### Performance and Usability

  * **Web browsing** : Firefox comes pre-installed, and performance is solid for basic browsing. However, websites heavy on media (like YouTube or news sites) will start to slow things down.
  * **Office tasks** : LibreOffice opens without much delay and handles basic word processing and spreadsheets fine.
  * **Multitasking** : Fedora supports multitasking, but once you have a few apps open, the microSD card’s speed becomes the limiting factor. This could be improved if you’re booting from an SSD instead.



GNOME is a full-featured desktop environment, and if you’re looking to use your Pi as a desktop PC, Fedora can definitely do the job. It just won’t feel as snappy as Raspberry Pi OS on a micro SD card.

### Fedora Vs. Raspberry Pi OS

Now, let’s talk about how Fedora stacks up against Raspberry Pi OS. Both have their strengths, but which one works better really depends on what you are using your Pi for.

##### **Boot times**

Fedora boots slower than Raspberry Pi OS (not the initial boot). Whether you want to wait 20–25 seconds for it to load up, or if it is too much for you? 😫

It depends on your preferences.

##### **Desktop performance**

If you are using your Pi 4 for basic tasks, Raspberry Pi OS feels a lot faster because it uses a lightweight desktop (LXDE or the newer Raspberry Pi Desktop).

Fedora’s GNOME environment is much heavier, so while it looks and feels more modern, it demands more resources. You will notice this when switching between apps or launching heavier software.

![There is no app running at this moment, these spikes are all due to Gnome][14]

##### **Package management**

Fedora uses `dnf` instead of `apt` (used by Raspberry Pi OS). It is not better or worse, just different.

Fedora’s updates tend to be more frequent and cutting-edge, while Raspberry Pi OS sticks to stable releases.

Fedora’s GNOME environment also comes with the **GNOME Software** app, which provides a friendly graphical interface for installing and updating software.

![][15]

It’s a more user-friendly experience compared to Raspberry Pi OS, where you’re likely to use the terminal or the basic “ _Add/Remove Software_ ” tool.

But, you can also use [Pi Apps][16]. So, it is your call.

![][17]

##### Hardware Support and Drivers

One area where Raspberry Pi OS has a clear advantage is in hardware support. Since it is specifically designed for the Raspberry Pi, you can expect better support for things like GPIO, the camera module, and hardware accelerations like video encoding and decoding.

Fedora works fine on the Pi, but it is a more general-purpose operating system, so some of these Pi-specific features might not work as seamlessly out of the box.

For instance, if you're doing projects involving the GPIO pins, sensors, or cameras, Raspberry Pi OS will have better tools and community support to get you up and running faster.

Fedora can handle these things too, but you may need to install additional drivers or do more troubleshooting.

I mean Fedora doesn't even install properly on the newer Raspberry Pi 5 even after one year of its release. That speaks volumes on the hardware compatibility.

##### **Customization and Flexibility**

The Raspberry Pi OS is tailored to be simple and functional. It is great if you just want a working environment with minimal setup.

But Fedora gives you more flexibility in terms of customization. GNOME allows for extensions and tweaks that can modify how the desktop behaves and looks.

For users who enjoy tinkering with their desktop environment, Fedora offers a more flexible platform.

##### **Community and Documentation**

Both Fedora and Raspberry Pi OS have active communities, but they cater to different kinds of users.

Raspberry Pi OS, being tailored for the Pi, has a larger collection of Pi-specific documentation, tutorials, and forums.

It’s more beginner-friendly, especially if you're diving into projects like home automation, robotics, [linux home server][18] or media centers.

Fedora, meanwhile, is backed by the larger Fedora community and Red Hat.

While it may not have as much Pi-specific support, its community is vast and knowledgeable and the Linux ecosystem in general, so help is never far away if you’re looking for more advanced configurations.

**Suggested Read 📖**

![][17]

### Final Thoughts

Installing Fedora on a Raspberry Pi 4 gives you a polished Linux desktop experience, but it does come with some trade-offs.

If you are looking for a feature-rich OS with more advanced capabilities, Fedora is a great choice.

But if you want speed and efficiency for lighter tasks, the Raspberry Pi OS is still the winner, especially when running off a micro SD card.

Fedora’s GNOME desktop can be a bit resource-hungry, but on the Raspberry Pi 4 with 4 GB of RAM, it is _mostly_ usable for everyday tasks like web browsing, coding, or light office work.

For a smoother experience to using it as a desktop replacement, I recommend upgrading to an SSD (with a bigger RAM too). It offers faster read/write speeds and is more reliable than an SD card, reducing the risk of data corruption.

_Are you thinking of 'hopping' to Fedora on your Raspberry Pi? Do share your experience in the comments below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/fedora-on-raspberry-pi/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/raspberry-pi-os/
[4]: https://fedoraproject.org/
[5]: https://www.redhat.com/en
[6]: https://www.gnome.org/
[7]: https://itsfoss.com/content/images/2024/10/fedora-homepage-1.png
[8]: https://fedoraproject.org/workstation/download
[9]: https://itsfoss.com/content/images/2024/10/fedora-downloads-page-1.png
[10]: https://www.raspberrypi.com/software/
[11]: https://itsfoss.com/content/images/2024/10/feodra-rpi-imager-steps.png
[12]: https://itsfoss.com/content/images/2024/10/fedora-after-first-boot.png
[13]: https://itsfoss.com/content/images/2024/10/fedora-app-drawer.png
[14]: https://itsfoss.com/content/images/2024/10/fedora-processes.png
[15]: https://itsfoss.com/content/images/2024/10/fedora-gnome-store-1.gif
[16]: https://itsfoss.com/pi-apps-store/
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[18]: https://itsfoss.com/homelab-usage/
