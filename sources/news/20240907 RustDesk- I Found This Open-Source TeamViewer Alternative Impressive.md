[#]: subject: "RustDesk: I Found This Open-Source TeamViewer Alternative Impressive!"
[#]: via: "https://news.itsfoss.com/rustdesk/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

RustDesk: I Found This Open-Source TeamViewer Alternative Impressive!
======
RustDesk is a fantastic secure remote desktop tool. Let's take it for a
spin!
[![][1]][2]

Remotely controlling a desktop or mobile device is an ability that's become indispensable in today's technology-driven world. It can be used for things like supporting a friend with their Arch Linux troubles, or more large-scale things like serving an organization's customers facing an IT outage.

With these types of tools, there's no need for physical access to a device, you just need to have an active network connection to it, and the tools configured.

On Linux, there are many [great remote desktop tools][3] that get the job done, and here, we are introducing you to one such option.

### RustDesk: TeamViewer Who? 🤔

![][4]

As the name suggests, [RustDesk][5] is written in the [Rust][6] programming language. It is offered by a Singapore-based company called [Purslane Ltd][7], with the founder [Huabing Zhou][8] also being based out of there.

Made freely available under the [AGPL-3.0 License][9], it has over 200 contributors, ensuring that it never goes unmaintained, or is subject to vulnerabilities.

#### ⭐ Key Features

For a remote desktop client, RustDesk offers plenty of usable features that help it take the fight to popular closed-source options. Some of the most interesting ones include:

  * **Lightweight**
  * **Cross-Platform**
  * **End-to-end Encryption**



#### 💻 User Experience

The test setup for this is divided into three different devices. One is the primary system, a laptop with Ubuntu 22.04.4 LTS installed, the second one is a desktop with dual-boot Ubuntu 22.04.4 LTS/Windows 10 22H2, and the final one is a smartphone with Android 14.

Both Ubuntu setups were running on the X11 session. Interestingly, RustDesk showed a non-dismissible warning about “ _login screens using Wayland not being supported_ ” throughout testing.

The first test I did was to see **remote control from Linux to Linux**. When RustDesk launched on the Ubuntu-equipped desktop ( _itsfoss-com_ ), it showed me the ID and password for the device.

![][10]

I entered the credentials into RustDesk on the Ubuntu-equipped laptop ( _Phoenix_ ), and initialized the connection.

![][11]

After successfully connecting, I could control _itsfoss-com_ using a mouse and keyboard, with **handy quick-access menus** at the top of the app **** helping me control RustDesk on _Phoenix_.

With those, I could go into full-screen mode, change the display settings, record the screen, end the connection and a few more things.

![][12]

After I disconnected from _itsfoss-com_ on my Ubuntu laptop, I noticed that RustDesk had remembered that device, it showed me its ID, along with the username, device name, and a Tux logo.

![][13]

Similarly, I tested **remote control from Linux to Windows**. After downloading the portable _.exe_ file, I double-clicked on it to launch RustDesk. ****** Connecting to this from the app on Ubuntu ( _Phoenix_ ) was the same, with familiar controls being shown.

![That's a NCR Veteran Ranger in the background][14]

On the Windows side ( _Cerberus_ ), there was a widget that contained the same controls as the quick-access menus. One of those options was to initiate a chat, I sent a message from both clients, and the result was this. 👇

![][15]

This is a great feature for when one has to provide technical support to someone on the other end, both parties can easily communicate with each other with this.

Finally, I did a **remote control test from Android to Linux** , and the results were good. The user interface followed what the desktop apps have, with an option to enable the on-screen keyboard.

If you want to control an Android device from Linux, then keep in mind that you won't be able to control the Android device, just see what's going on.

![][16]

However, **not everything was all good**. When I tried quitting the RustDesk app from the tray icon on Ubuntu ( _Phoenix_ ), it asked me for authentication ( _my account password_ ) to stop the service, before it would quit.

If I launched RustDesk again in the same session, then I would have to authenticate once more to manually start the service. It is probably a security feature, but, it could have an option to make it a seamless experience.

Moreover, the same service auto-started, when I logged into a new session.

On Windows, if you go for the portable .exe package and delete it after use, the files will still stay on your system. For completely getting rid of it, you will have to access the _Local_ folder under _AppData_ , and delete the folder named “ _rustdesk_ ”.

You can do that by going into:

```

    C: > Users > [Username] > AppData > Local

```

If you opt for the _.msi_ package, then you don't need to worry about the above, as it's a fully-fledged installer that will install RustDesk application onto your Windows system.

You can uninstall the app using the control panel or from the start menu.

Apart from these small hiccups, my experience with RustDesk was great, and **I would gladly use this over closed-source options** like [TeamViewer][17] and [AnyDesk][18] for my remote computing needs.

### ⚙️ Installing RustDesk on Linux

You can source the latest RustDesk release from the [official repo][19], where you should go for the latest numbered, non-pre-release version. There are packages for **Linux** , **Android** , **Windows** , **macOS** , and **iOS**.

They also provide both free and paid self-hosting plans, which range from $0 to $999, those can be explored on the [official website][20].

[RustDesk][19]

If you were searching for the source code, or wanted to contribute to the project, its [GitHub][21] repo is the place to be.

_💬 Have you used RustDesk before? What aspect of it did you like or dislike?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/rustdesk/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/remote-desktop-tools/
[4]: https://news.itsfoss.com/content/images/2024/08/RustDesk_a.png
[5]: https://rustdesk.com/
[6]: https://itsfoss.com/tag/rust-basics/
[7]: https://opencorporates.com/companies/sg/53481265A
[8]: https://www.linkedin.com/in/zhouhuabing/
[9]: https://www.gnu.org/licenses/agpl-3.0.en.html
[10]: https://news.itsfoss.com/content/images/2024/08/RustDesk_b.png
[11]: https://news.itsfoss.com/content/images/2024/08/RustDesk_c.png
[12]: https://news.itsfoss.com/content/images/2024/08/RustDesk_d.png
[13]: https://news.itsfoss.com/content/images/2024/08/RustDesk_g.png
[14]: https://news.itsfoss.com/content/images/2024/08/RustDesk_e.png
[15]: https://news.itsfoss.com/content/images/2024/08/RustDesk_f.png
[16]: https://news.itsfoss.com/content/images/2024/08/RustDesk_h.png
[17]: https://www.teamviewer.com/en-us/
[18]: https://anydesk.com/en
[19]: https://github.com/rustdesk/rustdesk/releases
[20]: https://rustdesk.com/pricing.html
[21]: https://github.com/rustdesk/rustdesk
