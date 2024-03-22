[#]: subject: "Change Default Web Browser in Ubuntu [Beginner's Tip]"
[#]: via: "https://itsfoss.com/ubuntu-change-browser/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Change Default Web Browser in Ubuntu [Beginner's Tip]
======

[![Warp Terminal][1]][2]

So you found yourself a perfect browser that you always wanted and now, you want to make it your default browser?

But the question is: **how do you change your default web browser on Ubuntu?**

Let us find out how to do that!

### Changing the default web browser on Ubuntu and other Linux

Here, I will be sharing two ways to change your default browser to make it more accessible:

  1. **Using GUI (easy and recommended)**
  2. **Using the terminal (only works with the Xorg session)**



🚧

To switch to another browser, you need to have other browsers installed on your system. For example, [install Chrome on Ubuntu][3] first and then make it default (if you want to).

#### Use GUI to change the default browser

By far, this is the easiest way to change your default browser, and there's a reason why.

Unlike the other method, it works with Wayland and Xorg desktop session. So regardless of what [display server][4] you are running, you can change your browser using this method.

The steps are similar for most desktop environments. Here, I give you pointers for GNOME, KDE Plasma, and Xfce:

**For GNOME**

If you're using the default offering of Ubuntu, it runs GNOME. To change the default browser on GNOME, here's what you have to do:

Search for the `default applications` in the search menu and open the first search result:

![][5]

It will bring the list of every default app configured for your system. From here, you can change your default browser:

![][6]

**For KDE Plasma:**

If you are using KDE, then the steps to change your default browser are just about similar to GNOME and can be done in two simple steps:

  1. Search for `default applications` in the application menu and choose the first result.
  2. Next, select your preferred default browser from the given options.



![][7]

**For Xfce:**

If you are using Xfce desktop, open the `default applications` from the app menu.

In the `Internet` section, you will see the option to configure the default web browser:

![][8]

**Suggested Read 📖**

![][9]

#### Use the terminal to change the default browser (Xorg only)

If you're using the Xorg display server and want to change your default web browser, you can use the `xdg-settings` command.

The first step is to find the `.desktop` file for your next default browser. For that purpose, [use the ls command][10] in the following manner:

```

    ls /usr/share/applications/

```

![][11]

It will bring a long list of desktop files. Sure, you can scroll through the output and find the name of your browser, but that's a hassle.

You can pipe the previous command with [the grep command][12] to filter the output as per your needs:

```

    ls /usr/share/applications/ | grep -w "browser-name"

```

For example, I'm looking for the Microsoft Edge browser, so my command would look like this:

```

    ls /usr/share/applications/ | grep -w "edge"

```

![][13]

Once you find the desktop file for the target browser, copy the output and save it somewhere (using [note-taking apps][14], or the default text editor) as you'll be using it shortly.

Next, use the `xdg-settings` command by appending the desktop file of your target web browser (output of the previous command) as shown here:

```

    xdg-settings set default-web-browser <browser-name.desktop>

```

For example, I want Microsoft Edge to be my next default web browser, so I will be using the following:

```

    xdg-settings set default-web-browser microsoft-edge.desktop

```

![][15]

That's it!

### Want browser suggestions?

Here are some of the [best browsers for Ubuntu][16] 👇

![][9]

If you are cautious about your online privacy, I suggest you switch your regular browser to a privacy-focused one.

Here's a list of [the best privacy-focused browsers][17]:

![][9]

Want something unusual? Explore these.

![][9]

_💬 I hope you will find this tutorial helpful. What do you like to keep as your default web browser? Let me know in the comments below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-change-browser/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/install-chrome-ubuntu/
[4]: https://itsfoss.com/display-server/
[5]: https://itsfoss.com/content/images/2024/03/Seach-for-the-default-applications-in-the-application-menu.png
[6]: https://itsfoss.com/content/images/2024/03/change-the-default-browser-in-Ubuntu-Linux.png
[7]: https://itsfoss.com/content/images/2024/03/Change-default-browser-in-KDE.png
[8]: https://itsfoss.com/content/images/2024/03/Change-the-default-browser-in-Xfce.png
[9]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[10]: https://itsfoss.com/ls-command/
[11]: https://itsfoss.com/content/images/2024/03/List-desktop-files-to-change-the-default-web-browser-in-linux.png
[12]: https://itsfoss.com/grep-command/
[13]: https://itsfoss.com/content/images/2024/03/Find-the-desktop-file-for-the-browser-you-want-to-be-your-next-default-browser.png
[14]: https://itsfoss.com/note-taking-apps-linux/
[15]: https://itsfoss.com/content/images/2024/03/Change-the-default-web-browser-in-Linux-using-the-terminal.png
[16]: https://itsfoss.com/best-browsers-ubuntu-linux/
[17]: https://itsfoss.com/privacy-web-browsers/
