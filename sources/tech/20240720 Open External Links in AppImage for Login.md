[#]: subject: "Open External Links in AppImage for Login"
[#]: via: "https://itsfoss.com/appimage-open-external-links/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Open External Links in AppImage for Login
======

[![Warp Terminal][1]][2]

AppImage is a popular packaging format for Linux systems. You'll often find applications packaged in this format.

Sometimes, when you try to log in to a service’s AppImage through a browser, even though it will report a success and tell you to go back to the app, it actually won’t.

Let me share a quick tip on how to force open external links in AppImage so that you can log into it through a browser.

### Make AppImage open external links

Here, I am using an AppImage for [Todoist][3] that needs you to log in through the browser.

First, open the app and click on login through the browser button.

![Click on Login via browser][4]

When it asks you to login, enter the credentials and log in.

💡

Use Firefox, as that will provide more options for opening external links.

![Login through Web Browser][5]

Once you successfully log in, it will ask you to open the app in an external app.

![Choose a different Application][6]

If your System Handler finds the proper app, then there is no issue. If you want to open it in another app of your choice, click on “Choose a different application” link.

Now, click on “Choose” button.

![Click on Choose][7]

This will bring you to the file chooser. Select the AppImage of your choice, in this case, Todoist, to open that particular link.

![Locate the AppImage][8]

Click on Select. Once selected, press “Open Link” to open it in the AppImage.

![Click on Open Link button][9]

That's it. You can see the AppImage will be now logged in.

Please note that this is a very specific scenario and you'll encounter it with very few applications.

I hope this quick tip helps you. Please let me know if you have questions or suggestions in the comments.

--------------------------------------------------------------------------------

via: https://itsfoss.com/appimage-open-external-links/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://todoist.com/
[4]: https://itsfoss.com/content/images/2023/10/1-click-on-login-via-browser.png
[5]: https://itsfoss.com/content/images/2023/10/2-click-on-login-button.png
[6]: https://itsfoss.com/content/images/2023/10/3-click-on-chose-different-application.png
[7]: https://itsfoss.com/content/images/2023/10/4-click-on-chose-to-open-file-browser-1.png
[8]: https://itsfoss.com/content/images/2023/10/5-select-appimage.png
[9]: https://itsfoss.com/content/images/2023/10/6-open-link-1.png
