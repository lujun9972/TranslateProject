[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Defining True Flexibility for SD-WAN)
[#]: via: (https://www.networkworld.com/article/3584074/defining-true-flexibility-for-sd-wan.html)
[#]: author: (Nirav Shah )

Defining True Flexibility for SD-WAN
======

iStock

SD-WAN was initially designed as a more flexible and cost-effective solution for connecting branch offices to cloud resources and the core network. And that is still the primary way it is deployed. Replacing static and costly MPLS connections and edge routers with a system that can manage and optimize connections and application performance has helped millions of organizations deploy a more robust and adaptable WAN strategy.

The right [SD-WAN][1] solution can do so much more. But far too many vendors have failed to realize the true potential of SD-WAN, or have over-promised on the flexibility of their solutions. It is not uncommon to find SD-WAN solutions, even from major vendors, that are unable to scale beyond 100 sites, provide overly complex management systems, or don’t provide solutions appropriate to meet the unique needs of essential verticals, such as retail. This failure on the part of the vendors limits the possibilities for the organizations that deploy them.

### When it Comes to SD-WAN, Flexibility is Key

If you are in the market for an SD-WAN solution or are looking to upgrade or expand an existing SD-WAN deployment, there are some key considerations that should be included in the selection process. Flexibility is one of those critical considerations, and far too many legacy SD-WAN solutions were not designed with the sort of flexibility in mind that many businesses require. This is what you should look for:

  1. **Scalability**. Not every remote environment is the same size. Branch offices can vary widely, and an SD-WAN needs to meet the demands of any sized office and support thousands of distributed locations. But new considerations, such as a greatly expanded remote workforce, means that some super users could benefit from the performance and functionality that a traditional VPN connection can't provide. Look for an SD-WAN solution that comes in a variety of footprints, such as built-in LTE/5G to enable high-speed failover should the local connections become unreliable or unstable. Details like this ensure that you can support everything from the largest branch offices to thousands of remote users desktops.
  2. **Security**. The lack of integrated security in most SD-WAN solutions means that IT teams have to create an overlay security solution to compensate for losing the traditional stack of security provided at the head end by eliminating the MPLS connection. And because it is not integrated with the SD-WAN's networking and connectivity functions, it simply cannot adapt to the rapid changes that many dynamic connections require. Security not only becomes a performance bottleneck but a barrier to flexibility as well. A truly flexible SD-WAN solution should be able to provide consistent security that is fully integrated into an on-premise device, as well as a cloud-native security service that can function as part of a [SASE solution][2].
  3. **SD-Branch**. Most branch offices also include a LAN that needs protecting, and the loss of its permanent connection to the headend means that they now have to rely on a local security platform of some sort. That means IT headaches for rollout, configuration, monitoring, and management. Organizations should look for an SD-WAN solution that includes integrated connectivity and application security and security functionality that can be easily extended into the branch LAN. [SD-Branch][3] enables organizations to protect things like wired and wireless access points, establish and maintain network access control, and secure data and workflows passing through internal devices as well as the SD-WAN connection.
  4. **Multi-Cloud**. The fact is, WANs exist in many places besides branch offices. A virtual SD-WAN solution can provide secure and reliable connectivity between public clouds, between public and private clouds, and between any cloud and the data center. This requires looking for SD-WAN solutions that can run natively in any public or private [cloud environment][4]. And all of these SD-WAN deployments need to be configured and orchestrated using a central management system that integrates all networking, connectivity, and security functionality into a single console.
  5. **Self-Healing**. If an SD-WAN solution has to be reconfigured or requires manual intervention every time there’s an internet connectivity issue, many of the other SD-WAN benefits become negligible. Similarly, there should never be a lag in protection while security scrambles to reconfigure itself whenever a connection changes. Instead, organizations need to insist on an SD-WAN solution designed to automatically bridge gaps in Internet reliability to maintain exceptional application performance. [Self-healing][5] functionality should do things like switch to an alternative transport model when an outage or disruption impacts connectivity, or dynamically adjust security policies and configurations with every connectivity changes—even when switching to another transport model.
  6. **Low-Touch**. And all of this needs to be done as seamlessly and as low touch as possible. Deployment needs to be quick, interconnections between SD-WAN systems need to be easily configured and managed, SLAs and other policies need to be universally applied, and a unified security policy needs to dynamically and automatically adapt to changes in traffic, connections, applications, and workflows.



This boils down to looking for an organically developed solution that consolidates advanced routing, self-healing SD-WAN capabilities, and intuitive orchestration with flexible security options via a fully integrated next-generation firewall or SASE-based cloud-delivered security solution. It also needs to be able to be deployed across the entire range of home, branch, campus, and multi-cloud network environments. This approach will help the organization realize numerous significant benefits, including: 

**Better user experience:** To maintain optimal user experience, an SD-WAN system needs to dynamically learn and overcome WAN impairments at all edges using comprehensive self-healing SD-WAN capabilities. It also needs to leverage [purpose-built ASICs][6] for maximized performance. And the addition of AI and ML-powered application learning provides additional visibility and control to ensure the best application performance possible without compromising security.

**Reduced costs and complexity: **By converging networking and security into a unified Secure SD-WAN solution and then adding centralized orchestration, an organization can reduce the number of point products they need to manage. This helps them keep operational complexity in check while achieving the best possible total cost of ownership (TCO). 

### The Goals of Today’s SD-WAN Deployments are Clear

There are four goals for effective SD-WAN deployment. First, provide seamless, reliable access to any resource, from any device, in any location. Second, ensure consistent user experience through continuously optimized connections and applications. Third, protect all applications, workflows, and transactions using enterprise-class security solutions designed to provide encryption and inspection at business speeds. And fourth, everything needs to be able to adapt to network changes, digital innovation requirements, and evolving cyber threats as a single system.

Achieving this requires a level of flexibility that few SD-WAN solutions can deliver. But finding and deploying a solution that can grow and adapt as your business and network requirements evolve is well worth the effort.

_Take a security-driven approach to networking to improve user experience and simplify operations at the WAN edge with _[_Fortinet’s Secure SD-WAN_][7]_ solution._

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3584074/defining-true-flexibility-for-sd-wan.html

作者：[Nirav Shah][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.fortinet.com/products/sd-wan.html?utm_source=pr&utm_campaign=2019-q3-sd-wan
[2]: https://www.fortinet.com/resources/cyberglossary/sase?utm_source=pr&utm_campaign=2020-q3-sase
[3]: https://www.fortinet.com/use-cases/sd-branch?utm_source=pr&utm_campaign=2020-q2-sd-branch
[4]: https://www.fortinet.com/solutions/enterprise-midsize-business/cloud-security.html?utm_source=pr&utm_campaign=2019-q3-cloud-security
[5]: https://www.fortinet.com/content/dam/maindam/PUBLIC/02_MARKETING/02_Collateral/point-of-view/pov-the-importance-of-self-healing-sdwan.pdf
[6]: https://www.fortinet.com/products/fortigate/fortiasic.html?utm_source=pr&utm_campaign=2020-q3-spu
[7]: https://www.fortinet.com/products/sd-wan.html?utm_source=blog&utm_campaign=2018-q2-sd-wan-web
