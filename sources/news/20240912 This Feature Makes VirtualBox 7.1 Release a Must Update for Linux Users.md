[#]: subject: "This Feature Makes VirtualBox 7.1 Release a Must Update for Linux Users"
[#]: via: "https://news.itsfoss.com/virtualbox-7-1-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Feature Makes VirtualBox 7.1 Release a Must Update for Linux Users
======
VirtualBox 7.1 brings gifts for Linux users, and of course, important
changes for everyone else.
[![][1]][2]

A [virtual machine][3] (VM) is an essential aspect of modern computing that allows people to run operating systems in a virtual environment, mimicking a physical machine with existing system resources.

Some of the [best virtualization software][4] for Linux have one thing in common: they are reliable. VirtualBox is one such option, which is a great choice if you want an install-it-and-forget-it solution.

It caters to both new users and professional users in an enterprise setting, with great control over the machines themselves. A few days ago, the developers introduced a new release, **VirtualBox 7.1** , that has landed with many useful tweaks.

Let's check it out. 😃

## 🆕 VirtualBox 7.1: What's New?

![][5]

From the get-go, you will notice that VirtualBox features **a new logo** and an **updated user interface** based on [Qt 6.5.3][6] that feels cleaner. It now asks for choosing between the two modes, “Basic”, and “Expert”, on the main screen itself for switching between different levels of UI functionality.

**For users on Linux** , it is now possible to take advantage of clipboard sharing on the Wayland session for both Linux hosts and guests, addressing a long-standing [issue][7].

With more distributions going the Wayland way, this feature improvement should provide relief to all VM users 😌

It is also possible to transfer files between Linux and Windows hosts/guests with shared clipboard after upgrading to 7.1 [Guest Additions][8].

They have also **upgraded unattended installations** , with there now being support for _subiquity- / cloud-init_ -based installers, the kind found on many modern Linux distros. Plus, you can now set different passwords for user and admin/root accounts.

On top of that, there is now a **new NAT engine** with IPv6 support, **Arm virtualization for Linux and BSD** on macOS installations running on Apple Silicon, and **improved screen recording** , which now uses less CPU resources.

To wrap things up, here are some **other notable changes** :

  * Tweaks to improve accessibility across the application.
  * A fix for the Oracle VirtualBox Extension Pack's PUEL license.
  * The performance dashboard can now show resource usage for cloud VMs.
  * Improved _EFLAGS.TF_ handling for CPUID instructions when Hyper-V is in use.



## 📥 Get VirtualBox 7.1

This release of VirtualBox is available for **Linux** , **Windows** , **macOS** , and **Solaris**. You can grab the package of your choice from the [official website][9], where you will also find the documentation should you run into issues.

[VirtualBox 7.1][9]

If you are interested in browsing the source code, the [official website][10] also hosts the code for VirtualBox.

_💬 Do you use VirtualBox for your virtualization needs? Use something else? Mention them in the comments below!_

**Suggested Read** 📖

![][11]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/virtualbox-7-1-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/virtual-machine/
[4]: https://itsfoss.com/virtualization-software-linux/
[5]: https://news.itsfoss.com/content/images/2024/09/VirtualBox_7.1.png
[6]: https://www.qt.io/blog/qt-6.5.3-released
[7]: https://www.virtualbox.org/ticket/20808
[8]: https://itsfoss.com/virtualbox-guest-additions-ubuntu/
[9]: https://www.virtualbox.org/wiki/Downloads
[10]: https://www.virtualbox.org/browser/trunk
[11]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
