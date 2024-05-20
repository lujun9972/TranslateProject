[#]: subject: "Switchroot Lets You Run Ubuntu 24.04 LTS On Your Nintendo Switch!"
[#]: via: "https://news.itsfoss.com/ubuntu-24-04-nintendo/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Switchroot Lets You Run Ubuntu 24.04 LTS On Your Nintendo Switch!
======
Start using Ubuntu 24.04 LTS on platforms you didn't expect?
[![][1]][2]

We all know Linux can run on almost everything 😎

Hence, I am always impressed when I come across cases where I see Linux being ported over to platforms that don't support it natively. Take, for example, the [Asahi Linux][3] project, they have managed to bring a very usable Linux experience to Apple's Mac devices.

Similarly, one such project that has been making waves, [switchroot][4], an open-source project that focuses on getting Linux and Android running on the NVIDIA [Tegra X1][5]-powered Nintendo Switch.

They have quietly introduced a new Linux image that comes equipped with the [Ubuntu 24.04 LTS][6] release. Let's check it out!

### Ubuntu 24.04 LTS on Nintendo Switch: What to Expect?

![][7]

Introduced under their [L4T][8] (Linux for Tegra) image lineup, this Ubuntu Noble build can run on all Nintendo Switch versions, with varying degrees of workarounds that are a prerequisite for switchroot to function properly.

Currently, the developers have only provided **two variants** , one is **Kubuntu** , and the other is a **Unity desktop** variant. The GNOME Shell variant is in the works too, but a few issues have been holding it back.

If you were to compare it with the previous Ubuntu 18.04 build, the Ubuntu Noble build lacks hardware encode/decode in _GStreamer_ -based players, and only works on _FFmpeg_ ones. Moreover, there's **no CUDA compiler support** , but it features the CUDA runtime 10.0.

Of course, it is still a work in progress, but I am impressed to know what the switchroot team has pulled off so far. And I wonder how [Nintendo][9] might react.

You see, they are **known to be a vicious bunch** when it comes to [exercising][10] their IP rights. So far, switchroot doesn't seem to have come into their litigating gaze, and I hope it remains that way.

### Want to Check it Out?

For starters, you can refer to the [official wiki][11] to get your bearings. Then, you can head to the [official index][12] to download any of the two available variants and follow [the instructions][13] to get it installed on your Nintendo Switch.

[Ubuntu 24.04 LTS (switchroot)][12]

If you are interested in contributing to the switchroot project, then you can check out its [GitLab][14] repo.

Via: [Omg! Ubuntu][15]

**Suggested Read** 📖

![][16]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-24-04-nintendo/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://asahilinux.org/
[4]: https://switchroot.org/
[5]: https://developer.nvidia.com/content/tegra-x1
[6]: https://news.itsfoss.com/ubuntu-24-04-lts/
[7]: https://news.itsfoss.com/content/images/2024/05/switchroot.jpg
[8]: https://wiki.switchroot.org/wiki/linux/linux-distributions
[9]: https://www.nintendo.com/
[10]: https://www.polygon.com/24090351/nintendo-2-4-million-yuzu-switch-emulator-settlement-lawsuit
[11]: https://wiki.switchroot.org/wiki
[12]: https://download.switchroot.org/ubuntu-noble/
[13]: https://wiki.switchroot.org/wiki/linux/l4t-ubuntu-noble-installation-guide
[14]: https://gitlab.com/switchroot/
[15]: https://www.omgubuntu.co.uk/2024/05/ubuntu-24-04-nintendo-switch
[16]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
