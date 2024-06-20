[#]: subject: "Fixing Applications Icon Missing from the Launcher in Ubuntu"
[#]: via: "https://itsfoss.com/ubuntu-app-icon-missing/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fixing Applications Icon Missing from the Launcher in Ubuntu
======

[![Warp Terminal][1]][2]

Recently I encountered a strange issue in Ubuntu 24.04.

When I ran some applications, their icons didn't show in the launcher. Instead, it displayed a gear/settings symbol.

![Some application icons are not shown in the launcher][3]

This was particularly weird because those applications did have icons and the thumbnails were very well displayed in the activity area.

![But the application icons are properly displayed in GNOME Activity][4]

Even more surprising was that it happened with the Transmission torrent client that comes preinstalled with Ubuntu.

In this tutorial, I'll share how I fixed this missing icon issue. But before that, let me discuss what was wrong here.

🚧

This tutorial is only valid for the GNOME desktop environment.

### The missing element mystery

Alright! Here's the thing. Every application you install should have a .desktop file that has various information, including the location of the application icon.

This .desktop file is essential for the desktop integration. Without it, you won't be able to search for the installed application in the menu, the thumbnail and icons won't be displayed.

But in my case, both ONLYOFFICE and Transmission had their desktop files in the `/usr/share/applications` directory. I even made sure that the icon image file was present.

It baffled me and I started going through GitHub and forum discussions. This is when I came across [this discussion about missing WM_CLASS property][5] in some KDE applications that caused this issue.

The applications I was using were not from KDE but this was a step in the right direction. [This blog post][6] confirmed my views.

📋

****TLDR****

You need to get the WM_CLASS property and update the .desktop file of the application with this value.

### Fixing the missing application icons from the launcher issue

✋

While I am trying to go in every step in detail, it still involves some effort on your end. This is not run-this-command to fix the issue kind of solution. You have to take my examples as a reference and use them in your scenario. Basic knowledge of the Linux command line is required.

#### Step 0: Run the applications in question

You'll have to run the applications that have missing icons. It is essential.

#### Step 1:

All this is a tad bit easier if you are using Xorg instead of Wayland. Run `xprop WM_CLASS` command in terminal, the cursor becomes crosshair and you click on the desired application to get its WM_CLASS property.

But that is not happening here in Wayland, so let's take the longer route.

Press Alt + F2 to launch “Run a Command” dialog. Your keyboard should have a F2 function key. Look for it. Sometimes they need to run in Fn+2 way. I let you discover that.

Pressing Alt + F2 launches a dialogue box. Enter `lg` (lowercase LG) here:

![][7]

It will bring up GNOME’s integrated debugger and inspector tool. Your mouse and keyboard has limited function at this stage. Here, click on the Window option and it will show the WM_CLASS property for each running application Window.

![Click to expand if not visible properly][8]

Note that copy-paste didn't work for me at this stage. I took a screenshot for reference.

Press Esc to close the debugger.

#### Step 2: Edit .desktop file

📋

If you don't have much experience editing config files such as these, make a backup copy of the .desktop file before modifying it.

The next step is to edit the application's .desktop file. You should find it in the `/usr/share/applications` directory. If it's not there, you may try looking for it in `~/.local/share/applications` and `/var/lib/flatpak/exports/share/applications/` locations as well.

Now, you can use Nano to edit files in the terminal. This is the example for me:

```

    sudo nano /usr/share/applications/onlyoffice-desktopeditors.desktop

```

**But if you are uncomfortable with that, you can also do it graphically**. Just go to the location of your application's .desktop file.

In the file manager, You can click Other Locations and then Ubuntu to access the root directory.

![][9]

From there, you can go to the user->share->applications folder. You could also just enter /usr/share/applications in the address bar of the file manager and access it quickly.

In here, **under the [Desktop Entry] section** , add a line

```

    StartupWMClass=Value-you-got-in-previous-step

```

![][10]

Save the file. You'll have to enter your account password to save the file.

And the effect is almost immediate. No need to reboot or even log out. The icons get displayed in the launcher almost as soon as you save the file.

![][11]

I experienced that you have limited mouse and keyboard control at this time. The WM Class text could not be copied. So, I took a screenshot and used that screenshot as a reference to see the value and manually type it in.

### Conclusion

It's good to get the missing icons back. It took some effort, but it taught me a few new things in the process. That's what I like about troubleshooting. It teaches you stuff that you would have never known otherwise.

Not sure if I should blame Ubuntu or GNOME. But this is a poor user experience specially when you encounter it with applications that are installed by default.

🗨️ I hope the tutorial is not overly complicated. Did it help you fix the missing icons problem in Ubuntu?

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-app-icon-missing/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/06/missing-icons-from-launcher-ubuntu.webp
[4]: https://itsfoss.com/content/images/2024/06/applications-icons-displayed-in-gnome-activity-menu.webp
[5]: https://askubuntu.com/questions/1251172/active-application-icon-not-shown-on-dock
[6]: https://ubuntuhandbook.org/index.php/2024/04/missing-icon-dock-ubuntu-2404/
[7]: https://itsfoss.com/content/images/2024/06/bring-debug-mode-gnome.webp
[8]: https://itsfoss.com/content/images/2024/06/get-wm-class-property-gnome.webp
[9]: https://itsfoss.com/content/images/2024/06/access-root-directory-ubuntu.webp
[10]: https://itsfoss.com/content/images/2024/06/editing-deskto-file.webp
[11]: https://itsfoss.com/content/images/2024/06/missing-application-icon-fixed-ubuntu.webp
