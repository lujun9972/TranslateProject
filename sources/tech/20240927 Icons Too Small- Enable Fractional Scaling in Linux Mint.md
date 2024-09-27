[#]: subject: "Icons Too Small? Enable Fractional Scaling in Linux Mint"
[#]: via: "https://itsfoss.com/linux-mint-fractional-scaling/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Icons Too Small? Enable Fractional Scaling in Linux Mint
======

[![Warp Terminal][1]][2]

A HiDPI (High Dots Per Inch) monitor has a high pixel density, meaning it packs more pixels into the same physical screen size compared to a standard monitor. This results in sharper images, crisper text, and finer details, an advantage seen in many newer displays out in the market.

With these advanced displays come issues like tiny text and icons that are hard to read and identify. This is where fractional scaling comes into the scene.

Fractional scaling on computers allows you to fine-tune the size of text, icons, and windows on your screen by scaling them in precise increments like 125%, 150%, etc.

Let's see how to apply fractional scaling on Linux Mint to make it the best fit for all your needs!

### Using fractional scaling in Linux Mint

First, search for Display in the [Linux Mint][3] system menu. Press enter to open the display settings.

![Open Display Settings][4]

💡

You can also open the display settings window by right-clicking on the desktop and then selecting “Display settings”.

In the display settings window, go to the **Settings** tab and enable Fractional Scaling.

🚧

Fractional Scaling in Linux Mint is still experimental, so you should be cautious about unexpected results. If you encounter issues with small icons, text, etc., font scaling is recommended (discussed later).

![Go to the Settings Tab][5]

When you come back to the **Layout** tab, you can see that several Fractional Scaling options are available in the _Monitor Scale_ section as shown in the screenshot below.

![Fractional Scaling Options][6]

You can select a particular Fractional Scaling value from this list that suits your needs.

⚠️

Fractional Scaling can result in increased power consumption in Laptops. This may lead to reduced battery backup.

If you have more than one display, it will show an additional display in the settings. Select a particular display and set the scaling accordingly.

![Scaling in multiple monitor][7]

As the scaling value increases, the size of text and icons displayed on the screen also increases. So, Fractional Scaling is an experimental process for you to determine what is your convenience in viewing items.

📋

Some Snap or Flatpak applications may not adhere to fractional scaling.

### Other manual solutions

There are some manual solutions you can use in cases when everything else fails.

#### Larger fonts

Either set is through Menu → Accessibility → Visual → Large Text.

![Set a larger text in Accessibility settings][8]

Or through Menu → Font Selection → Text Scaling.

![Text Scaling Factor][9]

#### Larger icons

Icons can be scaled in various ways.

The Menu provides a way to increase the size of the icons shown inside the menu. For this, right-click on the Menu and select **Configure**. In the configuration window, go to the **Menu** tab and increase the icon size for various parts:

![Menu Icon Size][10]

The desktop icon size can be increased my right-clicking on an empty space in desktop and selecting **Customize**.

![Change Desktop icon size][11]

Similarly, there are other settings you can check like:

  * Increasing the panel size/height. The Cinnamon panel supports section-wise size changes.
  * CTRL+Scroll to increase icon size in Nemo File Manager.
  * CTRL+Scroll in Firefox to scale Firefox view.
  * Setting a profile with customized text size in terminal.



### Conclusion

Using fractional scaling lets you use your 2K or 4K screen without squinting your eyes. If everything works well, it's a set and forget thing.

If it doesn't work as per your expectations, you may try changing the size of fonts and icons, although it's more manual work, in my opinion.

Enjoy Mint 😄

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-mint-fractional-scaling/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://linuxmint.com/
[4]: https://itsfoss.com/content/images/2024/09/search-and-open-display-settings-from-Linux-mint-start-menu.png
[5]: https://itsfoss.com/content/images/2024/09/go-to-the-settings-tab-in-display-settings.png
[6]: https://itsfoss.com/content/images/2024/09/several-fractional-scaling-options-are-available-in-display-settings.png
[7]: https://itsfoss.com/content/images/2024/09/multi-monitor-scaling-linux-mint.png
[8]: https://itsfoss.com/content/images/2024/09/larger-text-in-linux-mint-accessibilty-settings.png
[9]: https://itsfoss.com/content/images/2024/09/set-the-font-scale-value.png
[10]: https://itsfoss.com/content/images/2024/09/set-the-cinnamon-menu-icon-size.png
[11]: https://itsfoss.com/content/images/2024/09/change-desktop-icon-size.png
