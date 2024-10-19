[#]: subject: "Pi-Apps: The Unofficial but Definitely Better App Store for Raspberry Pi"
[#]: via: "https://itsfoss.com/pi-apps-store/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Pi-Apps: The Unofficial but Definitely Better App Store for Raspberry Pi
======

[![Warp Terminal][1]][2]

Though not popular, Raspberry Pi OS does provide a GUI method for installing and uninstalling applications.

It's the **Add/Remove Software** tool, introduced in 2016 as a GUI-based method for installing applications.

![Click to enlarge the image][3]

To give you an idea, here's how installing apps works with the default method. Here I'm installing Okular, a fantastic PDF reader and annotator app.

![You can see that the UI is not at all friendly and a beginner can easily download a wrong package.][4]

See? That's basic, but it's not the best one around. Let me share a better app store for your Raspberry Pi.

### Enter Pi-Apps

[Pi-Apps][5] is a user-friendly application manager for Raspberry Pi that simplifies the process of installing, managing, and uninstalling software.

It acts like an " **app store** " offering a curated collection of over 200 applications.

Unlike the traditional Add/Remove Software tool, Pi-Apps is faster, more reliable as less chance of getting confuse between packages with similar names, and packed with useful features.

![Pi- Apps Website][6]

Some of its key advantages include:

  * **One-Click Installation** : No need to deal with multiple command lines or manual configurations.
  * **Extensive App Library** : Pi-Apps offers everything from games and development tools to multimedia and internet browsers.
  * **Multi-OS Compatibility** : While designed for Raspberry Pi OS, Pi-Apps works seamlessly with other operating systems like Ubuntu for Raspberry Pi.



### How to Install Pi-Apps

Although Pi-Apps simplifies software installation, you’ll need to use the terminal one last time to install it. Fortunately, it’s straightforward.

**Open Terminal** on your Raspberry Pi and run the following command:

```

    wget -qO- https://raw.githubusercontent.com/Botspot/pi-apps/master/install | bash

```

This will download and run the installation script. Once installed, you can launch Pi-Apps from the Accessories menu or by typing `pi-apps` in the terminal.

![][7]

### Using Pi-Apps

Once installed, using Pi-Apps is incredibly simple:

**Launch Pi-Apps** : Open it from the menu or terminal.

![Click to enlarge the image][8]

**Browse Categories** : Pi-Apps organizes software into various categories like Games, Internet, Multimedia, and more. Alternatively, you can use the Search function to find a specific app.

![Click to enlarge the image][9]

**Install an App** : Select an app, read its description, and click the Install button. The terminal window will open, and the installation process will begin. Watch for interaction prompts during installation.

![Click to enlarge the image][10]

**Uninstalling Apps** : If you want to remove an app, simply find it in Pi-Apps, and click Uninstall.

![Click to enlarge the image][11]

Pi-Apps also offers a **Multi-Install** feature, allowing you to select several apps to install at once, perfect for setting up a fresh Raspberry Pi quickly.

### Tweaking Pi-Apps Settings

Pi-Apps also provides a range of customization options through its **Settings** menu.

![Click to enlarge the image][12]

Here, you can tweak the appearance, update settings, and more. Some useful tweaks include:

  * **App List Style** : Choose from various themes like dark mode, light mode, or even a 3D theme.
  * **Check for Updates** : Control how often Pi-Apps checks for updates—daily, weekly, or never.
  * **Text Editor Preference** : Switch between different text editors like Geany, Nano, or Mousepad.
  * **Multi-Install & Multi-Uninstall**



![Click to enlarge the image][13]

### Conclusion

Pi-Apps is a nice-to-have tool for anyone using a Raspberry Pi on the desktop, regardless of their experience level.

It eliminates the need for complex terminal commands and simplifies the entire process of managing applications.

Whether you’re installing games, productivity tools, or development software, Pi-Apps makes the Raspberry Pi more accessible and user-friendly.

So, if you're tired of the clunky Add/Remove Software tool or don’t want to fuss with the command line, give Pi-Apps a try. Your Raspberry Pi experience will never be the same.

--------------------------------------------------------------------------------

via: https://itsfoss.com/pi-apps-store/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/09/pi-apps-menu-for-add-rem-software-1.png
[4]: https://itsfoss.com/content/images/2024/09/pi-apps-add-rem-software.png
[5]: https://pi-apps.io/
[6]: https://itsfoss.com/content/images/2024/09/pi-apps-website.png
[7]: https://itsfoss.com/content/images/2024/09/pi-apps-installation-script.png
[8]: https://itsfoss.com/content/images/2024/09/pi-apps-menu-1.png
[9]: https://itsfoss.com/content/images/2024/09/pi-apps-main.png
[10]: https://itsfoss.com/content/images/2024/09/pi-apps-doom-installation.png
[11]: https://itsfoss.com/content/images/2024/09/pi-apps-uninstall-1.png
[12]: https://itsfoss.com/content/images/2024/09/pi-apps-settings.png
[13]: https://itsfoss.com/content/images/2024/09/pi-apps-settings-menu.png
