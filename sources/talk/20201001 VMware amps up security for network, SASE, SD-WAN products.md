[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (VMware amps up security for network, SASE, SD-WAN products)
[#]: via: (https://www.networkworld.com/article/3583939/vmware-amps-up-security-for-network-sase-sd-wan-products.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

VMware amps up security for network, SASE, SD-WAN products
======
VMware is filling out its SASE and SD-WAN offerings and bolstering NSX security capabilities, the company announced at its virtual VMworld event.
Peshkov / Getty Images

At its virtual [VMworld 2020][1] conclave this week, VMware took the wraps off a number of security enhancements aimed at the growing COVID-driven remote workforce.

For starters, the company boosted security for remote and mobile workers by extending its partnerships with zScaler and Menlo for its secure-access service edge ([SASE][2]) offering, [VMware SD-WAN Zero Trust Service][3]. VMware's SASE technology melds its Workspace ONE platform with its SD-WAN package. 

**More about edge networking**

  * [How edge networking and IoT will reshape data centers][4]
  * [4 essential edge-computing use cases][5]
  * [Edge computing best practices][6]
  * [How edge computing can help secure the IoT][7]



According to VMware, the Workspace ONE platform securely manages end users' mobile devices and cloud-hosted virtual desktops and applications from the cloud or on-premise. With Workspace ONE, a customer's remote-access client automatically connects to the closest VMware [SD-WAN][8] cloud point of presence. VMware's SASE platform takes advantage of VMware SD-WAN's global footprint of more than 2,700 cloud service nodes across 130 PoPs, the company stated this week.

Under a "preferred partnership" with cloud security vendor zScaler, customers can let only trusted devices and users access applications hosted on-premises or in the cloud. The service uses Zscaler's [Secure Web Gateway][9], which features URL filtering, malicious-code detection and filtering, and application controls for popular Web-based applications.

Another component of a SASE offering is a cloud access service broker ([CASB][10]), and for that VMware is partnering with Menlo for its cloud-based CASB service, which enforces access and security policies and controls for cloud applications.

Gartner, which coined the term SASE, this week stated that by 2024, more than 60% of software-defined, wide-area network (SD-WAN) customers will have implemented a SASE architecture, compared with about 35% in 2020.

Related to the SASE/SD-WAN integration, VMware said a new version of its VMware vRealize Network Insight software will get expanded SD-WAN management features.

"These updates will enable better planning for virtual and physical networks, improved network uptime and resiliency, faster troubleshooting, and proactive identification of potential network problems based on intent, and more effectiveness in achieving service level agreements," VMware stated.

On a broader scope, VMware announced Edge Network Intelligence, which is the integration of technology the company [acquired from AI-based network management and analytics firm Nyansa][11] in January.

Combining VMware's SD-WAN/ SASE package with Nyansa's cloud-based AIOps platform offering, "users will have access to a single platform that can deliver comprehensive and actionable data on network traffic and application performance from the cloud, to branch offices, to the end user and across their wired and/or wireless devices," VMware stated. 

VMware Edge Network Intelligence is part of VMware's Virtual Cloud Network architecture that defines how enterprises can build and control network connectivity and security from the [data center][12] across the WAN to multi-cloud environments. It includes the company's core networking software, [VMware NSX][13], which underpins the VCN architecture.

The company announced NSX version 3.1 and said with it, customers will be able to support larger-scale deployments and disaster recovery use cases and automated deployment workflows. One feature of NSX is the ability to control and synchronize multiple virtual networks as a single entity. Called NSX Federation, the feature lets customers set network configuration, management and policy setting across large environments. 

NSX Federation lets customers generate "fault tolerant zones" where they could contain network problems in a single zone, minimizing problems and preventing them from spreading, VMware stated. 

With version 3.1, VMware said it will double the scale of NSX Federation, add new API-driven advanced routing and multicast capabilities, and offer Terraform provider support.

Also under NSX, the company said it will roll out its stateful Layer 7 firewall-as-a-service, which will be useful for customers of its SASE package, offering customers cloud-based security protection, the company said.

VMware also announced NSX Advanced Threat Prevention, which combines NSX distributed IDS/IPS with advanced malware detection and AI-powered network traffic analysis the company acquired from AI-based network detection and response vendor Lastline in June. The package lets customers identify threats and minimize false positives, VMware said.

"The NSX architecture will allow Lastline to perform network analytics at massive scale, across tens of thousands of cores, without the burden of tapping network traffic," wrote Tom Gillis, senior vice president and general manager of VMware's Networking and Security Business Unit, in a [blog][14] about the Lastline purchase. "Furthermore, NSX has an intrinsic understanding of application topology and speaks Layer 7. So it knows the difference between a web server and a database and understands what an application is doing."

Join the Network World communities on [Facebook][15] and [LinkedIn][16] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3583939/vmware-amps-up-security-for-network-sase-sd-wan-products.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3583990/vmware-plan-disaggregates-servers-offloads-network-virtualization-and-security.html
[2]: https://www.networkworld.com/article/3574014/what-is-sase-a-cloud-service-that-marries-sd-wan-with-security.html
[3]: https://www.networkworld.com/article/3564154/vmware-offers-up-a-sase-service-with-sd-wan-built-in.html
[4]: https://www.networkworld.com/article/3291790/data-center/how-edge-networking-and-iot-will-reshape-data-centers.html
[5]: https://www.networkworld.com/article/3573587/4-essential-edge-computing-use-cases.html
[6]: https://www.networkworld.com/article/3331978/lan-wan/edge-computing-best-practices.html
[7]: https://www.networkworld.com/article/3331905/internet-of-things/how-edge-computing-can-help-secure-the-iot.html
[8]: https://www.networkworld.com/article/3031279/sd-wan-what-it-is-and-why-you-ll-use-it-one-day.html
[9]: https://www.zscaler.com/resources/security-terms-glossary/what-is-secure-web-gateway
[10]: https://www.networkworld.com/article/3104545/what-is-a-cloud-access-security-broker-and-why-do-i-need-one.html
[11]: https://www.networkworld.com/article/3515930/vmware-targets-sd-wan-management-with-nyansa-acquisition.html
[12]: https://www.networkworld.com/article/3223692/what-is-a-data-centerhow-its-changed-and-what-you-need-to-know.html
[13]: https://www.networkworld.com/article/3536607/vmware-overhauls-nsx-software-to-manage-secure-larger-virtual-networks.html
[14]: https://blogs.vmware.com/networkvirtualization/2020/06/lastline.html/
[15]: https://www.facebook.com/NetworkWorld/
[16]: https://www.linkedin.com/company/network-world
