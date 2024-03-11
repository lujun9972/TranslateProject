[#]: subject: "Linux Kernel 6.8 Released! Goes Big On Hardware Support"
[#]: via: "https://news.itsfoss.com/linux-kernel-6-8-release/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux Kernel 6.8 Released! Goes Big On Hardware Support
======
Raspberry Pi 5 graphics, Intel Xe, Snapdragon, Nintendo, you name it.
You will probably find it here.
With every Linux kernel release, we have numerous refinements and features. And, Linux kernel 6.8 is particularly interesting for all the hardware support it brings in.

Not to forget, Linux kernel 6.8 is planned to be included with Ubuntu 24.04 LTS, so you should get all the benefits with Ubuntu's next big release.

Here's what Linus Torvalds had to [mention][1]:

> This is not the historically big release that 6.7 was - we seem to be back to a fairly average release size for the last few years. You can see it in the overall diffstats too - this looks like an average release in pretty much all respects, and we don't have (for example) any obvious big new filesystems or architectures.

Furthermore, he also pointed out this is the last release featuring less than ten million git objects. So, **Linux kernel 6.9 will be the first one to surpass ten million git objects.**

So, what's new? Let us find out.

### Linux Kernel 6.8: What's New?

While it is a non-LTS release, it will come baked into most of the upcoming major distro releases, including Fedora 40 and Ubuntu 24.04 LTS.

Therefore, you do not have to worry about [upgrading the Linux kernel manually][2] if you plan to upgrade to the newer distro releases.

Highlights of the release include:

  * **New experimental Intel XRM driver**
  * **Raspberry Pi 5 graphics driver support**
  * **Support for upcoming AMD hardware**
  * **Initial support for Snapdragon Gen 3**



#### The New Intel Improvements

![][3]

The icing of the release — is the new experimental Intel XRM driver as an alternative to i915 to support Intel Lunar Lake graphics.

While this may not mean much to most people not running the latest Intel graphics hardware, it is good to see bleeding-edge support as usual.

Not just limited to the graphics, there are improvements to Intel Meteor Lake CPUs to be able to hit higher clocks, Intel Arrow Lake sound support, Lunar lake thunderbolt support, and more.

By the way, if you are confused about the new [naming scheme for Intel processors][4], we published an article about it last month:

![][5]

#### Rusty Additions

The Rust toolchain was upgraded to Rust 1.74.1. The improvements existed in the Linux-next branch before the [pull request for Linux Kernel 6.8][6].

And, there's also the [first Rust-written network PHY driver][7] as spotted by [Phoronix][8].

In addition, initial Rust support for LoongArch architecture has also been added with this release.

![][9]

#### More Hardware Goodness

![][10]

AMD hardware also gets a considerable set of new support with the Linux kernel 6.8.

Such as the P-State Preferred Core driver, removal of FreeSync Support in favor of Variable Refresh Rate (VRR), supporting newer RDNA 4 graphics, and initial work to support AMD Zen 5 platform.

Moving on from AMD, we have mobile chips that includes Snapdragon Gen 3, and X Elite SoCs.

Google's Tensor G1 also gets a spot in the mainline.

Not to forget, the V3D DRM driver adding support for Raspberry Pi 5 graphics/display.

The improvements also include:

  * **Gigabyte AORUS Waterforce driver**
  * **Nintendo Switch Online controllers support**
  * **Apple M1 USB4 support**
  * **Compatibility improvements for several low-end ARM-based handheld devices**



For all the technical details, refer to the [changelog][11] or the latest [shortlog][1].

### Installing Linux Kernel 6.8

If you are running rolling-release distros such as Arch or Fedora, then it is quite straightforward to upgrade.

You just have to wait a bit, as these distros take their time in releasing the update.

As for the rest, you can either wait for a major release (including Fedora 40 and Ubuntu 24.04 LTS), or **upgrade to the latest mainline Linux kernel on Ubuntu** by following our guide:

![][5]

🚧

We do not recommend you to upgrade the Linux kernel manually unless you really need to resolve some issue

You can download the tarball for the latest Linux kernel from its [official website][12] ( _it takes time for it to be available after release_ ).

[Linux Kernel 6.8][12]

_💬 What do you think of this kernel release?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/linux-kernel-6-8-release/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://lore.kernel.org/lkml/CAHk-=wiehc0DfPtL6fC2=bFuyzkTnuiuYSQrr6JTQxQao6pq1Q@mail.gmail.com/
[2]: https://itsfoss.com/upgrade-linux-kernel-ubuntu/
[3]: https://news.itsfoss.com/content/images/2024/03/intel-linux-kernel6-8.png
[4]: https://itsfoss.com/intel-processor-naming/
[5]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[6]: https://lore.kernel.org/lkml/20240108012055.519813-1-ojeda@kernel.org/
[7]: https://git.kernel.org/pub/scm/linux/kernel/git/netdev/net-next.git/commit/?id=d6beb085e8ff3d9547df8a5a55f15ccc7552c5d0
[8]: https://www.phoronix.com/news/Linux-6.8-Rust-PHY-Driver
[9]: https://news.itsfoss.com/content/images/2023/04/Follow-us-on-Google-News.png
[10]: https://news.itsfoss.com/content/images/2024/03/hardware-linux-kernel6-8.png
[11]: https://cdn.kernel.org/pub/linux/kernel/v6.x/ChangeLog-6.8
[12]: https://www.kernel.org/
