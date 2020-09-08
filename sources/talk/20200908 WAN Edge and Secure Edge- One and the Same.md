[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (WAN Edge and Secure Edge: One and the Same?)
[#]: via: (https://www.networkworld.com/article/3573805/wan-edge-and-secure-edge-one-and-the-same.html)
[#]: author: (Jason Bloomberg )

WAN Edge and Secure Edge: One and the Same?
======
The New Normal Changes Thinking About Securing the Edge Jason
iStock

Wide-area networks (WANs) have connected remote office locations to corporate headquarters for decades now. Put satellite offices on the corporate network, so the reasoning went, and now remote employees can connect to all internal applications and data available to any headquarters-based cube dweller.

Furthermore, WANs extended the corporate security perimeter, effectively drawing a line in the sand around all those remote locations that attackers would be loath to cross.

Ah, those were the days.

Today, enterprises are likely to turn to [SD-WAN technology][1] to leverage a mix of private networks and broadband. The goal: rearchitect the WAN to afford connectivity to an increasingly diverse collection of remote offices, pop-up locations, and individual employees working from coffee shops, client locations, and today, from home – what we can call the _WAN edge_.

Those employees all want to access cloud-based resources – and they certainly don’t want their traffic to take a detour through the corporate data center to get to the cloud if they can help it.

Furthermore, perimeter-based security is now woefully inadequate to deal with the cloud generally, or to address the exploding threat surface that today’s burgeoning WAN edge represents. 

From mobile devices to the Internet of Things (IoT), modern cybersecurity requires a complete revamp of the perimeter-based approaches of yore. This new take on security is the _secure edge_.

Predictably, many products have entered the market to provide the connectivity advantages of SD-WAN and address the limitations of perimeter-based security. Given that providing remote connectivity and securing that connectivity are interrelated, so too are the products that seek to address these challenges.

As a reaction to this plethora of products, several vendors have sought to combine WAN edge and secure edge capabilities onto a single platform that offers more than traditional SD-WAN – what Gartner calls a _Secure Access Service Edge_, or SASE.

Enterprises will want to implement SASE, Gartner’s theory goes, because (a), they’re moving to the cloud and by extension, the edge; and (b) an all-in-one converged offering will be less complicated and less expensive than maintaining a collection of different best-of-breed products. 

To be sure, it makes perfect sense to balance network functions and security resident in the branch while shifting more advanced security functions and capabilities to the cloud. If the applications, services, and infrastructure are in the cloud, then security should be too.

However, SASE might not be the best solution in the short term. Fundamentally, the WAN edge must integrate on-premises security capabilities, while the broader set of security functions should be in the cloud where the applications are. 

It must also be straightforward for enterprises to deploy and swap out these cloud-based security functions should a better security offering become available. 

##### **Lessons of the Work from Home Era**

In the old days (like last February), your WAN connected users in headquarters and branch or remote offices to applications wherever they reside. 

Today it also connects to Mary’s house, where she is accessing files on her corporate network and her kids are busy playing Fortnite. What is the best way to think about WAN and security now?

There are two parts of this challenge. From the WAN edge perspective, Mary’s employer should deploy SD-WAN technology that enables her to access resources on the corporate LAN, as well as enterprise cloud services. Furthermore, her son’s gaming would not interfere with her quality of experience for the business applications she uses to do her job.

In terms of security, the brutal truth is that bad actors have redoubled their attacks during the work from home (WFH) period, as the attackers know that corporations may be at their most vulnerable at the edge.

In any case, her employer should ideally implement both WAN edge and secure edge technologies appropriate for the WFH situation. Perhaps a SASE product is the best fit for this situation, or perhaps not. 

Other situations will have different requirements. Say, for example, a retailer wants to set up point-of-sale systems at pop-up (transitory) retail locations, say at a mall or a sporting event. 

WAN requirements may be straightforward, but the fact that point-of-sale deals with credit card numbers and other personal information jacks up the security requirement (specifically, privacy and compliance). In fact, SD-WAN enables the ability to segment such traffic for PCI compliance purposes.

Let’s add a third scenario to the mix. A large factory has a multifaceted IoT deployment, including sensors and cameras integrated into the factory production equipment.

Clearly, this factory’s WAN edge and secure edge requirements are quite different from the retailer and WFH scenarios. A SASE product may be adequate for one of them, but it’s unlikely to be the best choice for all three situations.

##### **The Intellyx Take**

The diversity of use cases this article describes is but one dimension to consider. The other dimension is change over time.

Not only are the WAN and secure edges extraordinarily dynamic, but so is the full breadth of enterprise IT infrastructure. Given the suddenness of COVID, the WFH example in particular illustrates how quickly the business environment can change. 

In this case, a pandemic caused the upheaval, but next time it could be a change in the economic climate, regulatory regime, or competitive landscape – or some other, even less predictable disruption.

Cybersecurity is also an extraordinarily fluid cat and mouse game, as attackers try ever more sophisticated attacks on overcommitted enterprise targets. Cybersecurity is a never-ending battle.

Converged product suites struggle with responding to such dynamic, diverse forces of change, while uncoordinated best-of-breed approaches risk succumbing to overwhelming complexity.

The WAN edge platform must have the ability to leverage open APIs to effectively integrate a host of different cloud security services, simplifying deployment without added management overhead. 

SASE may be appropriate long term, but it might not be the right solution today, given the variability of paths to arrive at a secure WAN edge.

[Watch this webcast][2] to learn how TrialCard extended its SD-WAN to support 400+ remote workers, going live in under two weeks, all while maintaining business productivity and continuity.

The Silver Peak Unity EdgeConnect SD-WAN Edge Platform has been named a leader for the second consecutive year in the Gartner 2019 Magic Quadrant for WAN Edge Infrastructure. [Get the full report][3].

_Copyright © Intellyx LLC. Silver Peak is an Intellyx customer. Intellyx retains final editorial control of this article._

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3573805/wan-edge-and-secure-edge-one-and-the-same.html

作者：[Jason Bloomberg][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.silver-peak.com/sd-wan
[2]: https://www.silver-peak.com/zero-to-400-in-just-two-weeks-webcast
[3]: https://nam05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.silver-peak.com%2Fsd-wan-edge-gartner-magic-quadrant-2019&data=02%7C01%7C%7C0c7399f0738441169ed408d83d4e7393%7C3aedb78fc8e04326888a74230d1978ff%7C0%7C0%7C637326754444037283&sdata=vsW%2BQAgt2cC05tNqcFaL%2B03r1jUtKQDU4zrHGP6a76Q%3D&reserved=0
