[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (What is SASE? A cloud service that marries SD-WAN with security)
[#]: via: (https://www.networkworld.com/article/3574014/what-is-sase-a-cloud-service-that-marries-sd-wan-with-security.html)
[#]: author: (Maria Korolov )

What is SASE? A cloud service that marries SD-WAN with security
======
Secure access service edge is a Gartner model for streamlining network access, improving security, boosting network performance and reducing the number of vendors and devices IT pros have to deal with.
LordRunar / Getty Images

Secure access service edge (SASE) is a network architecture that rolls [software-defined wide area networking (SD-WAN][1]) and security into a cloud service that promises simplified WAN deployment, improved efficiency and security, and to provide appropriate bandwidth per application.

Because it’s a cloud service, SASE (pronounced “sassy”) can be readily scaled up and scaled down and billed based on usage. As a result, it can be an attractive option in a time of rapid change.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][2]

While some vendors in this space offer hardware devices to connect at-home employees and corporate data centers to their SASE networks, most vendors handle the connections through software clients or virtual appliances.

Gartner created the term SASE and first described it in a 2019 white paper that lays out its goals and what a SASE implementation should look like. The consulting firm notes that SASE is still developing and that all of its features may not be readily available yet.

Let’s take a closer look.

### What is SASE?

Simply put, SASE combines SD-WAN capabilities with security and delivers them as a service. Security policies enforced on user sessions are tailored to each based on four factors:

  * the identity of the entity connecting
  * context (health and behavior of the device, sensitivity of the resources being accessed)
  * security and compliance policies
  * an ongoing assessment of risk during each session.



The [WAN][3] side of SASE relies on capabilities supplied by entities including SD-WAN providers, carriers, content-delivery networks, network-as-a-service providers, bandwidth aggregators and networking equipment vendors.

The security side relies on cloud-access security brokers, cloud secure web gateways, [zero-trust][4] network access, firewall-as-a-service, web-API-protection-as-a-service, DNS and remote browser isolation.

Ideally, all these capabilities are offered as a SASE service by a single entity that pulls it all together, Gartner says.

### Where is the edge?

The "edge" part of SASE is usually delivered through PoPs or vendor [data centers][5] close to the endpoints – the data centers, the people, and the devices – wherever they may be. In some cases, the SASE vendor owns the PoPs, while in others it uses a third-party or expects customers to provide their own connectivity.

### SASE benefits

Because it is a single service, SASE cuts complexity and cost. Enterprises deal with fewer vendors, the amount of hardware required in branch offices and other remote locations declines, and the number agents on end-user devices also decreases.

IT executives can centrally set policies via cloud-based management platforms, and the policies are enforced at distributed PoPs close to end-users.

End users have the same access experience regardless of what resources they need and where they and the resources are located. SASE also simplifies the authentication process by applying appropriate policies for whatever resources the user seeks based on the initial sign-in.

Security is increased because policies are equally enforced regardless of where users are located. As new threats arise, the service provider addresses how to protect against them, with no new hardware requirements for the enterprise.

SASE supports zero-trust networking, which bases access on user, device and application, not location and IP address.

More types end users – employees, partners, contractors, customers – can gain access without the risk that traditional security – such as [VPNs][6] and DMZs – might be compromised and become a beachhead for potential widespread attacks on the enterprise.

SASE providers can supply varying qualities of service so each application gets the bandwidth and network responsiveness it needs.

With SASE, enterprise IT staff have fewer chores related to deployment, monitoring and maintenance and can be assigned higher level tasks.

### SASE challenges

Gartner lists several hurdles for adoption of SASE.

Some services could come up short initially because they are implemented by providers with backgrounds in either networking or security and lack expertise in the other half.

Initial SASE offerings may not be designed with a cloud-native mindset because the vendors’ legacy experience is selling on-premises hardware, so they may opt for architectures where infrastructure is dedicated to one customer at a time.

Similarly, legacy hardware vendors may lack experience with the in-line proxies needed by SASE, so they may run into cost and performance problems.

Some traditional vendors may also lack experience in evaluating context, which could limit their ability to make context-aware decisions.

Due to SASE’s complexity, it’s important that providers have well integrated features, not ones that are stitched together.

Global build-out of PoPs could prove too costly for some SASE providers. This could lead to uneven performance across all locations because some sites may be located far from the nearest PoP, introducing latency.

SASE endpoint agents will have to be integrated with other agents in order to simplify deployments.

SASE transitions can put strain on personnel. Turf wars could flare up as SASE cuts across networking and security teams. Changing vendors to adopt SASE could require retraining corporate IT staff to handle new technology.

### Why is SASE necessary?

Gartner says that more of traditional enterprise data-center functions are now hosted outside the enterprise data center than in it – in IaaS providers clouds, in SaaS applications and cloud storage. The needs of IoT and edge computing will only increase this dependence on cloud-based resources, yet WAN security architecture remains tailored to on-premises enterprise data centers.

Remote users commonly connect via VPNs and require [firewalls][7] at each location or on individual devices. Traditional models have them authenticate to centralized security that grants access but may also route traffic through that central location. This legacy architecture is hampered by complexity and delay.

With SASE, end users and devices can authenticate and gain secure access to all the resources they are authorized to reach protected by security located close to them. Once authenticated, they have direct access to the resources, addressing latency issues.

According to Gartner analyst Nat Smith, SASE is more of a philosophy and a direction than a checklist of features. But, in general, he says, SASE is composed of five main technologies: SD-WAN, firewall as a service (FWaaS), cloud access security broker (CASB), secure web gateway, and zero-trust network access.

### Integrated SD-WAN

Traditionally, the WAN is comprised of stand-alone infrastructure, often requiring a heavy investment in hardware.

The SASE version is all cloud based, defined and managed by software, and has distributed PoPs that, ideally, are located near enterprise data centers, branches, devices, and employees. Numerous PoPs are crucial to ensuring that as much enterprise traffic as possible directly accesses the SASE network, avoiding the public internet's latency and security issues.

Through the service, customers can monitor the health of the network and set policies for their specific traffic requirements.

Because traffic from the internet first goes through the provider’s network, SASE can detect dangerous traffic and intervene before it reaches the enterprise network. For example, DDoS attacks can be mitigated within the SASE network, saving customers from floods of malicious traffic.

### Firewall as a service

More and more in today's distributed environment, both users and computing resources are located at the edge of the network. A flexible, cloud-based firewall delivered as a service can protect these edges. This functionality will become increasingly important as edge computing grows and IoT devices get smarter and more powerful.

Delivering FWaaS as part of the SASE platform makes it easier for enterprises to manage the security of their network, set uniform policies, spot anomalies, and quickly make changes.

### Cloud-access security broker

As more and more corporate systems move to SaaS applications, authentication and access become increasingly important.

CASBs are used by enterprises to make sure their security policies are applied consistently even when the services themselves are outside their sphere of control.

With SASE, the same portal employees use to get to their corporate systems is also a portal to all the cloud applications they have access, including CASB. Traffic doesn't have to be routed outside the system to a separate CASB service.

### Secure web gateway

In today's enterprise, network traffic is rarely limited to a pre-defined perimeter. Modern workloads typically require access to outside resources, but there may be compliance reasons to deny employees access to certain sites. In addition, companies want to block access to phishing sites and botnets command-and-control servers. Even innocuous web sites may be used maliciously by, say, employees trying to exfiltrate sensitive corporate data.

Secure web gateways (SGW) protect companies from these threats. SASE vendors that offer this capability should be able to inspect encrypted traffic at cloud scale. Bundling SWG in with other network security services improves manageability and allows for a more uniform set of security policies.

### Zero-trust network access

Zero-trust network access allows enterprises granular visibility and control of users and systems accessing corporate applications and services.

Zero-trust is a relatively new approach to network security, and moving to a SASE platform could allow companies to get those zero-trust capabilities.

A core element of zero trust is that security is based on identity, rather than, say, the IP address. This makes it more adaptable for a mobile workforce, but requires additional levels of authentication, such as multi-factor authentication and behavioral analytics.

### Other technologies may be part of SASE

In addition to the five core capabilities, Gartner also recommends a few other technologies that SASE vendors should offer.

They include web application and API protection, remote browser isolation, and network sandboxes. Also recommended: network privacy protection and traffic dispersion, which make it difficult for threat actors to find enterprise assets by tracking their IP addresses or eavesdrop on traffic streams.

Other optional capabilities include Wi-Fi-hotspot protection, support for legacy VPNs, and protection for offline edge-computing devices or systems.

Centralized access to network and security data can allow companies to run holistic behavior analytics and spot threats and anomalies that otherwise wouldn't be apparent in siloed systems. When these analytics are delivered as a cloud-based service, it will be easier to include updated threat data and other external intelligence.

The end goal of bringing all these technologies together under the SASE umbrella is to give enterprises flexible and consistent security, better performance, and less complexity – all at a lower total cost of ownership.

Enterprise should be able to get the scale they need without having to hire a correspondingly large number of network and security administrators.

### SASE service providers

Gartner says that because SASE is an amalgam of services, how that mix is achieved will vary. As a result, they say they can’t come up with a comprehensive list of providers, but it did compile this list of vendors it that  already do or that they expect to offer SASE:

  * Akamai
  * Cato Networks
  * Cisco
  * Cloudflare
  * Forcepoint
  * Fortinet
  * McAfee
  * Netskope
  * Palo Alto Networks
  * Proofpoint
  * Symantec
  * Versa
  * VMware
  * Zscaler



“The major IaaS providers (AWS, Azure, and GCP) are not yet competitive in the SASE market,” Gartner says in its SASE introductory publication. “We expect at least one will move to address the majority of the market requirements for SASE … in the next five years as they all expand their edge-networking presence and security capabilities.”

### How to adopt SASE

Enterprises will likely move to hybrid approaches first, with traditional networking and security systems handling pre-existing connections between data centers and branch offices. SASE will be used to handle new connections, devices, users, and locations.

SASE isn't a cure for network and security issues, nor will it prevent future disruptions, but it will allow companies to respond faster to disruptions or crises and so minimize their impact on the enterprise. In addition, SASE will allow companies to be better positioned to take advantage of new technologies, such as edge computing, 5G and mobile AI.

Join the Network World communities on [Facebook][8] and [LinkedIn][9] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3574014/what-is-sase-a-cloud-service-that-marries-sd-wan-with-security.html

作者：[Maria Korolov][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3031279/sd-wan-what-it-is-and-why-you-ll-use-it-one-day.html
[2]: https://www.networkworld.com/newsletters/signup.html
[3]: https://www.networkworld.com/article/3248989/what-is-a-wan-wide-area-network-definition-and-examples.html
[4]: https://www.networkworld.com/article/3487720/the-vpn-is-dying-long-live-zero-trust.html
[5]: https://www.networkworld.com/article/3223692/what-is-a-data-centerhow-its-changed-and-what-you-need-to-know.html
[6]: https://www.networkworld.com/article/3268744/understanding-virtual-private-networks-and-why-vpns-are-important-to-sd-wan.html
[7]: https://www.networkworld.com/article/3230457/what-is-a-firewall-perimeter-stateful-inspection-next-generation.html
[8]: https://www.facebook.com/NetworkWorld/
[9]: https://www.linkedin.com/company/network-world
