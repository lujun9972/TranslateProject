[#]: subject: "Handling 'Cannot refresh snap-store' Error in Ubuntu 24.04"
[#]: via: "https://itsfoss.com/update-snap-store/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Handling 'Cannot refresh snap-store' Error in Ubuntu 24.04
======

[![Warp Terminal][1]][2]

One of the annoying issues I encountered in Ubuntu 24.04 LTS is with updating the App Store. It gives the following error:

> Unknown Snapd Exception
>  cannot refresh "snap-store": snap "snap-store" has running apps (snap-store), pids:5263

And the way to get rid of this error and update the snap store is close it first and then manually update it from the terminal:

```

    killall snap-store && sudo snap refresh snap-store

```

Let me discuss it in a bit more detail.

### What happens here

This app store, which is actually Snap Store, shows the updates available for all the snap packages installed on your system. Since the app store itself is a snap package, it shows update available for itself as well.

![App store shows an update on Snap Store][3]

And that becomes an issue because from what I have observed, you cannot update this snap-based app store from within the app store itself. It will result in this error:

![Snap Store throws error if you try updating it from the Snap Store itself][4]

It's one of the half-baked, ignored issues that linger for years, one release after another. Ever since Ubuntu switched to this Snap Store, this issue has been there, but it is not fixed.

So, what can you do? You can resort to manual actions in the terminal.

### Updating Snap Store manually

The idea is to close any running instance of Snap Store first. You can close the application window or kill it from the terminal:

```

    killall snap-store

```

And then, force a refresh, i.e., update of the snap-store:

```

    sudo snap refresh snap-store

```

Wait for the command to complete:

![][5]

If you go to the app store now, you'll see that there is no longer an update available on the Snap Store itself.

### We need better UX

This is a small thing but it dents Ubuntu's image as a beginner-friendly distribution where things 'just work out of the box'.

Terminal and command line are powerful tools and it is always good to have some knowledge of them. But a user should not be forced to jump into the terminal for trivial things such as this.

Ubuntu should at least try and exclude showing the update available on Snap Store and update it in the background. Or, it should at least make the error message more meaningful and actionable for the end user. Just my two cents on the matter.

--------------------------------------------------------------------------------

via: https://itsfoss.com/update-snap-store/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/04/snap-store-update-available.webp
[4]: https://itsfoss.com/content/images/2024/04/snap-store-update-error.webp
[5]: https://itsfoss.com/content/images/2024/04/updating-ubuntu-snap-store-command-line-1.png
