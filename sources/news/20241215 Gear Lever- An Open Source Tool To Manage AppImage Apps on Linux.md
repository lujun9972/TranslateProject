[#]: subject: "Gear Lever: An Open Source Tool To Manage AppImage Apps on Linux"
[#]: via: "https://news.itsfoss.com/gear-lever/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Gear Lever: An Open Source Tool To Manage AppImage Apps on Linux
======
A nifty tool to help manage AppImage files.
[![][1]][2]

[Using AppImage in Linux][3] is a very convenient _click-to-run_ way of using applications, allowing users to execute software without installing.

If you didn't know, [AppImage][4] is **a universal packaging format** that was created to provide native binaries for Linux users, similar to what other operating systems like Windows and macOS do have with _.exe_ and _.app_ files.

However, as AppImage files are standalone bundles, **they have to be manually launched each time one wants to use the bundled application** , and that can get tedious if you have many AppImages in your computer.

With this App Of The Week, we have Gear Lever, **a utility that makes managing AppImage files easy** , allowing users to add AppImage files to the application launcher of their Linux distribution.

### Gear Lever: A Manager For Your AppImages

![][5]

Gear Lever is **a Python-based app** that is the work of over 20 open source contributors, with [Lorenzo Paderi][6] leading them. It is meant to be a no-nonsense app that just focuses on the essentials, allowing users to manage local AppImage files.

#### ⭐ Key Features

With handy features like file drag/drop support, managing AppImage updates, and opening AppImages from the file manager, here are some highlights:

  * **Intuitive Interface**
  * **Supports CLI Apps**
  * **Offered Under** [**GPL 3.0**][7]



#### 💻 User Experience

I loaded up the official Flatpak on my Fedora 40 laptop and started testing it out. On the first launch, there was **a welcome tutorial** that I launched to configure Gear Lever.

It was quite straightforward, letting me choose a folder where any added AppImage files would be stored ( _I went with the default_ ) and showing me how to set Gear Lever as the default app to handle AppImage files.

![Gear Lever's onboarding process.][8]

Right-clicking on an AppImage file automatically showed me the “ _Open With Gear Lever_ ” option. If it doesn't appear for you, then you can go into the “ _Open With…_ ” menu and get it added.

Alternatively, you could simply drag and drop any AppImage files directly into Gear Lever.

![][9]

I used it to add many AppImage files, starting with [Kdenlive][10] first. As you can see below, before the AppImage could be added, **I was asked to verify the source of the app** before opening it on my system.

![Adding a new AppImage to Gear Lever.][11]

As I had downloaded it from the official website, I didn't have to worry about it, so I clicked on “ _Unlock_ ”, and the interface then let me change the settings for Kdenlive. I immediately added the app to the app launcher of my distro by using the “ _Move to the app menu_ ” button.

I could also launch Kdenlive from within Gear Lever by using the “ _Launch_ ” button.

![The AppImages added using Gear Lever showed up nicely on GNOME's app launcher.][12]

Thereafter, I added three more AppImage files: [Heroic Games Launcher][13], [VS Codium][14], and [RetroArch][15]. All four of these apps showed up neatly on the app launcher, **allowing me to sort them into folders** or **pin to dock** if needed.

When launched, these apps work as expected, without any hiccups.

![Gear Lever can handle updates for any added AppImages, and the preferences menu provides useful controls.][16]

Gear Lever **provides additional options for any added AppImage entries** , such as seeing the package type, changing the path, adding a command-line argument, configuring updates, and adding environment variables.

During my testing, only the entry for VS Codium showed me a helpful “ _No updates available_ ” status after it checked for updates. As for the other apps, I would have to manually add update URLs before Gear Lever could show me the update status for those.

**So, wrapping up.**

My experience with Gear Lever so far has been wonderful. **Its minimal user interface has made it easy to add new AppImage shortcuts** to the app launcher, and I no longer have to manually go into the folder where AppImage files are stored to launch an app.

Going forward, I intend to use this for managing any AppImage apps I keep for long-term use.

### ⚙️ Installing Gear Lever on Linux

You can find the most recent release of Gear Lever on [Flathub][17], with the source code being hosted over on [GitHub][18] that has instructions on how to build from source. You can also contribute to development if you have the relevant skills.

[Gear Lever (Flathub)][17]

**Suggested Read** 📖

![][19]

* * *

[Get It's FOSS Plus Membership][20]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/gear-lever/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/use-appimage-linux/
[4]: https://appimage.org/
[5]: https://news.itsfoss.com/content/images/2024/12/Gear_Lever_a.png
[6]: https://github.com/mijorus
[7]: https://www.gnu.org/licenses/gpl-3.0.en.html
[8]: https://news.itsfoss.com/content/images/2024/12/Gear_Lever_b.png
[9]: https://news.itsfoss.com/content/images/2024/12/Gear_Lever_e-1.png
[10]: https://kdenlive.org/en/
[11]: https://news.itsfoss.com/content/images/2024/12/Gear_Lever_f.png
[12]: https://news.itsfoss.com/content/images/2024/12/Gear_Lever_l.png
[13]: https://heroicgameslauncher.com/
[14]: https://vscodium.com/
[15]: https://www.retroarch.com/
[16]: https://news.itsfoss.com/content/images/2024/12/Gear_Lever_i.png
[17]: https://flathub.org/apps/it.mijorus.gearlever
[18]: https://github.com/mijorus/gearlever
[19]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[20]: https://itsfoss.com/#/portal/signup
