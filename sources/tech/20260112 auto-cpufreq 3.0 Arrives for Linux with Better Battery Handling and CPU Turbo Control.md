[#]: subject: "auto-cpufreq 3.0 Arrives for Linux with Better Battery Handling and CPU Turbo Control"
[#]: via: "https://itsfoss.com/news/auto-cpufreq-3-0/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

auto-cpufreq 3.0 Arrives for Linux with Better Battery Handling and CPU Turbo Control
======

[![Warp Terminal][1]][2]

Us Linux users have access to [a large selection of system monitoring tools][3] that help us know the state of our computers. In some cases, these even let us tweak certain parameters of the hardware to eke out better performance or battery life.

While these utilities may not yet match the polish and maturity of their Windows counterparts, they have made significant progress in recent years.

auto-cpufreq is one such tool that automatically optimizes CPU speed and power consumption on Linux systems to save battery life, and it just received [a feature-packed 3.0 release][4].

### auto-cpufreq 3.0: What's New?

![][5]

The release comes packed with **the ability to manually control CPU turbo boost** , where you can now manually override auto-cpufreq's automatic decisions and set turbo to `Auto`, `Never`, or `Always`. This works through both the command-line interface and the GUI app, though the option only shows up in the GUI if your CPU supports [turbo boost][6].

Battery handling has gotten better too. You can now tell auto-cpufreq which specific battery device to monitor if your laptop has multiple power supply devices listed or if the automatic detection picks the wrong one.

And, for [ASUS laptop][7] owners, **there's now support for battery charge thresholds** , so you can set a maximum charging percentage to help preserve your battery's health over time.

There were also **several important bug fixes** in this release. The tool now properly reads CPU frequency information and scaling limits, fixing an issue where the `--monitor` mode would show incorrect values.

If you're running [NixOS][8] or [Pop!_OS][9], you'll find some welcome improvements. NixOS users won't run into the "`awk: command not found`" error anymore, and Pop!_OS installations should go smoothly without PyGObject failures.

The [changelog][10] has the complete list of changes and the source code if you want to go deeper into this release.

### Get Started with auto-cpufreq

![][11]

The recommended way to install auto-cpufreq is by building it from source, and don't worry, it is quite straightforward! First, you have to clone the [GitHub][12] repository to your system, create a new directory for it, and launch the installer by running these commands together:

```

    git clone https://github.com/AdnanHodzic/auto-cpufreq.git
    cd auto-cpufreq && sudo ./auto-cpufreq-installer

```

When you do that, you will be asked to enter your account password. Do it and verify the list of packages shown to you.

![][13]

When prompted, press " _Y_ " to confirm the installation of these new packages, and wait for the installation to complete. Once everything is set, you can start using the CLI version of auto-cpufreq by using the following command:

```

    sudo auto-cpufreq

```

There's also **a GUI version** that needs some additional configuration once you launch it from the app launcher. It will show you the steps for that, which involves installing the daemon for auto-cpufreq.

**For users of Ubuntu** and its derivatives, this release of auto-cpufreq is also available on the [Snap Store][14] and via the following command:

```

    sudo snap install auto-cpufreq

```

If you need pointers on how to operate this CLI tool, then the lead developer of this project, Adnan Hodzic, has [an AI-powered chatbot][15] up on his website, which should work well for any questions you have.

[auto-cpufreq][12]

* * *

**Suggested Read 📖:** [_This System Monitor Offers Something More_][16]

![][17]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/auto-cpufreq-3-0/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/linux-system-monitoring-tools/
[4]: https://www.reddit.com/r/linux/comments/1qa715a/autocpufreq_v300_is_out/
[5]: https://itsfoss.com/content/images/2026/01/auto-cpufreq-3-0.png
[6]: https://www.intel.com/content/www/us/en/gaming/resources/turbo-boost.html
[7]: https://www.asus.com/us/store/laptops/
[8]: https://itsfoss.com/nixos-tutorials/
[9]: https://itsfoss.com/news/pop-os-24-04-review/
[10]: https://github.com/AdnanHodzic/auto-cpufreq/releases/tag/v3.0.0
[11]: https://itsfoss.com/content/images/2026/01/auto-cpufreq-3-0-installation-a.png
[12]: https://github.com/AdnanHodzic/auto-cpufreq
[13]: https://itsfoss.com/content/images/2026/01/auto-cpufreq-3-0-installation-b.png
[14]: https://snapcraft.io/auto-cpufreq
[15]: https://foolcontrol.org/?p=4903
[16]: https://itsfoss.com/jdsystemmonitor/
[17]: https://itsfoss.com/content/images/icon/android-chrome-512x512-206.png
