[#]: subject: "Session's Co-Founder Thinks You Don't Need to Ditch WhatsApp Completely"
[#]: via: "https://itsfoss.com/news/session-co-founder-interview/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Session's Co-Founder Thinks You Don't Need to Ditch WhatsApp Completely
======

[![Warp Terminal][1]][2]

The world around us is gradually getting more polarized, with people losing hope that their governments can take them through these turbulent times. As a result, we are seeing more and more people switching to [decentralized social media platforms][3].

[Session][4] is one such service that offers encrypted messaging without requiring a phone number or email address to sign up. Their onion-powered routing system makes use of ~2,000 nodes to ensure the utmost levels of privacy.

We spoke with Alexander Linton of the Session Technology Foundation [back in December][5], and now we're talking with Session's Co-Founder, [Kee Jeffrys][6], who shares some interesting insights from the technical and founding side of things.

### What Got You into Privacy Tech?

While I was studying computer science at university, one of my lecturers briefly mentioned Bitcoin as a real-world application of public key cryptography. That sent me down a rabbit hole. Not because of price, but because of the underlying idea that cryptography could give individuals real control rather than forcing them to trust institutions by default.

Around the same time, I started attending crypto meetups and met the people who would later become my co-founders at Session. We were all looking at early decentralized and privacy-focused technologies like [Tor][7], [Bitmessage][8], [Monero][9], and [Zcash][10] and asking the same question: **if these ideas work for money and routing traffic, why are most communication tools still centralized and easy to surveil?**

I was still thinking about that question. The infrastructure of messaging is extremely delicate. It is typically run by a single company in a single jurisdiction, but it carries journalism, activism, legal work, and our regular private conversations. Our goal was to determine whether it was feasible to create a messaging system that didn't require users to have faith in any particular business, server, or nation.

In 2018, about a year and a half into my degree, I began working on Session and postponed my studies to devote all of my time to focus on decentralized and privacy preserving technology, driven by the belief that private communication should not be a luxury only for powerful or rich individuals, or a niche feature for the tech-savvy, but a default for all of us.

### When Did You Know Session was Going to be More Than Just a Proof of Concept?

I think it stopped feeling like a proof of concept when we saw people rely on it in situations we never could have simulated.

Since founding Session, we started working with a number of digital rights NGOs around the world, talking to them about Session and providing resources to help them use it to protect their comms.

In October 2022, as civil unrest was worsening in Iran following the death of Mahsa Amini, Signal was blocked by the Iranian government. The NGOs we had onboarded to Session then pushed the app to their networks, which **led to a domino effect that ultimately caused our user base to double overnight**.

This was one of the moments when we saw our vision materialised. Session helping activists and journalists communicate with freedom. That was when it became clear this was not just an experiment anymore. It was something people could genuinely depend on.

### How Does Session Handle Requests from Governmental Agencies?

The [Session Foundation][11] records all information requests from governments and releases an annual _Transparency Report_ with aggregated information about those requests and how they were handled. Transparency reports can be found [here][12].

The Session Foundation’s response to all requests for personal information of users starts with an explanation that the design of Session prevents the collection of user data and metadata at the network level by the Session Foundation. This **limits the Session Foundation's ability to provide the type of data and metadata typically requested by governments**.

The contents of messages in Session are end-to-end encrypted and communicated through a decentralized onion-routed network, which means that there is no way for the contributors working on Session to discover the content of a message nor the IP address and other personal identification information of users sending or receiving messages on Session.

Because of these constraints, thus far, all legal requests have resulted in the Session Foundation lacking access to any of the requested data, with the foundation responding to these requests accordingly.

For example, between Jan 1 and Dec 2025, **there were 17 requests or inquiries from government agencies**. For all of these requests, the requested data was not available to the Session Foundation, preventing any user data from being shared.

### Session Pro has been in Beta for a While. What's the Timeline for Full Launch and How's the Response Been?

Pro Beta features have been completed and are now progressing through quality assurance processes. We will roll out the Pro Beta in two parts. The first release will contain all of the code required for clients to recognize other users as _Pro_.

It will also include support for all of the initial [Session Pro Beta][13] features, such as badges, increased message pinning limits, animated profile images, and the ability for Pro users to send longer messages. Technically, these features are already released — but they are behind feature flags.

With this release, these feature flags will be removed, and the features will effectively be ‘ _in_ ’ Session. The second release will be the official beta launch, **as users will immediately be able to purchase Session Pro beta and utilize its additional features**.

The first release should be delivered soon; we are working on the final details and testing now. The second release enabling the users to upgrade to Pro will likely come a few weeks after the first release.

### How Would You Persuade a Person to Switch Away from a Mainstream Messaging App Like WhatsApp?

I wouldn’t try to overtly try to persuade someone to use Session; ultimately, the choice is up to the individual. **Most people use mainstream messaging apps because that is where their friends, family, and work contacts are** , and that is completely understandable.

Most of our daily conversations with family and friends are not secret, but they are still personal. People share emotions, political views, routines, jokes, voice notes, and photos. That kind of communication deserves respect by default.

Using Session is not about hiding, it's about ensuring that you aren’t turning your everyday life into data. You shouldn’t be forced to choose between connecting with friends and constantly feeding a central platform with data about who you talk to, when, and how often. For a lot of people, that idea resonates even more than high-stakes security scenarios.

What I usually say is that it does not have to be an all-or-nothing switch. Session is not about replacing every conversation you have. It is about having an option that behaves differently when privacy actually matters.

I also think it helps to say that switching does not have to be dramatic. You can start by inviting a couple of close people over and see how it feels. Once people experience messaging without phone numbers, ads, or algorithmic pressure, it often just feels calmer and more intentional.

### What Does Session’s 2026 Roadmap Look Like and Any Particular Worries?

We have been working on [Session Protocol V2][14], **an upgrade that will re-implement perfect forward secrecy, utilize new Post-Quantum Cryptography (PQC),** and deliver improved device management features to ensure better visibility and authorization of linked devices.

The V2 Session Protocol is still undergoing design, and it will take a significant amount of development resources to finalize and integrate into Session but it is something we plan to release in 2026.

For the contributors working on Session, it’s exciting that developing this protocol in the open allows community members, security researchers, and users to give feedback on the proposal, ensuring that the V2 Session Protocol provides maximal security while retaining ease of use. It’s one of the wonders of working with open source tech.

Besides the V2 protocol work, we will be releasing the beta of Session Pro, which will be a huge step in making the Session ecosystem truly sustainable. And as always the developers working on Session are continually squashing bugs and adding new features to Session which improve the Session user experience, and this work will continue throughout 2026.

* * *

**Suggested Read 📖:** [_Decentralized, Open Source Alternatives to Mainstream Social Media Platforms_][3]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/session-co-founder-interview/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/mainstream-social-media-alternaives/
[4]: https://getsession.org/
[5]: https://itsfoss.com/news/alexander-linton-interview/
[6]: https://www.linkedin.com/in/kee-j-090502157/
[7]: https://www.torproject.org/
[8]: https://wiki.bitmessage.org/
[9]: https://www.getmonero.org/
[10]: https://z.cash/
[11]: https://session.foundation/
[12]: https://session.foundation/transparency-reports
[13]: https://getsession.org/session-pro-beta
[14]: https://getsession.org/blog/session-protocol-v2
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-233.png
