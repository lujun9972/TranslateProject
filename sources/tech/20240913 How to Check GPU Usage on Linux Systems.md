[#]: subject: "How to Check GPU Usage on Linux Systems"
[#]: via: "https://itsfoss.com/gpu-usage-linux/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Check GPU Usage on Linux Systems
======

[![Warp Terminal][1]][2]

When you have a GPU on board, integrated or dedicated, there are some programs that help you get the necessary stats to check its temperature, free memory, and more. You can use them on Ubuntu and other Linux distributions as well.

Unfortunately, default [system monitoring tools][3] and command-line utilities like htop or top do not display GPU usage data.

So, you need to use a couple of specific programs or terminal tools that would let you access the usage data for your graphics card or integrated GPU.

Here, I highlight the same after testing it on Ubuntu and Arch Linux.

### The Recommended GUI Tool: Mission Center

![][4]

If you do not mind installing a GUI program for the job, Mission Center should be your preferred tool.

It supports NVIDIA, AMD, and Intel GPUs. So, you do not have to think twice regarding the support for your hardware. However, with Intel GPUs, you may not get all the essential details compared to AMD and NVIDIA powered GPUs.

You can install it as a Flatpak from [Flathub][5] or download the AppImage from its [GitLab releases section][6]. It is also available in certain repositories like AUR for Arch Linux. Head to its [GitLab page][7] for more information.

The command for Flatpak installation is (any Linux distribution):

```

    flatpak install flathub io.missioncenter.MissionCenter

```

For Arch Linux users, you can type in:

```

    sudo pacman -S mission-center

```

Furthermore, refer to our [AppImage guide][8] if you are not familiar with the type of package.

**Suggested Read 📖**

![][9]

### Command-line tools to check GPU stats

If you do not like GUI programs, don't worry, I got you. You have different ways you can monitor GPU usage stats, depending on [which GPU your Linux system has][10].

#### nvidia-smi

**For NVIDIA** , you can simply type:

```

    nvidia-smi -l 2

```

You do not need to install this. If you have your NVIDIA drivers installed (which should be the case by default on Ubuntu), you should be able to use this. We have NVIDIA driver installation guides for [Linux Mint][11] and [Fedora][12] that you can follow as well.

![][13]

In the command, 2 → denotes the second interval in which the terminal will be refreshed. You can change this or opt to get updates in milliseconds by following the instructions on its man page.

#### nvtop

**If you have a different GPU or want something else** , try **nvtop** , which is used under-the-hood by Mission Center GUI.

Just type in the following to get it installed and then launch it:

```

    sudo apt install nvtop
    nvtop

```

![][14]

It supports both AMD and NVIDIA GPUs ( **with proprietary drivers only** ). You can also find it in for Arch and other distributions in the respective repositories.

#### gpustat

There's another tool: [gpustat][15], a Python package that also gives you quick details regarding your GPU usage. You need [pip installed on your Ubuntu][16] or Linux system to get this installed.

✋

It only works for NVIDIA proprietary drivers.

Once done, just type in the following:

```

    pip install gpustat

```

If this fails for some reason, you can install `python-pipx` package, as an alternative, which I did on Arch Linux. Pipx manages a virtual environment for you to easily run the Python package. So, that is the only difference. The command would look like:

```

    pipx install gpustat

```

Once done, launch it using the command:

```

    gpustat

```

![][17]

### Wrapping Up

Whether you have an NVIDIA, AMD, or Intel GPU, monitoring your resources is helpful, especially, if you are system is not performing as intended. You also need to check if your GPU is being properly utilized for the programs you want it to offload tasks to instead of the CPU.

The terminal tool **nvtop** should be the best one in my option for stats on processing using the GPU, and the rest of the details. However, your preference can differ with just the default nvidia-smi or Mission Center GUI.

On a related note, you might want to [keep a tab on the GPU temperature in Linux][18].

![][9]

_💭 What do you think is the best way to check GPU usage on Linux? Let me know in the comments!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/gpu-usage-linux/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/linux-system-monitoring-tools/
[4]: https://itsfoss.com/content/images/2024/08/mission-center-gpu-usage.png
[5]: https://flathub.org/apps/io.missioncenter.MissionCenter
[6]: https://gitlab.com/mission-center-devs/mission-center/-/releases
[7]: https://gitlab.com/mission-center-devs/mission-center
[8]: https://itsfoss.com/use-appimage-linux/
[9]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[10]: https://itsfoss.com/check-graphics-card-linux/
[11]: https://itsfoss.com/nvidia-linux-mint/
[12]: https://itsfoss.com/install-nvidia-drivers-fedora/
[13]: https://itsfoss.com/content/images/2024/08/nvidia-smi.png
[14]: https://itsfoss.com/content/images/2024/08/nvtop.png
[15]: https://github.com/wookayin/gpustat
[16]: https://itsfoss.com/install-pip-ubuntu/
[17]: https://itsfoss.com/content/images/2024/08/gpustat.png
[18]: https://itsfoss.com/monitor-cpu-gpu-temp-linux/
