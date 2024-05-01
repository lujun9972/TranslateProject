[#]: subject: "Installing VS Code on Fedora"
[#]: via: "https://itsfoss.com/install-vs-code-fedora/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing VS Code on Fedora
======

[![Warp Terminal][1]][2]

VS Code is one of the most popular code editors out there, and it is only natural that you look for it after a fresh installation of Fedora.

Now, there are two ways to get VS Code on Fedora:

  * **Unofficial Flatpak package** : Easy to install from the software center. However, Flatpak apps run in sandboxed containers. So, you'll have to make additional effort to access SDKs on your actual system.
  * **Official RPM package** : VS Code offers a YUM repository for Fedora and Red Hat systems. The application is installed on the system and is well integrated. It requires running a few commands in the terminal, though.



You can use either method and see which one suits you better.

Let me show the steps for both methods in detail.

### Method 1: VS Code in Flatpak format

This is rather the easier method here. Fedora comes with Flatpak baked in. So, you could just run this command and get done with it.

```

    flatpak install https://flathub.org/repo/appstream/com.visualstudio.code.flatpakref

```

Or, if you don't like the terminal, open the software center and look for VS Code and install it from there. Just a matter of a few clicks.

The screenshots are shown for GNOME desktop environment. If you are using KDE or some other desktop environment, use their software center. The screenshots may look different but the steps remain the same.

Open the Software Center.

![][3]

Look for VS Code here. You'll see more than one results. The first one, [Visual Studio Code][4], is the one from Microsoft. Code - OSS is the same but in its open source format, instead of what Microsoft offers. Similar is the case with [VSCodium][5].

![][6]

You'll find the option to install Visual Studio Code. Click on it and it will be installed.

![][7]

Since it is a sandboxed application, you won't be asked to provide your account password while installing this program. However, you'll see a warning that extra effort is required for accessing some SDKs.

![][8]

#### Removal steps

To remove, use the following command:

```

    flatpak uninstall code

```

Alternatively, you can also just go to Software Center, look for VS Code again and uninstall it from there.

The Flatpak version works good for me. But if you don't like its sandboxed behavior and you are not comfortable with the extra steps required for setting your development environment, you can opt for the native RPM package.

### Method 2: VS Code in native RPM package

[Microsoft provides a YUM repository][9] that allows you to install VS Code on Fedora and update it with system updates when a newer version is available.

First, you need to import the repository signing key into your system:

```

    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

```

Next, add the repository to your system using this command:

```

    sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

```

The above command may look scary but that's what the official document mentions. Basically, you are creating a file `/etc/yum.repos.d/vscode.repo` and adding some text that has repository information in a specific format. `\n` is used for adding new line.

![Click to enlarge][10]

Now that repo is added, refresh the package cache so that your system knows about the availability of the new package.

```

    dnf check-update

```

![][11]

Everything is set now. You can install Visual Studio Code now with this command:

```

    sudo dnf install code

```

You'll have to press Y to confirm your choice:

![][12]

#### Removal steps

To uninstall the RPM version of VS Code, use the following command:

```

    sudo dnf remove code

```

### Do more with VS Code

I find it surprising that Microsoft has managed to name VS Code as code on all the platforms.

Anyway, it's good to see that Fedora has a few ways of installing VS Code and it's not that complicated.

I presume you'll be using GitHub so it's better to [integrate it directly in VS Code][13].

![][14]

Master the keyboard shortcuts to feel like the VS Code champion.

![][14]

Happy coding with (VS) Code 👩‍💻

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-vs-code-fedora/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/04/fedora-open-software-center-1.png
[4]: https://code.visualstudio.com/
[5]: https://itsfoss.com/vscodium/
[6]: https://itsfoss.com/content/images/2024/05/search-vs-code-fedora-software-center.png
[7]: https://itsfoss.com/content/images/2024/05/install-vs-code-fedora-software-center.png
[8]: https://itsfoss.com/content/images/2024/05/vs-code-flatpak-fedora-warning.png
[9]: https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions
[10]: https://itsfoss.com/content/images/2024/05/installing-vscode-rpm-fedora.png
[11]: https://itsfoss.com/content/images/2024/05/dnf-check-updates.png
[12]: https://itsfoss.com/content/images/2024/05/installing-vs-code-fedora-rpm.png
[13]: https://itsfoss.com/vs-code-github/
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
