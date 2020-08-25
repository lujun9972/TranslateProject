[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Silver Peak and Zscaler: Making SASE Work for You)
[#]: via: (https://www.networkworld.com/article/3572631/silver-peak-and-zscaler-making-sase-work-for-you.html)
[#]: author: (Derek Granath )

Silver Peak and Zscaler: Making SASE Work for You
======
WAN and security transformation powers a secure access service edge that maximizes the return on cloud investments
iStock

As part of their digital transformation strategy, many enterprises are actively migrating applications to public cloud infrastructure and Software-as-a-Service offerings. Enterprise IT objectives and expected benefits of cloud migration include:

  * Increased agility
  * Higher application performance and availability
  * Improved application accessibility for users
  * Reduced data center footprint
  * Lower costs



Unfortunately, the transformational promise of the cloud often falls short of meeting these expectations. Why? Because traffic patterns have changed. They have changed not only due to the migration of apps to the cloud, but also in response to today’s “work-from-anywhere” world.

Users now access applications from anywhere, from any device and across diverse WAN transports, including residential broadband. IT has quickly come to realize that making incremental investments in their legacy routers and firewalls didn’t yield the desired outcomes. Traffic bound for the Internet was still backhauled to the corporate data center, adding unnecessary latency and negatively impacting application performance. What’s required is a complete transformation of the wide area network, and this transformation has fueled the biggest evolution of the WAN in two decades: the software-defined wide area network or SD-WAN.

The combination of workers accessing business applications from home and remote locations (e.g. airports, coffee shops), along with the explosive growth of IoT devices is rendering the traditional enterprise security perimeter ineffective. Today’s cloud-first enterprise must arm workers with a security service solution that follows them wherever they go. As we’ve already seen, continuing to use a hub-and-spoke architecture, backhauling Internet-bound traffic to the data center for advanced security inspection, results in a sub-optimal user experience. What’s needed is a complete transformation of security infrastructure, and this has driven the rapid adoption of modern cloud-delivered security services.

#### **WAN Transformation + Security Transformation = Digital Transformation**

Only by transforming both the WAN edge and security architectures can the full promise of the cloud be fully realized. In a report published by Gartner in November 2019, they proposed a new model called the secure access services edge – SASE for short. The model describes the integration of core WAN edge capabilities such as SD-WAN, routing and WAN optimization at the branch locations with a comprehensive array of cloud-delivered security services such as secure web gateway (SWG), firewall-as-a-service (FWaaS), cloud access security broker (CASB), zero trust network access (ZTNA) and more. A key design principal of SASE is the transformation from complex hardware-laden branches to thin branches with cloud-native security services. The promises of the SASE model are many:

  * Improved user experience by delivering better application performance by breaking out cloud traffic locally over the internet from the branch
  * Operational efficiency by simplifying branch WAN infrastructure and through centralized orchestration of application, network and security policies
  * Reduced risk with consistent, always-up-to date, business-driven security policy enforcement
  * Increased business agility by significantly reducing the time to bring new sites and applications online or to update application and security policies



But simply adopting just any SD-WAN solution and cloud security offering is not enough to maximize the return on cloud investments described earlier. While those individual solutions might deliver on the app performance/availability and accessibility promises and enable shrinking the data center, that approach falls short of delivering increased business agility and lower costs. And it won’t address consistent security policy enforcement across all users, locations and devices to mitigate risk to the enterprise. What’s needed is fully automated orchestration of the WAN edge network functions and cloud-delivered security services. This is a 1 + 1 = 3 benefit for IT and the enterprise

#### **Silver Peak and Zscaler Automate Orchestration of Cloud-delivered Security**

In April of 2019, [Silver Peak][1] and [Zscaler][2] launched an [API-based integration][3] that fully automates the configuration of cloud-delivered security from a centralized orchestration point, using Silver Peak Unity Orchestrator™. From Orchestrator, IT can define and apply security policies to hundreds of sites in just a few minutes. Not only does the automation save significant time for IT, it also provides more consistent security policy enforcement by virtually eliminating human errors during the configuration process.

Fast forward to May 2020, Silver Peak and Zscaler have introduced an enhancement that provides even finer granularity of application, user and device control. The new enhancement allows exceptions to general security policies to be enforced for sub-locations – or segments – within a branch. This is more easily understood with an example. ACME Inc. might define the following set of policies:

  1. Enterprise traffic requires SSL inspection
  2. IoT devices accessing the network require SSL inspection but not user authentication, and
  3. Guest Wi-Fi access should not have SSL inspection enabled due to privacy concerns



With the new enhancement, SSL inspection will be enforced for all enterprise, cloud and IoT traffic, but not for traffic traversing the Guest Wi-Fi vLAN. Again, using Silver Peak Orchestrator, IT defines the policy exceptions for sub-locations and pushes them to all sites in a matter of minutes.

Silver Peak and Zscaler have also introduced a new capability that improves the performance and responsiveness of network and the security service if a degradation or failure is detected. With this enhancement, each EdgeConnect appliance continuously monitors the end-to-end health of branch connectivity to the Zscaler service. The health check includes all aspects of the end-to-end connectivity including the underlay network links, the IPsec tunnel and the Zscaler service itself. This comprehensive health check enables fully automated failover to secondary facilities when connectivity problems arise anywhere along the path from the branch office to the Zscaler security service.

#### **Silver Peak/Zscaler Collaborative Support**

In addition to the new product innovations, Silver Peak and Zscaler have established a formal collaborative support process (CSP) to expedite direct engagement between the respective support organizations. The objective of the CSP is to accelerate effective resolution of any issues that might arise with the joint solution. Customers can initiate a support case with either company at any time, and both support teams have the ability to escalate directly between one another. This eliminates the burden from the customer and provides the fastest path to root cause identification and issue resolution.

#### **Industry-leading WAN and Security **

Together, Silver Peak and Zscaler automated orchestration provides seamless WAN edge and cloud-delivered security integration, all managed from a central management system, Unity Orchestrator. Enterprises looking to adopt a SASE infrastructure require a “no compromise” WAN edge and security transformation strategy to realize a multiplier effect from their existing and ongoing cloud investments.

_The Silver Peak Unity EdgeConnect SD-WAN Edge Platform has been named a leader for the second consecutive year in the Gartner 2019 Magic Quadrant for WAN Edge Infrastructure. [Get the full report][4]._

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3572631/silver-peak-and-zscaler-making-sase-work-for-you.html

作者：[Derek Granath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.silver-peak.com/sd-wan/partners/zscaler
[2]: https://www.zscaler.com/solutions/partners/silver-peak
[3]: https://www.silver-peak.com/resource-center/solution-briefs/secure-wan-access-with-silver-peak-and-zscaler
[4]: https://nam05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.silver-peak.com%2Fsd-wan-edge-gartner-magic-quadrant-2019&data=02%7C01%7C%7C0c7399f0738441169ed408d83d4e7393%7C3aedb78fc8e04326888a74230d1978ff%7C0%7C0%7C637326754444037283&sdata=vsW%2BQAgt2cC05tNqcFaL%2B03r1jUtKQDU4zrHGP6a76Q%3D&reserved=0
