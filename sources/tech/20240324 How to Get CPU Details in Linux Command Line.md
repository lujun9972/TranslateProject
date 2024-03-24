[#]: subject: "How to Get CPU Details in Linux Command Line"
[#]: via: "https://itsfoss.com/cpu-info-linux/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Get CPU Details in Linux Command Line
======

[![Warp Terminal][1]][2]

Being a Linux user, I can relate to your fascination with CPUs.

There are times when you want to know every detail of your computer. How many cores are there? Is it virtual or physical processor? Who is the manufacture? And much more.

So, how do you get CPU details in Linux?

Well, In this tutorial, I will walk you through how you can find three critical aspects of yor CPU:

  1. **Getting CPU details**
  2. **What's the current CPU usage per core**
  3. **Know the CPU temperature**



So let's start with the first one.

### Find CPU details in Linux

The easiest way to get the CPU details in Linux is to use the lscpu command. And the best part is it does not require any installation.

To know every detail of your CPU, simply execute the `lscpu` command as shown here:

```

    lscpu

```

![][3]

Let's break down the output one by one.

  * `Architecture`: This indicates the CPU architecture which is **x86_64** indicating my CPU is 64-bit.
  * `CPU op-mode(s)`: It shows what kind of processes your computer can handle. As I'm running a 64-bit processor, I can run 32-bit and 64-bit processes.
  * `Address sizes`: It specifies the memory capabilities of your system.
    * **39 bits physical:** CPU can directly address physical RAM up to 512 512 terabytes.
    * **48 bits virtual:** CPU can manage virtual memory up to 256 petabytes.
  * `Byte Order`: Shows the order in which the bytes are arranged. **Little Endian** means byte with the least significance comes first.
  * `CPU(s)`: Total number of cores including the logical and physical cores.
  * `On-line CPU(s) list`: It indicates all the cores from 0 to 11 are available and online.
  * `Vendor ID`: Shows the name of the CPU manufacturer.
  * `Model name`: As the name suggests, it shows the name of your CPU.
  * `CPU family`: Indicates the family group of the processor.
  * `Model`: Shows the internal model number of the processor.
  * `Thread(s) per core`: A number of threads that each core can handle. In my case, it is 2 so each physical core can utilize 2 threads at once.
  * `Core(s) per socket`: Shows the number of the physical core on your system.
  * `Socket`: Number of physical CPU sockets on your system.
  * `Stepping`: Number of revisions done to your CPU model.
  * `CPU max` and `CPU min`: It shows the highest and lowest clock speeds of your CPU.
  * `BogoMips`: **B** ogus **M** illions of **I** nstructions **P** er **S** econd is a retired and unreliable measurement of CPU speed. It is often seen in the older system.
  * `Virtualization`: Shows what technology your CPU is using for virtualization. If you're an Intel user, then you'll see `VT-x`.
  * `Caches (sum of all)`: This section shows the size and level of cache:
    * **L1d:** Data cache
    * **L1i:** instruction cache
    * **L2:** L2 cache
    * **L3:** L3 cache
  * `NUMA node(s)`: NUMA nodes are a group of CPU cores and memory modules that are physically close together and share a local memory controller.
  * `NUMA node0 CPU(s)`: it indicates that I have a single NUMA node named node0 and all cores reside within the same NUMA code.



What else do you need?

### Find the current CPU usage per core

You can always use the top command to check the CPU utilization. However the htop command is a little [better tool than top][4]. It shows CPU usage for each core and in a better, friendly interface.

But it does not come pre-installed on most Linux distributions.

So here, I will show you [how to install and use the htop][5] to monitor the current CPU usage.

**For Ubuntu users:**

```

    sudo apt install htop

```

**For Fedora users:**

```

    sudo dnf install htop

```

For Arch Linux:

```

    sudo pacman -S htop

```

Once you are done with the installation, you can start the htop using the following:

```

    htop

```

![][6]

As you can see, it shows how each core is utilized along with the memory consumption and total number of tasks running in your system.

### Find CPU temperature in Linux

To [find the CPU temperature][7], all you need is a utility called `lm-sensors` and here's how to install on various Linux distributions:

**For Ubuntu/Debian users:**

```

    sudo apt install lm-sensors

```

**For Fedora:**

```

    sudo dnf install lm_sensors

```

**For Arch:**

```

    sudo pacman -S lm_sensors

```

Once you are done with the installation, execute the following command and it will show the temperature of the CPU:

```

    sensors

```

![][8]

### Wrapping Up

In this tutorial, I went through how you can get CPU details using the lscpu command and have also mentioned how you can [check the CPU usage][9] and temperatures.

There are many more tools to [get system hardware details in Linux][10]. I used the most common ones here.

I hope you will find this quick tip helpful. Let me know if you have any questions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/cpu-info-linux/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/03/Get-CPU-details-using-the-lscpu-command.png
[4]: https://itsfoss.com/linux-system-monitoring-tools/
[5]: https://itsfoss.com/use-htop/
[6]: https://itsfoss.com/content/images/2024/03/use-htop-to-find-the-current-CPU-usage.gif
[7]: https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/
[8]: https://itsfoss.com/content/images/2024/03/Check-the-CPU-temprature-using-the-sensors-command-in-LInux.png
[9]: https://linuxhandbook.com/cpu-usage-check/
[10]: https://itsfoss.com/hardinfo/
