[#]: subject: "Wow! Ubuntu Will Include The Latest Linux Kernel Version in Future Releases"
[#]: via: "https://news.itsfoss.com/ubuntu-latest-kernel/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Wow! Ubuntu Will Include The Latest Linux Kernel Version in Future Releases
======
Ubuntu is making changes to give users a front-row seat for improved
hardware support and latest kernel features.
[![][1]][2]

When it comes to the Linux kernel, staying up to date with a recent LTS release is generally a good idea, if you take security and stability into consideration. For older hardware, things can be different. And, if you are on bleeding edge hardware, you will need the latest Linux kernel (even if it's non-LTS).

But, **those get** [**outdated**][3] **very soon** , thanks to the fast [release cycle][4] of the Linux kernel.

If you are working with a [rolling release][5] distro, then you are just about on the bleeding edge of what the Linux kernel has to offer. But, with Ubuntu, they have always taken the safe route to include a stable kernel release, even if a newer version is available at the time.

Now, [Canonical][6] has [announced][7] some changes to how they will be handling Linux kernels going forward, and it's a good surprise.

### Ubuntu Commits To Newer Linux Kernel Releases

![Source: Canonical][8]

Previously, the Canonical Kernel Team (CKT) used to wait and see how an upstream Linux kernel performed, with flexibility in integrating a more recent version, if it were to arrive at a “workable time-frame”.

However, **that approach caused some dissatisfaction with their consumers,** who wanted to get the latest and greatest features, while also not compromising on hardware support.

Now, Canonical has decided to remedy that by **shipping all future Ubuntu releases with the latest upstream Linux kernel available** at a scheduled Ubuntu release freeze date, even if the kernel is in the Release Candidate (RC) status.

The example shown above is a good illustration of how the overlapping timelines of the Linux kernel and Ubuntu release cycles could interact with each other.

Moving on, for **users of the interim releases of Ubuntu** , if there's an issue with the latest kernel, a bridge kernel of an earlier stable kernel would be provided. It would come handy in situations where things like the drivers and other kernel code that aren't part of the upstream kernel prove to be unstable.

If you are an **Ubuntu LTS release user** , there won't be the need for a bridge kernel, as all upgrades are disabled until stabilization is complete. You see, a new image is generated for the .1 release, which then arrives months after the general availability LTS release, ensuring a smooth transition.

Similarly, users of Livepatch under [Ubuntu Pro][9], don't need to worry, as the service will keep on running as usual.

If you were wondering, **when does this change begin?**

Well, it's starting with the upcoming Ubuntu 24.10 interim release, with the developers laying out how they want to get it done. 👇

![Source: Canonical][10]

While outlining the changes, Director Kernel Engineering at Canonical, [Brett Grandbois][11] noted that:

> With this policy we will be able to be more aggressive about making kernel version commitment announcements for an upcoming release at a much earlier date than previously.
>
> However, due to the uncoupled nature of the upstream and Ubuntu releases as described above the CKT will only be able to announce the kernel version for the next upcoming release, not any successive ones.

Brett also added that **they expect late releases to be a rare occurrence** , and that in most releases, their guidelines won't be necessary, as an upstream kernel release would give the Ubuntu kernel ample time to become stable.

Of course, when it does happen, they are ready to handle it promptly.

If you are keen to learn more about this change, then you can go through the [announcement][7] post.

_💬 This was a surprise to me! What about you? Looking forward to newer kernels on Ubuntu?_

**Suggested Read** 📖

![][12]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-latest-kernel/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/why-distros-use-old-kernel/
[4]: https://itsfoss.com/linux-kernel-release-support/
[5]: https://itsfoss.com/rolling-release/
[6]: https://canonical.com/
[7]: https://discourse.ubuntu.com/t/kernel-version-selection-for-ubuntu-releases/47007
[8]: https://news.itsfoss.com/content/images/2024/08/Ubuntu_Kernel_Change_a.jpg
[9]: https://ubuntu.com/pro
[10]: https://news.itsfoss.com/content/images/2024/08/Ubuntu_Kernel_Change_b.jpg
[11]: https://www.linkedin.com/in/brettgrandbois/
[12]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
