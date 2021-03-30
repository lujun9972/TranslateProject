[#]: subject: (How to Play DVDs on Fedora Linux [Quick Tip])
[#]: via: (https://itsfoss.com/play-dvd-fedora/)
[#]: author: (John Paul https://itsfoss.com/author/john/)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

How to Play DVDs on Fedora Linux [Quick Tip]
======

You’ve probably tried to watch a DVD after installing Fedora, only to run into an error.

You are not alone. I faced this issue recently and I am pretty sure plenty of Fedora users like you and me who still use DVDs would like to overcome this petty issue.

![libdvdcss error][1]

### Fixing DVD issue on Fedora

Why do you see this error? Because the manufacturers of DVDs encrypt their disks using a Digital Rights Management system named [Content Scramble System][2].

You can get around it by installing the required software library. [Videolan][3], creators of the VLC player, introduced a project named [libdvdcss][4] to get around this issue. According to its page, libdvdcss is a “simple library designed for accessing DVDs like a block device without having to bother about the decryption”.

As an individual, you may use this software library and no company or FBI should be coming after you as an individual but Fedora or other distribution would avoid including it by default to avoid possible legal troubles at an organization level.

Due to this legal reason, this library is not available in the Fedora repos. However, it is available on [RPMFusion][5]. You can only install it via the command line, but the instructions are simple.

#### Step 1

First, you need to install RPMFusion’s free tainted repo. The [tainted repos][6] contain “FLOSS packages where some usages might be restricted in some countries”.

To install the required repo, enter the following command in the terminal:

```
sudo dnf install rpmfusion-free-release-tainted
```

Enter your password and press `Y` when prompted to approve the installation.

#### Step 2

Next, install the required package with the following command:

```
sudo dnf install libdvdcss
```

![][7]

Again, enter your password and press `Y` when prompted to approve the installation.

Once the installation is complete, you should be able to play your DVD. It’s that easy, at least it was for me. I hope this helps you too.

--------------------------------------------------------------------------------

via: https://itsfoss.com/play-dvd-fedora/

作者：[John Paul][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/john/
[b]: https://github.com/lujun9972
[1]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/03/libdvdcss-error-800x516.jpg?resize=800%2C516&ssl=1
[2]: https://en.wikipedia.org/wiki/Content_Scramble_System
[3]: https://www.videolan.org/
[4]: https://www.videolan.org/developers/libdvdcss.html
[5]: https://rpmfusion.org/Package/libdvdcss
[6]: https://rpmfusion.org/Configuration
[7]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2021/03/install-libdvdcss-fedora.jpg?resize=732%2C540&ssl=1
