[#]: subject: "Installing VS Code on Arch Linux Takes Some Thinking"
[#]: via: "https://itsfoss.com/install-vs-code-arch-linux/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Installing VS Code on Arch Linux Takes Some Thinking
======

[![Warp Terminal][1]][2]

There are two main choices for getting VS Code on Arch Linux:

  * Install Code - OSS from Arch repositories
  * Install Microsoft's VS Code from AUR



I know. It's confusing. Let me clear the air for you.

[VS Code][3] is an open source project but the binaries Microsoft distributes are not open source. They have telemetry enabled in it.

Code - OSS is the actual open source version of VS Code.

Think of Code - OSS as Chromium browser and VS Code as Google Chrome (which is based on Chromium browser).

Another thing here is that some extensions will only work in VS Code, not in the de-Micorsoft Code - OSS.

This is why you should think it through if you want to use Microsoft's VS Code or its 100% open sourced version.

Let me show you the steps for both installation.

### Method 1: Install Code - OSS

✅ Open source version of Microsoft VS Code
✅ Easy to install with a quick pacman command
❌ Some extensions may not work

This is simple. All you have to do is to ensure that your Arch system is updated:

```

    pacman -Syu

```

And then install Code - OSS with:

```

    pacman -S code

```

It cannot be simpler than this, can it?

As I mentioned earlier, you may find some extensions that do not work in the open source version of Code.

Also, I had noticed earlier that Ctrl+C - Ctrl+V was not working for copy paste. Instead, it was defaulted to Ctrl+Shift+C and Ctrl+Shift+V for reasons not known to me. I had not made any changes to key bindings or had opted for a Vim plugin.

#### **Removing Code OSS**

Removal is equally simple:

```

    sudo pacman -R code

```

### Method 2: Install the actual Microsoft's VS Code

✅ Popular Microsoft VS Code that is used by most people
✅ Access to all proprietary features and extensions in the marketplace
❌ Installation may take effort if you don't have an AUR helper

If you don't care too much about ethics, open source principles and just want to code without thinking it too much, go with VS Code.

There are a couple of VS Code offerings available in the AUR but the official one is [this][4].

Before installing it, you should remove Code OSS

```

    sudo pacman -R code

```

If you have an [AUR helper][5] like yay already installed, use it like this:

```

    yay -S visual-studio-code-bin

```

Otherwise, [install yay][6] first and then use it to install the desired package.

![][7]

Don't be deceived by the pretty looking screenshot above. I was using a different theme in VS Code.

#### Removal

You can use your AUR helper or the super [reliable pacman command][8] to remove Microsoft VS Code from Arch Linux.

```

    sudo pacman -R visual-studio-code-bin

```

I let you enjoy your preferred version of VS Code on Arch Linux. Please feel free to use the comment section if you have questions or suggestions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-vs-code-arch-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://code.visualstudio.com/
[4]: https://aur.archlinux.org/packages/visual-studio-code-bin
[5]: https://itsfoss.com/best-aur-helpers/
[6]: https://itsfoss.com/install-yay-arch-linux/
[7]: https://itsfoss.com/content/images/2025/05/Screenshot-From-2025-05-26-15-39-03.png
[8]: https://itsfoss.com/pacman-command/
