[#]: subject: "Age Verification Laws Are Multiplying Like a Virus, and Your Linux Computer Might be Next"
[#]: via: "https://itsfoss.com/news/age-verification-pandemic/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Age Verification Laws Are Multiplying Like a Virus, and Your Linux Computer Might be Next
======

[![Warp Terminal][1]][2]

As of today, about half of all U.S. states have some form of age verification law around. Nine of those [were passed in 2025 alone][3], covering everything from adult content sites to social media platforms to app stores.

Right now, California's [Digital Age Assurance Act][4] (AB 1043) is all the rage right now, which targets not only websites and apps but also operating systems. Come January 1, 2027, every OS provider must collect a user's age at account setup and provide that data to app developers via a real-time API.

Colorado is also working on a near-identical bill, [which we covered earlier][5].

The EFF's [year-end review][3] put it more bluntly: 2025 was " _ **the year states chose surveillance over safety**_." The foundation's concern, which I concur with, is, **where does this stop?** Self-reported birthday today, government ID tomorrow? There appears to be no limit to these laws' overreach.

📋

What's next—verify yourself to get access to potable water? ☠️

Governments across the world are pulling out the exact same argument ( _protect the children_ ) to push through laws with consequences that go well beyond keeping a kid off a harmful website. All while attendees of a certain island roam about the world freely.

### It's Not Just the U.S.

![][6]

The **UK** moved first [back in 2023][7]. The Online Safety Act's child safety duties went into force in July 2025, where it required platforms to deploy age verification measures, blocking minors from accessing harmful material.

**Australia** followed in December 2025 with [a ban on social media accounts][8] for under-16s, requiring age checks for adults to use the platform. It is narrower in scope, targeting platforms rather than app stores or operating systems.

**Brazil** has gone further. The [Digital Statute of the Child and Adolescent][9] comes into effect on March 17, 2026, and it explicitly names operating systems and app stores by definition.

![][10]

Article 12 requires both to implement auditable age verification, expose an age signal via API to third-party apps, and get parental/legal guardian consent before minors can download anything.

**Singapore** 's approach skips the OS side of things and goes straight for the app stores themselves. Their [IMDA][11] requires the likes of Apple, Google, Huawei, Microsoft, and Samsung [to implement age assurance by March 31, 2026][12].

Apple has already gotten it done, rolling out its [Declared Age Range API][13] on February 24, blocking 18+ apps in Singapore, Australia, and Brazil.

As usual, the **EU** is doing its own thing. In October 2025, the Commission introduced [the second version][14] of its age verification blueprint, which is a mobile app that lets users prove they're over 18 without revealing any personal data. It's built on the same technical foundation as the [EU Digital Identity Wallets][15] rolling out across member states.

Five countries are already in the process of customizing it for their needs: Denmark, France, Greece, Italy, and Spain.

### The Fallout

Predictably, the Linux community has not taken this quietly. While there is a bunch of misinformation strewn about, some things are clear.

Take **Ubuntu** , for instance. [Aaron Rainbolt][16], an Ubuntu Community Council member, posted on the [Ubuntu mailing list][17] raising this issue of age checks with a post titled:

> On the unfortunate need for an "age verification" API for legal compliance reasons in some U.S. states

![][18]

In the post, he proposed a [D-Bus interface][19] called `org.freedesktop.AgeVerification1`. Rather than storing raw personal data, it would only expose an age bracket to apps that request it. The goal is a spec loose enough that any distro can implement it however they see fit, while still satisfying what laws like _AB 1043_ actually require.

Then there's the thread up on **Fedora** 's Discourse, where a user asked whether the developers were aware of California's age verification law. [Jef Spaleta][20], Fedora Project Leader, [chimed in][21] with a measured approach, where **no telemetry was required** , and a local API would do the heavy lifting.

![][22]

Here, apps would query Fedora for an age bracket, and the OS would provide it. He even suggested it could be as simple as a new file in `/etc/` that would be populated during account creation.

As for what people think of this, take the example of a Redditor, who is going as far as [hoarding ISO files for old builds of Linux and Windows][23] once age verification-equipped versions start rolling out. I am sure many will follow in their footsteps.

Lastly, **my take on this situation?** This feels less like coincidence and more like a coordinated move being run under the guise of protecting children's rights. We already know how certain regimes around the world treat those rights.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/age-verification-pandemic/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.eff.org/deeplinks/2025/12/year-states-chose-surveillance-over-safety-2025-review
[4]: https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260AB1043
[5]: https://itsfoss.com/news/our-take-on-age-verification/
[6]: https://itsfoss.com/content/images/2026/03/australia-social-media-ban-law.png
[7]: https://www.gov.uk/government/publications/online-safety-act-explainer/online-safety-act-explainer
[8]: https://www.esafety.gov.au/about-us/industry-regulation/social-media-age-restrictions
[9]: https://www.gov.br/mdh/pt-br/assuntos/noticias/2025/novembro/brasil-apresenta-avancos-em-seguranca-digital-da-infancia-e-lanca-eca-digital-em-ingles-durante-cupula-social-do-g20-na-africa-do-sul/eca-digital-ing-v2.pdf
[10]: https://itsfoss.com/content/images/2026/03/brazil-digital-statute-child-adolescent.png
[11]: https://www.imda.gov.sg/
[12]: https://www.mddi.gov.sg/newsroom/mddi-s-response-to-pq-on-update-on-study-on-effectiveness-of-mandating-age-limits-for-social-media-access/#:~:text=Designated%20app%20stores%20are%20expected%20to%20implement%20these%20age%20assurance%20measures%20by%2031%20March%202026.%20At%20the%20outset%2C%20they%20are%20required%20to%20be%20able%20to%20minimally%20ascertain%20whether%20users%20are%20under%2018.
[13]: https://developer.apple.com/news/?id=f5zj08ey#:~:text=Apps%20rated%2018%2B%20in%20Australia%2C%20Singapore%2C%20and%20Brazil
[14]: https://digital-strategy.ec.europa.eu/en/news/commission-releases-enhanced-second-version-age-verification-blueprint
[15]: https://digital-strategy.ec.europa.eu/en/policies/eudi-wallet-implementation
[16]: https://github.com/ArrayBolt3
[17]: https://lists.ubuntu.com/archives/ubuntu-devel/2026-March/043510.html
[18]: https://itsfoss.com/content/images/2026/03/ubuntu-age-verification-approach.png
[19]: https://en.wikipedia.org/wiki/D-Bus
[20]: https://www.linkedin.com/in/jspaleta/
[21]: https://discussion.fedoraproject.org/t/california-age-verification/181968/7
[22]: https://itsfoss.com/content/images/2026/03/fedora-project-leader-views-age-verification.png
[23]: https://www.reddit.com/r/privacy/comments/1rl4gzk/how_long_can_i_use_an_outdated_linuxwindows/
