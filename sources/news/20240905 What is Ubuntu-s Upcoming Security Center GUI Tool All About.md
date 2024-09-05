[#]: subject: "What is Ubuntu's Upcoming Security Center GUI Tool All About?"
[#]: via: "https://news.itsfoss.com/ubuntu-security-center-near-stable/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What is Ubuntu's Upcoming Security Center GUI Tool All About?
======
This sounds like a good idea for accessing more security features.
[![][1]][2]

Seeing a security-focused application tailored for a specific Linux distribution is like spotting Windows being non-intrusive when delivering its updates; you don't get to see such occurrences often.

There are all kinds of security applications out there that can be used for a wide variety of use cases. But, [Canonical][3], the ones behind Ubuntu, have developed something called “ **Security Center** ” for catering to some specific needs, and **it is** [**nearing**][4] **a stable release** as spotted by [OMG!Ubuntu!][5].

### Security Center: What To Expect?

![Security Center on Ubuntu 24.04][6]

Introduced as part of the Ubuntu 24.04 LTS [roadmap][7] late last year ( _but couldn't make it to the final release_ ), the **Flutter-based** Security Center is a dedicated application for Ubuntu meant to bring out the hard-to-access “ _ninja security_ ” features of the distro.

The developers want to focus on four key areas with this app. One is that **they aim to make it easy to handle full-disk encryption**. The second is that they are **planning to move the Ubuntu Pro settings from the “ _Software & Updates_” app into a dedicated section in the new security app**.

The third is a **dedicated “ _Network_ ” section for facilitating easy firewall control** and enabling “Stealth Mode”. The final one is to introduce a prompting mechanism for apps; more on this one later.

Currently, the Security Center features only a single experimental option to require Snap apps to ask for system permissions. I tried enabling it after installing Security Center on an Ubuntu 24.04 installation on a virtual machine, but it just sent me into a loading loop.

#### Want To Check It Out?

If you want an early look at the Security Center, you can get it from [Snapcraft][8], or by running the following command:

```

    sudo snap install desktop-security-center

```

There's also something called a “ **Prompting Client** ”, which is meant to show a prompt when a Snap application requests additional permissions. It is meant for apps that cannot usually access resources from outside the app's [sandbox][9].

The Settings app will still provide a way to manage Snap permissions; this is just an additional way of accomplishing a similar goal. Take a look at the demo below. 👇

0:00

/0:12

1×

Source: [Canonical][3]

The developers acknowledge that the Prompting Client is quite similar to what Android and iOS have, but they will be focusing on getting the basics done right before they go any further with this.

If you are keen on checking it out, then you can follow the steps mentioned below ( _Ubuntu 24.04 or daily builds of 24.10_ ). Do note that there's no guarantee that it will work.

First, enable experimental Snap features by running the following command:

```

    snap set system experimental.user-daemons=true

```

Then, install the Prompting Client using this command:

```

    sudo snap install prompting-client

```

If it works for you, great; if it doesn't, no need to worry, as this is an under-development piece of software that will be stable soon.

💡

It should be included with a future Ubuntu 24.04 LTS point release when it's ready for prime-time.

_💬 Your thoughts on the Security Center? Do you see yourself using it once it has a stable release?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-security-center-near-stable/

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
[4]: https://github.com/canonical/desktop-security-center/pull/47
[5]: https://www.omgubuntu.co.uk/2024/09/ubuntus-new-security-center-readies-stable-release
[6]: https://news.itsfoss.com/content/images/2024/09/Ubuntu_Desktop_Security_Center.png
[7]: https://discourse.ubuntu.com/t/ubuntu-desktop-24-04-lts-roadmap-highlights/41032
[8]: https://snapcraft.io/desktop-security-center
[9]: https://snapcraft.io/docs/security-sandboxing
