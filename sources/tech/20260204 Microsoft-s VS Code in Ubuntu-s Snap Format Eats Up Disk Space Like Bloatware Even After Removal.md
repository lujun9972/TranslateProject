[#]: subject: "Microsoft's VS Code in Ubuntu's Snap Format Eats Up Disk Space Like Bloatware Even After Removal"
[#]: via: "https://itsfoss.com/news/vscode-snap-disk-space-issue/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft's VS Code in Ubuntu's Snap Format Eats Up Disk Space Like Bloatware Even After Removal
======

[![Warp Terminal][1]][2]

Have you noticed that disk space is filling up fast even when your Linux computer's trash folder is empty? There's a strong possibility that [VS Code][3] is responsible for it.

A [not-so-recent issue][4] in the Snap version of VS Code has cropped up again, and there's no fix in sight.

### An Absurd Bug

When you normally delete a file, it goes into the trash folder, located at `~/.local/share/Trash`. [GNOME][5] has supported automated emptying of the trash at selected intervals through its settings for quite some time now.

So, let's say you delete trash every seven days.

![][6]

Now, with [the Snap version of VS Code][7], any files or folders deleted using the `Delete` key in VS Code are being sent to the Snap's own trash folder, which is located at:

```

    ~/snap/code/current/.local/share/Trash

```

**You see the problem now?** This pesky folder is not cleared automatically, and this is not how deleted content should be handled. Especially when the deleted files are placed this deep inside a directory tree, hidden away from the user's eye.

_**There's more.**_

The `current` directory mentioned above corresponds to the version of VS Code that's installed on your system.

Now, if you update to a new version of VS Code, **the residuals of the old version will still be present** on your computer in a separate folder.

_See for yourself._ 👇

![][8]

_This drives up the unnecessary bloat in your system even more!_

The bug itself was reported all the way back in November 2024, and the issue is still present for current Snap versions of VS Code and even [VSCodium][9].

### What Can You Do?

If this issue is bothering you, then you can remove the Snap version and install the [DEB][10] or [RPM][11] version of VS Code. There's also an [unofficial Flatpak version][12] if you prefer that packaging.

📋

Deleting the Snap version of VS Code also deletes all of its associated junk files.

Some [Arch distributions][13], like Manjaro Linux, come with [Snapd][14] installed by default. If you are one of the people who used the Snap version of VS Code, then you can also try the open source build of VS Code (Code - OSS), which is available in the [Arch Linux repository][15].

Source: [How to Geek][16].

* * *

**Suggested Read 📖:** [_GNU's Very Own Kernel Project Hurd is Anything But Dead_][17]

![][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/vscode-snap-disk-space-issue/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://code.visualstudio.com/
[4]: https://github.com/microsoft/vscode/issues/233649
[5]: https://www.gnome.org/
[6]: https://itsfoss.com/content/images/2026/02/file-trash-removal-timer.png
[7]: https://snapcraft.io/code
[8]: https://itsfoss.com/content/images/2026/02/ubuntu-vscode-trash-different-inode-means-duplicate-1.png
[9]: https://itsfoss.com/vscodium/
[10]: https://itsfoss.com/install-visual-studio-code-ubuntu/#:~:text=Method%202%3A%20Using%20the%20.deb/.rpm%20packages
[11]: https://itsfoss.com/install-vs-code-fedora/
[12]: https://flathub.org/en/apps/com.visualstudio.code
[13]: https://itsfoss.com/arch-based-linux-distros/
[14]: https://github.com/canonical/snapd
[15]: https://archlinux.org/packages/extra/x86_64/code/
[16]: https://www.howtogeek.com/visual-studio-code-is-eating-up-hundreds-of-gigabytes-on-linux/
[17]: https://itsfoss.com/news/gnu-hurd-progress-report/
[18]: https://itsfoss.com/content/images/icon/android-chrome-512x512-259.png
