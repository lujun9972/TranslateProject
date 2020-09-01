[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (SD-WAN Enables Better Multi-Cloud Connectivity for Enterprises)
[#]: via: (https://www.networkworld.com/article/3572337/sd-wan-enables-better-multi-cloud-connectivity-for-enterprises.html)
[#]: author: (Nav Chander )

SD-WAN Enables Better Multi-Cloud Connectivity for Enterprises
======
Using SD-WAN to maximize cloud resources, deliver best experience, and eliminate speed bumps
iStock

Many enterprises are adopting multi-cloud strategies to leverage multiple cloud platforms to support an expanding range of SaaS and corporate workloads, each with unique performance and service level requirements. Typically, connecting branch office users to cloud-hosted applications requires backhauling the traffic to the corporate data center across an existing legacy WAN infrastructure consisting of traditional routers over private MPLS circuits. This conventional router-centric architecture is proving inefficient and was never designed to address the requirements of today’s modern cloud-first enterprises.

Does every SD-WAN platform ensure that cloud-hosted applications perform well over any underlying network, without compromising end user experience? Before we dive deeper into SD-WAN platform requirements and multi-cloud, let’s first examine key multi-cloud IT drivers that include the ability to:

  * Assure better application availability and reliability even if one cloud service provider experiences an outage, the application will still be available in another cloud
  * Support regulatory and compliance requirements allowing organizations to maintain the integrity of application data in a specific geographic region in accordance with local legal mandates
  * Leverage the unique advantages of each cloud, such as Google Cloud Platform’s strength in machine learning or Microsoft Azure’s seamless integration with Office 365 and Microsoft databases
  * Reduce IT spend on IT infrastructure CAPEX
  * Increase agility to on-board and connect enterprise users to new applications



A recent multi-cloud survey of 400 CIOs from [Propeller Insights][1], shown in Figure 1, highlights the most important  benefits of multi-cloud.

[][2] Silver Peak

Fig 1. Benefits of Multi-cloud deployments of 400 CIOs. March 2020

IT must ensure that end users accessing cloud applications always have an excellent, consistent quality of experience whether they are working from a remote office, branch or corporate campus site. 

What are the key SD-WAN platform requirements that enable IT to realize their multi-cloud deployment objectives and also support their end users’ ability to directly and securely access these multi-cloud applications from anywhere?

Three of the most important multi-cloud requirements for an SD-WAN platform are:

  * Automate branch-multi-cloud connectivity to scale applications horizontally across multiple cloud providers with the flexibility to select the best cloud provider for the right application
  * Assure consistent  performance of business applications by applying granular QoS and security policies based on end user, groups profiles prioritized by application
  * Support accessibility of enterprise hosted applications across the four leading public cloud providers



The Silver Peak [Unity EdgeConnect™][3]  SD-WAN edge platform is the right vehicle to address the challenges associated with backhauling branch-cloud-destined traffic to the data center, thereby reducing the cost of bandwidth connectivity from the data center to cloud providers and reducing latency by enabling direct branch-cloud connectivity. Silver Peak has integrated the EdgeConnect platform with cloud provider APIs to simplify connectivity for [multi-cloud deployments][4]. 

Key EdgeConnect SD-WAN capabilities include:

[][5] Silver Peak

**Business Intent Overlays:** Intent-based application security, connectivity and control that easily supports simultaneous use of multiple cloud platforms, enabling IT to optimize the best cloud provider for a particular application 

**Centralized orchestration** **of IaaS and SaaS connectivity policies and services:** The Unity Orchestrator™ intuitive graphical user interface (GUI) simplifies orchestrating cloud connectivity, changing and maintaining policies for multi-cloud hosted applications, ensuring consistent policies are enforced across the enterprise

**Automate and secure connectivity to public clouds:** Simplify branch connectivity to Microsoft Azure vWAN, providing access to the global Microsoft network, and between the global AWS network and branch locations via AWS Transit Gateway Network Manager (TGNM)

**Branch-to-Cloud Edge Connectivity:** An EdgeConnect appliance deployed at each branch office enables seamless end-to-end connectivity to the public cloud providers by extending the SD-WAN fabric and deploying a virtual instance of EdgeConnect in any or all of the four public cloud providers shown in Figure 2. This supports predictable application performance and the highest end user quality of experience. 

In this branch-to-cloud edge solution, enterprises can leverage the true benefits delivered by an EdgeConnect SD-WAN multi-cloud fabric. Enterprises can easily move workloads from one cloud provider to another, for example from AWS to Azure using business intent overlays. 

When you are planning your multi-cloud journey, remember that SD-WAN can help you maximize your cloud service resources, deliver the highest quality of experience to application users and ensure that that there are no speed bumps on your multi-cloud journey.

Learn more about flexible multi-cloud options for enterprises to leverage SD-WAN connectivity by tuning into the Silver Peak webinar, [“Powering the Multi-Cloud enterprise with SD-WAN.”][6]

The Silver Peak Unity EdgeConnect SD-WAN Edge Platform has been named a leader for the second consecutive year in the Gartner 2019 Magic Quadrant for WAN Edge Infrastructure. [Get the full report][7].

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3572337/sd-wan-enables-better-multi-cloud-connectivity-for-enterprises.html

作者：[Nav Chander][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.volterra.io/company/news/infrastructure-security-challenges-threaten-multi-cloud-edge-deployments
[2]: https://images.idgesg.net/images/article/2020/09/how-sd-wan-streamlines-your-multi-cloud-journey_1-100856258-orig.jpg
[3]: https://www.silver-peak.com/products/unity-edge-connect
[4]: https://www.silver-peak.com/sd-wan/multi-cloud-networking
[5]: https://images.idgesg.net/images/article/2020/09/how-sd-wan-streamlines-your-multi-cloud-journey_2-100856259-orig.jpg
[6]: https://www.silver-peak.com/resource-center/webcast-powering-multi-cloud-enterprise-sd-wan
[7]: https://nam05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.silver-peak.com%2Fsd-wan-edge-gartner-magic-quadrant-2019&data=02%7C01%7C%7C0c7399f0738441169ed408d83d4e7393%7C3aedb78fc8e04326888a74230d1978ff%7C0%7C0%7C637326754444037283&sdata=vsW%2BQAgt2cC05tNqcFaL%2B03r1jUtKQDU4zrHGP6a76Q%3D&reserved=0
