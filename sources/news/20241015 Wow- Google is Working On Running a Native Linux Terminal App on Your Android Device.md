[#]: subject: "Wow! Google is Working On Running a Native Linux Terminal App on Your Android Device!"
[#]: via: "https://news.itsfoss.com/google-android-linux-terminal/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Wow! Google is Working On Running a Native Linux Terminal App on Your Android Device!
======
Google engineers are up to something interesting here. Let's find out!
[![][1]][2]

If you use a smartphone, you've probably come across [Android][3] or are reading this on a device that has it. At its core, Android is powered by a heavily modified version of the [Linux kernel][4] and the Android Open Source Project ([AOSP][5]).

Together, they provide a robust platform for smartphone and [SoC][6] manufacturers to tailor their offerings to meet the needs of both the operating system and its users across a wide range of hardware configurations.

Last week, [Android Authority][7] spotted that Google was working on **a native Linux Terminal app for Android** , which could open up new possibilities for the operating system and its users.

### Terminal Support On Android: What To Expect?

![][8]

Google engineers have been busy [working on][9] enabling a Linux Terminal app via the developer settings on Android, which would enable users to carry out a range of tasks.

It works by making use of the Android Virtualization Framework ([AVF][10]) and opening up a [WebView][11] for connecting to a local [virtual machine][12] (VM) running [Debian][13], allowing the execution of various Linux commands.

In its current form, the Terminal app requires manual configuration of the Linux VM with a Debian image and a corresponding _vm_config.json_ file to work, but this will be simplified soon.

![][14]

And, as you can see above, Google developers are also working on bringing important settings like disk resizing, port forwarding, and recovery of disk partitions to the Terminal app.

They have [begun][15] by adding mock settings pages for those in the Terminal app.

![][16]

They have also been working on [improving support][17] for the various AVF APIs and are currently [working on][18] merging the Terminal app with _LinuxInstaller_ , which is used to download and configure Debian images for running as a VM.

![][19]

Last but not least, there have been some Debian-focused [changes][20] that have improved host-guest communication, which, I believe, are related to the VM functionality of the Terminal app for Android.

And, with a native terminal app, it also opens up the possibility to have other Linux apps run on your Android device, just like you do on Chrome OS.

Sure, running Linux apps may not be an exciting proposition for most mobile-focused users. But, it is **interesting to see that Google is venturing more into the Linux territory** , molding Android to be more capable, and developer-friendly.

**Suggested Read** 📖

![][21]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-android-linux-terminal/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.android.com/
[4]: https://itsfoss.com/linux-kernel-os/
[5]: https://source.android.com/
[6]: https://en.wikipedia.org/wiki/System_on_a_chip
[7]: https://www.androidauthority.com/android-linux-terminal-app-3489887/
[8]: https://news.itsfoss.com/content/images/2024/10/Android_Terminal_WIP_a.png
[9]: https://android-review.googlesource.com/c/platform/packages/modules/Virtualization/+/3295161
[10]: https://source.android.com/docs/core/virtualization
[11]: https://developer.android.com/reference/android/webkit/WebView
[12]: https://itsfoss.com/virtual-machine/
[13]: https://www.debian.org/
[14]: https://news.itsfoss.com/content/images/2024/10/Android_Terminal_WIP_b.png
[15]: https://android-review.googlesource.com/c/platform/packages/modules/Virtualization/+/3304677
[16]: https://news.itsfoss.com/content/images/2024/10/Android_Terminal_WIP_c.png
[17]: https://android-review.googlesource.com/c/platform/system/sepolicy/+/3274016
[18]: https://android-review.googlesource.com/c/platform/packages/modules/Virtualization/+/3307016
[19]: https://news.itsfoss.com/content/images/2024/10/Android_Terminal_WIP_e-1.png
[20]: https://android-review.googlesource.com/c/platform/packages/modules/Virtualization/+/3305418
[21]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
