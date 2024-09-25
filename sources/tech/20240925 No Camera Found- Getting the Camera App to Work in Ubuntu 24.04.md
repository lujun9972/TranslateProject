[#]: subject: "No Camera Found? Getting the Camera App to Work in Ubuntu 24.04"
[#]: via: "https://itsfoss.com/no-camera-found-ubuntu/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

No Camera Found? Getting the Camera App to Work in Ubuntu 24.04
======

[![Warp Terminal][1]][2]

Ubuntu 24.04 ships with GNOME's new camera app and it doesn't work. It simply fails to recognize the in-built or external webcams.

When you open the Camera app, it shows " **No Camera Found. Connect a camera device** " message.

This may make you doubt your machine's hardware but it likely to be a software issue as the Camera app does not work by default in Ubuntu 24.04.

![][3]

Several [workarounds have been suggested][4] for this problem on various Ubuntu forums. However, the one that worked for me was shared by an It's FOSS reader, Jack.

Here it is.

### Fixing the issue

The trick here is to add yourself to the `video` group. You can [use the usermod command][5] for this purpose. Fortunately or unfortunately, this is a command line fix.

🚧

Type the commands as it is or copy-paste them in the terminal. The `-a` part is of utmost important.

[Open a terminal in Ubuntu][6] (use Ctrl+Alt+T shortcut) and run the following command:

```

    sudo usermod -aG video $USER

```

If this is your first time with sudo, you should know that it asks to enter password. You have to enter your account's password through which you log into the system. **While typing the password, nothing is reflected on the screen**. That's normal in the UNIX/Linux world. Just blindly type the password and press enter.

There is no success message or output for the command.

💡 The usermod command modifies a user account. With `G` you are telling it to modify the groups the user belongs. The `-a` option is crucial because you are asking it to append a new group to existing groups of a user. If you don't use `-a`, then user will only belong to the group you specify (video here) and that will be catastrophic as you cannot use sudo and function as before.

You may have to log out or restart the system before the changes take effect.

When you start the Camera app again, it should work now.

![That's me thinking why Ubuntu won't fix these widespread issues][7]

### Conclusion

I still prefer the good old Cheese camera app.

![][8]

If you want, you can install it using this command:

```

    sudo apt install cheese

```

It is also available from the app store but the Snap version gets priority and that also doesn't work very well.

Each Ubuntu release has bugs, 24.04 is just buggier. I don't understand how this prevalent bug made it to a long-term support release and why it has not been fixed even after the first point release of 24.04.1.

I know we are not going to get answers but at least these troubleshootings help us explore an otherwise uncharted territory.

--------------------------------------------------------------------------------

via: https://itsfoss.com/no-camera-found-ubuntu/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/09/image.png
[4]: https://askubuntu.com/questions/1516484/camera-not-working-in-ubuntu-24-04-for-my-dell-xps-13-9320
[5]: https://linuxhandbook.com/usermod-command/
[6]: https://itsfoss.com/open-terminal-ubuntu/
[7]: https://itsfoss.com/content/images/2024/09/gnome-camera-app-working-ubuntu.webp
[8]: https://itsfoss.com/content/images/2024/09/open-camera-app-ubuntu-24-04.png
