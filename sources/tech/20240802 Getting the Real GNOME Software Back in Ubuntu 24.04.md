[#]: subject: "Getting the Real GNOME Software Back in Ubuntu 24.04"
[#]: via: "https://itsfoss.com/ubuntu-gnome-software-center/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Getting the Real GNOME Software Back in Ubuntu 24.04
======

[![Warp Terminal][1]][2]

Though Ubuntu uses a customized version of the GNOME desktop environment, it doesn't use the GNOME Software Center application.

Ubuntu has its own 'App Center' application that is focused on Snap packages. It gives priority to Snaps over Deb and doesn't support Flatpak integration as far as I know.

And I don't like that. I feel more at home with the original GNOME Software center.

The good thing is that it is quite simple to get the OG Software Center back on Ubuntu. I'll show you how in this tutorial.

### Install GNOME Software in Ubuntu

[GNOME Software][3] package is available in the default repositories of Ubuntu. So, you can simply install it using the command:

```

    sudo apt install gnome-software --install-suggests

```

The `--install-suggests` option makes sure that the **Flatpak plugins and other suggested packages** are also installed.

![Install and Install Suggests option][4]

💡

To install and work with Flatpak applications in Ubuntu, you should have [Flatpak support enabled][5].

You have now installed the GNOME Software app. For now, there will be two software applications, a Snap-focussed App Center and the GNOME Software.

![App Center and GNOME Software][6]

If you didn't use the `--install-suggests` option during installation, you should install the `gnome-software-plugin-flatpak` package separately to manage Flatpak apps. So, just run:

```

    sudo apt install gnome-software-plugin-flatpak

```

The Snap plugin will be automatically installed while installing GNOME Software.

You can reboot your system to make changes effective.

### Install some applications

It's time to install some applications using the GNOME software. Open the GNOME software app and click on the search button on the top-left.

![Search for an application][7]

Select the application name to get more details about that app.

![Install an Application][8]

Click on the repository button to get more repository suggestions. It means you can install an app as Flatpak, Snap, Deb, etc. right from the software center app.

#### Remove an installed application

Click on the “Installed” tab in GNOME Software and select the app, that you want to uninstall.

![Uninstall an App][9]

If you are removing a Flatpak application, it will ask to keep/delete the data along with it. If deleted, the data won't be retained on reinstallation.

![Keep/Delete Data][10]

### Make GNOME Software the default choice for deb files

Let's take your preference for GNOME Software to the next level by making it the default application for opening deb files.

First, open the location where you have downloaded the Deb file. Now, right-click on it and select “Open With”.

![Open a deb file with another app][11]

On the suggested apps, select “Software Install”. Do not forget to enable the “Always use this for file type” toggle button. This way, the future deb files can be opened in the software center by just double-clicking.

![Open the deb file with Software Install][12]

The file will now be opened in the GNOME Software, and you can install it using the “Install” button.

![Install the deb file using the GNOME Software app][13]

### Wrapping Up

GNOME Software is a comprehensive tool for managing all the package formats in Ubuntu. It also provides a convenient method for updating both system software and user-installed software.

I prefer it over the Snap Store and hence I installed it in my Ubuntu system. I thought perhaps some of you would be interested in it as well and hence wrote this quick tutorial.

💭 So, GNOME Software Center or Ubuntu's App Center (Snap Store)? Which one do you prefer? Please share it in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ubuntu-gnome-software-center/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://apps.gnome.org/en-GB/Software/
[4]: https://itsfoss.com/content/images/2024/06/install-and-install-suggests.png
[5]: https://itsfoss.com/flatpak-ubuntu/
[6]: https://itsfoss.com/content/images/2024/06/app-center-and-GNOME-software.png
[7]: https://itsfoss.com/content/images/2024/06/search-for-an-application-in-gnome-software.png
[8]: https://itsfoss.com/content/images/2024/06/install-an-app-from-any-selected-repository.webp
[9]: https://itsfoss.com/content/images/2024/06/Uninstall-an-app.png
[10]: https://itsfoss.com/content/images/2024/06/remove-a-flatpak-app-asks-data-deletion.png
[11]: https://itsfoss.com/content/images/2024/06/open-a-deb-file-with.png
[12]: https://itsfoss.com/content/images/2024/06/open-in-software-install.png
[13]: https://itsfoss.com/content/images/2024/06/install-the-deb-file-using-gnome-software.png
