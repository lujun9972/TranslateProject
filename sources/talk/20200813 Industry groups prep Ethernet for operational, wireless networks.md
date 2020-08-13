[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Industry groups prep Ethernet for operational, wireless networks)
[#]: via: (https://www.networkworld.com/article/3570159/industry-groups-prep-ethernet-for-operational-wireless-networks.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

Industry groups prep Ethernet for operational, wireless networks
======
The Ethernet Alliance and Avnu Alliance separately are moving Ethernet technology forward with a standard for twisted-pair Ethernet and a push for time-sensitive networking over wireless.
[Andrew Hart][1] [(CC BY-SA 2.0)][2]

As Ethernet-based networks continue to evolve, two industry groups recently announced plans to take it to yet another level – this time extending the technology to operational and  wireless time-sensitive communication applications.

This week the Ethernet Alliance said it was pushing an effort to bring faster, simpler communications to the operational technology (OT) networks typically found in building and industrial automation environments. The Ethernet Alliance includes a variety of communications players including Broadcom, Cisco, Dell, Juniper, Intel as well as university and industry members.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][3]

A recently standardized IEEE specification, 802.3cg, which defines the use of Single-Pair Ethernet (SPE) in many circumstances rather than a [wide range][4] of fieldbus cables, including RS‑485 twisted-pair, RG‑6 coaxial, and instrumentation cables is behind the group’s strategy. 

### Ethernet over twisted-pair

OT networks historically have been siloed from Ethernet-based IT networks and, “these networks, while operating effectively today, use dated, disparate network protocols. They are slow, typically 31.2kb/s, and require translation gateways to convert necessary data to Ethernet. SPE is purpose-built to address the challenges and topologies of OT networks,' said Peter Jones, chair of the Ethernet Alliance and a distinguished engineer with Cisco.

"The IEEE 802.3cg specification, which published in February 2020, is the standard we’ve needed for OT networks all along," he said. The alliance wants to help apply the standard to increase the value of OT networks and improve business outcomes. The ultimate goal is an enterprise-wide single-protocol network that addresses the needs of both IT and OT. "The convergence of these two networks is key to delivering on the goals of Industry 4.0."

The IEEE 802.3cg Task Force paid close attention to the needs of OT networks during the creation of the “cg” standard. Many of the proprietary implementations have common elements. Most are electrically compliant with RS-485, have two main topologies and share a common physical layer, twisted-pair cable. SPE leverages these common elements to create a means to adopt Ethernet and all of its benefits without “reinventing the wheel” so to speak, said Bob Voss, chair of the SPE subcommittee and a senior principal engineer with [Panduit][5].

“SPE allows users to build the facilities served by OT networks in the ways they know work best; SPE is designed to support proven topologies and even uses a similar physical layer. Many SPE experts believe, given good cable health, that it could be possible to reuse physical-layer elements of current OT networks,” said Voss.

In the past, application of Ethernet in OT networks required adapting the network to work with normal BASE-T Ethernet. It was effective but created  barriers, which limited adoption. SPE tears down those barriers, Voss said.

“Also, one of the problems with current propriety OT protocols is a looming skills gap. The tribal knowledge that supports these important networks is encased in the heads of folks who are retirement age. This creates a huge business continuity risk. And, as businesses want smarter buildings to create more pleasant, productive workspaces, higher functionality is needed in OT networks and Ethernet is a key enabler,” Voss said.

### Time-sensitive networking over wireless

In the untethered world, the uptick in [5G][6] and 802.11 development has created an interest in extending Ethernet’s Time-Sensitive Networking (TSN) technology over wireless. 

The push for melding wireless and Ethernet TSN comes from the Avnu Alliance which says its members include more than 95% of the Ethernet silicon suppliers as well as automotive industry and audio-visual vendors.  Its affiliates include Cisco, Intel, Bose, Bosch, and Extreme. The Avnu Alliance defines requirements for interoperability and is the certification authority – grants certification for interoperable products – for TSN.  The Alliance does not do the actual physical testing of products; this is handled by a network of registered test facilities. For example, the [University of New Hampshire InterOperability Laboratory][7] is one registered test facility.

TSN is a collection of standards developed by the IEEE 802.1 TSN Working Group, which defines a new set of mechanisms for providing time synchronization and timeliness (deterministic data delivery) for time-sensitive data in a LAN shared with other types of best-effort applications, said Dave Cavalcanti, Avnu Alliance Wireless TSN Workgroup chair and a principal engineer at Intel.

