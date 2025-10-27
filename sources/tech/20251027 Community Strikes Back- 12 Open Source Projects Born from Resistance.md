[#]: subject: "Community Strikes Back: 12 Open Source Projects Born from Resistance"
[#]: via: "https://itsfoss.com/community-strikes-back-with-forks/"
[#]: author: "Pulkit Chandak https://itsfoss.com/author/pulkit/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Community Strikes Back: 12 Open Source Projects Born from Resistance
======

[![Warp Terminal][1]][2]

When open source is spoken about, it is done so just as a licensing model for software. But when you think about it, it is often deeper than just that. With the open source philosophy, developers make good software exist just for the sake of its existence. Sometimes this good software is so good, that it disrupts the already existing players of the area, tipping the balance entirely. We'll be looking at the most significant cases of such an event in this article. So sit back and enjoy this casual read.

### 1\. Git decimates BitKeeper

![][3]

Imagine being the creator of Linux and yet [people know you more for creating Git][4]. That's the story of Linus Torvalds.

Before Git, BitKeeper was the primary software used for distributed revision control of Linux kernel source code. And it was revolutionary because before that, according to Torvalds, the only good option was to manually check the patches and put them in.

While Stallman and some others crticized the use of a properitary tool for the development of open source Linux kernel project, BitKeeper remained the choice of VCS tool.

It was in 2005, that BitKeeper revoked the free license for Linux kernel project. They blamed [Andrew Tridgell][5] who tried creating an open source version of BitKeeper, the same way he had created Samba protocol, by resevre engineering existing project.

This move violated BitKeeper's terms as Tridgell was employed by OSDL, predeccors of Linux Foundation, the non-profit organization pushing the Linux kernel development.

After a [public feud with Tridgell][6], Torvalds started working on his own source control software and released the first version before the month ended. And that's how Git was born, out of necessity, just like Linux project.

Fun fact, this incident also led to the birth of Mercurial, another open source VCS. Popularity of Git overshadowed Mercurial.

BitKeeper then turned open source before eventually being discontinued. Git, however, remains the most popular software control tool, with GitHub and GitLab, etc. being the most massive code bases used by everyone.

### 2\. X.Org takes on XFree86's advertising clause

![][7]

X Window System, aka X11 is one of the graphic windowing systems that are used in many Linux distributions as of now, and was used almost exclusively all major distributions before Wayland came along.

The most popular implementation of X11 used to be [XFree86][8]. It began to go sour when the development of the software started to stagnate, as the core team began to resist progress. Things changed in 2004 when XFree86 wanted to include an advertising clause in their license, making it incompatible with the GPL license. This caused some tension within the community with the developers of major distributions warning to pull out.

As a response, X.Org Foundation made the [X.Org Server][9] based on the last open source compatible version of XFree86. It became really popular really fast, replacing XFree86 in most of the major distributions within months. With a modular structure and transparency in development, X.Org became integral in graphical Linux operating systems, only now starting to be slowly replaced by a different windowing system entirely, [Wayland][10].

### 3\. Icinga takes on Nagios

![][11]

In an IT workplace, all the technological elements of the system need to be monitored well. This is what is done by a [network and infrastructure monitoring system][12], like [Nagios][13]. It is an application that can watch over servers, devices, applications, computers, etc. over a network, and report errors, if there are any.

Nagios dominated this area, being open-source and extensible. This modularity, however, became the reason for its downfall as the developers made the decision to move certain plugins and features behind paid tiers. Due to this increased commercialization and closed development, they started losing their users.

As a response, [Icinga][14] was made from a Nagios fork in 2009. They kept the backward compatibility to keep system from breaking, but put a step towards the future. Icinga offered a new web-interface, configuration format and improved scalability, essentially replacing Nagios as the preferred platform.

### 4\. Illumos carries the legacy of OpenSolaris

![][15]

Sun Microsystems had been a major player in the tech world, both hardware and software wise, during the dot-com boom. [Solaris][16] was a proprietary, UNIX based operating system designed by them that became really important in the industry. They then released [OpenSolaris][17], which was their daring attempt at open-sourcing their powerful OS. Eventually, however, Oracle acquired Sun in 2010, abruptly abandoning the OpenSolaris project, leaving a lot of people hanging in the process.

The solution? Some of the former Sun engineers and the open-source community came together to build [Illumos][18] from the last open-source version of OpenSolaris. It aimed to carry forward the userbase and legacy of OpenSolaris, and to continually develop new features, keeping the OS relevant. It has retained the excellent and distinguishing features of OpenSolaris such as the [ZFS filesystem][19] and [DTrace][20]. It has since then been the basis for other operating systems as well, like [OpenIndiana][21], [OmniOS][22] and [SmartOS][23].

### 5\. OpenSearch when ElasticSearch went SSPL

![][24]

[ElasticSearch][25], soon after its release became the preferred search engine of enterprises all across the world. Providing rich analytics and usage statistics, it seemed to fulfill all the needs. Initially open source under Apache 2.0, ElasticSearch was later on moved to the SSPL (Server Side Public License), which is not a license recognized by the OSI. Amazon saw the opportunity and picked up the slack by forking the last open source release of ElasticSearch and adding their own spin to it, bringing about [OpenSearch][26], which is open source.

OpenSearch retains most of the important features ElasticSearch had along with the look and feel, and adds more on top such as easy AWS integration and cloud alignment, which proves to be a great advantage for most web service purposes.

ElasticSearch came back as open source project again in 2024. But the damage was done as big players like Amazon has already put OpenSearch at the forfront of cloud servers.

### 6\. VeraCrypt continues TrueCrypt

![][27]

Disk encryption is one of the most, if not the most important security feature on an operating system. For a very long time, this job was reliably done by [TrueCrypt][28], with automatic and on-the-fly encryption. However suddenly in 2014, TrueCrypt [announced][29] that they would not develop the program any further, and that the program was "not secure". It is unclear what the proper reasoning was (as flaws that major were not found) but in their message, they asked the users to switch to [Microsoft's BitLocker][30].

That didn't seem to take with the open-source community, which them proceeded to build [VeraCrypt][31], forked from the last version of TrueCrypt. VeraCrypt carried on the existing features well, also improving various factors including stronger encryption algorithms, better key derivation functions and rapid bug fixing. It is known for being transparent and community-driven and hence very trusted.

### 7\. Rocky Linux born in the aftermath of CentOS fiasco

![][32]

[CentOS][33] was an operating system by Red Hat that was based on [RHEL][34] (Red Hat Enterprise Limited) source code, getting all of its features a few months after RHEL itself, only free of cost. CentOS was eventually transitioned into [CentOS Stream][35], which is a rolling release. The features now came in faster, but the stability was significantly hindered. This made is unsuitable for development environments, commercial uses or even personal usage.

To resolve the situation, one of the original creators of CentOS created [Rocky Linux][36] in 2021, filling in the gap that CentOS left behind. It was, and ever since has been enterprise-ready and rock-solid stable. Being based on RHEL, it can be used in high-performance computing, cloud and hyperscale computing, as well as for smaller commercial systems.

### 8\. OpenELA tackles RHEL's partially close source moves

Following up the previous point, this one carries it further. RHEL had announced that the only source code that will be publicly available related to RHEL would be the CentOS Stream, and for Red Hat customers, it would be available through the customer portal. Understandably, the developers of the distributions based on RHEL were not pleased with the decision.

CIQ, the company backing Rocky Linux, SUSE and Oracle responded by forming [OpenELA][37] (Open Enterprise Linux Association) with the goal of creating distributions compatible with RHEL, while keeping the source code open to all. It was supposed to be an answer to the hole that the dependency of enterprise operating systems on CentOS had left behind.

The group has automated the task of paying to get access to the source code and then publishing it on a [public repository][38], out for everyone to be able to access it and make an operating system out of it. Several distributions like [Rocky Peridot][39], [SUSE Open Build Service][40], [Fedora Koji][41], and the [AlmaLinux Build System][42] were born out of the same.

### 9\. OpenTofu fills the void after Terraform opted for Business Source License

![][43]

The story starts with [Terraform][44] being a terrific open source for IaC (infrastructure-as-code) purposes. The idea is that it will let you visualize, manage and plan your computing infrastructure (such as VMs, databases, VPNs, etc.) not manually, but as code, which automatically then executes the needed action.

Terraform started as as open source, cross-cloud and was very extensible, which made it the go-to choice for everyone to the point where other services were being build around Terraform. In 2023, however, they decided to move from the open source MPL license to a BSL (Business Source License), which put several restrictions that put certain users at risk.

Concerned about the problems that might occur in the future, open source developers forked the last open source version of Terraform and released [OpenTofu][45], which then was backed by the Linux Foundation itself. Now after some time has passed, OpenTofu has not only proven successful in its mission, but has features that Terraform lacks. Listening to the community and its needs, OpenTofu has found great success.

### 10\. Valkey forked from Redis as it changed license

![][46]

[Redis][47] (REmote DIctionary Server) was built to be an in-memory data store with blazing speed and utility. This meant that it could contain and retrieve data from RAM (with optional persistence to disk) with microsecond latency. This has several essential uses such as caching, session storage (like shopping carts), real-time analytics (like, share counts, etc.) and so on. Initially open source under the BSD license, it became wildly popular and an integral part of the internet's infrastructure.

In 2024, however, Redis announced a change in license which would restrict its use in commercial clouds, heavily affecting the users. In response, [Valkey][48] was created, which was born out of the last open source version of Redis. 100% Redis compatible and not governed by a single company, Valkey thrived as a drop-in replacement for Redis.

### 11\. LineageOS carries on after CyanogenMod's demise

For a very long time, [CyanogenMod][49] had been the go-to option for [Android users to install an alternative open-source operating system][50] which could give them more control, customization and most importantly, freedom from any of the manufacturer's proprietary trackers, etc. Eventually, Cyanogen Inc. shifted its focus to more proprietary projects and discontinued the project.

The developers' response was to fork the last known version into [LineageOS][51], successfully taking the place of CyanogenMod. It is still going strong as the best open-source option for Android, different ROMs for different devices, with enhanced security and customization. Not only that, but it offers extended software support to older devices that are not supported by their parent companies any longer.

### 12\. MariaDB, the OG Business Source Licensee

[MySQL][52] is an open-source database management system that has been the biggest program of its kind, and for good reason. It has had amazing support and documentation, can be used for extremely large databases with read-heavy purposes, and is very simple to use (so easy that it is taught to schoolchildren). It was acquired by (yet another time) Oracle, and the open-source community feared that the development might become slow, features might become proprietary, and it might lose the openness.

In response, the original creator of MySQL Michael "Monty" Widenius created [MariaDB][53], keeping it under the GPL license. It acted as a drop-in alternative to MySQL while also introducing new and exciting features that set it apart. It has since become the preferred management system in open-source projects.

📋

It is kind of ironical to include MariaDB in this list. While it was created as a modern version of MySQL, [MariaDB was the one that introduced the Business Source License][54]. This was done because cloud vendors like AWS and Azure were reaping the benefit of open source projects by offering their hosted versions. This impacted those open source projects as they were not getting enough enterprise customers to sustain the development. As you can see, whenever an open source project opted for BSL, big players like AWS, Azure etc would just fork them and create an open source project they themselves govern. Decide who is the hero and who is the villain in this story.

### Conclusion

Time and time again, the open source philosophy often trumps some rash business decisions, favoring openness and innovation. The twists and turns of these changes come from all sorts of different directions, but more often than not, good open source software has existed and thrived solely because people wanted them to. Let us know if you enjoyed this article in the comments. Cheers!

--------------------------------------------------------------------------------

via: https://itsfoss.com/community-strikes-back-with-forks/

作者：[Pulkit Chandak][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pulkit/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/10/Git-torvalds.png
[4]: https://news.itsfoss.com/torvalds-on-git/
[5]: https://en.wikipedia.org/wiki/Andrew_Tridgell
[6]: https://www.theregister.com/2005/04/14/torvalds_attacks_tridgell/
[7]: https://itsfoss.com/content/images/2025/10/xorg.png
[8]: https://xfree86.org/
[9]: https://www.x.org/wiki/
[10]: https://wayland.freedesktop.org/
[11]: https://itsfoss.com/content/images/2025/10/icinga-1-.png
[12]: https://linuxhandbook.com/server-monitoring-tools/
[13]: https://www.nagios.org/
[14]: https://icinga.com/
[15]: https://itsfoss.com/content/images/2025/10/illumos.png
[16]: https://www.oracle.com/solaris/
[17]: https://opensolaris.org/
[18]: https://illumos.org/
[19]: https://itsfoss.com/what-is-zfs/
[20]: https://dtrace.org/about/
[21]: https://www.openindiana.org/
[22]: https://omnios.org/
[23]: https://www.tritondatacenter.com/smartos
[24]: https://itsfoss.com/content/images/2025/10/opensearch-3-0-demo-dashboard.png
[25]: https://www.elastic.co/elasticsearch
[26]: https://opensearch.org/
[27]: https://itsfoss.com/content/images/2025/10/VeraCrypt_screenshot.png
[28]: https://www.truecrypt.org/
[29]: https://www.theregister.com/2014/05/28/truecrypt_hack/
[30]: https://support.microsoft.com/en-us/windows/bitlocker-drive-encryption-76b92ac9-1040-48d6-9f5f-d14b3c5fa178
[31]: https://veracrypt.io/en/Home.html
[32]: https://itsfoss.com/content/images/2025/10/rocky-linux.png
[33]: https://www.centos.org/
[34]: https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux
[35]: https://www.centos.org/download/
[36]: https://rockylinux.org/
[37]: https://openela.org/
[38]: https://github.com/openela
[39]: https://github.com/rocky-linux/peridot
[40]: https://build.opensuse.org/
[41]: https://koji.build/
[42]: https://wiki.almalinux.org/development/AlmaLinux-Build-System.html
[43]: https://itsfoss.com/content/images/2025/10/opentofu.webp
[44]: https://developer.hashicorp.com/terraform
[45]: https://opentofu.org/
[46]: https://itsfoss.com/content/images/2025/10/valkey.png
[47]: https://redis.io/
[48]: https://valkey.io/
[49]: https://www.wikiwand.com/en/articles/CyanogenMod
[50]: https://itsfoss.com/android-distributions-roms/
[51]: https://lineageos.org/
[52]: https://www.mysql.com/
[53]: https://mariadb.org/
[54]: https://itsfoss.com/making-the-business-source-license-open-source-compliant/
