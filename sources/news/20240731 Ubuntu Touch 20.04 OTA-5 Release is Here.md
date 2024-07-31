[#]: subject: "Ubuntu Touch 20.04 OTA-5 Release is Here!"
[#]: via: "https://news.itsfoss.com/ubuntu-touch-ota-5-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ubuntu Touch 20.04 OTA-5 Release is Here!
======
If you are one of the few using it, you might want to update!
[![][1]][2]

We are at a point of time when there are many robust mobile-focused Linux distributions that offer various features. Off the top of my head, there are some good ones like [Mobian][3], [postmarketOS][4], [Sailfish OS][5], and [Ubuntu Touch][6].

The latter of which was initially the making of [Canonical][7], but was discontinued back in April 2017. Luckily, for the project, [UBports][8] stepped in and took over it, committing to developing and maintaining it.

You can learn more about its history in our [earlier coverage][9].

Moving on to the topic at hand, the developers of Ubuntu Touch have introduced a new release that features many new improvements with the **Ubuntu Touch 20.04 OTA-5** release.

Let's take a look at it. 😃

## 🆕 Ubuntu Touch 20.04 OTA-5: What's New?

![][10]

Introduced as a maintenance release for the 20.04 series, **the developers have focused on improving the overall reliability and stability of the operating system** with many key changes.

Starting with the power profile system, it can now differentiate between sustained and interactive modes on supported devices. Then there's the calendar, which will now notify users if synchronization fails due to authentication issues.

🚧

Unfortunately, the article lacks an official screenshot of the release because the developers haven't provided any of their portals.

For users of Ubuntu Touch 16.04, they can now upgrade to the 20.04 series without any issues, with plenty of miscellaneous bug fixes and security updates waiting for them, should they choose to upgrade.

The devs also mentioned **two known issues** that affect this release, the first is the disabling of double-tap-to-wake on some devices _(e.g., Pixel 3a_ ) to avoid stability issues; they might re-enable this in the future if a fix is found.

The other is for the users of Waydroid Helper app, for which, the “ _Waydroid Stop_ ” app entry in the app launcher is broken due to an upstream change. If this impacts you, then you can keep an eye on this [issue][11].

If you are keen on learning more, go through the [release blog][12].

## 📥 Get Ubuntu Touch 20.04 OTA-5

Before you go about installing it on your smartphone, refer to the supported [devices list][13]. Then, you can head to the [official website][14] to get started.

If you require any further help, then the [documentation][15] is a must-read.

[Ubuntu Touch 20.04 OTA-5][14]

If you want to keep an eye on development, then you can head to UBports' [GitLab][16] repo.

**For existing users** , they can upgrade by heading into the “ _Updates_ ” menu in the _System Settings_ app. Do note that **not all users will receive the upgrade** with this method, as the developers are rolling it out slowly, to handle any issues that might pop up.

If you want the update now, connect your device to a computer, open the terminal, turn on [ADB access][17], and run the following command over ADB shell:

```

    sudo system-image-cli -v -p 0 --progress dots

```

_💬 Have you tried Ubuntu Touch before? Liked it, disliked it? Let me know below!_

**Suggested Read** 📖

![][18]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-touch-ota-5-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://mobian-project.org/
[4]: https://postmarketos.org/
[5]: https://sailfishos.org/
[6]: https://ubuntu-touch.io/
[7]: https://canonical.com/
[8]: https://ubports.com/en/
[9]: https://itsfoss.com/ubuntu-touch/
[10]: https://news.itsfoss.com/content/images/2024/07/Ubuntu_Touch_Poster.png
[11]: https://github.com/Aarontheissueguy/WaydroidHelper/issues/59
[12]: https://ubports.com/en/blog/ubports-news-1/post/ubuntu-touch-ota-5-focal-release-3933
[13]: https://devices.ubuntu-touch.io/
[14]: https://ubuntu-touch.io/get-ubuntu-touch
[15]: https://docs.ubports.com/en/latest/
[16]: https://gitlab.com/ubports
[17]: https://docs.ubports.com/en/latest/userguide/advanceduse/adb.html
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
