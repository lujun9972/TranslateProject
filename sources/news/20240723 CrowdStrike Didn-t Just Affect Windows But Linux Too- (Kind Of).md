[#]: subject: "CrowdStrike Didn't Just Affect Windows But Linux Too! (Kind Of)"
[#]: via: "https://news.itsfoss.com/crowdstrike-windows-linux/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

CrowdStrike Didn't Just Affect Windows But Linux Too! (Kind Of)
======
CrowdStrike wreaking havoc everywhere!
[![][1]][2]

At the end of last week, the IT industry saw a catastrophic event take place thanks to a faulty patch pushed in to Windows by [CrowdStrike][3], a cybersecurity firm based out of Austin, Texas.

Even though, its timing might've been a boon for those looking to get off work early.

Many critical infrastructures such as Airports and Medical facilities had to bear the brunt of it, **raising many important questions** over dependence on such centralized pieces of tech.

Luckily, the issue has since been [addressed][4], but this didn't stop many, including us, from creating some [funny memes][5] on CrowdStrike's plight.

Sadly, Linux was also affected by Crowdstrike weeks before this catastrophic event occurred, which largely went unknown, until now, that is. 🫤

### CrowdStrike's Incompetence: A Heavy Price To Pay For Second-Class Treatment

![][6]

Back in May, a Rocky Linux user posted [an issue][7] on the forum which reported that upgrading to [Rocky Linux 9.4][8] on servers equipped with CrowdStrike's [Falcon platform][9] would result in a system freeze due to a [kernel panic][10].

**Other users also chimed in** , facing similar issues, and after going around looking for potential fixes, they finally found one in Red Hat's Customer Portal, more on that in a bit.

On [Hacker News][11], another user suffering from CrowdStrike's incompetence shared that a fleet of production machines running [Debian][12] were taken offline when CrowdStrike pushed an incompatible patch for Debian stable.

When they initially contacted support, CrowdStrike took a day to respond, then asked for more proof, beyond what was already provided, they then took some days to acknowledge it.

And, after making them wait for a couple of weeks, they sent a [root cause analysis][13], which mentioned that they didn't support this specific scenario of Debian stable running version N-1, which the user believed was a supported configuration.

#### **But, wait, there's more!**

![][14]

In a similar situation, **many Red Hat Enterprise Linux (RHEL) users also faced issues due to Falcon** , for which Red Hat had to issue multiple warnings.

The [first case][15] ( _subscribers-only_ ) was the one I mentioned earlier for Rocky Linux, in which kernel panic was observed after booting on Linux kernel 5.14.0-410 and later systems due to the _falcon-sensor_ process.

The [second case][16] was a system crash issue on RHEL 6 and 7, where Red Hat offered a workaround, by suggesting users disable Falcon to mitigate the issue, with the other option being to contact CrowdStrike support for assistance.

_By now, we know how prompt CrowdStrike's customer service is._ ☠️

Unsurprisingly, thanks to all the chaos, the U.S. House of Representatives [Homeland Security Committee][17] has officially sent a letter to [George Kurtz][18], CEO of CrowdStrike, asking him to testify on the massive outage.

I would have liked to think that this was due to Linux-based OSes being affected, but, as we all know, [Windows][19] is the favorite child among all the operating systems for a bulk of the population.

Fun ( _or ominous!?_ ) fact, George was the Chief Technology Officer (CTO) of McAfee back in 2010, when the infamous [DAT 5958][20] antivirus update managed to cripple millions of Windows-equipped computers around the world.

_💬 The motorsport fan in me knows CrowdStrike from the sponsorship and infrastructure support they do for the Mercedes-AMG PETRONAS_ [_F1 Team_][21] _. What about you? Did you know of them before?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/crowdstrike-windows-linux/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.crowdstrike.com/
[4]: https://www.crowdstrike.com/falcon-content-update-remediation-and-guidance-hub/
[5]: https://x.com/itsfoss2/status/1814314761254838419
[6]: https://news.itsfoss.com/content/images/2024/07/CrowdStrike_Linux_Booboo_a.png
[7]: https://forums.rockylinux.org/t/crowdstrike-freezing-rockylinux-after-9-4-upgrade/14041
[8]: https://rockylinux.org/news/rocky-linux-9-4-ga-release
[9]: https://www.crowdstrike.com/platform/
[10]: https://en.wikipedia.org/wiki/Kernel_panic
[11]: https://news.ycombinator.com/item?id=41005936
[12]: https://www.debian.org/
[13]: https://en.wikipedia.org/wiki/Root_cause_analysis
[14]: https://news.itsfoss.com/content/images/2024/07/CrowdStrike_Linux_Booboo_b.png
[15]: https://access.redhat.com/solutions/7068083
[16]: https://access.redhat.com/solutions/6971903
[17]: https://homeland.house.gov/
[18]: https://www.linkedin.com/in/georgekurtz
[19]: https://www.microsoft.com/en-us/windows/
[20]: https://en.wikipedia.org/wiki/McAfee#DAT_5958_update
[21]: https://www.mercedesamgf1.com/
