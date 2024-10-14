[#]: subject: "6 New Things to Look Out For in Ubuntu 24.10"
[#]: via: "https://news.itsfoss.com/ubuntu-24-10/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

6 New Things to Look Out For in Ubuntu 24.10
======
Ubuntu 24.10 is a fantastic release. Learn more about its features here.
[![][1]][2]

Every year, we get to see a new interim release for Ubuntu, which receives nine months of support from [Canonical][3], after which there are no new updates or critical security patches for the release.

Usually, people who prefer a stable experience stick to the long-term support ([LTS][4]) release of Ubuntu, maintained for a longer period of time, [up to 12 years][5], depending on the release.

Now, a couple of months after [Ubuntu 24.04 LTS][6] release, we have the **Ubuntu 24.10** interim release, codename “[ **Oracular**][7] **** [**Oriole**][8]”.

![][9]

But, that's not all; this release also [marks][10] **Ubuntu's 20th anniversary** , with special wallpapers, and a very ethereal-sounding startup sound, making this release a truly unique one.

Keep on reading to see what else is new with Ubuntu 24.10 “Oracular Oriole”. 👇

### 1\. Linux Kernel 6.11

![][11]

Powering Ubuntu 24.10 is [Linux kernel 6.11][12], which has brought about some interesting hardware-focused upgrades.

There are **patches for AMD's upcoming RDNA4 GPUs** , initial support for Intel's Battlemage GPUs, simplified _HWMon_ code for Intel CPUs, and better support for the LoongArch CPU architecture.

### 2\. GNOME 47

![][13]

The second highlight of Ubuntu 24.10 is undoubtedly [GNOME 47][14], which has brought about many cool features like support for **accent colors** , which, by the way, Ubuntu already had. With this, they are now following what's being done upstream.

To complement that, there are **many updated GNOME apps** such as GNOME Terminal 3.54.0, System Monitor 47, Clocks 46, Calculator 47, and Eye of GNOME 47.

Additionally, there are **new wallpapers** that were selected from the usual [wallpaper competition][15] that Canonical runs before a new Ubuntu release comes out.

You can go through our earlier coverage if you would like to know more about GNOME 47. 👇

![][16]

### 3\. Better User Experience

![Updated File explorer in Ubuntu 24.10.][17]

The file manager app Nautilus (Files) sees many improvements, with the most notable one being the redesigned sidebar, which now **features removable bookmarks** in the lower part of the left-hand column.

Personally speaking, I prefer my bookmarks on the top part of the sidebar, but I really like the decluttered look of the new one.

Similarly, **any internal storage devices will now show up in the sidebar by default** , the file transfer dialog has been reorganized, and the “Other Locations” page has been replaced with a new “Network” page.

![][18]

For the Dock, Ubuntu 24.10 introduces **support for progress bars on Snap apps** that are being updated in the background. Additionally, when right-clicking on any app, an updated context menu is shown with the app name at the top.

### 4\. App Center Tweaks

![App Center upgrades with Ubuntu 24.10.][19]

The [Flutter][20]-based App Center also gets some attention, with **the “ _Manage_ ” page allowing for easy Snap app uninstalls** (which is also available on Ubuntu 24.04 LTS) and a new category called “ _Art and Design_ ”, which features popular apps such as GIMP, Inkscape, Darktable Krita, and more.

### 5\. Security Upgrades

![The Security Center on Ubuntu 24.10.][21]

Continuing the trend of introducing Flutter-based core apps, Ubuntu 24.10 debuts [Security Center][22] as a dedicated application that is designed to expose the hard-to-access features of the distro.

Currently, it only has the experimental App Permissions security setting, which can be enabled for Snap apps. As you can see above, after I enabled it, a security notification popped up, asking for permission before I could upload files to a website using Firefox (snap).

Canonical has also worked on bringing support for the [OpenVEX][23] and [OSV][24] formats for vulnerability reporting and improved PPA security, with **APT now requiring stronger signatures for PPAs and any other repositories**.

![][16]

### 6\. Developer-Specific Changes & Package Updates

![Just a stand in screenshot of the Fastfetch output on Ubuntu 24.10.][25]

We close this out with some developer-focused changes and application upgrades that I haven't mentioned above:

  * Up-to-date versions of Python, Java, Go, C, C++, and .Net.
  * Cargo and Rust 1.80 being the default, with previous versions available in the archives.
  * Inclusion of [Valkey][26], an open source key-value data store designed for large workloads like caching.
  * [TCK][27]-certified [OpenJDK 21][28] and [OpenJDK 17][29] packages for _amd64_ , _arm4_ , _s390x_ , _ppc64el_ and _armhf_.
  * Updated software in the expanded installation such as LibreOffice 24.8.1, Shotwell 32.7, Transmission 4.06, Remmina 4.35, etc.



The [release blog][30] is worth a read if you are interested in learning more about this release.

### 📥 Get Ubuntu 24.10

You can grab this release from the [official website][31], if that proves to be a slow experience ( _it was for me)_ , you can get it from one of the alternative [download mirrors][32].

[Ubuntu 24.10][31]

_💬 Are you going to install this interim release? Sticking to the LTS release? Let me know below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-24-10/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://canonical.com/
[4]: https://itsfoss.com/long-term-support-lts/
[5]: https://news.itsfoss.com/ubuntu-24-04-lts-support/
[6]: https://news.itsfoss.com/ubuntu-24-04-lts/
[7]: https://www.merriam-webster.com/dictionary/oracular
[8]: https://simple.wikipedia.org/wiki/Oriole
[9]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_a.png
[10]: https://ubuntu.com/20years
[11]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_a2.png
[12]: https://news.itsfoss.com/linux-kernel-6-11-release/
[13]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_b.png
[14]: https://news.itsfoss.com/gnome-47/
[15]: https://discourse.ubuntu.com/t/vote-oracular-oriole-wallpaper-competition/47006/10
[16]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[17]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_d-2.png
[18]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_c.png
[19]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_f.png
[20]: https://flutter.dev/
[21]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_g.png
[22]: https://news.itsfoss.com/ubuntu-security-center-near-stable/
[23]: https://github.com/openvex
[24]: https://osv.dev/
[25]: https://news.itsfoss.com/content/images/2024/10/Ubuntu_24.10_h.png
[26]: https://valkey.io/
[27]: https://en.wikipedia.org/wiki/Technology_Compatibility_Kit
[28]: https://openjdk.org/projects/jdk/21/
[29]: https://openjdk.org/projects/jdk/17/
[30]: https://canonical.com/blog/canonical-releases-ubuntu-24-10-oracular-oriole
[31]: https://ubuntu.com/download/desktop
[32]: https://launchpad.net/ubuntu/+cdmirrors
