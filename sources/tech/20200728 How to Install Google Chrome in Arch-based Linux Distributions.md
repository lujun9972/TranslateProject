[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Install Google Chrome in Arch-based Linux Distributions)
[#]: via: (https://itsfoss.com/install-chrome-arch-linux/)
[#]: author: (Dimitrios Savvopoulos https://itsfoss.com/author/dimitrios/)

How to Install Google Chrome in Arch-based Linux Distributions
======

_**Brief: A step-by-step beginner’s tutorial showing how to install Google chrome in Arch, Manjaro and other Arch-based Linux distributions.**_

Google Chrome is undeniably the most popular web browser. It is **not open source software** and this is why you won’t see it preinstalled in Linux distributions you use. You won’t even find Chrome in the software center.

[Installing Google Chrome is easy in Ubuntu][1] and Fedora based distribution. You can go to Chrome’s website and download the DEB or RPM installer files and install it easily.

Arch Linux users may notice that there is no package for them on the official Google Chrome website.

Fortunately, [Google Chrome][2] is available on [Arch User Repository][3] (AUR) for Arch, Manjaro and other [Arch-based Linux distributions][4]. You can install Google Chrome using an [AUR Helper][5] easily or use Git to install it without AUR helper.

I will cover both options in this tutorial.

### Method 1: Installing Google Chrome with an AUR Helper

I hope that you are familiar with the concept of AUR (Arch User Repository) and AUR helpers. If not, please read our articles on [what is AUR][3] and [what are AUR helpers and how to install them][5].

#### Step 1: Install an AUR helper (if you haven’t got one already)

There are quite a few [AUR Helpers][5] to choose but in this tutorial, I will use [yay][6] which I have installed on my machine. You should install it if you haven’t got it already:

```
sudo pacman -S --needed base-devel git
sudo git clone https://aur.archlinux.org/yay-git.git
cd yay
makepkg -si
```

#### Step 2: Install Google Chrome using AUR helper

Now, to install Google Chrome in Arch Linux using yay:

```
yay -S google-chrome
```

As you see, yay found all the available packages related to Google Chrome. I will choose the stable package to install, the same as I chose for the other installation method.

![][7]

#### Step 3: Upgrading Chrome version with yay

You successfully installed Chrome on your Arch-based distribution. However, you should also know what to do if there is a new version of Google Chrome available.

You cannot upgrade AUR packages with [pacman command][8] unfortunately. But the good thing is that Yay and [pacman][8] share common flags for performing similar actions.

Keep in mind that unlike pacman, [yay shouldn’t be run with “sudo” privilege][9].

The following command will upgrade all the packages – both AUR and official.

```
yay -Syu
```

![][10]

### Method 2: Install Google Chrome without an AUR Helper

You’ll still be getting the package from Arch User Repository. However, instead of AUR helper, you’ll be doing it manually.

#### Step 1: Install base-devel package

To install a package from AUR you must have Git and base-devel group installed. Base-devel group contains all the essential tools for compiling from source.

```
sudo pacman -S --needed base-devel git
```

#### Step 2: Install Chrome from AUR

Clone Google Chrome from the AUR and install it like this:

```
git clone https://aur.archlinux.org/google-chrome.git
cd google-chrome
makepkg -si
```

![][11]

#### Step 3: Upgrading Google Chrome afterward

When a new version of Google Chrome is released and it is available in the AUR, you can upgrade it manually like this:

```
git pull
makepkg -si
```

### Conclusion

As you can see, it is slightly complicated to install Google Chrome in the Arch domain. But that’s the beauty of it. Many [people use Arch because it gets you doing more things in the terminal][12].

If you encountered any difficulty when you try to install Google Chrome, let us know at the comment section or share your thoughts.

Make sure to subscribe on our social media to get first the latest Linux news!

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-chrome-arch-linux/

作者：[Dimitrios Savvopoulos][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/dimitrios/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/install-chrome-ubuntu/
[2]: https://aur.archlinux.org/packages/google-chrome/
[3]: https://itsfoss.com/aur-arch-linux/
[4]: https://itsfoss.com/arch-based-linux-distros/
[5]: https://itsfoss.com/best-aur-helpers/
[6]: https://github.com/Jguer/yay
[7]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/yay-S-google-chrome.png?ssl=1
[8]: https://itsfoss.com/pacman-command/
[9]: https://forum.manjaro.org/t/can-using-the-yay-aur-helper-without-sudo-become-a-bad-habit-when-installing-packages/71014/2
[10]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/yay-Syu.png?ssl=1
[11]: https://i2.wp.com/itsfoss.com/wp-content/uploads/2020/07/chrome-git-clone.png?ssl=1
[12]: https://itsfoss.com/why-arch-linux/
