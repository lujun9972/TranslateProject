[#]: subject: "LocalSend: An Open-Source AirDrop Alternative For Everyone!"
[#]: via: "https://news.itsfoss.com/localsend/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

LocalSend: An Open-Source AirDrop Alternative For Everyone!
======
It's time to ditch platform-specific solutions like AirDrop!
[![][1]][2]

If you are an Apple user, then you have most likely used [AirDrop][3] to wirelessly transfer files to other Apple devices.

Similarly, for Android, there's [Quick Share][4] (formerly known as Nearby Share) that does the job perfectly. For Linux, there's an app called [Warp][5] that does the same, but between Linux and Windows only.

And, if you want to transfer between your Android and Windows device, you will have to try the Windows Phone Link app.

It is subjective to what your use-case is, and what you find more intuitive. But, what if I said that there's an open-source app that can do file transfers, but across all the above-mentioned devices? 🤔

With this [First Look][6], we will be taking a look at an **open-source** **file transfer app** called “ **LocalSend** ”, which allows you to securely share files and messages across devices.

### LocalSend: Overview ⭐

![][7]

LocalSend is **a cross-platform file transfer app** that's freely available under the [MIT License][8], and is maintained actively by various contributors. It is primarily written in the [Dart][9] programming language.

Some **key features** include:

  * **Offline Sharing**
  * **No Account Creation**
  * **End-to-end Encryption**



#### Initial Impressions 👨‍💻

For testing this out, I disconnected the modem from my Wi-Fi router, but this should also work well with internet access, and even for wired networks in a home or office setting.

Do note that the sending/receiving speeds will depend on your router and/or Ethernet cables.

First, I checked out how **file transfers between Linux and Android** worked.

On my Ubuntu 22.04.4-equipped laptop, I installed the official flatpak, and similarly, the official app for my Android 14-equipped Samsung smartphone.

![][10]

After selecting a few images, documents, and audio files by going into the “ _Send_ ” page, I initiated transfer to my Android device ( _Determined Pineapple_ ), for which approval was required on the phone's app to start receiving files.

![][11]

As you can see below, the Android app asked me whether I wanted to accept or reject the files being sent by “ _Big Banana_ ”, the name of my Ubuntu device on the LocalSend app.

![Receiving files from Ubuntu on Android using LocalSend][12]

Before I accepted, I went into the “ _Options_ ” menu to review what files I was about to receive, I had the chance to select specific files, and even rename them before the upload started.

During the transfer, a handy progress bar showed up, with options to enable “ _Advanced_ ” that would show me detailed metrics like transfer speed, and another option to “ _Cancel_ ” the transfer.

![][13]

After the file transfer was done, I was shown a “ _Finished_ ” prompt on both the apps, and I must say, **the transfer speeds were superb**.

I then checked out how **file transfers between Android and Linux went**.

The experience was pretty similar to what I found on the Linux app, with tight integration with Android's “ _Share_ ” functionality, that allowed me to directly share files from the gallery app of my phone.

![Sending files from Android to Ubuntu using LocalSend][14]

Before I accepted the transfer on my Ubuntu laptop, I could rename the files, and remove the ones I didn't want.

![][15]

After the transfer was complete, I clicked on the “ _Advanced_ ” option to see the speeds it went to, and it was good, seeing those were just .jpg files.

Finally, I checked how **file transfers between Linux and Windows worked**.

I booted up a Windows 10-equipped [virtual machine][16], and installed the official .exe for it. When I started the app, it was showing me three different “ _Big Banana_ ” devices, I went with the first one, and started transferring two .exe files that were already present.

![Sending files from Windows to Ubuntu using LocalSend][17]

The transfer was a success, and I didn't face any problems, with transfer speeds going up to 40 MB/s.

As for the weird three-device issue, my best bet is that it was a bug caused by me running a VM on the same device, and it probably also had to do something with how VirtualBox handles networking.

📋

I also tried the messaging feature with LocalSend, it worked well. I could also send installed apps ( _ _as .APKs__ ) from my smartphone to other devices.

### Closing Thoughts

Overall, **my experience with LocalSend was great!** I have now installed it on all my devices to facilitate wireless file transfers. 😃

Though, **smaller transfers are the way to go with this app**. As I tried a ~90 GB transfer from my Ubuntu laptop to my Android tablet, and the speeds were fluctuating a lot, in the end, the transfer just stopped due to a connection error.

But, in comparison to [KDE Connect][18], I would say that LocalSend is a better option for file transfers. I say that due to its more intuitive user experience and comparable transfer speeds, that ought to catch on with most users.

### 📥 Get LocalSend

You can get LocalSend for a wide range of devices, such as **Linux** , **Android** , **Windows** , **iOS** , and **macOS**.

For Linux users, they can get it from the [Flathub store][19], for Android, the [Play Store][20], and for iOS/iPadOS/macOS, the [App Store][21].

Those who are looking for alternative packages can head to the [official website][22] or its [GitHub][23] repo.

[LocalSend][22]

_💬 Do let me know if you know of other similar tools in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/localsend/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://support.apple.com/en-us/119857
[4]: https://support.google.com/android/answer/9286773?hl=en
[5]: https://news.itsfoss.com/warp-file-sharing/
[6]: https://news.itsfoss.com/tag/first-look/
[7]: https://news.itsfoss.com/content/images/2024/07/LocalSend_a.png
[8]: https://opensource.org/license/mit
[9]: https://dart.dev/
[10]: https://news.itsfoss.com/content/images/2024/07/LocalSend_b.png
[11]: https://news.itsfoss.com/content/images/2024/07/LocalSend_c.png
[12]: https://news.itsfoss.com/content/images/2024/07/local-send-android-screenhots.jpg
[13]: https://news.itsfoss.com/content/images/2024/07/LocalSend_h.png
[14]: https://news.itsfoss.com/content/images/2024/07/localsend-android-2.jpg
[15]: https://news.itsfoss.com/content/images/2024/07/LocalSend_m.png
[16]: https://itsfoss.com/virtual-machine/
[17]: https://news.itsfoss.com/content/images/2024/07/LocalSend_n.png
[18]: https://kdeconnect.kde.org/
[19]: https://flathub.org/apps/org.localsend.localsend_app
[20]: https://play.google.com/store/apps/details?id=org.localsend.localsend_app
[21]: https://apps.apple.com/us/app/localsend/id1661733229
[22]: https://localsend.org/download
[23]: https://github.com/localsend/localsend/
