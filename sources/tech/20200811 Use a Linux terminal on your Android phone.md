[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Use a Linux terminal on your Android phone)
[#]: via: (https://opensource.com/article/20/8/termux)
[#]: author: (Seth Kenlon https://opensource.com/users/seth)

Use a Linux terminal on your Android phone
======
Use a text editor, SSH into a computer, or even maintain your Kubernetes
cluster right from the palm of your hand with Termux.
![Tux and Android stuffed animals on shelf][1]

When it comes to ultra-mobile computing, I prefer the [PocketCHIP][2] or a [Raspberry Pi][3] with a screen rather than a mobile phone or tablet. These solutions offer a pure Linux environment that's as open source as the hardware allows and make no assumptions about how I expect to work.

Sometimes, though, the only thing I have on me is a mobile phone. While there are some really great Android apps out there, many feel like overkill for simple tasks, especially knowing how much can be done in a simple terminal on my Linux desktop. I'm not the only person who feels this way, and that's why the [Termux][4] project was born.

Termux is a terminal emulator and Linux environment app for Android. It also doesn't require you to root your device.

![Termux][5]

(Seth Kenlon, [CC BY-SA 4.0][6])

Termux installs a minimal base system automatically, and additional packages are available using a package manager, just as you do with Fedora, Debian, or the like.

### Install Termux

Installing Termux is as easy as installing any app on your Android device. You can use either the default [Google Play][7] store or the open source app repository [F-Droid][8].

![Termux on F-Droid][9]

(Seth Kenlon, [CC BY-SA 4.0][6])

You can also [download the source code][10] and compile it yourself.

### Linux-like Android

Once you have Termux installed on your mobile phone, you essentially have a minimal Linux system running as an application on your (Linux-based) Android device. You can use most of the usual terminal applications you are familiar with, or you can become familiar with them now that you have them on your phone. Most importantly, the Termux interface provides software Ctrl, Alt, Esc, and arrow keys, so essential keystroke shortcuts are easy to type—even on a virtual keyboard. On long trips, I prefer to carry a Bluetooth keyboard with me, so I can use Termux as easily as a terminal on my desktop or laptop.

By default, Termux runs Bash:


```
`$ echo $0 /data/data/com.termux/files/usr/bin/bash`
```

Most of the commands you're used to will work as expected, whether they're built-in Bash commands or the usual array of common Linux commands and utils. There are also several other shells available, including [Zsh][11] and [tcsh][12].

### Installing commands

If you're used to Linux, or even [Homebrew][13] on a Mac or [Chocolatey][14] on Windows, then you already know how to install more commands for Termux. Its backend package manager is Apt from [Debian][15] Linux, but Termux uses the `pkg` command as a simplified frontend interface. The result approximates the consistent simplicity of Fedora's [DNF][16] experience, and I'd love to see `pkg` as an abstraction layer on more platforms (imagine using the same package management commands on Debian, RHEL, and Slackware).

The first package I installed was a simple text editor:


```
`$ pkg search jed [...] jed/stable 4.6-4 aarch64 Lightweight text editor $ pkg install jed`
```

Running [Jed][17] was exactly the same as running it on my RHEL desktop. Both run in the terminal and use the same keyboard shortcuts. That's exactly the mobile experience I want: the same as my desktop.

### Remote control

A text editor is one thing, but Termux reveals its true potential the first time you SSH into a computer. Through this simple terminal, you can log onto any computer on any network you have access to. You have a portable console you can use either as a host or as a terminal into any amount of computing power available to you.

This doesn't end with SSH, though. There's a Termux package for [kubectl][18], so by using the `use-context` option in `kubectl`, you can maintain your Kubernetes cluster from anywhere.

### Contributing to Termux

One of my favorite things about Termux is that it removes a significant barrier to contributing to a mobile project. All current open source mobile platforms are Android or Android-based, requiring a special toolchain and a fair amount of Java knowledge.

Termux, by nature, shields a potential new contributor from much of that because you can write packages for Termux without knowing anything about Android. You can create a package definition for Termux as long as you know how to [write a shell script][19] because you're writing a package for the Termux subsystem.

### Put a terminal in your pocket

Termux is a great way to learn the Linux terminal, and it's easy to install. Put Termux on your phone or tablet, check out some of our [terminal basics][20] (such as our articles about mastering the [ls][21] and [cat][22] commands) and our [Bash cheat sheet][23], and transform the way you use your mobile.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/termux

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/tux_penguin_linux_android.jpg?itok=ctgANLI7 (Tux and Android stuffed animals on shelf)
[2]: https://opensource.com/article/17/2/pocketchip-or-pi
[3]: https://opensource.com/resources/raspberry-pi
[4]: https://termux.com/
[5]: https://opensource.com/sites/default/files/uploads/termux-pkg.jpg (Termux)
[6]: https://creativecommons.org/licenses/by-sa/4.0/
[7]: https://play.google.com/store/apps/details?id=com.termux
[8]: https://f-droid.org/repository/browse/?fdid=com.termux
[9]: https://opensource.com/sites/default/files/uploads/termux-fdroid.jpg (Termux on F-Droid)
[10]: https://github.com/termux/termux-app
[11]: https://opensource.com/article/19/9/getting-started-zsh
[12]: https://opensource.com/article/20/7/why-i-still-love-tcsh
[13]: https://opensource.com/article/20/6/homebrew-linux
[14]: https://opensource.com/article/20/3/chocolatey
[15]: http://debian.org
[16]: https://developers.redhat.com/blog/2016/08/30/why-red-hats-new-dnf-package-manager-is-not-just-another-yum-2/
[17]: http://www.jedsoft.org/jed/
[18]: https://opensource.com/article/20/5/kubectl-cheat-sheet
[19]: https://opensource.com/article/20/4/bash-programming-guide
[20]: https://opensource.com/article/19/10/learn-bash-command-line-games
[21]: https://opensource.com/article/19/7/master-ls-command
[22]: https://opensource.com/article/19/2/getting-started-cat-command
[23]: https://opensource.com/downloads/linux-common-commands-cheat-sheet
