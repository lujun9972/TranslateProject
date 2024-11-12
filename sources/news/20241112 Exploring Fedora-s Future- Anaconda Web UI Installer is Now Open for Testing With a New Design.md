[#]: subject: "Exploring Fedora’s Future: Anaconda Web UI Installer is Now Open for Testing With a New Design"
[#]: via: "https://news.itsfoss.com/fedora-anaconda-web-ui/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Exploring Fedora’s Future: Anaconda Web UI Installer is Now Open for Testing With a New Design
======
Fedora's new Anaconda Web UI installer looks way simpler, and focused.
That's a good thing.
[![][1]][2]

[Anaconda][3] is a popular system installer choice for Linux distributions like Fedora, Red Hat Enterprise Linux, Rocky Linux, AlmaLinux, CentOS, and many others. However, it has **started to show signs of being old** , with its initial version being released back in 1999.

To tackle that, Fedora introduced the web browser-based [Anaconda Web UI][4] last year, where they showed off **a modern installer** with a _Python_ , _DBus_ , _Cockpit_ , and _React/PatternFly_ backend to address many of the shortcomings with the current Anaconda implementation.

Months have passed since, and we now have a [closer look][5] at the final version of it, **all set to debut next year.**

And, it looks simpler than what we saw last year.

### Anaconda Web UI Is Ready for Prime Time!

With the **aim of creating a more streamlined installation experience** , the developers of Anaconda Web UI have ensured that it is a “ _guided_ ” experience with good defaults, letting people do what they want.

Following a “ _task-oriented design_ ” approach, they have managed to incorporate some neat features. There is a “ _Reclaim space_ ” feature where the installer can carve out free space on dual-boot systems for installing a Linux distro.

Similarly, there is a “ _Reinstall Fedora_ ” option, where Anaconda Web UI can be used for system recovery in case something goes wrong, keeping user data untouched.

Other **features of Anaconda Web UI** include:

  * Share disk space with other operating system ( _while this was supported for dual-boot, you get an explicit option for it_ ).
  * Ability to choose a particular partition for installation, which was created/configured before installation using Storage Editor tool ( _based on_ [_Cockpit_][6]) or any external tool like gparted.
  * Easy process to create custom partitions, even for users who are new to it.
  * Much easier for developers to maintain compared to traditional desktop installers.



Additionally, there are **** plans to work on things like **adding support for remote installations via browser** , **better small-screen support** for catering to mobile and virtual machine users, **having better settings for filesystem configuration** , and **integrating a terminal** for debugging.

### Initial Impressions

![][7]

I fired up the provided test ISO for Anaconda Web UI, which was powered by [Anaconda 42.13][8] and running on [Firefox 132.0.1][9]. At first glance, **the user interface felt familiar** , and I could manage the disk partitions, enable encryption, and review the installation before it began.

![][10]

During installation, handy progress spinners were shown on all the stages, like _Storage configuration_ , _Software installation_ , _System configuration_ , and _Finalization_.

In the final stage, Anaconda Web UI prompted me to reboot my system to use the Fedora 42 Workstation installation, with a feedback [call-to-action][11] at the bottom accompanied by a QR code.

Overall, **my experience with the near-final version of Anaconda Web UI was great**. I didn't feel lost throughout the process, and even though I didn't really test out its disk management features, it was a very satisfactory trial for me.

### Want To Try It Out?

![Take note of the pre-release warning.][12]

Currently, Anaconda Web UI is in the testing phase, with **a debut in the upcoming Fedora Linux 42 Workstation release** next year.

Meanwhile, you can test out the pre-release version by downloading the [Fedora Workstation Live ISO][13] ( _GNOME only_ ) for virtual machines. Just ensure that you **don't install the demo image on bare metal for production/general use** , as it is a testing image after all.

[Fedora Workstation Live ISO][13]

The developers have mentioned that **they are planning a staged rollout** , starting with the Workstation ISO (GNOME), then gradually moving towards other editions, and finally server installations.

You can go through the announcement blog linked above to learn more about Anaconda Web UI.

_💬 Do you like what you see? Could it have been better? Let me know!_

**Suggested Read** 📖

![][14]

* * *

[Get It's FOSS Plus Membership][15]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/fedora-anaconda-web-ui/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://github.com/rhinstaller/anaconda
[4]: https://news.itsfoss.com/fedora-new-web-ui-install-dev/
[5]: https://fedoramagazine.org/anaconda-installer-redesign/
[6]: https://cockpit-project.org/
[7]: https://news.itsfoss.com/content/images/2024/11/Anaconda_Web_UI_a.jpg
[8]: https://github.com/rhinstaller/anaconda/releases/tag/anaconda-42.13
[9]: https://www.mozilla.org/en-US/firefox/132.0.1/releasenotes/
[10]: https://news.itsfoss.com/content/images/2024/11/Anaconda_Web_UI_d.jpg
[11]: https://en.wikipedia.org/wiki/Call_to_action_(marketing)
[12]: https://news.itsfoss.com/content/images/2024/11/Anaconda_Web_UI_g.jpg
[13]: https://dl.fedoraproject.org/pub/fedora/linux/development/rawhide/Workstation/x86_64/iso/
[14]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[15]: https://itsfoss.com/#/portal/signup
