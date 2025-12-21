[#]: subject: "jdSystemMonitor: More Than Your Regular System Monitor on Linux"
[#]: via: "https://itsfoss.com/jdsystemmonitor/"
[#]: author: "Roland Taylor https://itsfoss.com/author/roland/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

jdSystemMonitor: More Than Your Regular System Monitor on Linux
======

[![Warp Terminal][1]][2]

[jdSystemMonitor][3] is an app for viewing your system's internals, expanding beyond the typical system monitor with handy features that let you dig deeper into your system than most others. Described as "desktop independent", it's a rare entry among a sea of fresh [system monitoring tools for Linux][4], that doesn't attempt to be flashy or fit in with any particular style.

It's in the camp of apps that just do what they do, giving you the information you need without going for any additional fluff. As a result, it falls somewhere in the niche between such apps and the likes of top and [htop][5]. In spirit, it resembles CPU-Z or [CPU-X][6], though with a focus on displaying software info rather than hardware.

### Quick introduction to jdSystemMonitor

![The Performance tab in jdSystemMonitor][7]

jdSystemMonitor is an open-source app developed by Jakob Dev, who's created a number of [other similar utilities available on Flathub][8]. Written in Python and using PyQt for the GUI, it is designed to relatively portable, and resembles the apps of earlier days when the Linux desktop was a little less "opinionated".

At the backend sits a daemon written in Go, meaning dependencies are more on the minimal side, though since it's distributed mainly as a [Flatpak][9], it's unlikely most users would need to wrangle with dependencies anyway.

By contrast, most recent arrivals, like Usage, Resources, and Mission Center are designed to integrate well with one platform and deliver a combination of aesthetic polish, at-a-glance data presentation, and tighter platform integration.

### Distinctive features

![Viewing user processes in jdSystemMonitor][10]

Setting itself apart from other system monitoring apps, jdSystemMonitor bundles in features you’d typically expect to find in separate tools. Yet it presents all of this through a minimalist interface.

It’s a clever blend of sleek, uncomplicated design and an “everything _plus_ the kitchen sink” philosophy: the expected feature set is covered outright, and then a handful of unexpected (but genuinely useful) extras are thrown in. I'll cover some of these distinctive features here.

#### Actionable system information

![The Systeminfo tab in][11]

When you launch the application for the first time, you’re not shown a list of running processes, but a system overview. It’s akin to running `uname -a` or opening your desktop environment’s system information panel: you get a readout of your kernel, distribution (along with distro-specific links), and the last boot time.

Info in this tab is pulled from os-release data

#### Viewing running services (systemd only)

![The Services tab lets you see all of what systemd controls at a glance][12]

Along with the usual display of running processes and standard system performance, jdSystemMonitor can show all the systemd services running on your system, whether they're running as a user-level or system-wide service. This tab only shows if systemd is in use on the system. Otherwise, if you're using another init system, then this tab won't be visible.

#### Viewing running Flatpaks

![The "Running flatpaks" tab separates Flatpaks from other processes][13]

jdSystemMonitor also lets you view and control your running Flatpaks separately from other processes. This is especially useful since Flatpaks show up as `bwrap` processes in most system monitors, and require you to check the full process path in order to know what you're actually running.

Another helpful fact is that jdSystemMonitor actually shows the executable name for each Flatpak, which can be harder to find or remember than with traditional packaging formats and even compared to Snap.

#### Viewing autostart entries

![The Autostart tab in jdSystemMonitor, showing all autostart entries across desktop environments][14]

Yet another unique feature in jdSystemMonitor is the ability to view all autostart entries across all your installed desktop environments. You can also launch jdSimpleAutoStart from this tab to edit these entries.

Typically, when you view or [edit your autostart entries][15] in any given desktop environment, only the entries that are relevant to that particular environment are shown. This makes sense of course for day-to-day usage, but if you run into an issue where a particular application or service is blocking startup in any desktop environment, it's quite handy to be able to remove that entry from the list.

#### Viewing installed packages

![The native packages tab in jdSystemMonitor lists all packages installed with your distro's packaging system][16]

This one may not seem as meaningful at first glance, but when you take into consideration the inclusion of a search box and version numbers displayed right up front, it's actually quite helpful to have in a system monitor.

What's not immediately obvious at first glance is that when you right-click on any installed package, you can also view its properties, including installed files, dependencies, and any dependant packages.

![The package info window in jdSystemMonitor][17]

This is a feature that you'd typically expect to find in legacy package managers, but it's helpful to have baked into a system monitor as well.

#### Viewing all users (including system users)

![jdSystemMonitor provides rich information for each user on the system][18]

On Linux systems, the concept of a "user" extends beyond just the individual human being using the computer, and can include virtual users for the sake of the Linux permissions system.

Most system monitors let you filter by user, but it's less common to be able to see what users are actually on your system, and where their requisite home directories are located. Beyond this info, jdSystemMonitor also lets you see which shell each user uses.

#### Viewing system configuration (sysctl values)

![Viewing the kernel's system control variables in jdSystemMonitor][19]

Finally, jdSystemMonitor lets you view your kernel's system control (sysctl) variables and their values in the "System Configuration" tab. This essential gives a graphical interface to the `sysctl -a` command. There's no way to change these values from here, but there is a menu for copying relevant info upon right click.

### Quirks

Overall, jdSystemMonitor is a solid piece of tech; there are just a few small quirks worth noting if you choose to use it.

#### Wide window and tab layout

The choice to present everything in a single horizontal tab list can lead to a fairly wide default window. If you shrink it, you may find yourself doing a bit of sideways tab scrolling to get to specific views. It’s not a show-stopper, but it’s something to keep in mind if you prefer working in tighter layouts.

#### No dark mode integration (yet)

jdSystemMonitor doesn’t currently follow GNOME’s dark/light preference. On a dark-themed desktop, this can make it feel a little visually separate from the rest of your apps. The project does position itself as desktop-independent, which helps explain this, but honouring the user’s light/dark choice is increasingly seen as part of accessibility as well as usability. For users who rely on dark themes for comfort, this may be more than just a cosmetic detail.

#### Package info window cannot be resized

This isn’t a show-stopper either, but it is a notable quirk, especially on single-monitor setups. If you choose to use this feature, you’ll need to drag the window around to view all the tabs in this dialog.

### Wrapping up

If you're looking for a tool that brings system resources and internal details together in one place, jdSystemMonitor is a solid and lightweight option. It's not a replacement for platform-integrated tools, but it doesn’t try to be one.

Instead, it offers a comprehensive yet practical overview of your system, along with a few helpful extras you don’t often find elsewhere. It's a great fit for power users and sysadmins who know what they're looking for, or curious users who just want to peek at some of the inner workings of their operating system.

--------------------------------------------------------------------------------

via: https://itsfoss.com/jdsystemmonitor/

作者：[Roland Taylor][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/roland/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://jakobdev.codeberg.page/work/app/jdSystemMonitor/
[4]: https://itsfoss.com/linux-system-monitoring-tools/
[5]: https://itsfoss.com/use-htop/
[6]: https://itsfoss.com/cpu-x-alternative-cpu-z-linux/
[7]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-18-15-33-07.png
[8]: https://flathub.org/en/apps/collection/developer/JakobDev/1
[9]: https://itsfoss.com/what-is-flatpak/
[10]: https://itsfoss.com/content/images/2025/11/image-8.png
[11]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-18-03-19-11.png
[12]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-18-17-51-57.png
[13]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-18-17-52-29.png
[14]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-19-01-06-41.png
[15]: https://itsfoss.com/manage-startup-applications-ubuntu/
[16]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-19-01-26-43.png
[17]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-19-01-32-09.png
[18]: https://itsfoss.com/content/images/2025/11/Screenshot-From-2025-11-19-03-24-23.png
[19]: https://itsfoss.com/content/images/2025/11/image-7.png
