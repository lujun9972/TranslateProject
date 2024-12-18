[#]: subject: "Use Zoom In and Out While Recording in OBS Studio"
[#]: via: "https://itsfoss.com/obs-zoom/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Use Zoom In and Out While Recording in OBS Studio
======

[![Warp Terminal][1]][2]

Have you ever wanted to **zoom the screen recording area to where your cursor currently is**? OBS can do it for you with the help of third-party scripts. You don't need a [dedicated video editor in Linux][3] just for zooming into an area.

Before starting this guide, let's make sure you have [OBS Studio installed][4] on your system.

### Step 1: Download Zoom to Mouse Lua script

Now that you have installed and set [OBS Studio][5], let's see how to set the Zoom to mouse feature. First, you need to download the “Zoom to Mouse” Lua script.

Use the link below to go to the GitHub repository of the project.

[OBS Zoom to Mouse][6]

In this repository, click on the `obs-zoom-to-mouse.lua` Lua script file link.

![Click on Lua Script file][7]

On the code page, click on the download button available on the top-right.

![Click on the Download Button][8]

📋

You can also use the [releases section][9] to get the file.

### Step 2: Install the lua script in OBS

Open OBS Studio and select Tools → Scripts.

![Click on Tools → Scripts][10]

In the scripts window, click on the “+” button in the bottom-left, as shown below.

![Click “+” to add Script][11]

This will open a file chooser, where you can see the location of the scripts. For me, it is `/usr/share/obs/obs-plugins/frontend-tools/scripts`.

🚧

This location may vary according to the OBS Studio installation method (deb, snap, flatpak etc_. Replace the location according to your method of installation.

You need to copy the downloaded Lua script file to this location.

For this, open a terminal. Now, assuming you have downloaded the Lua script to the `~/Downloads` directory, use the command:

```

    sudo cp ~/Downloads/obs-zoom-to-mouse.lua /usr/share/obs/obs-plugins/frontend-tools/scripts

```

Now, you can see this script appear in the Scripts dialog we have opened earlier. Click on it and select Open.

![Select and Open the Lua Script File in OBS Studio][12]

This will open the script settings. Here, you need to select a **Zoom Source**. This **should be the same as the screen capture source**.

![Zoom to mouse settings][13]

You can go through the rest of the settings for further tweaks.

### Step 3: Set a hotkey for Zoom

Now that you have installed the Zoom to Mouse script, you should set a hotkey for this action. Otherwise, it will be difficult to access this feature.

On the main menu of OBS Studio, click on File → Settings.

![Click on File → Settings][14]

In the settings window, go to **Hotkeys**. Here, scroll down a bit to get the **Toggle zoom to mouse** and **Toggle follow mouse during zoom** shortcuts.

  * **Toggle zoom to mouse** : Toggle between zoom and normal views.
  * **Toggle follow mouse during zoom** : Decides whether the zoom follows the cursor, or lock in the current position. If locked, the other part of the video won't be visible if the cursor is out of the zoomed location.



In the field corresponding to these options, press your required shortcuts.

![Set a Hotkey][15]

🚧

You should not be adding hotkeys that have other preset values in the system. For example, setting a key like __CTRL A__ will cause issue since this is the shortcut to select all items in the supported windows. Use some obscure shortcut which is not common.

Once set, click on Apply and close the settings windows. Now restart the OBS Studio and enjoy zooming in and out.

Enjoy [OBS Studio for screen recording in Linux][16].

--------------------------------------------------------------------------------

via: https://itsfoss.com/obs-zoom/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/best-video-editing-software-linux/
[4]: https://itsfoss.com/install-obs-ubuntu/
[5]: https://obsproject.com/
[6]: https://github.com/BlankSourceCode/obs-zoom-to-mouse
[7]: https://itsfoss.com/content/images/2024/12/click-on-the-lua-script-file.png
[8]: https://itsfoss.com/content/images/2024/12/click-on-the-download-button-to-download-the-script.png
[9]: https://github.com/BlankSourceCode/obs-zoom-to-mouse/releases
[10]: https://itsfoss.com/content/images/2024/12/obs-click-on-tools-and-then-scripts.png
[11]: https://itsfoss.com/content/images/2024/12/click-on-the-plus-button-to-load-a-script-from-file.png
[12]: https://itsfoss.com/content/images/2024/12/open-the-copied-lua-script-file-in-obs-scripts.png
[13]: https://itsfoss.com/content/images/2024/12/set-zoom-script-settings.png
[14]: https://itsfoss.com/content/images/2024/12/click-on-file-and-then-settings-in-obs.png
[15]: https://itsfoss.com/content/images/2024/12/set-a-hotkey-to-zoom-to-mouse-in-obs-studio.png
[16]: https://itsfoss.com/screen-record-obs-wayland/
