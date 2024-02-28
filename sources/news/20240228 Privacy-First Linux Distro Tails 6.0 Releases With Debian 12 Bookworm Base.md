[#]: subject: "Privacy-First Linux Distro Tails 6.0 Releases With Debian 12 Bookworm Base"
[#]: via: "https://news.itsfoss.com/tails-6-0-release/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Privacy-First Linux Distro Tails 6.0 Releases With Debian 12 Bookworm Base
======
Want to protect your privacy? Tails 6.0 should let you do that better.
Tails is a popular Linux distribution for those who prefer [tools that protect privacy][1]. Once it is configured on a USB drive, you can use it on any computer; just plug it in and get started.

With a recent announcement, the developers have released the next major upgrade, i.e, **Tails 6.0**. Let's see what it has to offer.

💡

The distro ****does not retain any data after you shut it down****. Be it settings, your files, your logins, anything. But, you can set up “ _ _Persistent Storage__ ” if you want to keep important files and settings behind an encrypted wall.

**Suggested Read** 📖

![][2]

## 🆕 Tails 6.0: What's new?

![][3]

Based on the **Debian 12 “Bookworm”** release, Tails 6.0 features the [GNOME 43][4] desktop environment with plenty of new features and improvements.

Some **key highlights** include:

  * **User Interface Improvements**
  * **Updated Application Suite**
  * **Better Devices Support**



**Suggested Read** 📖

![][5]

### User Interface Improvements

![][6]

Tails 6.0 features **four new display modes** that consist of a “ _light_ ” mode, which is the default one with a bright look, a “ _dark_ ” mode with a blacked out look. Then there's a “ _night light_ ” mode that has warmer colors and less brightness, and a dark mode version of it.

### Updated Application Suite

![][7]

For starters, **Thunderbird on Tails 6.0 can now easily configure Gmail accounts**. Then there's the GNOME screenshot/screen recording tool, and the [GNOME Text Editor][8] being introduced, thanks to GNOME 43.

Other than that, many existing applications were updated, some highlights include:

  * **KeePassXC 2.7.4**
  * **Inkscape 1.2.2**
  * **Audacity 3.2.4**
  * **GIMP 2.10.34**
  * **Tor Browser 13.0.10**
  * **Metadata Cleaner 2.4.0**



### Better Device Support

![][9]

Going forward with this release, when an external storage device is plugged into the system, Tails will automatically mount it and even open up a dialog to unlock it if the device is encrypted.

![][10]

After reading the above, you maybe worried; What if some malicious USB device is plugged in? Well, Tails takes care of that too.

When your system is locked, Tails will not accept any new devices, you have to unlock the system to use any new USB device.

For users of Persistent Storage, Tails will now alert you if there are any hardware failures on your USB drive so that you can back up your data quickly.

### 🛠️ Other Changes and Improvements

To wrap this up, here are some other changes worth noting:

  * Removal of the “ _Remove metadata_ ” option from the shortcut menu in the Files browser.
  * Similarly, the “ _Wipe_ ” and “ _Wipe available disk space_ ” options were also removed from the shortcut menu.
  * Various fixes to the screen keyboard that had issues handling special characters and non-Latin scripts.
  * Passphrase suggestions during Persistent Storage creation now support _Catalan_ , _German_ , _Italian_ , _Portuguese_ , and _Spanish_.



You may go through the official [release notes][11] or the [changelog][12] to explore rest of the technical changes.

## 📥 Download Tails 6.0

This release of Tails can be downloaded from the [official website][13], and if you are running an older version of Tails, you can also refer to the [upgrade guide][14] to get the latest version.

[Tails 6.0][13]

_💬 Do you use Tails? How has the experience been so far?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/tails-6-0-release/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/privacy-tools/
[2]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[3]: https://news.itsfoss.com/content/images/2024/02/Tails_a.png
[4]: https://news.itsfoss.com/gnome-43-release/
[5]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[6]: https://news.itsfoss.com/content/images/2024/02/Tails_b.png
[7]: https://news.itsfoss.com/content/images/2024/02/Tails_c.png
[8]: https://apps.gnome.org/TextEditor/
[9]: https://news.itsfoss.com/content/images/2024/02/Tails_d.png
[10]: https://news.itsfoss.com/content/images/2024/02/Tails_e.png
[11]: https://tails.net/news/version_6.0/index.en.html
[12]: https://gitlab.tails.boum.org/tails/tails/-/blob/master/debian/changelog
[13]: https://tails.net/install/index.en.html
[14]: https://tails.net/doc/upgrade/index.en.html
