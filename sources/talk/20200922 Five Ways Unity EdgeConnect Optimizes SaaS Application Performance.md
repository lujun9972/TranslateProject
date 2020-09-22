[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Five Ways Unity EdgeConnect Optimizes SaaS Application Performance)
[#]: via: (https://www.networkworld.com/article/3576000/five-ways-unity-edgeconnect-optimizes-saas-application-performance.html)
[#]: author: (Karan Singh Dagar )

Five Ways Unity EdgeConnect Optimizes SaaS Application Performance
======
Intelligence is Key Ingredient for Advanced SD-WAN
iStock

More and more enterprises have migrated business-critical applications to software-as-a-service (SaaS) offerings such as Box, Dropbox, Salesforce, and Office365. Backhauling SaaS application traffic to the data center and then to cloud is inefficient and adds to the latency experienced by the application. Therefore, many cloud-first enterprises are adopting [SD-WAN solutions][1] to breakout SaaS application traffic locally from the branch site to optimize SaaS application performance and deliver the highest quality of experience to users.

With local breakout from the branch, the Internet is used as a primary means of transport for SaaS applications. However, achieving MPLS-like performance over Internet is complex because of its unpredictable nature. Congested one day and tolerable the next, Internet “weather” undermines the consistency of SaaS delivery, even in regions with highly developed internet infrastructure. Therefore, it is critical for cloud-first enterprises to deploy an advanced SD-WAN solution that address performance concerns of sending traffic over the Internet. The Silver Peak [Unity EdgeConnect™ SD-WAN Edge platform][2] incorporates five technology pillars that optimize the performance of every type of SaaS application.

**Pillar #1: Cloud Intelligence, DNS Proxy and First-packet iQ**

SaaS applications are constantly changing, including the IP addresses used to access them. Programming ACLs for specific IPs is an impossible task since IP addresses are deleted and re-provisioned continuously. Silver Peak Cloud Intelligence maintains a database of the IP addresses utilized by more than 10,000 SaaS applications. Automated daily updates are automatically pushed to deployed EdgeConnect appliances to keep them up to date with ever-changing definitions and attributes of cloud applications.

In order to reach a SaaS application, the DNS server needs to quickly resolve the names of the SaaS applications into IP addresses. With EdgeConnect, customers can reach DNS servers in the nearest proximity to branch sites, eliminating backhaul of the DNS request to the remote data centers where enterprise DNS servers are hosted.

EdgeConnect appliances not only distinguish traffic from different applications, they do so with maxi­mum efficiency. Silver Peak First-packet iQ™ identifies and classifies application traffic on the first packet, enabling granular traffic steering. Using Silver Peak central management software, Unity Orchestrator™, customers can define custom traffic steering policies for each class of application.

[
][3] Silver Peak

#####  

**Pillar #2: O365 REST API Integration**

With Office 365 REST API integration, Silver Peak continuously learns and discovers new Office 365 end points and/or IP addresses and automatically re-configures EdgeConnect if a new, closer Office 365 end point becomes available. By doing so, users always achieve optimal Office 365 con­nectivity and performance by reducing the round-trip time (RTT).

The EdgeConnect SD-WAN edge platform has been independently tested and certified to support the Microsoft Office 365 Connectivity Principles and provide reliable connections directly from branch office locations to the nearest Office 365 entry point. As a result of the independent testing, the EdgeConnect platform has been inducted into the Microsoft 0ffice 365 Networking Partner Program and has been given the official “Works with Office 365” designation.

[][4] Silver Peak

**Pillar #3: Intelligent Cloud Breakout**

Most UCaaS service providers (Ring Central and 8×8) and many SaaS applications like Dropbox, Box, Salesforce, Slack, Skype for Business and G Suite have deployed high-speed backbone connections with massive band­width between their data centers and leading IaaS platforms such as AWS, Azure, and GCP.  With Silver Peak, customers can deploy a virtual EdgeConnect SD-WAN appliance within their IaaS instance. All Silver Peak path conditioning and optional WAN optimization capabilities operate between branches and the IaaS platform which “ruggedizes” the first mile. This provides higher levels of performance and reliability for SaaS applications with points of presences co-located in the same data center as the IaaS instance.

[][5] Silver Peak

As shown above, EdgeConnect continuously monitors the throughput, packet loss, latency, jitter and MOS across all transport services and automatically adapts if performance falls below pre-defined service level thresholds. Should a brownout or blackout occur, the remaining link(s) in the tunnel continue to carry traffic so that the users don’t notice any disruption to voice calls, audio and video conferences, or any other application.

**Pillar #4: Support for Custom User-Defined Applications**

Many organizations continue to support custom in-house applications that are hosted in their corporate data centers. Users at branch locations typically access these custom apps across an MPLS connection back to the data center. Such custom applications are critical for the enterprise and using Silver Peak SD-WAN solution, customers can ensure optimal performance of these applications. From Orchestrator, IT can easily configure a custom application definition that enables EdgeConnect to identify and classify it on the first packet. The application definition may include parameters such as the destination IP address and TCP port number, protocol type (TCP or UDP) and other application identifying information within the packet header. Once the application signature has been programmed, EdgeConnect identifies and dynamically steers traffic as defined by the applicable business intent overlay (BIO).

**Pillar #5: Intelligent Internet Breakout**

Often enterprises provision two or more WAN links from the remote branch site to increase network and application availability and performance. These links are used for breaking out traffic locally at each branch. To optimize utilization of the provisioned WAN internet links, EdgeConnect monitors the performance of all WAN links by continuously measuring packet loss, jitter, latency and mean opinion score (MOS) in real-time. EdgeConnect uses statistical learning to determine the optimal forwarding link, maintaining peak application performance.

Implementing a SaaS application is critical for the enterprises to maintain a competitive edge. Silver Peak SaaS Optimization features ensure that no matter what combination of SaaS applications an enterprise deploys, performance is highly optimized and delivers best quality of experience for end users.

**The Silver Peak Unity EdgeConnect SD-WAN Edge Platform has been named a leader for the second consecutive year in the Gartner 2019 Magic Quadrant for WAN Edge Infrastructure. [Get the full report][6].**

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3576000/five-ways-unity-edgeconnect-optimizes-saas-application-performance.html

作者：[Karan Singh Dagar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.silver-peak.com/sd-wan
[2]: https://www.silver-peak.com/products/unity-edge-connect
[3]: https://images.idgesg.net/images/article/2020/09/five-ways-unity-edgeconnect-optimizes-saas-application-performance_1.1-100858493-orig.jpg
[4]: https://images.idgesg.net/images/article/2020/09/screen-shot-2020-09-22-at-10.45.54-am-100858499-orig.jpg
[5]: https://images.idgesg.net/images/article/2020/09/screen-shot-2020-09-22-at-10.51.32-am-100858503-orig.jpg
[6]: https://nam05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.silver-peak.com%2Fsd-wan-edge-gartner-magic-quadrant-2019&data=02%7C01%7C%7C0c7399f0738441169ed408d83d4e7393%7C3aedb78fc8e04326888a74230d1978ff%7C0%7C0%7C637326754444037283&sdata=vsW%2BQAgt2cC05tNqcFaL%2B03r1jUtKQDU4zrHGP6a76Q%3D&reserved=0
