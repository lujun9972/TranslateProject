[#]: subject: "New Updates Make Mission Center the Best Task Manager for Linux Desktop"
[#]: via: "https://news.itsfoss.com/mission-center-services-update/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

New Updates Make Mission Center the Best Task Manager for Linux Desktop
======
Mission Center adds a new tab, making it more useful with additional
information.
[![][1]][2]

[Mission Center][3] is an increasingly popular open-source system monitor for Linux, written in the Rust programming language, and follows the GTK4 + Libadwaita approach to provide users with a well-organized interface.

It's been some time since I last checked it out, but, as it turns out, there's a new release that features plenty of useful improvements, making it one of the best task managers ( _system monitor_ ) for Linux.

Let's check it out! 😃

### Mission Center 0.5.0: What to Expect?

![][4]

The CPU tab can now **properly show the CPU frequency governor data, alongside the CPUFreq driver data** for supported processors. In my case, it worked very well, as you can see on the right-hand side of the app.

I was also surprised to see that it showed which power mode I was using, that's really great!

Then there's the **new “ _Services_ ” tab**, which the developers have finally implemented, which allows you to see the currently running services, with controls to start, stop or restart them.

![][5]

You can also check the details of any listed service by clicking on the “Details” button at the top, or by right-clicking on one. The window has controls to start/stop/restart the service, with details like its name, description, status, log output, and more.

![][6]

The developers have also shipped a few small tweaks to make the app more consistent, with better accessibility thanks to the updated translations.

Introduced with a previous _0.4.5_ release, there is also **support for hot plugging disks and network devices** , eliminating the need to restart Mission Center to get these devices to show up.

You can also **customize the chart data point** to show resource utilization over a specific time range. Options range from 10 seconds to 600 seconds, and you have to keep in mind that it is a separate option apart from the update interval setting.

There's also a **new “ _Smooth Graphs_ ” feature** that eliminates the sharpness/jaggedness of a graph, and replaces that behavior with a more rounded/curvy look

![][7]

The feature-rich release was followed by a bug fix update _0.5.1_ , which addresses a crashing issue when using an unsupported service manager, and the services page will also be hidden when using one.

### Get Mission Center

You can get the latest Mission Center release from the [Flathub][8] store, and if you are looking for alternative packages such as AppImage, head to its [GitLab][9] repo, where you will also find the source code.

_Our_ [_AppImage guide_][10] _and_ [_Flatpak guide_][11] _can be useful if you are a new Linux user._

[Mission Center (Flathub)][8]

Mission center has been progressing very well. Sure, there are some [issues][12] (some inconsistent reporting) that need to be ironed out, it is a suitable option when compared to other [system monitor apps][13].

![][14]

I think the developers are trying their best to stay on top of things, constantly taking in feedback and working on them. If you would like to learn more about this app, then you should give its [official website][15] a visit.

Via: [OMG! Ubuntu][16]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/mission-center-services-update/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/mission-center/
[4]: https://news.itsfoss.com/content/images/2024/06/Mission_Center_0.5.1_a.png
[5]: https://news.itsfoss.com/content/images/2024/06/Mission_Center_0.5.1_b.png
[6]: https://news.itsfoss.com/content/images/2024/06/Mission_Center_0.5.1_c.png
[7]: https://news.itsfoss.com/content/images/2024/06/Mission_Center_0.5.1_d.png
[8]: https://flathub.org/apps/io.missioncenter.MissionCenter
[9]: https://gitlab.com/mission-center-devs/mission-center/-/releases
[10]: https://itsfoss.com/use-appimage-linux/
[11]: https://itsfoss.com/flatpak-guide/
[12]: https://gitlab.com/mission-center-devs/mission-center/-/issues/
[13]: https://itsfoss.com/linux-system-monitoring-tools/
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://missioncenter.io/
[16]: https://www.omgubuntu.co.uk/2024/06/mission-center-system-monitor-new-features
