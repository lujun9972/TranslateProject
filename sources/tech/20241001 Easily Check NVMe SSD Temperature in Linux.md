[#]: subject: "Easily Check NVMe SSD Temperature in Linux"
[#]: via: "https://itsfoss.com/ssd-temperature-linux/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Easily Check NVMe SSD Temperature in Linux
======

[![Warp Terminal][1]][2]

Recently, NVMe, short for Non-Volatile Memory Express drives, has become the go-to storage option for modern desktops. Unlike traditional hard drives, NVMe drives are significantly faster, allowing for quicker boot times, faster file transfers, and smoother overall performance.

Like all other functional devices, NVMe devices also heat upon usage. If they heat too much, it will degrade the performance of your system.

Let me show how you can monitor the temperature of SSDs in Linux-based operating systems.

### nvme-cli: The go-to tool to check NVMe stats

The [nvme-cli][3] is a simple tool that lets you control and manage your NVMe SSD drive right-from the terminal. It gives you more control over its performance and behavior.

With this nifty tool, you can optimize your drive for better performance, troubleshoot issues, and do much more.

In this quick tutorial, I will use this tool to measure the temperature of NVMe SSDs.

#### Install nvme-cli

If you are using Ubuntu or any other Debian-based Linux distribution, nvme-cli is available in the official repositories. To install, just run:

```

    sudo apt install nvme-cli

```

The nvme-cli tool is available in the official repositories of all major Linux distributions. You can use the respective package managers to install the package.

#### Listing the NVMe drives in the system

In order to check the temperature, you need the NVMe device name. This is not the manufacturing name, instead the NVMe block device location on Linux.

To find the drives in the system, use the **`nvme`** command.

```

    nvme list | cut -d' ' -f1

```

This will list all the NVMe device names.

![List NVMe Drives][4]

As you can see, we got the name of the NVMe device. Also, you can use [the **lsblk** command][5] to list all the drives attached and then find the name of NVMe from there.

```

    lsblk | grep "nvme"

```

![Listing Drives using lsblk command.][6]

🚧

You should note that `nvme0` should be used as `/dev/nvme0`. If the /dev is omitted, nvme-cli won't show output, and results in a syntax error.

#### Checking the temperature of SSDs

Now you know the name of the drive you want to check, let's check the temperature.

The syntax used to check the temperature is:

```

    sudo nvme smart-log <device-name> | grep -i '^temperature'

```

Here, replace the **< device-name>** with the name you have found in the earlier step. For me, it will be:

```

    sudo nvme smart-log /dev/nvme0 | grep -i '^temperature'

```

📋

The nvme0 is the top-level device file. The `nvme0n1`, `nvme0n2`, etc. are name spaces. Since temperature is a physical property of the drive, to check the temperature of a drive, you can use the top-level device file.

![NVMe temperature monitor \(Click to enlarge the image\)][7]

### Other tools to check SSD temperature

While `nvme-cli` is the comprehensive tool to check the temperature, a few alternative solutions offer a more convenient GUI. Let's see them.

#### Vitals, the GNOME extension

If you are a GNOME user, Vitals is a must extension. It is not limited to temperature, instead it offers a whole lot of other system monitors.

On the panel, click on the temperature option to expand the temperature monitors. From there, you can monitor the NVMe temperature in real time.

![NVMe Temperature in Vitals][8]

[Vitals][9]

#### Hardinfo2

[Hardinfo2][10] is a [system information and benchmark tool][11]. You can use this to know the temperature of your devices.

You can go to the sensors page under the Devices section for the purpose.

![NVMe temperature - hardinfo2][12]

[hardinfo2][13]

### Conclusion

The nvmi-cli tool is an awesome tool for your NVMe SSDs on Linux. I prefer it for its simplicity. Not everyone would be comfortable with a CLI tool and hence I added a couple of GUI options.

On a similar note, you may want to [know a thing or two about checking CPU temperature on your Linux system][14].

![][15]

And something [about checking NPU usage][16], too.

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/ssd-temperature-linux/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/linux-nvme/nvme-cli
[4]: https://itsfoss.com/content/images/2024/09/list-all-nvme-drives-using-nvme-command.png
[5]: https://linuxhandbook.com/lsblk-command/
[6]: https://itsfoss.com/content/images/2024/09/listing-drives-using-lsblk.png
[7]: https://itsfoss.com/content/images/2024/09/recorded-temperature-nvme-smart-log.png
[8]: https://itsfoss.com/content/images/2024/09/nvme-temperature-vitals.png
[9]: https://extensions.gnome.org/extension/1460/vitals/
[10]: https://github.com/hardinfo2/hardinfo2
[11]: https://itsfoss.com/hardinfo/
[12]: https://itsfoss.com/content/images/2024/09/nvme-temp-hardinfo.png
[13]: https://hardinfo2.org/
[14]: https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/
[15]: https://itsfoss.com/content/images/icon/android-chrome-192x192.png
[16]: https://itsfoss.com/monitor-npu-linux/
