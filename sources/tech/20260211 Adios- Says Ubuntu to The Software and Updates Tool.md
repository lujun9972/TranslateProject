[#]: subject: "Adios! Says Ubuntu to The Software and Updates Tool"
[#]: via: "https://itsfoss.com/news/ubuntu-software-and-updates-removal/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Adios! Says Ubuntu to The Software and Updates Tool
======

[![Warp Terminal][1]][2]

Desktop builds of the upcoming [Ubuntu 26.04 LTS][3] won't ship with the Software & Updates application ( _software-properties-gtk_ ) pre-installed. This is the tool that facilitates the managing of software sources and repository settings on an Ubuntu system.

It handles [PPAs][4], lets users switch between different software channels like _main_ , _restricted_ , _universe_ , and _multiverse;_ pick faster download mirrors; control automatic update behavior; and manage additional drivers.

Now Ubuntu developers are removing it from the desktop image. The package isn't disappearing completely, of course; it just won't be included out of the box.

### Why is It Being Ditched?

![When I fired up the daily build for Ubuntu 26.04 LTS, Software & Updates was still around.][5]

Canonical's Jean-Baptiste Lallement [filed a bug report][6] explaining that several features in Software & Updates are " _dangerous or too complex for normal users_."

He adds that the tool lets users disable _main_ repositories through the GUI, and accidentally toggling this option could break system updates and software installation.

Another problematic thing is said to be the enabling of the _proposed_ repository ( _where unstable packages live_ ) by the user.

If you were wondering what happens to the [Ubuntu Pro][7] settings, don't worry; that is being moved to the [Security Center][8]. It is Ubuntu's dedicated app for simplifying access to security features.

The CLI tools remain untouched, as the software-properties-common package [is retained][9], allowing for command-line based repository management.

### What This Means for Users

Upgrading from older Ubuntu versions **won't remove Software & Updates**. Ubuntu doesn't remove packages that were previously included when users upgrade to new releases.

Fresh Ubuntu 26.04 LTS and later desktop installations won't have Software & Updates pre-installed, but the package stays in Ubuntu's _main_ repository, so installing it takes just one command:

```

    sudo apt install software-properties-gtk

```

[Ubuntu flavors][10] like _Xubuntu_ , _Ubuntu MATE_ , Ubuntu Budgie, and others can still ship Software & Updates in their default installations. The package remains available for any flavor that wants to include it.

Via: [OMG! Ubuntu][11]

* * *

![][12]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ubuntu-software-and-updates-removal/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/ubuntu-26-04-release-features/
[4]: https://itsfoss.com/ppa-guide/
[5]: https://itsfoss.com/content/images/2026/02/ubuntu-26-04-software-and-updates.png
[6]: https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2140527
[7]: https://ubuntu.com/pro
[8]: https://itsfoss.com/news/ubuntu-security-center-near-stable/
[9]: https://launchpad.net/ubuntu/+source/software-properties
[10]: https://itsfoss.com/which-ubuntu-install/
[11]: https://www.omgubuntu.co.uk/2026/02/ubuntu-26-04-drops-software-and-updates-gui
[12]: https://itsfoss.com/content/images/icon/android-chrome-512x512-274.png
