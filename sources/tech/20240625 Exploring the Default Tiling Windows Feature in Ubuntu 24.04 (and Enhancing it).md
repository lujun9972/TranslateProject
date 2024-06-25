[#]: subject: "Exploring the Default Tiling Windows Feature in Ubuntu 24.04 (and Enhancing it)"
[#]: via: "https://itsfoss.com/ubuntu-tiling-windows/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Exploring the Default Tiling Windows Feature in Ubuntu 24.04 (and Enhancing it)
======

[![Warp Terminal][1]][2]

Tiling windows is a method of arranging open windows on a computer screen so that they do not overlap, but instead fit neatly alongside one another.

It's been popular among people customizing their desktops. Probably why Ubuntu has also started providing support for some basic tiling with the 24.04 LTS release.

In this article:

  * I'll show how the default tiling works in Ubuntu
  * I'll discuss the keyboard shortcuts and some enhancing you can do with the tiling feature
  * I'll also share another extension that takes the tiling feature to the next level



There are many tiling window managers available, that performs the action in their own specific method.

Ubuntu uses GNOME and GDM, and these are not dedicated tiling window managers. For a long time, Ubuntu has supported basic tiling features like snapping the window to left or right.

From Ubuntu 23.10 Mantic Minotaur onwards, we saw the inclusion of a built-in extension called [Ubuntu Tiling Assistant][3]. With this extension, you will be assisted in placing windows during tiling operation, according to the available screen space.

But there is more it can do, other than placing the windows on a grid like pattern. Let’s take a look at some rather unknown use cases of Ubuntu tiling assistant.

### Experiencing the window tiling in Ubuntu

Ubuntu has long supported basic tiling features like snapping the window to the left or right, but it has 'enhanced' them in recent versions by including the built-in extension called [Ubuntu Tiling Assistant][3].

The 'enahnced tiling' setting can be found under the Ubuntu Desktop section.

![][4]

📋

Note that the tiling assistant is not an automatic tiling system. This means your windows won’t be tiled automatically when opened. You need to tile it to a space using either a keyboard shortcut or drag it using a mouse.

#### Using mouse drag to tile

Let’s say you have four windows opened, and you want to tile them.

First, drag a window by clicking on its title bar and then move to any edge. It will be tiled to that edge.

0:00

/0:13

1×

Tile Windows using Mouse

Once a window is tiled to a position, the tiling assistant will suggest other apps, that can be placed to fill the remaining space. This is shown in the video above.

🚧

If you tile a window to any of the corners, the tiling assistant won’t suggest apps until another window is tiled to another corner.

You can drag a window from an existing tiling layout to another layout position at any time.

#### Use keyboard shortcuts to tile windows

Ubuntu Tiling Assistant has some preconfigured keyboard shortcuts to tile windows to a particular layout position. Let’s see it with the help of a small video.

0:00

/0:33

1×

Small animated video for Ubuntu Tiling Assistant Shortcuts.

Take a look at these table for various default tiling shortcuts:

Purpose | Shortcuts
---|---
To the right | Super + Numpad 6
or
Super + Right Arrow
To the left | Super + Numpad 4
or
Super + Left Arrow
To the top | Super + Numpad 8
To the bottom | Super + Numpad 2
Top right corner | Super + Numpad 9
Top left corner | Super + Numpad 7
Bottom right corner | Super + Numpad 3
Bottom left corner | Super + Numpad 1
Restore the window | Super + Numpad 5
or
Super + Down arrow
Maximize the window | Super + Up arrow

### Fine control Ubuntu tiling

But it can do more than place the windows in a grid-like pattern. Let’s take a look at some rather unknown use cases of the Ubuntu tiling assistant.

In order to control the Tiling Assistant, [install the GNOME Extension Manager App][5]. Open a terminal and run:

```

    sudo apt install gnome-shell-extension-manager

```

Once installed, open it. The default tab will be the installed extensions. You can find the Ubuntu [Tiling Assistant extension][6] at the bottom of System Extensions section. Click on the settings gear icon adjacent to the extension as show below.

![Click on Settings Gear][7]

This will open the extension settings in a new window. Here, there are options to tweak it in different ways. Let’s see some of the cool items.

#### Set the window gaps

By default, there is no gap between the tiled windows, which means the borders are touched. It would be nice if there was a small gap between the windows.

For this, go to the gaps section and set the Windows and Screen Edge gap to a number that is convenient for you.

![Window gaps and screen edge gaps][8]

🚧

If you enable the Maximized Windows button, maximized windows will also get a gap from the edges as specified. But, it is not applicable for full screen you get by double-clicking on the title bar or using the maximize button in the windows. For me, it only worked by using the shortcut Super + Up.

![Custom Window and Screen Edge Gaps][9]

#### Show active window hint

In a tiling set up, it is always good to know which window is currently active. In Ubuntu tiling assistant, you can get a small border along the active window.

On the extension settings, scroll down to find “Active Window Hint” section. Here, select **Always** option.

![Active window hint is enabled][10]

As soon as you enable it, you can see a rectangular border appearing for the active window.

📋

It has several issues with Wayland and GTK 4 pop-ups. Also, the color is not changeable. Another major drawback was the rectangular shape, not aligning with the round design of windows. Still, it is useable.

### Want more tiling? Use Tiling Shell extension

Ubuntu’s default tiling manager has its limitations. If you are coming from any other tiling window manager, you may not find it lacking.

For such people, there is the [Tiling Shell extension][11].

🚧

Before installing the Tiling Shell, disable the Ubuntu Tiling Assistant.

![Disable Ubuntu Tiling Assistant Extension][12]

Now, you can install it either through the Extension Manager app, or through a browser.

![Install Tiling Shell Extension][13]

[Tiling Shell Extension][14]

Once installed and enabled, you can see an icon on the system tray, that lists some preset layout configurations. You can also create new layouts.

![Tiling Shell Tray Icon][15]

It's time to know it better.

#### Default tiling

When you enable the extension for the first time, you can drag a window by catching on the title bar. This will show you a small dropdown bar on the top. Drag to it to reveal the tiling layout. Place the window on top of any layout position to tile it there.

0:00

/0:07

1×

Drag and move to the top so that the tiling layouts are revealed.

The same can be done by pressing the CTRL key and dragging the windows. For this to work properly, first select the Tiling Shell tray icon and set the required layout.

![Select a layout from tray menu][16]

Now, CTRL and drag windows to place them in the layout position selected in the previous step.

#### Edit or create new layouts

To edit an existing layout, click on the “Edit Layout” button in tiling shell tray icon.

![Click on "Edit Layouts"][17]

This will give you a list of current layouts. Click on any existing layout to edit it. Or click on the “+” icon to create a new one.

![Edit an Existing layout or create a new one][18]

This will allow you to edit the layout. There are certain commands you need to remember. They are listed when you first enter editing.

![Click on Start Editing][19]

In case you missed the commands, here are those commands, refer to them when needed.

Command | Function
---|---
Left-click | Split a tile
Left-click + CTRL | Split vertically
Right-click | Delete a tile
Click the Tiling Shell Tray Icon | Save / Cancel changes

Once you have created a layout, or edited one, click on the Tiling shell tray icon and select the Save button to save the changes.

![Save or Cancel Changes][20]

This extension will now be available to access for you.

You can access the Tiling Shell settings from the extension manager, just like the Tiling Assistant. Click on the gear icon adjacent to the extension.

![Tiling Shell Extension Settings Gear][21]

This will open the settings for the Tiling Shell. Here you can tweak it to adjust window gaps and screen edge gap, along with some other tweaks.

![Tiling Assistant important settings.][22]

#### Export and import layouts for future use

This is a cool feature, where you can export a layout, that can be imported later. Open the Extension Manager and go to the Tiling Shell settings page. Scroll down to the bottom to the “Layouts” section.

Here, you need to click on the **Export** button to export the layouts to a file.

![Click on Export Layout][23]

It will ask you to give a name to the file. Name it and click on Save to save the layout export. The export will be a plain text file.

🚧

Name the exported layout file with extension file.json. It should be saved in JSON, otherwise, the import won’t work.

At a later stage, when you want to import the same layouts, click on the Import Layouts button.

![Click on Import Layouts][24]

This will show a file chooser. Select the exported layouts JSON file to import it.

### Wrapping Up

So, you saw the enhanced tiling feature of Ubuntu and learned the keyboard shortcuts to use it. You also learned that Ubuntu's enhanced tiling is quite basic but it can be further enhanced using the Tiling Assistant extension or using a different extension.

Of course, the experience is nowhere near what an actual tiling window manager provides. But [configuring a window manager like i3][25] is a pain in itself.

![][26]

This is why projects like Regolith exist to give you an out of the box tiling experience.

![][26]

I hope you find this helpful in your Ubuntu journey. Please let me know your views on tiling windows in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-tiling-windows/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/gnome-tiling-assistant/
[4]: https://itsfoss.com/content/images/2024/06/tiling-windos-ubuntu-settings.png
[5]: https://itsfoss.com/extension-manager/
[6]: https://extensions.gnome.org/extension/3733/tiling-assistant/
[7]: https://itsfoss.com/content/images/2024/06/click-on-the-settings-gear-icon-near-tiling-assistant-extension.png
[8]: https://itsfoss.com/content/images/2024/06/set-the-window-and-screen-edge-gap.png
[9]: https://itsfoss.com/content/images/2024/06/ubuntu-tiling-assitant-windows-gap.webp
[10]: https://itsfoss.com/content/images/2024/06/active-window-hint-enabled.png
[11]: https://github.com/domferr/tilingshell
[12]: https://itsfoss.com/content/images/2024/06/disable-ubuntu-tiling-assistant-extension.png
[13]: https://itsfoss.com/content/images/2024/06/install-tiling-shell-extension-1.webp
[14]: https://extensions.gnome.org/extension/7065/tiling-shell/
[15]: https://itsfoss.com/content/images/2024/06/tray-icon-for-tiling-shell.png
[16]: https://itsfoss.com/content/images/2024/06/select-a-layout-from-tray.png
[17]: https://itsfoss.com/content/images/2024/06/edit-a-layout.png
[18]: https://itsfoss.com/content/images/2024/06/edit-or-create-new-layout-1.png
[19]: https://itsfoss.com/content/images/2024/06/click-on-start-editing.png
[20]: https://itsfoss.com/content/images/2024/06/save-layout-after-chaging-it-1.png
[21]: https://itsfoss.com/content/images/2024/06/select-tiling-shell-extension-settings.png
[22]: https://itsfoss.com/content/images/2024/06/tiling-shell-extension-settings-page.png
[23]: https://itsfoss.com/content/images/2024/06/click-on-export-layout.png
[24]: https://itsfoss.com/content/images/2024/06/click-on-import-layout-1.png
[25]: https://itsfoss.com/i3-customization/
[26]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
