[#]: subject: "Packet is the Linux App You Didn’t Know You Needed for Fast Android File Transfers"
[#]: via: "https://itsfoss.com/linux-android-file-transfer/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Packet is the Linux App You Didn’t Know You Needed for Fast Android File Transfers
======

[![Warp Terminal][1]][2]

Most file sharing today takes place through cloud services, but that's not always necessary. **Local file transfers are still relevant** , letting people send files directly between devices on the same network without involving a nosy middleman ( _a server, in this case_ ).

Instead of uploading confidential documents on WhatsApp and calling it a day, people could share them directly over their local network. This approach is faster, more private, and more reliable than relying on a third-party server.

_Remember, if you value your data, so does_ [_Meta_][3] _._ 🕵️‍♂️

That’s where [Packet][4] comes in, offering an easy, secure way to transfer files directly between Linux and Android devices.

### Wireless File Transfers via Quick Share

It is **a lightweight, open source app for Linux** that makes transferring files effortless. It leverages a partial implementation of Google's [Quick Share][5] protocol ( _proprietary_ ) to enable easy wireless transfers over your local Wi-Fi network ( _via mDNS_ ) without needing any cables or cloud servers.

In addition to that, **Packet supports device discovery via Bluetooth** , making it easy to find nearby devices without manual setup. It can also be integrated with GNOME’s [Nautilus file manager][6] ( _Files_ ), allowing you to send files directly from your desktop with a simple right-click ( _requires additional configuration_ ).

**⭐ Key Features**

  * Quick Share Support
  * Local, Private Transfers
  * File Transfer Notifications
  * Nautilus Integration for GNOME



### How to Send Files Using Packet?

![][7]

First things first, you have to download and install the latest release of Packet from [Flathub][8] by running this command in your terminal:

```

    flatpak install flathub io.github.nozwock.Packet

```

Once launched, sending files from your Linux computer to your Android smartphone is straightforward. Enable Bluetooth on your laptop/computer, then click on the big blue " _Add Files_ " button and select the files you want to send.

![Adding new files for transfer to Packet is easy.][9]

You **can also drag and drop files directly into Packet** for a quicker sharing experience. If you are looking to transfer a whole folder, it’s best to first compress it into an archive like a _TAR_ or _ZIP_ , then send it through Packet for transmission.

Once you are done choosing files, choose your Android phone from the recipients list and verify the code shown on screen.

![File transfers from Linux to Android are lightning fast!][10]

Though, before you do all that, ensure that [Quick Share][11] is set up on your smartphone to allow Nearby sharing with everyone. Additionally, take note of your device’s name; this is how it will appear on your Linux machine when sending/receiving files.

When you start the transfer, your smartphone will prompt you to " _Accept_ " or " _Decline_ " the Quick Share request. Only proceed if the PIN or code shown on both devices matches to ensure a secure transfer.

![][12]

Transferring files the other way around, **from Android to Linux** , is just as simple. On your Android device, select the files you want to share, tap the " _Share_ " button, and choose " _Quick Share_ ". Your Linux computer should appear in the list if Packet is running and your device is discoverable.

![File transfers from Android to Linux are the same!][13]

You can change your Linux device’s name from the " _Preferences_ " menu in Packet ( _accessible via the hamburger menu_ ). This is the name that will show up on your Android device when sharing files.

Packet also **shows handy system notifications** for file transfers, so you don’t miss a thing.

![Packet shows helpful notifications and lets you change a few basic settings.][14]

If you use the GNOME Files app ( _Nautilus_ ), then there’s [an optional plugin][15] that adds a " _Send with Packet"_ option to the right-click menu, making it even easier to share files without opening the app manually.

Overall, Packet feels like a practical tool for local file sharing between devices. It works well across Android and Linux devices, and can do the same for two Linux devices on the same network.

And, I must say, it gives tough competition to LocalSend, another file transfer tool that’s [an AirDrop alternative for Linux users][16]!

**Suggested Read 📖**

![][17]

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][18].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][19] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][19]

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-android-file-transfer/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.meta.com/
[4]: https://github.com/nozwock/packet
[5]: https://en.wikipedia.org/wiki/Quick_Share
[6]: https://itsfoss.com/nautilus-tips-tweaks/
[7]: https://itsfoss.com/content/images/2025/07/packet-about-dialog.png
[8]: https://flathub.org/apps/io.github.nozwock.Packet
[9]: https://itsfoss.com/content/images/2025/07/packet-linux-send-1.png
[10]: https://itsfoss.com/content/images/2025/07/packet-linux-send-3.png
[11]: https://support.google.com/android/answer/9286773
[12]: https://itsfoss.com/content/images/2025/07/packet-linux-send-5.png
[13]: https://itsfoss.com/content/images/2025/07/packet-android-send-1.jpg
[14]: https://itsfoss.com/content/images/2025/07/packet-gnome-notifications.png
[15]: https://ubuntuhandbook.org/index.php/2025/06/android-quick-share-nautilus-integration/
[16]: https://news.itsfoss.com/localsend/
[17]: https://itsfoss.com/content/images/icon/android-chrome-192x192-528.png
[18]: https://itsfoss.com/plus-member-resources/
[19]: https://itsfoss.com/lifetime-membership/
