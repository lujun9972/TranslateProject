[#]: subject: "Azure Linux In, CentOS Out: LinkedIn Switches its Server Operating System"
[#]: via: "https://news.itsfoss.com/azure-linux-centos-linkedin-os/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Azure Linux In, CentOS Out: LinkedIn Switches its Server Operating System
======
LinkedIn embraces Microsoft's Azure Linux for its hosting requirements.
[![][1]][2]

[LinkedIn][3] is the **most popular business-focused social media platform out there**. You can find all kinds of professionals on the platform, be it someone who's starting a new career fresh out of college, all the way to CEOs of multi-billion dollar companies.

Over the years, it has been growing consistently, both in terms of user count, and infrastructure. Its acquisition by Microsoft in 2016 has only accelerated that process in the years since.

Today, LinkedIn [claims][4] that they have **1 billion members** in more than 200 countries/territories across the world. Their vision states that they want to “ _create economic opportunity for every member of the global workforce._ ”

In a recent announcement, the developers revealed that LinkedIn has successfully migrated to a new open-source, Linux-based operating system for their servers, virtual machines, and containers, ditching CentOS.

### LinkedIn Bets On its Modern Linux Distro

![The It's FOSS LinkedIn page. \(give it a follow, maybe?\)][5]

As part of a massive migration campaign, LinkedIn has successfully moved their operations to Microsoft's [Azure Linux][6] as of April 2024, ditching [CentOS 7][7] in the process and taking advantage of a more modern compute platform.

As many of you might already know, back on June 30, 2024, CentOS 7 [reached][8] the end-of-life status, resulting in no new future updates for it, including fixes for critical security vulnerabilities.

With this new operating system in place, **the LinkedIn developers have managed to address various shortcomings of the previous setup** , and have achieved things like better user-space handling, faster bootstrapping times on bare-metal servers/containers, effortless firmware updates, and more.

The developers have gone with the high-performing [XFS][9] filesystem, which was made to work with Azure Linux to fit LinkedIn's use case. In their testing, they found that XFS was performing well for most of their applications, except [Hadoop][10], which is used for their analytics workloads.

When they compared the issues that cropped up, XFS came out as a more stable and reliable choice than the other candidate, [Ext4][11].

Commenting on this major platform-wide change, [Ievgen Priadka][12], who was part of the Systems Infrastructure team behind the migration, added that:

> By embracing open-source solutions, LinkedIn, in partnership with Microsoft, harnessed the power of community-driven innovation and unlocked new levels of efficiency, agility, and competitiveness.

Additionally, LinkedIn's MaaS ( _Metal-as-a-Service_ ) team has developed a new [Azure Linux Image Customizer][13] tool for automating image generation, that takes an existing generic Azure Linux image, and modifies it to use with a given scenario. In this case, a tailored image for LinkedIn.

In the end, for me, as a [LinkedIn user][14], I haven't faced any kind of disruption to my use of the platform in the past few months. They have made sure that users do not face any major disruption.

I highly suggest you check out the detailed [Engineering Blog][15] Ievgen co-authored; it's filled with many interesting insights on how both LinkedIn and Microsoft developers were able to pull this off.

_💬 Do you think Microsoft will ever launch a fully-fledged desktop Linux distro for general use? Just a question that came to my mind looking at Azure Linux here._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/azure-linux-centos-linkedin-os/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.linkedin.com/
[4]: https://about.linkedin.com/
[5]: https://news.itsfoss.com/content/images/2024/08/It-sFOSS_LinkedIn.png
[6]: https://github.com/microsoft/azurelinux
[7]: https://www.centos.org/
[8]: https://blog.centos.org/2023/04/end-dates-are-coming-for-centos-stream-8-and-centos-linux-7/
[9]: https://en.wikipedia.org/wiki/XFS
[10]: https://hadoop.apache.org/
[11]: https://en.wikipedia.org/wiki/Ext4
[12]: https://www.linkedin.com/in/ievgen-priadka
[13]: https://github.com/microsoft/azurelinux/blob/3.0-dev/toolkit/tools/imagecustomizer/README.md
[14]: https://www.linkedin.com/in/sourav666/
[15]: https://www.linkedin.com/blog/engineering/architecture/navigating-the-transition-adopting-azure-linux-as-linkedins-operatingsystem
