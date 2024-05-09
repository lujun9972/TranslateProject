[#]: subject: "Things I Recommend Doing After Installing Ubuntu 24.04 LTS 'Noble Numbat'"
[#]: via: "https://itsfoss.com/things-to-do-after-installing-ubuntu-24-04/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Things I Recommend Doing After Installing Ubuntu 24.04 LTS 'Noble Numbat'
======

[![Warp Terminal][1]][2]

So, you have installed or upgraded to Ubuntu 24.04 LTS. That's wonderful!

It is a fantastic release with a bunch of good things (and some hiccups). You can read our [Ubuntu 24.04 LTS review][3] if you are still deciding, or just want to know what I think about the release.

Sure, the latest Ubuntu release improves on the usability front and makes the experience easier than ever before.

However, there are still a few things that you can do to enhance your experience. We have categorized them so you can do what you prioritize.

### Setting Up

These are things that you should choose to do for a better experience managing software packages.

#### 1\. Perform a system update

![][4]

Yes, you just installed a new operating system (or an upgrade).

But, often, with these big releases, you might find important security or bug fixes waiting to be installed right after its release.

So, before you encounter an annoyance and start complaining about it, run the “ **Software Updater** ” and apply available updates.

#### 2\. Install essential applications

The default mode for Ubuntu 24.04 LTS is a minimal installation, where you only get the basic utilities pre-installed.

![][5]

There is a chance that you went with the defaults without thinking much.

In a way, it is a good bloatware-free experience. But, you might feel that you lack certain apps you need.

If that is the case, you can explore [essential Linux apps][6] and get them installed through any of your favorite sources (Flathub, Snap, Debian package or AppImage).

![][7]

#### 3\. Get Flatpak support

Canonical's Ubuntu naturally encourages you to use Snap packages. However, you should know that there is another impressive source for getting your software, i.e., [Flathub][8].

To get Flatpak packages from Flathub. You need to install Flatpak on your Ubuntu system.

**Not sure if you require Flatpak apps?** Learn the differences between [Flatpak vs. Snap][9] and then decide for yourself.

You can follow our [Flatpak installation guide][10] to get it installed:

![][7]

#### 4\. Handle deb files

With Ubuntu 22.04 LTS, you can install .deb packages by opening them with " **Software Install** " or the software center. It is a GUI method.

![][11]

Unfortunately, with Ubuntu 24.04 LTS, I failed to open/install a .deb package using the new App Center.

![][12]

So, it becomes an inconvenience if you like to install .deb packages.

Hence, you can choose to [install GDebi on Ubuntu][13] or [Eddy debian package manager][14].

![][7]

With GDebi, you can configure to install .deb files with a double click, saving you all the time in the world 😉

By the way, you cannot see the apps installed from local deb files on the Ubuntu App Center.

So, how do you manage them? You can manage these packages by install the good-old [Synaptic package manager][15] to easily manage software.

![][7]

#### 5\. Get AppImage support

Sooner or later, you'll come across some interesting new application that is only available in the [AppImage format][16].

But to run an AppImage file, you need to install FUSE lib with the following command first:

```

    sudo apt install libfuse2t64

```

#### 6\. Install media codecs to play various kinds of media files

To play media files like MP3, MPEG4, AVI, etc, you will need to install media codecs, if you missed doing that in the installation setup.

Ubuntu doesn’t install it by default because of copyright issues in various countries.

You can install these media codecs as an individual [using the Ubuntu Restricted Extra package][17]. It installs media codecs and [Microsoft True Type Fonts on your Ubuntu system][18].

You can install it by using this command:

```

    sudo apt install ubuntu-restricted-extras

```

If you encounter the EULA or the license screen, remember to use the tab key to select between the options and then hit enter to confirm your choice.

![][19]

### Customization tips

Ubuntu 24.04 LTS is easy to use. But you can make the experience snappier with some of these things:

#### 7\. Minimize to click

When you click an icon in the launcher, it opens the application. But, you cannot minimize it by clicking it again.

I don’t like this. And, if you agree, you can do something about it.

Use this command in the terminal to [enable minimize on click in Ubuntu][20]:

```

    gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'

```

#### 8\. Experiment with the dock

Go to the **Ubuntu Desktop** settings, and you shall notice the option for disabling Panel mode:

![][21]

This will shrink the launcher on the left side and make it look like the Vanilla GNOME launcher. You should use it with ‘auto-hide’ option for a nicer effect.

You may [move the launcher to the bottom][22] or the right side if you like. There are plenty of [ways to customize the dock in Ubuntu][23].

#### 9\. Get GNOME Tweaks tool for additional customization

Though the system settings application now includes several new options, [GNOME Tweaks still provides additional customization options][24].

With GNOME Tweaks, you can move the windows control button to the left, change themes, change the lock screen background, etc. More on its usage later. For the moment, just get this tool from the software center or use the apt command.

![GNOME Tweaks Tool][25]

#### 10\. Tweak date Info with Nautilus

With GNOME 46, you can get a detailed info on the date of a file/folder if you are using the list view.

![][26]

You can enable this setting through the preference menu in the file manager as shown above.

#### 11\. Enable fractional scaling if you’ve got a 4K screen

If you have a 2K or 4K screen, you’ll find that the icons, fonts, and folders look too small. You should enable the fractional scaling and scale the size that suits your preference.

![][27]

I'll be adding more tips as I discover new things and issues while using Ubuntu 24.04 LTS as my daily driver. Stay tuned for it.

Meanwhile, why don't you share you favorite tweaks in the comment section?

--------------------------------------------------------------------------------

via: https://itsfoss.com/things-to-do-after-installing-ubuntu-24-04/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/ubuntu-24-04-lts-review
[4]: https://itsfoss.com/content/images/2024/04/ubuntu-24-04software-updater-1.png
[5]: https://itsfoss.com/content/images/2024/04/ubuntu-24-default-selection.png
[6]: https://itsfoss.com/essential-linux-applications/
[7]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[8]: https://flathub.org/
[9]: https://itsfoss.com/flatpak-vs-snap/
[10]: https://itsfoss.com/flatpak-ubuntu/
[11]: https://itsfoss.com/content/images/2024/04/ubuntu-22-04-debian.png
[12]: https://itsfoss.com/content/images/2024/04/ubuntu-24-04-debian-open.png
[13]: https://itsfoss.com/gdebi-default-ubuntu-software-center/
[14]: https://github.com/donadigo/eddy
[15]: https://itsfoss.com/synaptic-package-manager/
[16]: https://itsfoss.com/use-appimage-linux/
[17]: https://itsfoss.com/install-media-codecs-ubuntu/
[18]: https://itsfoss.com/install-microsoft-fonts-ubuntu/
[19]: https://itsfoss.com/content/images/2024/04/ubuntu-24-04-media-codecs.png
[20]: https://itsfoss.com/click-to-minimize-ubuntu/
[21]: https://itsfoss.com/content/images/2024/04/ubuntu-desktop-dock-1.png
[22]: https://itsfoss.com/move-unity-launcher-bottom/
[23]: https://itsfoss.com/customize-ubuntu-dock/
[24]: https://itsfoss.com/gnome-tweak-tool/
[25]: https://itsfoss.com/content/images/2024/04/ubuntu-gnome-tweaks.png
[26]: https://itsfoss.com/content/images/2024/04/ubuntu-detailed-date-view.png
[27]: https://itsfoss.com/content/images/2024/04/ubuntu-fractional-scaling.png
