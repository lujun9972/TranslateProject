[#]: subject: "The Curious Case of AUR Updates Fetching 30 GB of Data for Electron"
[#]: via: "https://itsfoss.com/aur-electron-update-issue/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Curious Case of AUR Updates Fetching 30 GB of Data for Electron
======

[![Warp Terminal][1]][2]

I am using CachyOS on my primary system these days and pretty content with its performance.

Since it is based on Arch Linux, I am using a few software installed from the [Arch User Repository (AUR)][3] with [Yay AUR Helper][4].

While updating, it showed me a few packages that required upgrades.

![][5]

I did not pay attention as there was nothing alarming and pressed the usual enter keys one after another.

Only when it reached a certain stage that I realized that it was taking a lot longer to install these updates. I paid close attention at this stage and noticed an issue.

It was trying to download GBs of data for Electron.

![More than 25GB of updates? That's not usual][6]

✅

Since it was fetching electron version 32, getting the binary from AUR itself easily fixed the issue:

`yay -S electron32-bin`

But there is more to it that I would like to discuss.

### What's going on here?

In simpler terms, Elecron is a JavScript framework that builds a graphical interface of an application on top of the Chromium web browser. From VS Code to Discord, [tons of popular applications are built on Electron][7].

When you run these applications, you are basically running a web browser underneath, and not everyone likes that. But it is easier to package an application, and the interface looks modern, and that's why it is popular.

Anyways, it is the functioning of AUR that complicates the issue here. It tries to build all the dependencies of a package.

It seems like at some point in the past, I just pressed enter keys without paying attention and somehow the AUR system thought that it needed to download a specific version of electron as a dependency.

The next problematic thing is that since it tries to build the package from source, it tries to get the entire source code of the Chromium project, which is in GBs.

### What should you do in such case?

🚧

I am using `electron32` in the example here. Your electron version might be different and thus, you MUST change the commands in the examples here to reflect the correct electron version.

First check what goes on with the troubled electron version. Where was it installed from and which packages require it?

```

    pacman -Qi electron32

```

It gave me two interesting details. Electron32 came from the 'Extra' (cachyos-extra) repository and it was not required by any packages, not even as an optional dependency.

![][8]

This was interesting and gave me the idea that perhaps it was of no use getting electron's other version using AUR. So, what I did was to exclude electron from the AUR update.

![I entered 4 here to exclude electron from the update][9]

And as I had guessed, rest of the three packages were updated without any issues. I wonder why AUR wanted to get it in the first place.

**But your case might not be as smooth as mine** and you may actually need to get the electron version it needs. But downloading 30GB of update is surely not the way forward.

Instead of getting the entire source code and then building the binaries from it, you can directly install the binary itself.

So, if it was complaining about elctron32 in my case, I would get the binary in this manner:

```

    yay -S electron32-bin

```

And as you can see in the image below, it only needed a package of around 100 MB.

![][10]

I did this for demonstration purpose and since I had an existing electron version from another source, it showed me a potential conflict and asked me to remove the existing electron version.

![][11]

Once that was done, it installed the `electron32-bin` package successfully.

### Summary

When you are in a situation where AUR is downloading GBs of electron/chromium source code, you should do this:

  * See if you can exclude electron from the AUR update and the rest goes fine.
  * Otherwise, install the binary of the required electron version instead of getting the source code.



Hope this helps some of you awesome readers 😸

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][12].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][13] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/aur-electron-update-issue/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/aur-arch-linux/
[4]: https://itsfoss.com/install-yay-arch-linux/
[5]: https://itsfoss.com/content/images/2025/07/aur-update.png
[6]: https://itsfoss.com/content/images/2025/07/AUR-electron-huge-update.png
[7]: https://www.electronjs.org/apps
[8]: https://itsfoss.com/content/images/2025/07/pacman-inspect-package-1.png
[9]: https://itsfoss.com/content/images/2025/07/exclude-packages-from-aur-update.png
[10]: https://itsfoss.com/content/images/2025/07/install-electron-binary-arch.webp
[11]: https://itsfoss.com/content/images/2025/07/conflict-with-electron-binary.webp
[12]: https://itsfoss.com/plus-member-resources/
[13]: https://itsfoss.com/lifetime-membership/
