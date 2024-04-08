[#]: subject: "Install ADB and Fastboot on Ubuntu and other Linux"
[#]: via: "https://itsfoss.com/install-adb-fastboot-linux/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Install ADB and Fastboot on Ubuntu and other Linux
======

[![Warp Terminal][1]][2]

If you are a developer and want to install apps directly to Android for testing purposes, then using adb (Android Debug Bridge) and fastboot will get things done in the most efficient manner possible.

Sure, it can also be useful when you want to access the device shell to execute commands directly which is quite helpful for unlocking the bootloader and installing custom ROMs.

So in this tutorial, I will walk you through how you can install adb and fastboot on various Linux distributions.

### How to install ADB and Fastboot on Linux

You get adb and fastboot available in the default repository of almost every modern Linux distribution and it does not require any third-party repository.

So let's take a look at how those two packages can be installed on various Linux distributions.

**For Ubuntu/Debian:**

```

    sudo apt install adb fastboot

```

**For Fedora Linux:**

```

    sudo dnf install android-tools

```

**For Arch Linux:**

```

    sudo pacman -S android-tools

```

That's it. Once you are done with the installation, you can check the installed version of adb using the following command:

```

    adb --version

```

![][3]

🚧

Please note that some manufacturers do not like unlocking bootloader. Do check if it violates the warranty.

### How to use ADB in Linux

To use adb, the first step is to enable the developer options on your Android device. For that, first, go to `Settings` and find the software information.

Inside the software information, tap multiple times on the build number and it will enable the developer options for you:

![][4]

Next, go to the developer options and enable the USB debugging option:

![][5]

Now, connect your device to your computer and start the adb server using the following command:

```

    sudo adb start-server

```

![][6]

Once you start the adb server, it will prompt you on your phone asking for your permission to allow USB debugging (if you don't see the below prompt, re-enable USB debugging while keeping your phone connected to the computer):

![][7]

After allowing the USB debugging, check if the device is connected or not using the following:

```

    adb devices

```

![][8]

#### Installing APK using ADB

To install an apk to your Android directly, all you have to do is use the `install` flag and specify the name or path to the APK you are trying to install:

```

    adb install <apk_name or path/to/apk>

```

For example, here, I want to install the `pianoli.apk` file which is located inside the home directory, so I will be using the following:

```

    adb install ~/pianoli.apk

```

![][9]

#### Executing shell commands

To execute shell commands in a connected device, the first step is to get into the shell using the following command:

```

    adb shell

```

Now, you can use the basic commands. For example, here, I used the ls command to list the content of the current directly:

![][10]

#### Sending files from the computer to the Android

To send files to the connected Android, you'd have to use the `adb push` command by specifying the filename and location where to send the file in Android:

```

    adb push Filename where/to/send/in/Android

```

Let's say I want to send `Image.jpg` to the `/storage/emulated/0` directory, so I will be using the following:

```

    adb push Image.jpg /storage/emulated/0

```

![][11]

#### Sending files from Android device to local machine

To send files from the connected Android device to your local computer, you'll have to use the `adb pull` command as shown here:

```

    adb pull /path/to/file/in/Android /target

```

For example, here, I've sent the `Image.jpg` file located in the `/storage/emulated/0` directory of my Android phone to my home directory:

```

    adb pull /storage/emulated/0/Image.jpg ~/

```

![][12]

I hope it gave you enough pointers to get started with adb on Ubuntu. Let me know if you have questions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-adb-fastboot-linux/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/03/Check-the-installed-version-of-adb-on-linux.png
[4]: https://itsfoss.com/content/images/2024/03/Enable-developer-options-in-android.gif
[5]: https://itsfoss.com/content/images/2024/03/enable-usb-debugging-in-android.jpg
[6]: https://itsfoss.com/content/images/2024/03/Start-adb-server.png
[7]: https://itsfoss.com/content/images/2024/03/Allow-USB-debugging.jpg
[8]: https://itsfoss.com/content/images/2024/03/List-adb-devices.png
[9]: https://itsfoss.com/content/images/2024/03/install-apk-using-adb.png
[10]: https://itsfoss.com/content/images/2024/03/Execute-commands-in-android-shell-through-adb.png
[11]: https://itsfoss.com/content/images/2024/03/Send-file-to-android-device.png
[12]: https://itsfoss.com/content/images/2024/03/Send-files-from-android-to-local-computer.png