TSN standards define new functions for 802-based LANs such as traffic shaping, frame pre-emption, traffic scheduling, ingress policing, and seamless redundancy. When all parts of a network are running with the same sense of reference time, traffic can be coordinated based on a time-aware schedule, one method that allows for better control of latency for time-critical traffic. These new features provide a whole new layer of control for managing traffic over Ethernet, Cavalcanti said.

According to Cavalcanti the IEEE 802.1 TSN standards have seen a lot of growth in the past three to five years, particularly in the industrial market.

Wireless communications using TSN not only enable mobility, they are flexible and reduce wiring costs. "TSN capabilities over wireless, for instance, can enable manufacturers to easily reconfigure industrial automation and control systems as well as enable optimized routing and utilization of mobile robots and automatic guided vehicles,” Cavalcanti said. Industrial automation system and mobile robots are important use cases because wireless is fundamental for mobility, flexibility and reconfigurability of tasks and routes.

“Electrical power grid systems are another interesting use-case for wireless TSN, as these systems have varied coverage areas which may vary from local (e.g. substation) to wide areas (distribution and transmission). Industrial control systems could also benefit from wireless connectivity, but they will require the highest level of determinism and reliability and rely exclusively on time-aware (IEEE 802.1Qbv) scheduling over wireless links,” Cavalcanti said.

There are some challenges to implementing wireless TSN extensions. 

Interference is typically the number one concern when it comes to wireless TSN extensions. The susceptibility to malicious jamming is often raised as a concern as well,  Cavalcanti said. “Although the scale of the threat needs to be considered in each specific wireless deployment and application, it is important to enable tools to mitigate the potential impact of interference (malicious or not) in a wireless TSN domain. Because TSN is based on Ethernet and wireless standards (IEEE 802.11/Wi-Fi and 5G), networks can take advantage of security best-practices and standards that have been developed for Ethernet, 802.11 and 3GPP systems.”

An additional layer of security for TSN can also be added with precise timing mechanisms that facilitate early detection of a network breach as defined in the IEEE 802.1Qci specification. The 802.1Qci capability identifies the time-sensitive streams and uses timing and schedule information to accept or discard packets. The right packet must arrive in the right time window on the right port to be accepted. This capability also needs to be extended to wireless networks, Cavalcanti said.

“Finally, not every wireless technology can (or should) currently support TSN features. Given the current and upcoming wireless capabilities in both Wi-Fi and 5G, for example, use cases that require high-speed mobility across wide areas are not yet considered practical for wireless TSN-grade performance,” Cavalcanti said. 

TSN is a networking layer that leverages underlaying data communication technologies (such as Ethernet, 802.11/Wi-Fi and eventually 5G). As such, TSN can be seen as a unifying layer operating across and potentially integrating heterogeneous connectivity technologies. The role of TSN is to ensure the end-to-end data delivery with determinism, Cavalcanti said. “Each of the individual connectivity technologies may implement its own features to help achieve TSN goals, but TSN has a broader scope than any particular connectivity technology.”

Despite the momentum and progress from others in the industry, more work is needed to bring Wireless TSN capabilities to market.  For instance, wireless specific TSN configuration interfaces, parameters, and test procedures still need to be developed, Cavalcanti said. “That is why we’ve put together the Wireless TSN working group within Avnu Alliance. The WTSN workgroup work has highlighted that it is important to start early discussions and alignment on topics such as consistent TSN interfaces for wired and wireless technologies, interoperability testing, and certification efforts.”

Join the Network World communities on [Facebook][8] and [LinkedIn][9] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3570159/industry-groups-prep-ethernet-for-operational-wireless-networks.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://www.flickr.com/photos/andrewfhart/8106189987
[2]: https://creativecommons.org/licenses/by-sa/2.0/legalcode
[3]: https://www.networkworld.com/newsletters/signup.html
[4]: https://blog.siemon.com/standards/ieee-p802-3cg-10-mbs-single-twisted-pair-ethernet-task-force
[5]: https://www.panduit.com/en/about/Research-and-Development.html
[6]: https://www.networkworld.com/article/3569282/gartner-5g-rises-as-overall-wireless-infrastructure-spending-falls.html?nsdr=true
[7]: https://www.iol.unh.edu/
[8]: https://www.facebook.com/NetworkWorld/
[9]: https://www.linkedin.com/company/network-world
