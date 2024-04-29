[#]: subject: "How to Use Pop Shell on GNOME Desktop"
[#]: via: "https://itsfoss.com/pop-shell-gnome-desktop/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Use Pop Shell on GNOME Desktop
======

[![Warp Terminal][1]][2]

I've been using Pop!_OS since my college days, so whenever I distro hop, the first thing that I miss are the benefits of the **Pop!_OS Shell**.

Especially the ability to get tilting ability without much configuration is a must for someone like me.

So in this tutorial, I will walk you through how you can install the Pop Shell extension on the GNOME desktop. And yes, it will cover most Linux distros so you can get the most out of this.

### Installing Pop Shell in GNOME Desktop

![][3]

Unlike most installation methods, installing the Pop!_OS Shell is a little different.

For example, if you're an Ubuntu user, you have to build Pop Shell from the source whereas Fedora users can directly install it using its package manager (as it is available in its repository).

To make things easy to follow, I have divided the installation steps for every distro into different sections:

#### For Ubuntu

If you are using Ubuntu, first install the required dependencies using the following:

```

    sudo apt install git node-typescript make nodejs npm gnome-shell-extensions

```

In the next step, you have to clone the GitHub repository based on your current Ubuntu release. You can use the following command to know your release version:

```

    lsb_release -a

```

![][4]

Once you find the codename of your current release, head over to the [official GitHub page of Pop Shell][5] and select the branch named after your release:

![][6]

Next, download the zip file of the branch by clicking on the `<> Code` button:

![][7]

Once done, open the terminal and switch to the directory where you've downloaded the zip file. For most users, it will be the `Downloads` directory:

```

    cd ~/Downloads

```

Now, use the unzip command to extract files in the following manner:

```

    unzip -q <Filename>

```

![][8]

Next, use the cd command to change to the extracted directory. In my case, it was `shell-master_jammy` so I used the following:

```

    cd shell-master_jammy

```

Finally, build the file using the given command:

```

    make local-install

```

During the installation, it will ask you if you want Pop Shell to override your default shortcuts. Enter `y` and press the Enter key:

![][9]

Once done, open the GNOME extensions from the app menu and enable the Pop Shell:

![][10]

#### For Fedora

If you are using Fedora, then you're in luck. Pop!_OS Shell is readily available in the Fedora repository and can be installed with a single command:

```

    sudo dnf install gnome-shell-extension-pop-shell

```

![][11]

Now, log out and log back in, and open the GNOME extension manager to enable Pop Shell:

![][12]

#### For Arch:

While the Pop!_OS Shell extension is available in the pacman repository, you have to build it from source if you want shortcuts to work.

First, install the prerequisites for building a package:

```

    sudo pacman -S git typescript make

```

Next, clone the Pop Shell repository using the given command:

```

    git clone https://github.com/pop-os/shell.git

```

Now, change your directory to `shell` using the following command:

```

    cd shell

```

Finally, use the make command to build the package:

```

    make local-install

```

That's it! Now, enable the Pop Shell extension from the GNOME extension manager:

![][13]

#### For Manjaro

If you don't know, Majaro Linux uses its repository and Pop!_OS Shell is available in it.

To install Pop Shell in Manjaro, use the following command:

```

    sudo pamac install gnome-shell-extension-pop-shell

```

Once done, enable the Pop Shell extension from the GNOME extension manager and that's it!

### Your Pop!_OS Experience is Ready

This was a quick tutorial on how you can install the Pop!_OS Shell extension on GNOME desktop.

_💬 I hope you find this guide helpful, and for any clarifications or suggestions, feel free to leave a comment._

--------------------------------------------------------------------------------

via: https://itsfoss.com/pop-shell-gnome-desktop/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/04/Pop-shell.png
[4]: https://itsfoss.com/content/images/2024/04/Find-the-release-name-in-ubuntu.png
[5]: https://github.com/pop-os/shell
[6]: https://itsfoss.com/content/images/2024/04/Select-release.png
[7]: https://itsfoss.com/content/images/2024/04/Download-the-zip-file-of-the-branch.png
[8]: https://itsfoss.com/content/images/2024/04/Unzip-the-branch-zip-file.png
[9]: https://itsfoss.com/content/images/2024/04/Override-with-popshell-shortcuts.png
[10]: https://itsfoss.com/content/images/2024/04/Enable-pop-shell-in-ubuntu.png
[11]: https://itsfoss.com/content/images/2024/04/Install-pop-shell-in-Fedora.png
[12]: https://itsfoss.com/content/images/2024/04/Enable-Pop-Shell-extension-in-Fedora.png
[13]: https://itsfoss.com/content/images/2024/04/Enable-Pop-Shell-extension-in-Arch-Linux.png
