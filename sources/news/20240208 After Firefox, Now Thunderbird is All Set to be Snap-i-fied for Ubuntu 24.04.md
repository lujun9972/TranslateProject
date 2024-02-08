[#]: subject: "After Firefox, Now Thunderbird is All Set to be Snap-i-fied for Ubuntu 24.04"
[#]: via: "https://news.itsfoss.com/thunderbird-snap/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

After Firefox, Now Thunderbird is All Set to be Snap-i-fied for Ubuntu 24.04
======
Ubuntu 24.04 LTS is bringing in more snaps to your way!
Canonical is not slowing down with Snaps for 2024, after it revealed last year that they were working on an [all-snap Ubuntu desktop][1] for Ubuntu 24.04 LTS.

We now have a renewed push that will see Thunderbird, one of the [best email clients for Linux][2], being packaged as a Snap package by default on the upcoming Ubuntu LTS release 😲

So, let's see what this is all about.

### A Snappy Future for Thunderbird on Ubuntu?

Most likely, yes.

[Spotted first][3] on the Ubuntu community Discourse forum, [Sebastien Bacher][4] from Canonical shared something fascinating that he was working on and how they intend to handle Thunderbird on Ubuntu going forward.

![][5]

Usually, the Snap version of Thunderbird is built by repacking the upstream binaries, however, Sebastien made some modifications to the packaging, and now it is **built directly from the source** instead.

He reused much of what the existing Snap for Firefox does, with the main advantage he claimed to be that **it will now be easier for them to build Thunderbird. And, the end-result reflects for other architectures** besides [amd64][6], making it “ _more compliant with the Ubuntu standards_ ”.

Sebastien mentioned the following for the same:

> We are aiming at using the snap built from source instead of the deb in Noble. (the reasons are the same than for Firefox, making it easier to roll new versions on older supported series and reducing the maintenance efforts).

Well, considering Thunderbird will be a better email client soon ([embracing Rust][7]), Canonical's push to unify the app experiences should end well if done correctly.

![][8]

Yes, if things go as planned, then **the Snap version of Thunderbird should replace the Deb version on the upcoming Ubuntu 24.04 LTS release**.

Furthermore, he has already made a beta build of the Thunderbird Snap available that users can check out if they want an early sneak peek.

### Want to try it out?

![][9]

🚧

Before we begin, keep in mind that this beta version of Thunderbird is not recommended for general use, proceed with caution.

First, ensure that you have either backed up your data or removed any existing installation.

Then, run one of the following commands according to your situation:

```

    sudo snap install thunderbird --beta #For a new installation

```

OR

```

    sudo snap refresh thunderbird #For updating your existing installation

```

And that's it, you now have the latest beta build of the Thunderbird Snap installed on your system.

As things stand now, [Canonical][10] is not stopping anytime soon with their aggressive push for Snaps, it will only get more ingrained into the Ubuntu ecosystem as time passes. Many may not like that, but, it is what it is.

**Suggested Read** 📖

![][11]

The good news is that there are always [ways to get rid of Snaps][12] from Ubuntu, or the option to switch to another distro entirely to avoid Snaps. For me, I am interested in seeing how far they are willing to go with this.

_💬 What do you think? Are Snaps the future for Ubuntu?_

Via: [OMG! Ubuntu][13]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/thunderbird-snap/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/ubuntu-all-snap-desktop/
[2]: https://itsfoss.com/best-email-clients-linux/
[3]: https://discourse.ubuntu.com/t/thunderbird-beta-snap-built-from-source-call-for-testing-and-next-steps-for-noble/42294
[4]: https://discourse.ubuntu.com/u/seb128
[5]: https://news.itsfoss.com/content/images/2024/02/discourse-thunderbird.jpg
[6]: https://en.wikipedia.org/wiki/X86-64
[7]: https://mstdn.io/@codewiz/111868481684467288
[8]: https://news.itsfoss.com/content/images/2023/04/Follow-us-on-Google-News.png
[9]: https://news.itsfoss.com/content/images/2024/02/Thunderbird_Snap.png
[10]: https://canonical.com/
[11]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[12]: https://itsfoss.com/remove-snap/
[13]: https://www.omgubuntu.co.uk/2024/02/thunderbird-snap-in-ubuntu-24-04
