[#]: subject: "I Just Removed Ubuntu for Archcraft and my Linux PC Looks Awesome!"
[#]: via: "https://news.itsfoss.com/archcraft-experience/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Just Removed Ubuntu for Archcraft and my Linux PC Looks Awesome!
======
Switching away from Ubuntu, again, to try Archcraft. Here's what I
think!
[![][1]][2]

My distro hopping days are not over. And, probably, will never be 😉

On some days, I love Ubuntu, and others, I hate it. But, for the majority, I stick with Ubuntu-based distributions including Ubuntu, Pop!_OS, and Linux Mint.

I have an NVIDIA-powered system with 1080p+2K displays. And, many distros do not play nice with this setup.

Some background to it:

I tried [switching to Manjaro Linux two years back][3] in a bid to try Arch Linux. But, broken system updates and some other hiccups made me go back to Ubuntu 😁

In my next stop earlier this year, [I switched to Fedora][4], and it did not play nice with my NVIDIA graphics card (hardware acceleration) along with some other issues, and I found myself back to Ubuntu, yet again 😮

Now, I am back with another adventure. This time, it is a little more interesting ⚡

I tried **Archcraft** (an Arch-based distro) developed and maintained by a single developer since 2021. It also happens to be one of the most [user-friendly Arch-based distros][5] out there.

❗ **Spoiler:** It went better than the last two experiences.

### Enter Archcraft: A Bit About The Distro

![My Archcraft home screen][6]

[Archcraft][7] is for Linux users who want a pre-configured window manager with a unique look out of the box. You get a pretty theme setup, but you can choose from a couple of pre-installed options ( _10 free themes_ ) as well.

With the ISO ( _Nvidia driver included_ ), you get the ability to have Openbox or bspwm window manager with X11 desktop.

You can pick other window managers like Sway, Wayland desktop session, and unlock access to extra themes on [Ko-fi][8] by supporting the developer. So, some can call it a freemium model, and I do not mind that, considering you are paying the dev to give you a refined pre-configured experience, saving all the time to set it up yourself.

I opted for the free ISO, so I get a starting base to go on with. And, eventually, I can customize my experience as I learn and explore about it.

Now, let us move on to my experience so far...

### First Impressions: Ubuntu Problems Are Gone!

0:00

/0:06

1×

To start with, I got rid of some annoying issues I was facing with Ubuntu 24.04 LTS:

  * Performance issues with file selection screen
  * Screen recording quality
  * The login screen getting stuck at times
  * Hibernation did not work



Yes, all those issues with Ubuntu 24.04 LTS on board (which was supposed to give a stable experience).

The file selection dialogue screen took ages to appear when trying to upload something through the browser. I had to utilize _SimpleScreenRecorder_ utility to get quality screen recording, as the default Ubuntu screenshot utility resulted in pixelated videos. And, at times, when trying to log in for the first time, it resulted in a black screen and only a reboot fixed it.

So, I was pretty happy about all these issues going away: **everything works fast** , the **screen recording quality is just as I need it to be** by default, and I can successfully log in every time.

What else do I find great about Archcraft? Let me tell you next...

📋

Archcraft is not recommended to someone who has never used Linux before or wants a familiar Windows-like experience. You need to have some Linux experience to try it out as your daily driver.

### The Exciting Part: It's Pretty, Customizable, & Stable So Far…

I have always been fascinated by the desktop setups users share on [r/Unixporn][9]. It gives you the chance to see what you can achieve with Linux, if you set out to customize the look and feel yourself.

I love how my desktop looks out of the box, when compared to the Ubuntu experience:

![][10]

I know, you can do it with Arch Linux or any other setup if you set it out as your goal.

But, with Archcraft, I get a **good starting point to customize things** on top of Arch Linux with minimal effort. So, if you want a similar approach to save some time, Archcraft should be a good pick.

Here, I get to use the default Openbox window manager and polybar (for the top panel). And, I was able to easily remove elements that I did not want in the top panel, and I could also change the colors/icons if I wanted.

This is how my panel looks after removing certain default elements:

![][11]

Yes, you need to access the terminal to change a few things, but I like the ability to do it, and I am getting used to it. If you are a new user, you can try editing these files to find your best match on the color, modules in the top panel, and more:

```

    sudo nano ~/.config/openbox/themes/default/polybar/config.ini
    sudo nano ~/.config/openbox/themes/default/polybar/colors.ini
    sudo nano ~/.config/openbox/themes/default/polybar/modules.ini

```

If you know [bash scripting][12], or have a bit of coding experience, I am sure, you can achieve a great deal of customization.

But, even without it, you can change the look and feel using the default styles in the right-click preferences menu that you see here (with Openbox window manager):

![][13]

You can do plenty of tweaks using the GUI menu as well. So, it is not like only users with some terminal prowess can tweak things.

Here's one of the styles that made the desktop look like this in a single click:

![Free pre-installed style on Archcraft][14]

Pretty cool, right? Moreover, a couple of other highlights:

  * Roll up/down a window in Openbox is a neat feature
  * Ability to easily install i3 window manager and get a pre-configured setup can help you start your advanced customization journey. You can follow our [i3 customization guide][15] to get started.



Not to forget, it comes with AUR support. So, you can use Yay helper to install packages from AUR. You can follow our guide if you are new to this:

![][16]

Finally, I got the latest [Linux kernel 6.10][17] with the system updates as you should expect in an Arch distribution:

![][18]

And, unlike my Manjaro experience, I have updated the system a couple of times (including newer kernel) without breaking anything:

0:00

/0:11

1×

💡

Interestingly, the keyboard shortcut bindings in Archcraft Openbox configuration makes me want to utilize them to open apps, terminal, utilities, and more, over using the mouse pointer. So, I like that for a change.

### The Ugly Part: Every Distro Has One!

That's the beauty of Linux. Every user can choose something meant for their use-cases.

But, of course, nothing is ever perfect. Everything has flaws. It is you who pick what flaws you can live with, and what you can't.

With Archcraft some issues I encountered include:

  * No fractional scaling with Openbox (you need some manual tweaking to get it at best settings). You can try a different window manager/desktop session/environment to get support for it.
  * Even though Hibernation works, the second screen sometimes gets disabled when waking up the PC (need to reset the resolution for the screen to show up again)
  * Weird lock screen for dual-monitor (I don't see any password field, but I can log back in when I enter the password).
  * Unresponsive shutdown button in the panel (with cursor/mouse — works with keyboard shortcut)
  * For hibernation to work, it requires a swap as big as your RAM (it required 34 GB in my case).



So, as is the case with dual-monitor, **every distro I tried fails to be perfect at it.** Yes, even Ubuntu.

**Ubuntu used to fail scaling apps like Insync and Steam at the correct resolution**. But, with Archcraft, that is not an issue. However, both of my monitors do not work at 144Hz.

![][19]

I need to set the 1080p monitor at 120 Hz using the display manager for it to be active, while the primary 2K display works at 144 Hz.

Regarding fractional scaling, I tweaked the DPI, and it seems to do the trick for now. It is sharp, not too small, and not blurry at all. **Yes, Ubuntu was better at this**. But, I can manage with what I get here.

### So, What's My Final Verdict?

**✅ Archcraft is a beautiful distribution for a beginner who always wanted to try an easy and pretty Arch Linux experience.**

Like any other Nvidia-powered multi-monitor system, it wasn't too different when it came to encountering bugs/issues. Not to forget that this distribution is being maintained by a single developer.

If more contributors come along to help with the project, I think, Archcraft could make Arch Linux an easy and beautiful experience at the same time for new users.

It has a solid potential, and the developer seems to be doing a pretty good job at maintaining it, and finding a way to keep the project alive with paid items available.

Unless I have an experience breaking bug with it which I cannot solve. I am going to keep using Archcraft and explore the customization capabilities I get with it.

I really want it to work for a long time, so I can say — BTW, I use Arch 😄

_💬 What do you think about Archcraft? Have you tried switching to it yet? What are your thoughts on Arch Linux in general over Ubuntu?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/archcraft-experience/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/manjaro-linux-experience/
[4]: https://news.itsfoss.com/fedora-ubuntu-switch/
[5]: https://itsfoss.com/arch-based-linux-distros/
[6]: https://news.itsfoss.com/content/images/2024/08/archcraft-default-with-tweak.jpg
[7]: https://archcraft.io/
[8]: https://ko-fi.com/adi1090x
[9]: https://www.reddit.com/r/unixporn/
[10]: https://news.itsfoss.com/content/images/2024/08/archcraft-openbox-xfce.png
[11]: https://news.itsfoss.com/content/images/2024/08/polybar-left-side.png
[12]: https://itsfoss.com/bash-scripting-tutorial/
[13]: https://news.itsfoss.com/content/images/2024/08/openbox-menu-archcraft.jpg
[14]: https://news.itsfoss.com/content/images/2024/08/archcraft-style-1.jpg
[15]: https://itsfoss.com/i3-customization/
[16]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[17]: https://news.itsfoss.com/linux-kernel-6-10-release/
[18]: https://news.itsfoss.com/content/images/2024/08/neofetch-archcraft-latest.png
[19]: https://news.itsfoss.com/content/images/2024/08/archcraft-display-manager.png
