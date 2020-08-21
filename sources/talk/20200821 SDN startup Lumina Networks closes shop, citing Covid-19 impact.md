[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (SDN startup Lumina Networks closes shop, citing Covid-19 impact)
[#]: via: (https://www.networkworld.com/article/3571116/sdn-startup-lumina-networks-closes-shop-citing-covid-19-impact.html)
[#]: author: (Andy Patrizio https://www.networkworld.com/author/Andy-Patrizio/)

SDN startup Lumina Networks closes shop, citing Covid-19 impact
======
Some of the software will be released as open source but much of it will fade out as the company refused to sell to a closed-source vendor.
bigstock

Lumina Networks, a startup spun-off from the [purchase and splintering][1] of Brocade in 2017, is shutting down, citing delays in customer deployments due in part to Covid-19, which starved it for cash. The company had raised $14 million in venture capital, including investments from AT&amp;T and Verizon, but it wasn’t enough.

Lumina Networks provided an open source-based SDN controller, called the Lumina SDN Controller, which was formerly the Brocade SDN Controller and power by the OpenDaylight technology. Lumina’s claim to fame was that the SDN Controller could manage both the physical and virtual from the same platform.

Lumina says the OpenDaylight SDN controller has three parts: a central Service Abstraction layer that normalizes all data exchange via YANG; a “southbound” selection of control interfaces that connect to common switches and routers using protocols such as NETCONF, OpenFlow, BGP/PCEP, and OVSDB; and a “northbound” API aimed at supporting applications using RESTCONF.

This architecture allows the controller to enable software-defined networking by abstracting and normalizing the interface to a variety of network devices and providing telemetry for closed-loop automation.

The company sounded a little bitter in announcing its shutdown, although it’s hard to fault them. “Essentially, revenue continued to flow to proprietary vendors. The switch to open source did not take place at a pace anywhere close to the speed that would enable us to operate and grow our business, despite commitments from many to the contrary. We have also found that COVID-19 has actually redirected funds away from automation projects and into building-out raw infrastructure, further delaying adoption,” the statement read.

“Selling Lumina to a proprietary vendor who is naturally antithetical to our mission proved an impossible task and for this reason we must now close our business,” it concluded.

Some of the work done on the controller will be available as open source through the [OpenDaylight Project][2].

Join the Network World communities on [Facebook][3] and [LinkedIn][4] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3571116/sdn-startup-lumina-networks-closes-shop-citing-covid-19-impact.html

作者：[Andy Patrizio][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Andy-Patrizio/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3138085/broadcom-doesnt-want-all-of-brocade-so-what-will-happen-to-the-leftover-ethernet-business.html
[2]: https://www.opendaylight.org/
[3]: https://www.facebook.com/NetworkWorld/
[4]: https://www.linkedin.com/company/network-world
