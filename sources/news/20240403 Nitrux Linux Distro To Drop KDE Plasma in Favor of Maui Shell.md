[#]: subject: "Nitrux Linux Distro To Drop KDE Plasma in Favor of Maui Shell"
[#]: via: "https://news.itsfoss.com/nitrux-maui/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Nitrux Linux Distro To Drop KDE Plasma in Favor of Maui Shell
======
Nitrux's in-house desktop environment will finally make its debut.
When I came across the latest [Nitrux 3.4.0 release][1], I was left wondering why they included the older KDE [Plasma 5.27][2] instead of the newer [Plasma 6][3] desktop environment that many recent distro releases come equipped with.

That's when I noticed their [announcement][4], which explained what they are doing, and how it affects the future of Nitrux. Let's get into it without any further ado.

**What's Happening:** In a surprising move, the developers of Nitrux have signalled a move away from Plasma, and **committed to using Maui Shell by default from late 2024, as the only desktop environment option with Nitrux**.

It's been some time since we took a look at the [first alpha release][5] of Maui Shell, and as it stands, its development seems to have progressed consistently when you look at its [GitHub repo][6].

**What to Expect:** Well, the switch is coming, but not anytime soon. Nitrux's developers will continue using the older Plasma 5.27.x LTS release for the majority of 2024.

However, **what made them switch to Maui Shell** was the fact that many of the widgets and plasmoids used to make [NX Desktop][7] (Nitrux's customization layer for Plasma) will stop functioning with Plasma 6.

📋

It is one of the key components that makes Nitrux different from your run-of-the-mill Plasma-equipped distro.

The developers believe that NX Desktop has achieved what it set out to do, while also helping Plasma further its development. But, they also mention that Nitrux will still continue to use various KDE components such as [_KDE Frameworks_][8], [_Extra CMake Modules_][9], and a few more.

Despite the above, the developers have stated that **they are open to the idea of providing an AppImage of KDE Plasma 6** “ _for fun_ ”. Those who want to use it with their Nitrux installation could benefit from this.

For now, the devs are focused on porting their apps and Maui Shell to [Qt6][10], while also carrying out some remaining work with AppImages on NX AppImage Build Hub.

_💬 What do you think? Would you prefer using Plasma 6 or Maui Shell?_

**Suggested Read** 📖

![][11]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/nitrux-maui/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://nxos.org/changelog/release-announcement-nitrux-3-4-0/
[2]: https://news.itsfoss.com/kde-plasma-5-27-release/
[3]: https://news.itsfoss.com/kde-plasma-6/
[4]: https://nxos.org/news/plasma-6-in-nitrux-when/
[5]: https://news.itsfoss.com/maui-shell-alpha-release/
[6]: https://github.com/Nitrux/maui-shell
[7]: https://nxos.org/english/nxd/
[8]: https://develop.kde.org/products/frameworks//
[9]: https://invent.kde.org/frameworks/extra-cmake-modules
[10]: https://www.qt.io/product/qt6
[11]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
