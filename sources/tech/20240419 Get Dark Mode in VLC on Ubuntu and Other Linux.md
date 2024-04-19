[#]: subject: "Get Dark Mode in VLC on Ubuntu and Other Linux"
[#]: via: "https://itsfoss.com/vlc-dark-mode/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Get Dark Mode in VLC on Ubuntu and Other Linux
======

[![Warp Terminal][1]][2]

VLC is an [awesome video player for Linux][3]. However, there is a problem with it if you are a fan of dark mode.

I have noticed that when I am [using Ubuntu in dark mode][4], VLC doesn't adhere to the dark theme. It keeps a white menu bar and control bar at the bottom.

![VLC default mode does not fully support dark mode automatically][5]

I can guess that it probably will be the case in other distributions as well.

Allow me to share a few methods to achieve dark mode with VLC on Ubuntu.

📋

You may try the same methods in other distributions but the package management commands may differ. Also, some methods are desktop environment specific.

### Method 1: GNOME Adwaita dark mode

First, [check the desktop environment][6] you are using. If it is GNOME, you can follow this section.

To make VLC full dark, first install the package `adwaita-qt`, which is a Qt port of the GNOME Adwaita theme.

```

    sudo apt install adwaita-qt

```

Now, open VLC and go to Tools → Preferences.

![Go to Preferences][7]

Alternatively, you can use the keyboard shortcut **CTRL + P** to open the preferences window. Inside the preferences window, go to the Interfaces tab.

![Use Adwaita-Dark][8]

Here, you need to force the window style to point Adwata-Dark. So, set **Force window style** * to Adwaita-Dark.

📋

Even though it won't match the Ubuntu theme in perfection, this will be more than good, if you only want to make VLC dark mode.

### Method 2: Apply dark theme with Kvantum

If you are not satisfied with the above result, or you are using a different theme altogether, you can get help from the [Kvantum engine][9].

First, install Kvantum on Ubuntu using the command:

```

    sudo apt install qt5-style-kvantum

```

Once Kvantum is installed, open Kvantum Manager from Activities overview.

![Open Kvantum Manager][10]

Inside Kvantum manager, go to Change/Delete Theme section.

![Change/Delete Theme][11]

Here, you need to select your installed Kvantum theme. I have selected Layan Kvantum theme, that I have installed already.

💡

You can download Kvantum themes from the [KDE Store website][12]. Once you have downloaded a theme, follow [our guide to install the theme][13].

![Apply a Kvantum Theme][14]

Now, open VLC and go to Tools → Preferences → Interfaces.

![Go to the Preferences window in VLC][15]

Inside the Interfaces tab, set the **Force window style** to Kvantum Dark.

![Apply Kvantum dark][16]

At this time, you have notified the change in the appearance. Click Save to apply changes. Now close VLC and reopen it to complete the process.

🚧

You may need to log out and log back in to get the changes visible.

![VLC Kvantum Dark Theme][17]

### Method 3: Download a custom dark skin

VLC provides a massive list of custom skins that you can use. From there, you can find a good-looking dark skin if you wish.

🚧

Do note that applying these third-party skins on VLC will change the default look of VLC. The placement of buttons and other options will be different in different skins.

First, open the VLC media player and then go to **Tools > Preferences**.

![Go to Preferences][18]

Here, click on **Interface**. Inside the Interfaces tab, select **Custom Skin**. Now, you will see a link, that points to the VLC skins web page. Click on it.

![Click on Skins Page Link][19]

This will bring you to the official VLC skins download page. Select any dark theme from the list.

For this tutorial, I am going with the first one, called **eDark Vlc**.

![Download eDark Vlc Theme][20]

Click on the Download link, to download the theme.

![Click on Download][21]

It will download a file called _**eDark vlc.vlt**_.

Once you have downloaded the dark skin, as in the previous step, go to **Tools → Preferences → Interface**.

Inside the Interface tab, click on custom skin and then select the downloaded theme file using the **Choose** button.

![Select the downloaded skin][22]

Once selected, use the **Save** button to apply the changes. You need to quit VLC and reopen it to see the changes.

![Apply a custom VLC skin][23]

VLC will now become dark mode.

### Conclusion

Life would be so much easier if VLC just adopted the dark mode with system theme. Alas! That's not the case. And that's why we need to resort to additional tweaks to get dark mode VLC. It requires some effort, but a true dark mode lover should not hesitate to go the extra mile.

--------------------------------------------------------------------------------

via: https://itsfoss.com/vlc-dark-mode/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/video-players-linux/
[4]: https://itsfoss.com/dark-mode-ubuntu/
[5]: https://itsfoss.com/content/images/2024/04/default-vlc-mode-in-ubuntu.png
[6]: https://itsfoss.com/find-desktop-environment/
[7]: https://itsfoss.com/content/images/2024/04/tools-preferences-in-vlc.png
[8]: https://itsfoss.com/content/images/2024/04/apply-force-style-adwaita-qt-dark.png
[9]: https://github.com/tsujan/Kvantum/tree/master/Kvantum
[10]: https://itsfoss.com/content/images/2024/04/open-kvantum-manager-from-activities-overview.png
[11]: https://itsfoss.com/content/images/2024/04/go-to-change-theme-section-in-kvantum-manager.png
[12]: https://store.kde.org/browse?cat=123
[13]: https://itsfoss.com/properly-theme-kde-plasma/
[14]: https://itsfoss.com/content/images/2024/04/apply-a-kvantum-theme.png
[15]: https://itsfoss.com/content/images/2024/04/tools-preferences-in-vlc-2.png
[16]: https://itsfoss.com/content/images/2024/04/apply-vlc-kvantum-dark.png
[17]: https://itsfoss.com/content/images/2024/04/VLC-with-kvantum-dark-theme.png
[18]: https://itsfoss.com/content/images/2024/04/click-on-tools-and-select-preferences.png
[19]: https://itsfoss.com/content/images/2024/04/click-on-the-link-to-skins-page-on-vlc.png
[20]: https://itsfoss.com/content/images/2024/04/download-edark-vlc-theme-from-the-website.png
[21]: https://itsfoss.com/content/images/2024/04/click-on-download-to-start-download-the-dark-theme.png
[22]: https://itsfoss.com/content/images/2024/04/select-the-downloaded-skin-on-custom-skin-field-and-save.png
[23]: https://itsfoss.com/content/images/2024/04/apply-custom-vc-skin.png
