[#]: subject: "Customizing GNOME's Top Panel: Here's How to do that!"
[#]: via: "https://itsfoss.com/customize-gnome-top-panel/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Customizing GNOME's Top Panel: Here's How to do that!
======

[![Warp Terminal][1]][2]

GNOME is a popular desktop environment that provides a modern experience.

While it works for the most part, some of their decisions have left the user fuming and questioning.

You cannot have icons and files on the desktop, [new document option has been removed][3] from the right click context menu. In addition to that, GNOME has also removed the applet indicator functionality in the top panel.

You know what indicator applets are, don’t you? Those little icons that let you access additional features of the given application. I have plenty of them in my Ubuntu system.

![][4]

And this creates a problem, for applications that rely completely on these applet indicators to function. Take [Dropbox][5], for example. The only way to access Dropbox settings is through the app indicator.

Unfortunately, **GNOME at its core does not support app indicators** , unless you are using a GNOME-powered distro that supports it by default.

That’s an issue, but thankfully, there are several workarounds, with varying level of customizations for that. Here, I discuss some possible options.

### **First: Setup Third-Party GNOME Extension Support**

If you are using GNOME, you probably already know what GNOME Extensions are. They give you extra functionalities on top of your desktop experience.

💡

Whether you want to enable app indicators or want to customize things, you need GNOME extensions.

You can [enable the GNOME extensions][6] by following this tutorial:

![][7]

It is easy. Go to any GNOME extension’s page using Firefox or Chrome, and it will suggest downloading a browser extension. Install it and you are good to go!

![Install Browser Add-on][8]

You may also need to install a package called `chrome-gnome-shell`, which can be installed in Ubuntu and Fedora by:

```

    sudo apt install chrome-gnome-shell
    OR
    sudo dnf install chrome-gnome-shell

```

If you are using Arch Linux, install it using:

```

    sudo pacman -Syu gnome-browser-connector

```

Once you are ready to use extensions, we can start customizing the top panel using them. Let's go!

### Enable App Indicators for GNOME Panel

App indicators are essential for the top panel experience. With them, you can interact with the apps running in the background, launch them, configure them, and stop them easily.

So, first we enable the app indicators, then we proceed customizing the panel.

📋

If you already have app indicators enabled or if your distro supports it, you can skip this section and move on to the customization tips next.

#### 1\. Using AppIndicator and KStatusNotifierItem Extension

There are various GNOME extensions available that allow adding applet indicators in the top panel. At the time of writing this tutorial, [AppIndicator and KStatusNotifierItem Support][9] is a well-developed extension that is supported for recent GNOME versions.

Head to its extension page using the button below:

[Install AppIndicator Extension][9]

On the page, you should see a toggle button. Click it to install it.

![Install the Extension][10]

There will be a pop-up. Hit install when you see it.

![Click on Install][11]

The results may be seen immediately. If you have any applications installed that provides an indicator applet, you should see it on the top panel.

If that's not the case, you’ll have to restart GNOME. On Xorg, you could just use Alt+F2 and enter “r” but that does not work in Wayland.

Log out of the system and log back in. The Applet indicator should be activated now.

In my case, I had Dropbox already installed; hence it started showing the icon in the top panel.

![Dropbox Panel Applet][12]

This extension does not provide a lot of customization options, but the basics.

![AppIndicator Settings][13]

Things you can do include:

  * Bring the Tray icon to center, left or right (default).
  * Change the appearance of the icons, including size and opacity.



#### 2\. Using Tray Icons: Reloaded

[Tray Icons: Reloaded][14] is another tray icon support extension for GNOME. By default, it works well in Xorg and XWayland. You can go to the extensions page and install it.

[Install Tray Icons: Reloaded][15]

Once installed, you can do several tweaks with this cool extension.

**Overflow Mode**

Usually, in this extension, if there are more than 3/4 applet indicators active in the top panel, it will show you an overflow mode. Here, the indicators are placed neatly on an overflow menu.

![Overflow Mode][16]

It is possible to set the Tray icon limit to your liking so that, the excess icons are moved to overflow, resulting in a very neat top panel.

**Other Features**

  * Wine App Support (Left and middle click affect all wine apps)
  * Invoke app to current workspace, from where it is opened at the moment.
  * You can use Shift + Middle Click to kill an app.
  * Hide selected apps in your tray
  * Other visual tweaks



**Now that you know how to enable app indicators for the top panel. Here's how you can customize the experience:**

### Customizing the GNOME Panel Using Unite

![Unite Default Appearance][17]

[Unite][18] is an extension, that applies some pre-configured settings to your top panel. You can introduce changes to them using the extension’s settings page. According to the documentation, by default, when you install this extension, it will help you:

  * Add window buttons to the top panel for maximized windows.
  * Show current window title in the app menu for maximized windows.
  * Remove title bars on maximized windows.
  * Hide window controls on maximized windows with header bars.
  * Move the date to the right, fixes icons spacing and removes dropdown arrows.
  * Move legacy tray icons to the top panel.
  * Move notifications to the right.
  * Hide activities button.
  * Add the desktop name to the top panel.



[Install Unite][19]

When you open the extension settings, you will get several options with toggle buttons and drop-down menu. Make changes as you require.

![Unite Extension Settings][20]

Here, I have marked some settings that can make your desktop experience a bit different.

  * Setting the **notification area position** to a location convenient to you is one handy trick



Similarly, you can **show a desktop name in the top bar**. By default, it will display “GNOME Desktop” on the top left of the panel. The text can be changed in the Appearance menu.

![Custom Desktop Name][21]

Now, when you are on the desktop, it will display the name of your choice on the top left of the panel.

Likewise, it is possible to **change the position and theme of the windows buttons** (close, minimize, and maximize) on the top panel. Here, you can set a different theme and position.

![Change Position and Theme of Window Button][22]

### Customizing the GNOME Panel Using Quick Settings Tweaker

[Quick Settings Tweaker or QSTweaker][23] is another cool GNOME Extension that works on GNOME 43+. If you are running Ubuntu 23.10, Fedora 39, etc., you can take advantage of this.

[Install Quick Settings Tweaker][24]

When you install this extension, it will move the notification part to the right side of the panel. This will leave a very neat and small calendar in the center, with all other controls going to the right side.

0:00

/0:07

1×

Default Quick Settings Tweaker Appearance

Now, there are many useful customizations available in this extension. Let me highlight some two important ones.

#### 1\. Remove Selected Items from Quick Toggle

If you don’t want some item inside the quick toggle, you can hide it using this setting. You can also bring back what you disabled/removed.

![Hide Selected Buttons][25]

You can see it in the above screenshot, I have removed the icons for tools like settings, screenshot, etc. from the quick toggle. Scroll down the settings page to hide more options like Bluetooth, Dark Mode toggle, etc.

#### 2\. Control Volumes and Media Playing

By default, it places a volume mixer and also adds a media widget, that allows to manage various media sources.

The main attraction is, everything is now accessible from the right side of the panel.

![Multiple Audio Sources][26]

You can choose to disable the media widget, and the sliders, if you do not like it. Moreover, you can adjust the position, if you want the sliders to appear below the toggle buttons.

### Bonus: Blur My Shell

You can use [Blur my shell][27] to make your panel look really cool. Here is a simple customizing tip for you!

First install the extension from its page or through the [Extension manager][28] application.

[Blur My Shell][27]

Now, access the settings and go to the panel tab. Here, toggle on the **Panel blur** and **Customize Properties** buttons.

![Reduce Sigma Value to Zero][29]

Under **Customize properties** , adjust the value of **Sigma** to Zero.

Then, scroll down a bit and toggle on the **Override Background** Button. Under this setting, change the **Background Style** to “ **Contrasted** ”. Furthermore, enable the “Disable when a window is near” option.

![Set Background Properties][30]

That’s it. You can see that the panel now becomes more attractive.

0:00

/0:09

1×

Panel with Blur My Shell Settings Applied

### Wrapping Up

It is pretty easy to adjust the GNOME top panel, for a better look, or quick accessibility.

Of course, that's not all. If you want more GNOME customization, try this:

![][7]

--------------------------------------------------------------------------------

via: https://itsfoss.com/customize-gnome-top-panel/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/add-new-document-option/
[4]: https://itsfoss.com/content/images/wordpress/2021/09/indicator-applet-linux.webp
[5]: https://www.dropbox.com/
[6]: https://itsfoss.com/gnome-shell-extensions/
[7]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[8]: https://itsfoss.com/content/images/2024/01/click-to-install-the-gnome-extensions-browser-add-on.png
[9]: https://extensions.gnome.org/extension/615/appindicator-support/
[10]: https://itsfoss.com/content/images/2024/01/appindicator-and-kstatusnotifieritem-extension.png
[11]: https://itsfoss.com/content/images/2024/01/install-the-extension-confirm.png
[12]: https://itsfoss.com/content/images/wordpress/2021/09/gnome-dropbox-indicator-800x561.webp
[13]: https://itsfoss.com/content/images/2024/01/tweaks-for-appindicator.png
[14]: https://github.com/MartinPL/Tray-Icons-Reloaded
[15]: https://extensions.gnome.org/extension/2890/tray-icons-reloaded/
[16]: https://itsfoss.com/content/images/2024/01/tray-icons-reloaded-overflow.png
[17]: https://itsfoss.com/content/images/2024/01/unite-default-panel-showing.png
[18]: https://github.com/hardpixel/unite-shell
[19]: https://extensions.gnome.org/extension/1287/unite/
[20]: https://itsfoss.com/content/images/2024/01/unite-extension-toggle-settings-1.png
[21]: https://itsfoss.com/content/images/2024/01/showing-a-custom-name-for-desktop.png
[22]: https://itsfoss.com/content/images/2024/01/change-theme-and-appearance-of-window-button-1.png
[23]: https://github.com/qwreey/quick-settings-tweaks
[24]: https://extensions.gnome.org/extension/5446/quick-settings-tweaker/
[25]: https://itsfoss.com/content/images/2024/01/remove-selected-quick-toggle-items.png
[26]: https://itsfoss.com/content/images/2024/01/various-application-playing-sound-in-quick-settings.png
[27]: https://extensions.gnome.org/extension/3193/blur-my-shell/
[28]: https://itsfoss.com/extension-manager/
[29]: https://itsfoss.com/content/images/2024/01/make-sigma-zero-in-panel-settings.png
[30]: https://itsfoss.com/content/images/2024/01/set-background-properties-in-blur-my-shell.png
