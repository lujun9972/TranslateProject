[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (SASE: One Year Later)
[#]: via: (https://www.networkworld.com/article/3574921/sase-one-year-later.html)
[#]: author: (Derek Granath )

SASE: One Year Later
======
Discover What You Need to get Started
iStock

A year ago on Aug. 30, 2019, Gartner published its seminal report, “The Future of Network Security is in the Cloud[[1]][1].” Even more hyped than the term “SD-WAN” a few years ago, nearly every SD-WAN vendor and every security vendor is now marketing and messaging about “SASE,” or the Secure Access Service Edge. Gartner coined the term to describe the need for the combination of WAN transformation and security transformation at the edge to enable enterprises to realize all of the benefits – the promises – of moving applications and workloads to the cloud.

To build an SASE architecture, an enterprise might start with just one transformational project, but ultimately, both WAN and security architectures must be addressed. That’s because traditional WAN and security architectures based on routers and next-gen firewalls backhaul cloud-destined application traffic through their data centers or hub sites to keep it secure (see Figure 1). But backhauling adds latency (delay) that negatively impacts cloud application performance.

[][2] Silver Peak

Figure 1: Traditional network and security architectures backhaul cloud-destined traffic to the data center, adding latency which impairs cloud application performance.

Why not send cloud-destined traffic directly to the cloud and why not do so using the Internet together with cloud-delivered security services? That’s what SASE addresses both in terms of transforming networking architecture and security architecture.

_**Network Transformation**_

From a network architecture perspective, the SASE model advocates a greatly simplified WAN edge, placing only the network functions required at the edge, ideally within a single platform that unifies the following:

  * SD-WAN
  * Routing
  * Stateful zone-based firewall
  * Advanced segmentation
  * WAN optimization
  * Application visibility and control



[SD-WAN][3] offerings are now well-beyond the early adopter stage and continue to be deployed at a breakneck pace.

_**Security Transformation**_

When applications are hosted everywhere, and users access them from anywhere and from any device (only exacerbated by the huge increase in remote workers due to the COVID-19 pandemic), the traditional security model must adapt. In the SASE model, Gartner also prescribes that the majority of security services are best served when hosted in the cloud and not on expensive, complex-to-manage next-gen firewalls deployed across branch locations. Keeping the latest threat detection and mitigation capabilities up to date is far easier when centralized in cloud. And just like SD-WAN displaces routers at the branch, cloud-delivered security services eliminate the need for next-gen firewalls at the branch.

Over the course of the past year, a myriad of differing perspectives have been published by vendors and the media alike about SASE including, it’s a replacement for SD-WAN, SD-WAN is dead, and security is the primary function with a sprinkling of SD-WAN features. These misconceptions have led to confusion and a need to clarify the meaning and intent of SASE.

A careful read of the aforementioned Gartner report, as well as follow-on reports from Gartner and other respected analysts, clearly defines SASE as the combination of SD-WAN + cloud-delivered security services; SD-WAN is a foundational component of the SASE architecture. In fact, it’s the synergy between best-of-breed SD-WAN and best-of-breed cloud-delivered security that will ultimately deliver on the vision for a secure access service edge.

_**Getting Started**_

So, how should enterprises that have not yet adopted SD-WAN or cloud-delivered security services embark on their journey to implement a secure access service edge?

Silver Peak recommends starting now with an industry-leading, field-proven, advanced SD-WAN platform such as [Unity EdgeConnect™][4]. EdgeConnect fulfills all of the branch wide area network functions as recommend in Gartner’s report as listed above.

And basic SD-WAN functionality falls short; an advanced SD-WAN is required to fully enable SASE. What SD-WAN capabilities are required to implement a robust SASE architecture?

  1. Identify applications on the first packet and granularly steer them to enforce both QoS and security policies as defined by business intent (see Figure 2)
  2. Keep cloud application definitions and TCP/IP address ranges up to date, automatically and daily, to always enable accurate and optimal internet breakout
  3. Automate orchestration between the SD-WAN and cloud-delivered security services from a single console
  4. Automatically failover to a secondary cloud security enforcement point should the primary become unreachable, avoiding application interruption
  5. Automate reconfiguration of connections to cloud security enforcement points if a newer, closer location to the branch is deployed to further minimize application latency
  6. Enable enterprises to adopt cloud security services – and their SASE implementation – at their own pace
  7. And most importantly, avoid vendor lock-in to provide freedom of choice to adopt new security innovations as they become available



[][5] Silver Peak

Figure 2: Adaptive internet breakout from the branch delivers the highest cloud application performance and enables granular, consistent security policy enforcement to provide a superior end user quality of experience while protecting the enterprise from security vulnerabilities.

Silver Peak EdgeConnect is an open WAN edge platform that provides enterprises with the freedom-of-choice to easily evaluate and integrate with any cloud-delivered security service, avoiding vendor lock-in. And Gartner’s latest “Hype Cycle for Cloud Security, 2020[[2]][6],” published in July affirms that most of today’s SASE implementations include two vendors’ network and security solutions.

_“By 2023, 20% of enterprises will have adopted SWG, CASB, ZTNA and branch FWaaS capabilities from the same vendor, up from less than 5% in 2019. However, today most implementations involve two vendors (SD-WAN + Network Security), although single-vendor solutions are appearing. Dual-vendor deployments that have deep cross-vendor integration are highly functional and largely eliminate the need to deploy anything more than a L4 stateful firewall in the branch office.”_

Silver Peak proven best-of-breed security vendor integrations include [Zscaler Internet Access][7], [Netskope Security Cloud][8], [Check Point CloudGuard Connect][9] and [Palo Alto Prisma Access][10].

As interest in SASE increases and SD-WAN solutions mature, cloud-first enterprises can confidently begin their SASE journey today with Silver Peak. Please contact your Silver Peak sales partner to schedule a deeper dive and demonstration.

**To learn more about WAN and Security Transformation, read our latest** [White Paper][11]**.**

**The Silver Peak Unity EdgeConnect SD-WAN Edge Platform has been named a leader for the second consecutive year in the Gartner 2019 Magic Quadrant for WAN Edge Infrastructure. [Get the full report][12].**

[[1]][13] “The Future of Network Security is in the Cloud,” Gartner ID G00441737, August 30, 2019

[[2]][14] “Hype Cycle for Cloud Security, 2020,” Gartner ID G00448014, July 17, 2020

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3574921/sase-one-year-later.html

作者：[Derek Granath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://blog.silver-peak.com/sase-best-of-breed-sd-wan-and-best-of-breed-cloud-delivered-security#_ftn1
[2]: https://images.idgesg.net/images/article/2020/09/sase-one-year-later_fig1-100857470-orig.jpg
[3]: https://www.silver-peak.com/sd-wan/sd-wan-explained
[4]: https://www.silver-peak.com/products/unity-edge-connect
[5]: https://images.idgesg.net/images/article/2020/09/sase-one-year-later_fig2-100857471-orig.jpg
[6]: https://blog.silver-peak.com/sase-best-of-breed-sd-wan-and-best-of-breed-cloud-delivered-security#_ftn2
[7]: https://www.silver-peak.com/sd-wan/partners/zscaler
[8]: https://www.silver-peak.com/resource-center/solution-briefs/secure-wan-access-with-silver-peak-and-netskope
[9]: https://www.silver-peak.com/resource-center/solution-briefs/check-point-and-silver-peak-optimize-enterprise-wan-security
[10]: https://www.silver-peak.com/resource-center/videos/how-edgeconnect-sd-wan-integrates-with-palo-alto-prisma-access
[11]: https://www.silver-peak.com/resource-center/access?item=4132&Asset_Downloaded__c=Successful%20Network%20and%20Security%20Transformation%20Powers%20the%20Digital%20Enterprise
[12]: https://nam05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.silver-peak.com%2Fsd-wan-edge-gartner-magic-quadrant-2019&data=02%7C01%7C%7C0c7399f0738441169ed408d83d4e7393%7C3aedb78fc8e04326888a74230d1978ff%7C0%7C0%7C637326754444037283&sdata=vsW%2BQAgt2cC05tNqcFaL%2B03r1jUtKQDU4zrHGP6a76Q%3D&reserved=0
[13]: https://blog.silver-peak.com/sase-best-of-breed-sd-wan-and-best-of-breed-cloud-delivered-security#_ftnref1
[14]: https://blog.silver-peak.com/sase-best-of-breed-sd-wan-and-best-of-breed-cloud-delivered-security#_ftnref2
