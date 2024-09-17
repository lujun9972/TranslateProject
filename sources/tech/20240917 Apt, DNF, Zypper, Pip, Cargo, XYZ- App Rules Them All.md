[#]: subject: "Apt, DNF, Zypper, Pip, Cargo, XYZ! App Rules Them All"
[#]: via: "https://itsfoss.com/app-package-manager/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Apt, DNF, Zypper, Pip, Cargo, XYZ! App Rules Them All
======

[![Warp Terminal][1]][2]

Managing packages in Linux distribution varies depending on the distribution. All the Debian-based distros use APT as the package management app. While Fedora uses DNF, openSUSE depends on Zypper package manager.

Recently, distro-agnostic [package managers][3] like Snap, Flatpak, AppImage, etc. made the scene even more fragmented.

More package managers mean more commands to get familiar with.

If that's what you feel as you [distrohop around the Linux-verse][4], I have a new app for you. It's called app 😬

[App][5], a cross-platform package management assistant written in Go, can help you in this scenario. Basically it is a wrapper for package managersand offers the same commands on all supported distributions. It means you don't need to memorize per-distro package management commands.

That's not it. The app keeps a record of installed applications in its config file. So, if you move distros, just use the previous config file to install the same packages in the new distro.

🚧

In my opinion, you should stick to the official package managers, specially if you are managing a critcal infrastructure. Don't experiment with such tools if you easily get overwhelmed and don't like to troubleshoot.

### Install App Package Management Assistant

The App provides an installation script, which you can install on any Linux distribution. Open a terminal and run the command below:

```

    bash <(curl -sL https://hkdb.github.io/app/getapp.sh)

```

![Install App Utility][6]

To update the app to the latest version, use:

```

    app -m app update

```

![Update App Utility][7]

### What happens behind the scene

App utility has its own simpler syntax. Since the utility uses the same syntax across distributions, you only need to remember the syntax of App utility.

When you install an app using the `app` command, it records the action. Be it an installation or removal of the package, the information is stored inside the `~/.config/app` directory.

Now, when you want to migrate to another distribution, you can copy this directory and paste it inside the `~/.config` folder of the new distribution to start installing packages. We will see the process in detail in the next section.

📋

For the App to work, you need to install the packages using the app command. Only then the package details are stored and restored on a new system.

### Basic App utility commands

Let's see some of the important commands you need to remember while using this tool.

#### Enable/Disable necessary package managers

By default, package managers like Flatpak, Snap, AppImage, Yay, Pip, Go, and Cargo are disabled.

You can enable them using the general syntax:

```

    app -m <package-manager> enable

```

For example, to enable Flatpak support,

```

    app -m flatpak enable

```

![Enable Flatpak Support][8]

To disable an enabled package manager, use the command:

```

    app -m <package-manager> disable

```

![Disable a Package Manager][9]

#### Search for packages

In order to search for packages using the App utility, do the following:

```

    app search <package-name>

```

![Search for packages in official repos][10]

To search for a package on another package manager like Flathub, specify the package manager.

```

    app -m <package-manager> search <package-name>

```

For example, if I am searching for Blackbox terminal emulator in Flatpak, I will run:

```

    app -m flatpak search blackbox

```

![Search packages in Flatpak Flathub][11]

#### Install a package

To install a package on your system, run the command:

```

    app install <package-name>

```

Let's say I want to install `fortune`. So I will run:

```

    app install fortune

```

![Install a package][12]

##### Install apps from other package manager

To install an app as a Flatpak, use the command:

```

    app -m flatpak install <package-name>

```

![Install a Flatpak package][13]

This is a general formula, so, we can install packages from other package managers using:

```

    app -m <package-manager> install <package-name>

```

##### Install an AppImage

First go to the directory where the AppImage file is downloaded. Now, to install the AppImage file:

```

    app -m appimage install <appimage-file-name>

```

I have an AppImage of Standard Notes app. So, I will open my Downloads directory in a terminal and run:

```

    app -m appimage install standard-notes-3.195.1-linux-x86_64.AppImage

```

![Install an AppImage File][14]

On the official page, you have a detailed description of all package managers that are supported and respective installation methods.

💡

The project has a neat [documentation on installing apps like Brave browser][15], that needs its own repo configuration.

#### List installed packages

You can list the packages that were installed using App from official repos by using the command:

```

    app history

```

Similarly, to list all the installed packages from a particular repository, run:

```

    app -m <package-manager> history

```

![App install history][16]

#### Remove a package

To remove a package, you can use:

```

    app remove <package-name>

```

![Remove a Package][17]

For other package managers, use:

```

    app -m <package-manager> remove <package-name>

```

![Remove a Flatpak Package][18]

If you are on a Debian-based distribution, you can use `purge` as well.

```

    app purge <package-name>

```

Similarly, `App` supports `autoremove` for native package managers.

```

    app autoremove

```

#### Upgrade packages

To upgrade all the packages installed on the system, use the command:

```

    app update
    app upgrade all

```

At the same time, the App allows individual package manager upgrades as well. For this, use the syntax:

```

    app -m <package-manager> upgrade

```

#### Add PPA in Ubuntu

In an Ubuntu-based system, you can [use PPA][19] to install additional packages that are not available in the [native Ubuntu repositories][20] or there are old versions available in the repos.

So, if you are using the App for installing packages, you need to use the syntax:

```

    app add-repo ppa:graphics-drivers/ppa

```

### Restoring the packages in another distro

🚧

While restoring packages in cross-platform, not all platforms have the same package names.

Now, when you want to hop to a new distro, or want to replicate the current distribution, all you need to do is described below.

📋

You need to set up the extra package managers like Flatpak, Snap, etc. before starts restoring.

First, install the App utility on the new system, as mentioned in the first section.

Now, copy the `~/.config/app` directory to the new system. Then open a terminal and run:

```

    app -r all

```

That's it. Your packages will be installed on the new system.

🚧

Restoring Flatpak apps on a new system asked me to select an app from a huge list. So, when I inspected its `~/.config/app/packages/flatpak.json` file, there was an additional space present on the beginning of the line.
I removed that space and rerun the command to restore Flatpak apps successfully.

You can restore individual package managers separately by using the command:

```

    app -r <package-manager>

```

### Conclusion

This seems like a useful tool if you distrohop quite often. You can get the list of the packages you install regularly and you can install them with less effort on a new system.

There are a few tools like [Nala][21] that try to provide similar features.

By the way, we are also offering Linux courses through our other portal. Something you might be interested in.

![][22]

--------------------------------------------------------------------------------

via: https://itsfoss.com/app-package-manager/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/package-manager/
[4]: https://itsfoss.com/distrohopping-issues/
[5]: https://github.com/hkdb/app
[6]: https://itsfoss.com/content/images/2024/08/install-app-package-management-assistant.gif
[7]: https://itsfoss.com/content/images/2024/08/update-app-utility.gif
[8]: https://itsfoss.com/content/images/2024/08/enable-a-package-manager-app.gif
[9]: https://itsfoss.com/content/images/2024/08/disable-a-package-manager-app.gif
[10]: https://itsfoss.com/content/images/2024/08/search-for-package-from-official-repo.gif
[11]: https://itsfoss.com/content/images/2024/08/search-for-package-from-flathub.gif
[12]: https://itsfoss.com/content/images/2024/08/install-an-app-using-app.gif
[13]: https://itsfoss.com/content/images/2024/08/install-a-flatpak-using-app-utility.gif
[14]: https://itsfoss.com/content/images/2024/08/install-an-appimage-file.gif
[15]: https://github.com/hkdb/app/blob/main/docs/EXAMPLES.md#example-2--lets-use-the-brave-browser-for-example
[16]: https://itsfoss.com/content/images/2024/08/get-app-install-history.gif
[17]: https://itsfoss.com/content/images/2024/08/remove-a-package.gif
[18]: https://itsfoss.com/content/images/2024/08/remove-a-flatpak-app.gif
[19]: https://itsfoss.com/ppa-guide/
[20]: https://itsfoss.com/ubuntu-repositories/
[21]: https://itsfoss.com/nala/
[22]: https://itsfoss.com/content/images/icon/cropped-lhb-courses-favicon-270x270.png
