[#]: subject: "Linux Mint Shows How The New Cinnamon Theme Looks Like"
[#]: via: "https://news.itsfoss.com/linux-mint-cinnamon-theme-look/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Mint Shows How The New Cinnamon Theme Looks Like
======
The new default cinnamon theme is here, take a look!
[![][1]][2]

Earlier this year, we were introduced to the [Linux Mint 22][3] release, which landed with many major changes, including an updated desktop environment, [Cinnamon 6.2][4].

Since then, the developers have been busy working on further refining their offerings and [recently announced][5] that they were working on a new default Cinnamon theme and some tweaks for Linux Mint.

Now, it appears that they have [delivered][6] on their claims. Let's see what they have been up to. 😃

### Linux Mint Delivers The Refinements

![Source: The Linux Mint Blog][7]

As you can see above, **the default Cinnamon theme is now much darker and more contrasty than before** , making it look less washed out, and giving it more depth. The developers have also worked on making the various elements more rounded, with gaps being introduced between the applets and the panel for a more polished look.

The force quit dialog sees a change as well, with it now being written in Clutter, instead of being a [GTK][8] window to make it look like the rest of Cinnamon.

If you didn't know, [Clutter][9] is a toolkit for designing modern-looking user interfaces, but it has been in a state of “ _deep maintenance_ ” since at least 2016.

![Source: The Linux Mint Blog][10]

Similarly, other system dialogs like the app uninstall dialog, and the media button and workspaces on-screen displays (OSDs) have been redesigned using Clutter to make them on par with the rest of the system.

There are also **plans to revamp the main menu, notifications, animations, and pkexec/logout dialogs** , along with the introduction of a new status applet. Details on those will be shared on the official Linux Mint blog as development progresses.

![Source: The Linux Mint Blog][11]

Those were just the user interface side of things, the Linux Mint developers have also successfully streamlined the APT libraries and utilities used by apps on Linux Mint by implementing [AptKit][12] and [Captain][13].

The diagram shared by the developers shows how they are handling things going forward. They have completely done away with their dependence on _aptdaemon_ , _synaptic_ , _gdebi_ and _apturl_.

The above-mentioned transition will be complete when Linux Mint 22.1 releases in December.

**So, wrapping up.**

I can't wait to check out the next Cinnamon and Linux Mint releases. With improvements like these, those two are shaping up to be exciting releases with a more refined user experience than ever before.

_💬 What about you? Are you looking forward to these changes? Add your thoughts below!_

**Suggested Read** 📖

![][14]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-mint-cinnamon-theme-look/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/linux-mint-22-release/
[4]: https://news.itsfoss.com/cinnamon-6-2/
[5]: https://news.itsfoss.com/default-cinnamon-linux-mint-changes/
[6]: https://blog.linuxmint.com/?p=4749
[7]: https://news.itsfoss.com/content/images/2024/10/LM_Theme_Tweaks_a.png
[8]: https://www.gtk.org/
[9]: https://blogs.gnome.org/clutter/
[10]: https://news.itsfoss.com/content/images/2024/10/LM_Theme_Tweaks_c.png
[11]: https://news.itsfoss.com/content/images/2024/10/LM_Theme_Tweaks_d.png
[12]: https://github.com/linuxmint/aptkit
[13]: https://github.com/linuxmint/captain
[14]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
