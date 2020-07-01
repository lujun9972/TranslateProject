[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Inside network automation trends)
[#]: via: (https://www.networkworld.com/article/3539051/inside-network-automation-trends.html)
[#]: author: (Jeff Vance )

Inside network automation trends
======
How to cut costs, boost uptime and streamline data center operations through network automation.
Automation-Innovation

With the novel coronavirus dragging the global economy into recession and forcing entire workforces to telecommute, many businesses have been forced into an early stress test of their digital transformation (DX) investments.

The results of those pop quizzes have been mixed. On one hand [Zoom Bombs][1] are now a thing, but on the positive side, most IT organizations have found that supporting a surge in remote workers is a challenge they were ready for, one different mostly in scale, not kind.

After all, in the past few years, businesses in a range of market sectors, from banking to insurance to retail, have invested heavily in DX initiatives. In the financial sector, Ovum Research found that [banks spent close to $10 billion in 2018 on front-office digital banking initiatives][2] alone.

##### [ Career roadmap: [How to become an enterprise architect][3] ]

Globally, spending on the technologies and services that enable the DX of business practices, products, and organizations is forecast to reach $2.3 trillion in 2023, according to International Data Corporation’s ([IDC][4]) [Worldwide Semiannual Digital Transformation Spending Guide][5]. DX spending is expected to steadily expand throughout the 2019-2023 forecast period, achieving a five-year compound annual growth rate of 17.1%.

Yet, anytime there is a spike in the demand for bandwidth, you can bet that new bottlenecks will form. Now, as social distancing and stay-at-home mandates exponentially increase the demand for bandwidth, networks that run on legacy infrastructure are straining to keep up with the spike in demand.

A major, but often overlooked, bottleneck that holds bandwidth-hungry applications back is the one caused by outdated network infrastructure and routing systems. Too much networking infrastructure is still manually maintained and managed, and adding capacity, especially with private lines, can take not just hours or days, but weeks or even months.

Meanwhile, DX efforts have evolved in how they treat the cloud. “We’ve gone from the cloud being a destination, as somewhere to store data, to the cloud being a concept. Now, IT leaders regard cloud computing as an operating model and set of principles,” said [Brad Casemore, research VP, data center networks][6] for IDC.

##### [ Tech careers: [IT certifications and training center][7] ]

As that operating model and those computing principals catch on, however, there remains a gap between the reality on the ground and the eventual goal. In the meantime, the transitional period involves hybrid architectures that stitch together various private and public clouds. These hybrid models do the job, and they protect legacy investments, but they also add layers of complexity.

From a maintenance, control, and, in heavily regulated industries, compliance standpoint, these large, multi-cloud, service-focused infrastructures have grown too unwieldy to manage, secure and govern using legacy tools and manual methodologies.

### IBM SaltStack tackles hyperscale problems through automation

When Brian Armstrong, a network engineering executive, arrived at IBM Cloud in 2017, the networking team had already built out a hyperscale-sized network that featured 68,000 switches and routers.

“Our engineers are talented and good at scripting, so the last thing they want to do is manually configure devices,” Armstrong said. Plus, manually managing and maintaining a network of that size using traditional tools and methodologies would require a much larger staff, especially as IBM Cloud continues to scale up.

The use of scripts is common in DevOps, but this approach only scales in environments with consistent computing platforms and operating systems. It’s a different story for NetOps teams, especially those working with hyperscale environments that have evolved over time and feature heavy investments into legacy gear.

##### **[ Don't miss:** [Mike Elgan every week on Insider Pro][8] ]

“If we wanted to do a firmware update across our network, we had no unified way to do that,” Armstrong said. “So, our first automation goal was a simple one: we needed to get organized.”

IBM Cloud data centers feature a range of different devices from different vendors in a variety of different models running on different OSes. In large heterogeneous networks, even scripting shortcuts is still extremely labor-intensive. Moreover, relying on a bunch of ad-hoc scripts leaves you with security, risk management and governance issues.

Yet, IBM Cloud couldn’t justify forklift replacements, nor would they want the vendor-lock that came with it. IBM Cloud’s network team quickly realized that in order to keep up with demand, the only way to effectively wrangle their heterogeneous hardware infrastructure would involve decoupling networking hardware from the control plane once and for all.

IBM Cloud decided to establish a software-defined (SDN) network layer over their existing physical infrastructure. Creating an SDN layer would allow them to centrally manage and programmatically configure all of their physical infrastructure. Ideally, the SDN layer would also allow them to easily and systematically audit and update all of their heterogeneous infrastructure devices. This meant that vendor-specific SDN solutions were out.

After an intensive search, the network team at IBM Cloud turned to the infrastructure automation platform from startup [SaltStack][9]. IBM uses SaltStack as a global command-and-control layer that provides comprehensive audit, remote execution, automation, patch, security detection, and remediation for the entire IBM Cloud network.

**Related:** [**Business goal achievement tied to greater network automation**][10]

With SaltStack IBM Cloud was able to cut the time it took to update all of their legacy data centers and the ~70,000 networking devices within them from months down to a few weeks. This includes testing configuration changes, updating firmware, and onboarding new features. IBM Cloud estimates that its network team saved more than 40,000 hours of labor, as well as eliminating any customer downtime due to maintenance.

IBM Cloud continues to centrally manage and maintain its networking gear via SaltStack, while also using other parts of the SaltStack software suite to manage virtual environments, automate compliance and streamline SecOps.

### DDoS attacks spur Rhode Island schools and non-profits to take (automated) action

Security is one of the key automation drivers for resource-strapped organizations that have trouble keeping up with the current threat landscape. After all, many attackers now use automated tools to outflank traditional defenses, so if you’re handling cybersecurity mitigation and remediation manually, you have, as the saying goes, brought a knife to a gun fight.

The Ocean State Higher Education Economic Development and Administrative Network (OSHEAN) began investigating security automation due to a spike in distributed denial-of-service (DDoS) attacks targeting its members. OSHEAN provides internet connectivity for public institutions in Rhode Island. OSHEAN’s 160 members include universities, K-12 schools, libraries, hospitals, government agencies and other nonprofit organizations.

The status quo for OSHEAN had been to handle each DDoS attack separately. When malicious traffic was spotted (often because a member called into the service desk in a panic), OSHEAN’s technical team would manually blackhole the malicious traffic. This resulted in downtime for the targeted member for the duration of an attack.

David Marble, president and CEO of OSHEAN, understood that a manual approach would not scale as both OSHEAN’s membership and the number of inbound attacks continued to grow. Marble and his team investigated a range of possible solutions, rejecting several because they were either appliance-based or managed services not based on open standards. Appliances required upfront Capex, as well as ongoing maintenance costs, while proprietary managed services lacked features and would prevent Kentik from developing service chains and other automations.

After researching various options, Marble and his team turned to [Kentik’s][11] network performance monitoring and diagnostics platform to help them protect their members from DDoS attacks.

Using probes within the network, Kentik continuously monitors millions of individual IP addresses, recognizing and focusing on the IPs that are currently the top traffic receivers. Kentik automatically baselines their traffic patterns and measures anomalies in their traffic.

Because Kentik relies on open APIs, OSHEAN was also able to split detection and analytics apart from mitigation and remediation. OSHEAN integrated the Kentik platform with Akamai Prolexic, so that sites under attack are automatically put into quarantine and scrubbed.

**Related:** [**How to buy network automation tools**][12]

In less than a year, OSHEAN has relied on Kentik to automatically repel more than 300 volumetric DDoS attacks that targeted its members.

As an added benefit, the same analytics that help OSHEAN automatically mitigate DDoS attacks now also helps the organization improve application delivery and performance. “The analytics we use for DDoS protection is also useful for application traffic,” Marble said. “If one of our members has an issue with an application, we can automatically trace that traffic to pinpoint the source of the problem.”

### Automation paves the way for application-based networking

As software defined networking (SDN) services continue to displace traditional hardware-centric infrastructure, the opportunity arises to optimize on top of basic networking functions. For instance, as SD-WAN services evolved beyond basic branch office connectivity to target use cases such as cloud connectivity, application-aware services became key features.

Application-based QoS (i.e. prioritize video traffic), application-specific routing (sending Google application traffic directly to Google servers), and even cost-saving measures (only send email over inexpensive links) are all possible with software-defined infrastructure.

**Related:** [**Network automation leads to improved organizational and team performance**][13]

“Distributed clouds are driving automation. You can’t have different rules across different clouds,” Casemore of IDC said. “As enterprises and service providers work to develop consistent policies around networking, security and especially around workloads distributed across various clouds, networking professionals must worry less about old siloes and more about how we automate around application workflows.”

Hybrid cloud environments are driving automation now, but there are a whole host of other emerging technologies that are also pushing traditional infrastructures past their limits. IoT, streaming media, and M2M communications all stress traditional architectures, but there are two other issues looming on the horizon that could pose even bigger problems: Compliance and 5G.

Join the Network World communities on [Facebook][14] and [LinkedIn][15] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3539051/inside-network-automation-trends.html

作者：[Jeff Vance][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://techcrunch.com/2020/03/17/zoombombing/
[2]: https://ovum.informa.com/resources/product-content/2018-ict-spending-predictions-for-the-banking-sector-infographic
[3]: https://www.idginsiderpro.com/article/3488866/career-roadmap-enterprise-architect.html
[4]: http://www.idc.com/
[5]: http://www.idc.com/getdoc.jsp?containerId=IDC_P32575
[6]: https://www.idc.com/getdoc.jsp?containerId=PRF004078
[7]: https://www.idginsiderpro.com/article/3482642/welcome-to-insider-pros-certifications-and-training-center.html
[8]: https://www.idginsiderpro.com/author/Mike-Elgan/
[9]: https://www.saltstack.com/
[10]: https://www.cio.com/article/3445901/business-goal-achievement-tied-to-greater-network-automation.html
[11]: https://www.kentik.com/
[12]: https://www.networkworld.com/article/3490459/7-considerations-when-buying-network-automation-tools.html
[13]: https://www.cio.com/article/3448116/network-automation-leads-to-improved-organizational-and-team-performance.html
[14]: https://www.facebook.com/NetworkWorld/
[15]: https://www.linkedin.com/company/network-world
