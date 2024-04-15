[#]: subject: "My Experience With Ubuntu 24.04 Beta So Far..."
[#]: via: "https://news.itsfoss.com/ubuntu-24-04-beta-experience/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

My Experience With Ubuntu 24.04 Beta So Far...
======
Taking Ubuntu 24.04 LTS for a spin.
With any beta software, you should expect some hiccups. Hence, it is not recommended for all users to try beta versions of a distro or an app. You should only download/upgrade when a stable release is available for the best user experience.

However, what happens if a tinkerer or a curious cat like me tests Ubuntu 24.04 LTS?

Well, that is what I share here...

I know a lot of you may be tempted to try the beta releases, but unless you want to help test things (and be okay with inconveniences), you should not try them 🙅‍♂️

Even though I do not recommend you to try it, I share my experience with you to help you know the state of things before the final release.

### Ubuntu 24.04 LTS: A Pretty Upgrade

![][1]

If you are going for a fresh installation, you will find the new desktop installer for Ubuntu 24.04 LTS pretty.

A modern take, more clarity, easier for new users to understand, and follow through the installation screen.

I installed Ubuntu 23.10 before trying to [upgrade to Ubuntu 24.04 LTS beta][2]. So, it was an upgrade for me.

![][3]

The upgrade process went smooth, you can even follow that here:

![][4]

I was able to set up everything correctly, and the system booted up as expected. The system I tried it on has the following specifications:

_**Intel i5-11600k CPU, 32 GB RAM 3200 Mhz, ASUS TUF Gaming 3060 Ti OC, 250 GB SSD for Linux OS installation.**_

I decided to keep my `/etc/systemd/resolved.conf` configuration intact from the old system, and did not replace it. Everything else was updated, and worked as usual.

I only had a couple of apps installed, like **GIMP, Discord, Vivaldi, and Firefox.**

So, what changed after the upgrade? Of course, the obvious core changes include:

  * **GNOME 46**
  * **Improved notification style**
  * **A new "Show apps" button in the dock in bottom-left of the screen**
  * **Improved and brand new "App Center"**



![][5]

And, the usual goodies that we already covered in the Ubuntu 24.04 LTS feature article:

![][6]

Those are all the good things. But, then the issues started to show up, as one would expect in a beta version.

The issues for me are:

  1. **Wayland was not my default session after upgrade (it was still X11).**
  2. **App Center fails to update the snap store.**
  3. **The settings app in the Wayland session crashes, forcing me to use X11 for now.**
  4. **Fractional scaling does not work in X11.**



![Fractional scaling not working with X11 session][7]

When publishing this, I applied the latest updates available to the system, and all the issues persist for me.

Not just the fractional scaling, but I also see a third unknown display being listed in the settings. And, I have no idea what's that for:

![][8]

Moreover, some other pesky bugs that I noticed are:

  * The home screen sometimes loads/refreshes when booting for the first time. I had the same issue on Ubuntu 23.10. So, maybe it, is something related to my NVIDIA graphics?
  * The suspend feature fails occasionally.



📋

It is important to know that I did not change any defaults, or customize anything. The NVIDIA graphics driver was not installed manually, but through Ubuntu's setup process that involves proprietary software installation.

Considering Ubuntu 24.04 LTS is due for release next week, I believe these issues will get in the way of the user experience if it does not go away by the release date.

While I have reported all the bugs/issues through the proper channels (Launchpad and GitHub issues), I don't see an update to it yet. The Ubuntu release testing Matrix channel and Telegram sees no response when people report issues/want to discuss it. 🤔

There was activity with alpha testing, but I don't see any responses yet after the beta release. So, I hope they don't neglect the problems reported by the beta testers.

_💭 Have you tested Ubuntu 24.04 LTS beta yet? Do you encounter similar issues? Is it smooth sailing for you? Do you look forward to an upgrade to Ubuntu 24.04 LTS?_

_Let me know your thoughts!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-24-04-beta-experience/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/content/images/2024/04/ubuntu-24-04-home-beta.png
[2]: https://itsfoss.com/upgrade-ubuntu-beta/
[3]: https://news.itsfoss.com/content/images/2024/04/ubuntu-24-04-upgrade-process.png
[4]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[5]: https://news.itsfoss.com/content/images/2024/04/ubuntu-24-04-notification-area.png
[6]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[7]: https://news.itsfoss.com/content/images/2024/04/ubuntu-24-04-fractional-scaling-x11.png
[8]: https://news.itsfoss.com/content/images/2024/04/ubuntu-24-04-unknown-display.png
