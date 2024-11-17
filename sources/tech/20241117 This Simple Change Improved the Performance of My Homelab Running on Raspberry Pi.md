[#]: subject: "This Simple Change Improved the Performance of My Homelab Running on Raspberry Pi"
[#]: via: "https://itsfoss.com/pi-swap-increase/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Simple Change Improved the Performance of My Homelab Running on Raspberry Pi
======

[![Warp Terminal][1]][2]

Running a homelab on a Raspberry Pi can be a rewarding yet challenging experience. My journey began with a [Raspberry Pi 4][3] (4 GB) hosting several [WordPress][4] websites and a few [Ghost][5] blogs.

Recently, I became more ambitious, aiming to expand my setup with [Nextcloud][6] for private cloud storage and [ONLYOFFICE][7] to create a fully self-hosted ecosystem. This is where things got interesting and a bit messy.

Adding Nextcloud and ONLYOFFICE to the mix put a significant strain on my Pi 4, leading to slowdowns, occasional freezes, and a slew of input/output errors.

After some investigation, **I found that the default 200 MB swap memory was entirely maxed out**.

Curious, I thought, “Why limit it to just 200 MB? Let’s see what happens if I increase it.” **So, I expanded the swap space to 2 GB, and my Pi started running noticeably smoother.**

Here’s how I did it, and some tips if you're considering the same.

### Prerequisites

To follow along, make sure you have:

  * A Raspberry Pi running Raspberry Pi OS.
  * Access to a terminal (either directly or via SSH).
  * Sufficient free space on your SD card for the additional swap.



### Step 1: Turn off the current swap

Before resizing the swap file, you’ll need to turn off the active swap space. Run the following command in your terminal:

```

    sudo dphys-swapfile swapoff

```

This disables the swap temporarily, allowing you to adjust its size.

![][8]

### Step 2: Edit the swap configuration file

Next, open the swap configuration file in a text editor. I prefer `nano`, but any editor will do:

```

    sudo nano /etc/dphys-swapfile

```

Look for the line `CONF_SWAPSIZE=200` (or a similar value). This line defines the current swap size in megabytes.

![][9]

### Step 3: Increase the swap size

Change the value to your desired size. For instance, setting it to 2048 will give you 2GB of swap space:

```

    CONF_SWAPSIZE=2048

```

![][10]

Remember that the size you specify must be available on your SD card. Save your changes by pressing `CTRL + X`, followed by `Y`, then `Enter` to confirm.

### Step 4: Apply the new swap size

After updating the configuration, recreate the swap file to match the new size by running:

```

    sudo dphys-swapfile setup

```

This command will delete the old swap file and create a new one with the size specified in the configuration file.

![][11]

### Step 5: Turn the wwap back on

Now, re-enable swap with:

```

    sudo dphys-swapfile swapon

```

At this point, your new swap file is active, but for the best results, reboot your Pi to ensure all applications recognize the additional memory:

```

    sudo reboot now

```

![Actual screenshot of my Pi 4 resource usage after adding 2Gb of swap][12]

### Why Increase Swap Space?

The Raspberry Pi’s swap file acts as an overflow for RAM, giving the system extra memory by writing some data to disk when physical RAM is fully utilized.

Although accessing swap memory is slower than RAM, it can help manage resource-intensive applications by preventing crashes or system freezes.

However, keep in mind that an unnecessarily larger swap file can wear down your SD card over time.

### Final Thoughts

Increasing my Raspberry Pi's swap space from 200 MB to 2 GB made a noticeable difference. My Nextcloud and OnlyOffice setup has been running more smoothly, with fewer slowdowns and far less system freezing.

However, this solution is still not perfect, SD card wear and the slower nature of swap memory mean it's more of a temporary solution than a permanent fix.

For anyone trying to push the limits of a Pi like I have, increasing swap space can provide short-term relief, but it’s essential to consider upgrading to hardware with more RAM if you're regularly maxing out your resources.

In my case, I'm exploring x86 servers to handle my containers and self-hosted applications more robustly, and I’ll cover that journey in a future article.

This experience has further reinforced my love for tinkering and optimizing setups, but also reminded me of the limitations of working on minimal hardware.

Sometimes, a modest hardware upgrade can make all the difference in creating a smoother, more reliable self-hosted ecosystem.

--------------------------------------------------------------------------------

via: https://itsfoss.com/pi-swap-increase/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.raspberrypi.com/products/raspberry-pi-4-model-b/
[4]: https://wordpress.org
[5]: https://ghost.org/
[6]: https://nextcloud.com/
[7]: https://www.onlyoffice.com/
[8]: https://itsfoss.com/content/images/2024/11/turning-off-swap.png
[9]: https://itsfoss.com/content/images/2024/11/initial-swap-size-1.png
[10]: https://itsfoss.com/content/images/2024/11/increased-swap-space-to-2048.png
[11]: https://itsfoss.com/content/images/2024/11/reloading-swap-setup.png
[12]: https://itsfoss.com/content/images/2024/11/my-pi4-with-2GB-swap.png
