[#]: subject: "Set an AppImage Application as Default App"
[#]: via: "https://itsfoss.com/set-appimage-as-default/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Set an AppImage Application as Default App
======

[![Warp Terminal][1]][2]

Imagine you found a cool text editor like [Pulsar][3] and downloaded it in the [AppImage format][4]. You enjoy using it and now want to make it the default application for markdown files.

You right-click on the file and click 'open with' option, but here, you don't see the Pulsar listed here.

That's a problem, right? But it can be easily fixed by creating a desktop entry for that AppImage application.

Let me show you how to do that.

### Step 1: Create a desktop entry for AppImage

The very first step is to create a desktop file for the AppImage application. Here, we will use the [Gear Lever][5] app to create the desktop entry.

Gear Lever is [available as a Flatpak package][6] from [FlatHub][7]. I know. Another package format, but that's how it is.

Anyway, if you have Flatpak support enabled, install Gear Lever with this command:

```

    flatpak install flathub it.mijorus.gearlever

```

Now, right-click on the AppImage file you downloaded and select **Open With Gear Lever**.

![Open AppImage in Gear Lever][8]

Click on the Unlock button in Gear Lever.

![Click on Unlock][9]

Now click on the " **Move to app menu"** button.

![Click on the "Move to the app menu" button][10]

Verify everything is ok by searching for the app in the system menu.

![Verify the app integration][11]

Great! So we have the application integrated in the desktop. Let's move to the second step.

### Step 2: Setting default app through file manager

Let's say you want to open all your .txt text files in the Pulsar editor.

The easiest way to achieve is through the File Manager.

Open the file manager and right-click on the file of your choice. Now select the **Open With** option.

![Select the "Open With" option][12]

In the next window, you can start typing the name of the application to begin a search. It will also show you the AppImage program you integrated with the desktop previously.

![Search for an App][13]

Once you spot the app, click on it to select and then enable the " **Always use for this file type** " toggle button. Then click **Open** as shown in the screenshot below.

![Set a default app][14]

That's it. From now on, your file will be opened in the AppImage of your choice. To verify this, you can right-click on the file. The first entry on the context menu will be the name of your AppImage application. In this case, Pulsar.

![First item in the context menu][15]

### Alternative method: Change apps from settings

Let's say you have an AppImage for applications like Web Browser, Music Player, etc. These can be changed from the system settings.

Given you have created the AppImage desktop entry following the first step, open the system settings in Ubuntu.

Go to Apps → Default Apps.

Here, set the apps for categories you want.

![Set Default Browser][16]

If you click on the drop-down menu corresponding to a category in settings, you can select an app. The AppImage app will also be listed here. In the screenshot above, you can see Vivaldi AppImage is set as the default browser.

For Linux Mint users, you can set it using the Preferred Application settings.

![Preferred application in Linux Mint][17]

### Conclusion

A lot of AppImage 'issue' or should I say shortcomings, can be solved by desktop integration. It surprises me that AppImage doesn't provide an official way of doing these things.

Well, we have the wonderful open source developers that help us by creating helpful utilities like [Gear Lever][18] here.

I hope this quick little tip helps you enjoy your AppImages 😄

--------------------------------------------------------------------------------

via: https://itsfoss.com/set-appimage-as-default/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://news.itsfoss.com/pulsar-editor/
[4]: https://itsfoss.com/use-appimage-linux/
[5]: https://news.itsfoss.com/gear-lever/
[6]: https://itsfoss.com/flatpak-guide/
[7]: https://flathub.org/
[8]: https://itsfoss.com/content/images/2025/03/open-appimage-with-gear-lever-app.png
[9]: https://itsfoss.com/content/images/2025/03/unlock-the-appimage-file-in-gear-lever.png
[10]: https://itsfoss.com/content/images/2025/03/click-on-move-to-app-menu-button.png
[11]: https://itsfoss.com/content/images/2025/03/verify-by-searching-in-the-menu-1.png
[12]: https://itsfoss.com/content/images/2025/03/select-open-with-from-context-menu.png
[13]: https://itsfoss.com/content/images/2025/03/search-for-an-app.png
[14]: https://itsfoss.com/content/images/2025/03/select-an-app-toggle-and-open.png
[15]: https://itsfoss.com/content/images/2025/03/open-with-pulsar.png
[16]: https://itsfoss.com/content/images/2025/03/set-browser-appimage-as-default.png
[17]: https://itsfoss.com/content/images/2025/03/preferred-application-in-mint.png
[18]: https://flathub.org/apps/it.mijorus.gearlever
