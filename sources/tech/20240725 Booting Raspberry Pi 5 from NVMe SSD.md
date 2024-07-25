[#]: subject: "Booting Raspberry Pi 5 from NVMe SSD"
[#]: via: "https://itsfoss.com/raspberry-pi-ssd-boot/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Booting Raspberry Pi 5 from NVMe SSD
======

[![Warp Terminal][1]][2]

Looking to give your Raspberry Pi an SSD boost? The good news is that it is a lot easier to boot from NVMe SSD with Raspberry Pi 5.

Raspberry Pi OS has built-in tool that allow you to easily copy existing OS from the SD card on the SSD.

This way, you switch the existing operating system on to the SSD without changing anything. You have the same applications, same configuration, same everything.

In this tutorial, I'll share the steps I used to switch from SD card and boot from a NVMe SSD on my Raspberry Pi 5.

📋

Screenshots in this tutorial are a bit poor as I recorded the entire procedure and then took screenshots from the video recording. Perhaps when I repeat this process again, I can take better quality screenshots. For now, please ignore this minor inconvenience.

### What do you need?

Here are the accessories that you are going to need to follow this tutorial with your Raspberry Pi 5.

  * The [tutorial uses Raspberry Pi as a desktop][3], so you'll need the usual accessories like keyboard, mouse, monitor etc.
  * You should have Raspberry Pi OS installed on a micro SD card.
  * Raspberry Pi 5 doesn't have a built-in NVMe SSD slot. You need an external plugin or device that gives you access to NVMe. I am [using the Pironman 5 case][4] which comes with NVMe slot among many other stuff. You can use this or a HAT with NVMe support.



![][5]

##### Pironman 5 Case With Tower Cooler and Fan

This dope Raspberry Pi 5 case has a tower cooler and dual RGB fans to keep the device cool. It also extends your Pi 5 with M.2 SSD slot and 2 standard HDMI ports.

[Explore Pironman 5][6]

The [official Raspberry Pi M.2 HAT][7] will be the cheaper option here.

![][8]

🚧

Not all the NVMe SSDs will be compatible with M.2 HAT or case you are using. Please explore what brand and make of SSD is supported by the HAT/case before buying them.

### Step 1: Format your SSD

First thing, plug in your SSD to the NVMe HAT and power on the Raspberry Pi.

Please ensure that Raspberry Pi can see the plugged-in SSD. Check it with the following command:

```

    lsblk -f

```

![][9]

As you can see, although my SSD is recognized, there are no details about it. That's because I have a brand new SSD and it didn't have any partitions on it.

If you are in the same situation, install Gparted first:

```

    sudo apt install gparted

```

And then use it to create a new partition on the SSD.

Run Gparted. **Make sure you have chosen the correct disk from the top right corner**.

![][10]

You can go with MSDOS when you see a screen like this:

![][11]

Next, click on the + sign on the top left to create a new partition and create a single partition of the entire disk size. You can choose Ext4 filesystem although it should not matter as your SSD will be formatted again during SD card copying. Click Apply and then press on the ✔️ to confirm the changes.

![][12]

You can verify the partitions by running the `lsblk -f` command again.

### Step 2: Copy the SD Card to SSD

Raspberry Pi has a built-in tool for copying the content of the SD card to the USB/SSD.

This makes things much more convenient as it will just duplicate the SD Card onto the SSD. This means that your current configurations, applications, everything will remain the same even when you are booting from the SSD. Now that's super, isn't it?

Open up the menu and go to Accessories->SD Card Copier.

![][13]

✋

I found the SD Card Copy tool buggy. It was not showing the option to start the copying for almost a minute.

In the Copy From Device, choose SD Card and in the Copy To Device, choose the SSD.

![][14]

Click start and wait for the process to finish. It will take some to finish copying the data on the SSD.

Once the data is copied on the SSD, move on to the last stage of this process and that is to change the boot order.

### Step 3: Change the boot order

In the terminal, run the following command:

```

    sudo raspi-config

```

You'll see a terminal user interface like the image below and you have to use the arrow keys to select Advanced Options here and press the enter key.

![][15]

In the next screen, select Boot Order.

![][16]

You'll see a few options here. Choose the middle one that says 'NVMe/USB Boot' and press enter key.

![][17]

You'll see some output in the terminal and then the following screen notifying you that your boot order has been changed.

![][18]

When you press enter key on the last step, it will ask you to reboot your system. You can do that or continue your work.

### Step 4: Booting from the NVMe SSD

If you reboot in your Pi 5, you'll be booting from the SSD and your SD Card will be mounted as an external disk with two partitions on it.

Still, if you want to ensure that it is actually booting from the SSD and not from the SD card, power off the Pi and take out the Micro SD Card. Turn on the Pi again and see if it boots as before.

### Conclusion

Does SSD provide a performance benefit over SD Card? I don't know. I didn't do any benchmarking. I didn't notice faster boot time. Perhaps if there are any programs that do a lot of read and write on the disk could benefit from the SSD.

I think there is another way to boot the Pi from SSD. If the SSD can be connected to the regular computer (there are UBS-based connectors) and then burn the Raspberry Pi OS image directly on the SSD. Not sure if the boot order needs to be changed or not. I'll try this method some other day and share my experience.

For now, enjoy the fact that you can easily switch to SSD from SD Card on your Raspberry Pi 5 device.

Please let me know if you have questions or suggestions on this topic.

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-ssd-boot/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/raspberry-pi-5-review/
[4]: https://itsfoss.com/pironman-5-review/
[5]: https://itsfoss.com/content/images/2024/06/pironman-5.webp
[6]: https://www.sunfounder.com/products/pironman-5-nvme-m-2-ssd-pcie-mini-pc-case-for-raspberry-pi-5?ref=itsfoss
[7]: https://www.seeedstudio.com/Raspberry-Pi-M-2-HAT-for-Raspberry-Pi-5-p-5881.html?sensecap_affiliate=YtQVXkS&referring_service=link
[8]: https://media-cdn.seeedstudio.com/media/favicon/stores/4/seeedstudio.png
[9]: https://itsfoss.com/content/images/2024/07/mount-ssd-raspberry-pi.jpg
[10]: https://itsfoss.com/content/images/2024/07/format-ssd-raspberry-pi-5.jpg
[11]: https://itsfoss.com/content/images/2024/07/formatting-ssd-raspberry-pi-msdos.jpg
[12]: https://itsfoss.com/content/images/2024/07/create-new-partitions-raspberry-pi.jpg
[13]: https://itsfoss.com/content/images/2024/07/sd-card-copier-raspberry-pi.webp
[14]: https://itsfoss.com/content/images/2024/07/copy-sd-card-to-ssd-raspberry-pi.png
[15]: https://itsfoss.com/content/images/2024/07/change-boot-order-raspberry-pi-1.webp
[16]: https://itsfoss.com/content/images/2024/07/change-boot-order-raspberry-pi-2.webp
[17]: https://itsfoss.com/content/images/2024/07/change-boot-order-raspberry-pi-3.webp
[18]: https://itsfoss.com/content/images/2024/07/change-boot-order-raspberry-pi-4.webp
