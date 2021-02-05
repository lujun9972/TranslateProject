[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Install GNOME Tweaks on Fedora Linux)
[#]: via: (https://itsfoss.com/install-gnome-tweaks-fedora/)
[#]: author: (John Paul https://itsfoss.com/author/john/)

How to Install GNOME Tweaks on Fedora Linux
======

If you use [GNOME desktop environment][1] on [Fedora][2], you can use the default Settings app to access a wide variety of settings options.

[GNOME Tweaks][3] is a great little app that gives you access to extra options to modify your GNOME experience. This includes everything from extensions, to changing themes and tweaking power settings.

Today, I’ll be showing you how to install GNOME Tweaks on Fedora.

### Method 1: Install GNOME Tweaks in Fedora from the Software Center

The easiest way to install GNOME Tweaks is via GNOME Software. Simply open Software and enter “GNOME Tweaks” into the search box. (It’s the little magnifying glass in the upper right corner.)

![Install GNOME Tweaks in Software][4]

Click the page for the application and then click install. You may be asked for your password. Once the installation is complete, you will be able to find GNOME Tweaks in the applications menu.

### Method 2: Install GNOME Tweaks in Fedora using the terminal

If you’re a power user, you can quickly install GNOME Tweaks from the terminal. Simply open the terminal of your choice and enter:

```
sudo dnf install gnome-tweaks
```

Enter your password when asked and enter `Y` to approve the installation. Then you’re done.

![Install GNOME Tweaks from the terminal][5]

An even faster method is to just type `gnome-tweaks` into the terminal. Fedora then tries to access the application. Once it discovers that GNOME Tweak is not installed, it will ask you if you would like to install GNOME Tweaks. Enter `Y` to approve and enter your password when asked. And you’re done.

![Install GNOME Tweaks from the terminal, method 2][6]

That’s it. You’ll have the GNOME Tweaks available in your Fedora system and you can use it to change various additional settings.

![GNOME Tweaks][7]

I am not going to show the [things you can do with GNOME Tweaks][8] because it has already been covered in the past and you may refer to that.

I hope this quick tip was helpful in your Fedora journey. If you would like to see more Fedora beginner tips, please let us know in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-gnome-tweaks-fedora/

作者：[John Paul][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/john/
[b]: https://github.com/lujun9972
[1]: https://www.gnome.org
[2]: https://getfedora.org
[3]: https://wiki.gnome.org/action/show/Apps/Tweaks?action=show&redirect=Apps%2FGnomeTweakTool
[4]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2021/01/installl-gnome-tweaks-gui.jpg?resize=800%2C434&ssl=1
[5]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/01/installl-gnome-tweaks-cli.png?resize=800%2C596&ssl=1
[6]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2021/01/gnome-tweaks-terminal.png?resize=800%2C586&ssl=1
[7]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2021/01/gnome-tweaks.png?resize=800%2C560&ssl=1
[8]: https://itsfoss.com/gnome-tweak-tool/
