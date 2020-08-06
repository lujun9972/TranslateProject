[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Cutting Through the SASE Hype is Important)
[#]: via: (https://www.networkworld.com/article/3570449/cutting-through-the-sase-hype-is-important.html)
[#]: author: (John Maddison )

Cutting Through the SASE Hype is Important
======

iStock

[Secure Access Service Edge (SASE)][1] is an emerging enterprise strategy that incorporates multiple solutions to enable secure remote access to on-premises, cloud-based, and online resources. Unfortunately, there has been a lot of hype that has left some organizations wondering what exactly SASE is. Understanding the basic concepts and components of SASE is important, as the benefits can be significant for many organizations. Fortunately, getting to the bottom of this is easy, as many of the fundamentals of SASE – such as bringing networking and security together– are trends that customers have been gravitating to for years. However, it is still critical to properly define SASE up front in order to avoid adding complexity or, worse, missing the true value of SASE at all.

### SASE is All About Delivering Security Everywhere

Today’s organizations require immediate, uninterrupted access to network and cloud-based resources and data, including business-critical applications, no matter where their users are located. The reality is that consumption patterns are changing due to the implementation of 5G, cloud migrations, sustained work from home, and similar outcomes from digital innovation efforts. This has transformed the traditional network to a network of many edges.

At the same time, these dynamically changing network configurations, and the rapid expansion of the attack surface, mean that many traditional security solutions no longer provide the level of protection and access control that organizations and users require. In this environment, security has to be delivered anywhere from any place, at any time, and for any device – the WAN Edge, Cloud Edge, DC Edge, Core Network Edge, Branch Edge, and Mobile Remote Worker Edge. This requires the convergence of traditional and cloud-based security, as well as deep integration between security and fundamental networking elements.

### Accurately Defining SASE

[SASE][1] is designed to help organizations secure these new distributed networks. However, as with any emerging technology category, there is still some uncertainty about what precisely a SASE solution means—and what technologies are included. In addition, vendors are attempting to redefine this market in ways that best reflect their current offerings – which means that some elements are being overemphasized and other, often essential elements get overlooked. Unfortunately, some market definitions of SASE already include important omissions that are leaving some organizations confused about how to best select, implement, and manage the right sort of solution for their unique environments.

_**Not Just Cloud**_

SASE is generally classified as a cloud-delivered service, providing secure access to cloud-based resources, secure communications between remote users, and always-on security for devices off-premises. However, there are situations where organizations may require a combination of physical and cloud-based solutions for SASE to work effectively. This may include supporting a physical SD-WAN solution in place that already contains a full stack of security, or the desire to provide protection at the edge when processing confidential or sensitive information rather than shuttling it out to the cloud for inspection.

By combining physical and cloud-based elements, the role of SASE can also be easily extended deep into the network, rather than simply handing off security to an entirely different system at the edge. This ensures that a secure SASE connection is seamlessly integrated with critical solutions that also rely on hardware, such as network segmentation and compliance requirements that a strictly cloud-based security approach can’t address, to provide end-to-end protection.

_**Secure LAN and WAN**_

Some [SASE definitions][1] also omit things like Secure LAN and Secure WLAN that are essential considerations for many organizations. Including these sorts of technologies in a SASE solution helps ensure that security is applied consistently across an entire security architecture, rather than deploying separate security components for their SASE deployment – which could create gaps in security policy enforcement and limit visibility. And for SASE to function as an extension of an existing secure LAN or WLAN, it will also need to support physical solutions such as routing and WAN optimization controllers (WoC), alongside SD-WAN for dynamic path selection. It also needs to function consistently whether using an [NGFW][2] or FWaaS solution, as well as both physical and cloud-based ZTNA solutions – along with networking tools such as WLAN/LAN/5G controllers – to ensure secure network access and dynamic segmentation.

_**Flexible Consumption**_

But regardless of which tools are used or where they are deployed, there is a central issue that needs to be remembered. Every SASE solution must not only meet the access needs of today, but also have the capability to quickly adapt to rapidly evolving network changes and business requirements as they occur. This explains a key criteria for SASE, which is flexible consumption models that give organizations choices depending on their unique use-cases in order to achieve the _true vision_ of SASE.

### Essential Security Elements Defined

Any true SASE solution must include a core set of essential security elements. To realize the full potential of a SASE deployment, organizations must understand and implement these security components across the WAN-edge, LAN-edge, and Cloud-edge.

  * [**A fully functional, SD-WAN solution**][3]. SASE starts with an SD-WAN solution that includes such things as dynamic path selection, self-healing WAN capabilities, and consistent application and user experience for business applications.
  * **An NGFW (physical) or FWaaS (cloud-based) firewall.** SASE also needs to include a full stack of security that spans both physical and cloud-based scenarios. For example, remote workers require a combination of cloud-based security for accessing resources located online, and physical security and internal segmentation to prevent network users from accessing restricted corporate network resources. However, physical hardware and cloud-native security need to deliver the same high performance at scale, enabling maximum flexibility and security.
  * [**Zero-trust Network Access**][4]**.** It is primarily used to identify users and devices and authenticate them to applications. Because ZTNA is more of a strategy than a product, it includes several technologies working together, starting with multi-factor authentication (MFA) to identify all users. On the physical side, ZTNA should include secure network access control (NAC), access policy enforcement, and integration with dynamic network segmentation to limit access to networked resources. And on the cloud side, ZTNA needs to support things like microsegmentation with traffic inspection for secure East-West communications between users, and always-on security for devices both on and off-network.
  * [**A Secure Web Gateway**][5]**.** It is used to protect users and devices from online security threats by enforcing internet security and compliance policies and filtering out malicious internet traffic. It can also enforce acceptable use policies for web access, ensure compliance with regulations, and prevent data leakage.
  * [**A CASB**][6]**.** A cloud-based service enables organizations to take control of their SaaS applications, including securing application access and eliminating Shadow IT challenges. This needs to be combined with on-premises DLP to ensure comprehensive data loss prevention.



### SASE – The Convergence of Networking and Security

At a high level, implementing SASE really comes down to enabling secure connectivity and access to critical resources from anywhere on any edge. Unfortunately, very few vendors can provide this because their portfolios are full of disparate, acquired products, or they simply don’t have enough breadth to provide all of the security elements that a robust SASE solution requires. And even when they do, their solutions simply do not interoperate well enough to be effective.

This is a problem, because for [SASE][1] to work well, all of its components need to interoperate as a single integrated system – connectivity, networking, and security elements alike. Which means every component needs to be designed to interoperate as part of an integrated strategy bound together by a single, centralized management and orchestration solution. They also need to seamlessly integrate with the larger corporate security framework, as well as dynamically adapt as networking environments evolve. If not, it’s not a true SASE solution.

The recent market momentum around SASE is exciting because it underscores the need for a [Security-driven Networking][7] approach. In the era of cloud connectivity and digital innovation, networking and security must converge. There’s no going back to outmoded and siloed architectures.

[_Learn more_][1] _about how SASE is the future of security and networking. From SD-WAN, ZTNA, CASB, and NGFW, the Fortinet platform provides complete readiness for embracing SASE._

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3570449/cutting-through-the-sase-hype-is-important.html

作者：[John Maddison][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.fortinet.com/resources/cyberglossary/sase?utm_source=pr&utm_campaign=2020-q3-sase
[2]: https://www.fortinet.com/products/next-generation-firewall.html?utm_source=pr&utm_campaign=2019-q3-fortigate
[3]: https://www.fortinet.com/products/sd-wan.html?utm_source=pr&utm_campaign=2019-q3-sd-wan
[4]: https://www.fortinet.com/solutions/enterprise-midsize-business/network-access?utm_source=pr&utm_campaign=2020-q2-network-access
[5]: https://www.fortinet.com/products/secure-web-gateway.html?utm_source=pr&utm_campaign=2019-q3-secure-web-gateway
[6]: https://www.fortinet.com/products/cloud-access-security-broker.html?utm_source=pr&utm_campaign=2019-q3-forticasb
[7]: https://www.fortinet.com/solutions/enterprise-midsize-business/network-security?utm_source=pr&utm_campaign=2020-q2-network-security
