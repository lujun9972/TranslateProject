[#]: subject: "Switching Between Intel and Nvidia Graphics Cards on Ubuntu"
[#]: via: "https://itsfoss.com/intel-nvidia-graphics-switch-ubuntu/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Switching Between Intel and Nvidia Graphics Cards on Ubuntu
======

[![Warp Terminal][1]][2]

My [TUXEDO InfinityBook Pro][3] has two graphics cards on it. Integrated Intel and dedicated Nvidia GeForce.

It is more common these days to have a hybrid setup of two graphics cards on laptops.

The integrated Intel graphics act as the primary driver and handle most of the less intensive tasks without consuming much power, thus prolonging the battery duration.

For gaming, 3D rendering and other such graphics heavy work, the dedicated Nvidia GPU should be used.

**In this tutorial, I will also show you how to switch between the two graphics cards on Ubuntu and possibly other Linux distributions.**

There are two ways to do that. You can explicitly run an application with Nvidia instead of Intel or you can change the settings to always use Nvidia graphics. This is a lot easier if you are using Nvidia proprietary drivers instead of the open source

### Check which graphics cards you have

✋

This tutorial is specifically for Intel and Nvidia graphics card (also known as video cards) setup. It is likely not to work with AMD.

For this reason, you must ensure you are using [Nvidia graphics card][4].

To [check your graphics card in Linux][5], use this command:

```

    lspci | grep VGA

```

Here's what it shows for my system:

```

    lspci | grep VGA
    00:02.0 VGA compatible controller: Intel Corporation Alder Lake-P GT2 [Iris Xe Graphics] (rev 0c)
    01:00.0 VGA compatible controller: NVIDIA Corporation GA104 [Geforce RTX 3070 Ti Laptop GPU] (rev a1)

```

As you can see in the output above, my laptop has Intel Iris Xe Graphics and Nvidia Geforce RTX 3070 Ti.

With that aside, let's see about using Nvidia instead of integrated Intel video drivers.

### Method 1: Running certain applications with Nvidia

Actually, Ubuntu provides a way to launch an application with the dedicated Nvidia graphics card.

In the launcher, you will notice a 'Launch using Discrete Graphics Card' option when you right click on an icon. This "[discrete graphics card][6]" is your dedicated graphics card, Nvidia in this case.

![][7]

You can see this option for applications in GNOME Activities area as well.

Note that not every application started with this option will actually use Nvidia graphics card. I tested it and found that while Firefox started with the dedicated graphics driver, many other applications such as Video player, Inkscape etc did not.

📋

How did I know if an application was using Nvidia or not? I used the `nvidia-smi` command line tool that comes with proprietary Nvidia drivers. I'll discuss it in the next section of this tutorial.

To run an application with Nvidia drivers from the terminal, you can use:

```

    DRI_PRIME=1 application_name

```

So, if you have to run Firefox with Nvidia, you can use:

```

    DRI_PRIME=1 firefox

```

This `DRI_PRIME` environment variable seems to work only with the open source Nouveau drivers of NVIDIA. If you are using the proprietary driver, you should use:

```

    __GLX_VENDOR_LIBRARY_NAME=nvidia __NV_PRIME_RENDER_OFFLOAD=1 application_name

```

💡

Using the proprietary NVIDIA drivers makes things a lot easier in switching the graphics drivers and even monitoring the GPU usage per process basis. The next section covers it.

### Method 2: Use Nvidia proprietary drivers and tools that come with it

Look for the 'Additional Drivers' tool in the GNOME Activities area:

![][8]

You can also find it under the Additional Drivers tool in the Software & Updates tool.

In here, ensure that you are using the proprietary Nvidia drivers. Go for the highest version unless you have an older graphics card which is supported with the legacy driver (470 in the picture below).

![][9]

**You'll have to restart your system** if you change the graphics drivers.

In a few cases, you'll be prompted to sign MOK. Just use a password and when you reboot your system and see the blue MOK screen, sign it with the password you used earlier.

Anyways, when you are back in your system, look for the tool called NVIDIA X Server:

![][10]

In here, go to PRIME Profiles from the left sidebar and then you'll see the options to change between the graphics drivers.

![][11]

Performance mode means Nvidia will be the primary graphics driver running for all the applications.

On-Demand is the default behavior where Intel integrated driver is used all the time and Nvidia is used when specified (as we saw in method 1).

💡

When you change the graphics profile, you'll have to log out of the system and log back in to see the effect.

You can also make Nvidia the primary driver from the command line:

```

    sudo prime-select nvidia

    abhishek@itsfoss-tuxedo:~$ sudo prime-select nvidia
    [sudo] password for abhishek:
    Info: selecting the nvidia profile
    Deleting /lib/modprobe.d/nvidia-runtimepm.conf
    Updating the initramfs. Please wait for the operation to complete:
    Done

```

Or, if you want to run an application with Nvidia proprietary drivers from the command line, use:

```

    __GLX_VENDOR_LIBRARY_NAME=nvidia __NV_PRIME_RENDER_OFFLOAD=1 application_name

```

### 💡Bonus tip: Check graphics use per process

With the Nvidia proprietary drivers, you also get another handy CLI tool; `nvidia-smi`.

Just run it like this:

```

    nvidia-smi

```

And it will show the GPU usage statistics at a glance:

![][12]

If you want to keep an eye on the GPU usage continuously like top command, you can combine it with the watch command like this:

```

    watch -n1 nvidia-smi

```

And it will refresh the stats every second. use ctrl+c to stop the running program.

### Conclusion

I was surprised to find the lack of CPU usage utility for the open source Nvidia Nouveau driver. There should be one, in my opinion.

The proprietary driver provides handy tools for switching between the graphics drivers and monitoring the GPU usage.

Which driver performs better depends entirely on you. I let you experiment and conclude on that.

🗨️ Still facing issues with the steps mentioned here? Let me know in the comments and I'll try to help you out.

--------------------------------------------------------------------------------

via: https://itsfoss.com/intel-nvidia-graphics-switch-ubuntu/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://news.itsfoss.com/tuxedo-infinitybook-pro-16-review/
[4]: https://developer.nvidia.com/
[5]: https://itsfoss.com/check-graphics-card-linux/
[6]: https://www.intel.com/content/www/us/en/support/articles/000057824/graphics.html
[7]: https://itsfoss.com/content/images/2024/05/launch-using-discrete-graphics-card.webp
[8]: https://itsfoss.com/content/images/2024/05/ubuntu-additional-drivers-tool.png
[9]: https://itsfoss.com/content/images/2024/05/using-nvidia-properitary-driver-ubuntu.webp
[10]: https://itsfoss.com/content/images/2024/05/nvidia-x-server.png
[11]: https://itsfoss.com/content/images/2024/05/make-nvidia-default-graphics-ubuntu.png
[12]: https://itsfoss.com/content/images/2024/05/nvidia-smi.png
