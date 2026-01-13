[#]: subject: "Exploring Dash to Dock: (Probably) The Most Downloaded GNOME Extension"
[#]: via: "https://itsfoss.com/dash-to-dock-tips/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Exploring Dash to Dock: (Probably) The Most Downloaded GNOME Extension
======

[![Warp Terminal][1]][2]

Do you know which is the most popular GNOME extension out there?

I don't know for sure, but if I have to make a guess, I would say Dash to Dock is a good candidate for that title.

Why do I say that? Because at the time of writing this article, this extension has more than ten million downloads.

### What is Dash to Dock?

In the clean GNOME layout, you don't see any quick launcher. It's just the wallpaper. You press the Super key (Windows key), a launcher appears at the side or on the bottom. This launcher is called Dash in GNOME. The Dash to Dock extension takes the "dash" from GNOME Activities Overview and "docks" it to make it visible on the desktop all the time.

![Dash to Dock][3]

You can guess the popularity of this extension from the fact that even Ubuntu uses a customized version of Dash to Dock for its launcher.

![Ubuntu Launcher is also based on Dash to Dock extension][4]

I have written a [detailed tutorial on customizing the Ubuntu launcher][5] in the past. I thought of doing the same with Dash to Dock. Behold this tutorial.

### Installing Dash to Dock

🚧

Please [check which desktop environment you are using][6]. It has to be GNOME.

You can install it using the GNOME Shell Extension Manager application. For that, you need to install it first.

Please use your distribution's package manager to install it. For Debian/Ubuntu users, use:

```

    sudo apt install gnome-shell-extension-manager

```

![Dash to Dock in Extension Manager][7]

You can also use the classic method of installing an extension from the GNOME Extensions official website. But you need to [install GNOME extension support][8] first.

[Dash to Dock in GNOME Extensions Website][9]

![Dash to Dock in GNOME Extensions official website][10]

Once you have installed Dash to Dock, it will be activated immediately.

![Dash to Dock][11]

### Exploring Dash to Dock features

Now let me show a few examples of how you can tweak this most downloaded GNOME extension. Since these changes are available from the settings, you need to know how to access that first.

#### Accessing Dash to Dock Settings

**To access settings of Dash to Dock,** right-click on the application menu button and click Settings.

![Access settings][12]

#### Access panel items using keyboard shortcuts

In the Settings, go to **Behaviour - > Use keyboard shortcuts to activate apps** settings and enable it if it is not already enabled.

![Access app from Dock][13]

Now, you can use the Super + (0-9) keys to access the items in the dock.

0:00

/0:14

1×

Using the super key and number to launch an app of a position in the dock.

#### Set Ubuntu like dock

If you are using vanilla GNOME on Fedora, Debian or some other distro, you can change the appearance of Dash to Dock and make it look like the launcher in Ubuntu.

Change the position to left using the **Position and Size - > Position on screen -> Left**.

![Dock position][14]

Check **Panel extend to edge** option. This will make the dock extend for the entire screen.

![Panel mode][15]

It would be wise to reduce icon size. In the same **Position and Size** setting tab, scroll down to access the icon size settings:

![Reduce icon size][16]

In the **Appearance** section, toggle on the **Shrink the dash** option.

![Shrink the dash][17]

Here's what it looks like now:

![Ubuntu like dock][18]

#### Preview scale

You can also experiment with the window preview. Make it bigger so that it is easier to see what's going on in an application window.

In the **Position and size** section, scroll to the bottom adjust the window preview size to make the window preview smaller or larger.

![Preview Scale Settings][19]

#### Click to minimize (my favorite)

In the **Behavior** tab in Settings, click on the drop-down list in the **Click Actions** segment and set it to **Focus Minimize or app spread**.

![Focus, Minimize, or App Spread][20]

**T** his will have the following behavior:

  * Clicking on the icon of an unfocused application window will bring it to focus.
  * Clicking on the icon of an application window in focus will minimize it (given only one window of that app is opened).
  * If there are more than one window of an app open, clicking on the icon of the app on the dock will enable the app spread, an overview screen where only the windows of the current app are present.



See it in action in the demo video below:

0:00

/0:12

1×

A recording showing the working of the click action.

#### More click settings

Click on the settings gear button adjacent to **Click Actions.**

![Click Actions Settings][21]

In the new dialog box, set what you like. In the example, I have set:

  * **Shift Click:** Show window preview.
  * **Middle Click:** Launch New Instance
  * **Shift Middle Click:** Quit the whole app.



![Additional Click Actions][22]

💡

There is an option to switch workspace through scrolling the dock. But it seems less useful as you can just press the super key and scroll anywhere in GNOME desktop to switch workspaces. Also, the ****Super Tab**** is the most efficient way to switch applications.

#### Control the dock color and opacity

📋

In most cases you don't need to change the background color, since the default Dark is pretty good with an added opacity.

I prefer setting background color for the dock. A dark color is more logical as it forms a better view with most of the wallpapers.

In the Appearance tab, enable the **Customize dash color** toggle button and select a color of your choice.

![Dock color change][23]

To set the opacity, first change the **Customize opacity** option to **Dynamic**. Then, click on the adjacent settings gear.

![Set opacity to dynamic][24]

Enable the **Customize minimum and maximum opacity values** option and then set minimum and maximum opacity values as needed.

![Customize opacity values][25]

💡

Setting the minimum opacity value to 0% will make the Dash background transparent when it is not near any window.

  * **Minimum opacity:** When no window is near the Dock
  * **Maximum opacity:** When window near the dock



0:00

/0:09

1×

The opacity of the dock is changed when a window appears near by.

🚧

Blur my shell users may need to adjust the dash opacity settings in that app to make Dock completely transparent.

#### Notification counter

In the **Launchers** tab, set the **Show icons emblem** and toggle the sub options. Now, apps like Discord, etc. will show the number of unread notifications. This is the same unread notification that we see in the notification section in top panel.

![Show icons emblems][26]

#### Show network volumes

In the **Launchers** section, enable the **Include network volumes** to show Google Drive and other mounted network drives in the dock.

![Show network volume][27]

#### Bonus tip: Dash to Dock and Blur my shell

If you are using the Blur my shell extension in GNOME, there is a dedicated Dash to Dock section in its settings.

![Dash option in Blur my Shell][28]

### Conclusion

Dash to Dock enables the Intelligent Hide by default. You can change this settings in the **Position and Size** section.

When you log in to GNOME, the overview appears by default; you can also disable it by toggling off the **Show overview on startup** options in Appearance settings.

There are probably some other options and I let you explore them on their own.

Of all the [docks available for Linux desktop][29], Dash to Dock remains a popular choice. Considering the vast configuration options it offers, you can guess why so many Linux users prefer Dash to Dock over others.

I hope you find this article helpful in your desktop customization journey 🐧

--------------------------------------------------------------------------------

via: https://itsfoss.com/dash-to-dock-tips/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2026/01/dash-to-dock-1.png
[4]: https://itsfoss.com/content/images/2026/01/image-23.png
[5]: https://itsfoss.com/customize-ubuntu-dock/
[6]: https://itsfoss.com/find-desktop-environment/
[7]: https://itsfoss.com/content/images/2025/11/dash-to-dock-install-page-in-extension-manager.png
[8]: https://itsfoss.com/gnome-shell-extensions/
[9]: https://extensions.gnome.org/extension/307/dash-to-dock/
[10]: https://itsfoss.com/content/images/2025/11/install-dash-to-dock-from-gnome-extensions-page.png
[11]: https://itsfoss.com/content/images/2025/11/dash-to-dock-in-gnome.png
[12]: https://itsfoss.com/content/images/2025/11/open-settings-of-dash-to-dock.png
[13]: https://itsfoss.com/content/images/2025/11/dock-app-access.png
[14]: https://itsfoss.com/content/images/2025/11/change-the-dock-position.png
[15]: https://itsfoss.com/content/images/2025/11/panel-extend-to-edge.png
[16]: https://itsfoss.com/content/images/2025/11/reduce-icon-size.png
[17]: https://itsfoss.com/content/images/2025/11/shrink-the-dash-dock.png
[18]: https://itsfoss.com/content/images/2025/11/ubuntu-like-dock.png
[19]: https://itsfoss.com/content/images/2025/11/preview-scale.png
[20]: https://itsfoss.com/content/images/2025/11/click-action.png
[21]: https://itsfoss.com/content/images/2025/11/settings-gear-of-click-action.png
[22]: https://itsfoss.com/content/images/2025/11/set-additional-click-actions.png
[23]: https://itsfoss.com/content/images/2025/11/dock-color-change.png
[24]: https://itsfoss.com/content/images/2025/11/set-opacity-to-dynamic.png
[25]: https://itsfoss.com/content/images/2025/11/customize-opacity-values.png
[26]: https://itsfoss.com/content/images/2025/11/show-emblem-icon.png
[27]: https://itsfoss.com/content/images/2025/11/show-network-volume.png
[28]: https://itsfoss.com/content/images/2025/11/dock-option-in-blur-my-shell.png
[29]: https://itsfoss.com/best-linux-docks/
