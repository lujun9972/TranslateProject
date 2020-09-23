[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Cisco extends SD-WAN options with AWS, Azure hybrid-cloud integration)
[#]: via: (https://www.networkworld.com/article/3576002/cisco-extends-sd-wan-options-with-aws-azure-hybrid-cloud-integration.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

Cisco extends SD-WAN options with AWS, Azure hybrid-cloud integration
======
New Cisco SD-WAN Cloud OnRamp features simplify access to multi-cloud services and provide better security and lower latency.
iStock

Cisco has further broadened the cloud-integration options available to its [SD-WAN][1] customers with new connectivity options to AWS and Microsoft Azure cloud services.

With these additions, Cisco’s goal is to ensure cloud-destined traffic gets into the cloud network faster, improving management, performance, security and reducing the latency that can impact cloud workloads.

**More about SD-WAN**: [How to buy SD-WAN technology: Key questions to consider when selecting a supplier][2] • [How to pick an off-site data-backup method][3] •  [SD-Branch: What it is and why you’ll need it][4] • [What are the options for security SD-WAN?][5]

“Hybrid cloud is the norm and Cisco’s plan is bringing the networking support to improve app performance and add security without adding pain—it’s the right direction,” said Lee Doyle, principal analyst at Doyle Research.

In this case, the enhancements center around Cisco’s SD-WAN Cloud OnRamp feature that lets customers tie distributed cloud applications back to a branch office or private data center. The idea is that a cloud-to-branch link would be shorter, faster and possibly more secure that tying cloud-based applications directly to the data center.  SD-WAN Cloud OnRamp is part of Cisco’s overarching SD-WAN software package, and the new features are found in a new release of that software--version 17.3.

With the Cloud OnRamp package each branch office or private data center is equipped with a network interface that provides a secure tunnel to a regional colocation facility. In turn, the Cloud onRamp for CoLocation establishes secure tunnels to SaaS application platforms, multi-cloud platform services, and enterprise data centers.

The package includes security features such as application-aware firewalls, URL-filtering, intrusion detection/prevention, [DNS][6]-layer security, and Advanced Malware Protection (AMP) Threat Grid, as well as other network services such as load-balancing and Wide Area Application Services, according to Cisco.

The integration of Cloud OnRamp and AWS lets customers securely link to AWS cloud resources with a few clicks, Cisco stated. The package also lets customers utilize the  AWS Transit Gateway which lets customers connect their Amazon Virtual Private Clouds (VPCs) and their on-premises networks to a single gateway.

With Transit Gateway integration, customers can apply network segmentation and security policies to cloud traffic flows, and the package will also enable policy exchange between Cisco SD-WAN Controller and AWS Transit Gateway, which will let IT teams implement consistent network and data-security rules, Cisco stated.

On the Microsoft side, Cisco added a Cloud OnRamp feature to help customers manage and improve application performance of Azure-based workloads.

One of the new features, called URL categorization, lets  customers create separate policies around specific types of traffic feeding into Microsoft 365, giving customers more detailed control over traffic management within the platform, said JL Valente, vice president of Product Management for Cisco Enterprise Networking in a blog detailing the new features.

By creating different parameters for different traffic types, users can route traffic more efficiently around their needs and usage habits for optimized response times, Valente stated.

“The new Cisco SD-WAN and Microsoft 365 integration allows customers to easily remediate sub-optimal application performance. With application infused path selection, customers can improve their end user experience via monitoring and automatic intervention whenever performance is deficient relative to Office 365’s specific expectations,” Valente stated.  

Using network telemetry, customers can automate application route and firewall policies to steer traffic to the best path, to improve remote-worker experience, according to Jim Kleewein, a technical fellow with Microsoft. “Cisco SD-WAN Cloud OnRamp integration with Microsoft O365 application performance telemetry, enables intelligent application classification and automation of best path selection with secure policy orchestration to deliver the most optimized experience,” he stated.

The companies also enhanced connectivity between OnRamp and Azure’s Virtual WAN offering.

The Virtual WAN integration between Cisco and Microsoft extends the Cisco SD-WAN fabric directly into the Azure Virtual WAN, Cisco stated, which will enable users to automatically connect to other networking gateways and routers within the Virtual WAN hubs. These can include ExpressRoute, IPSec VPN gateways, Azure Firewall, and push and pull policies or requirements to the Hub in the Virtual WAN as a site within Cisco SD-WAN, Cisco stated.

This integration allows customers to extend Cisco SD-WAN to Microsoft Azure Cloud and access Azure enterprise workloads with little or no additional configuration, according to Cisco.

Cisco said its current SD-WAN customers can unlock the Cloud OnRamp capability from their vManage panel, giving them the ability to use the same policy, security, and other SD-WAN policies for all Cisco SD-WAN devices—whether on-premises or in a cloud.

These [AWS][7] and Microsoft cloud networking integrations follow other work the companies have done to enhance support for cloud workloads. Cisco has released  software-defined networking (SDN) software that will let customers manage and secure applications running in the data center or in Amazon Web Services cloud environments. The service, Cisco Cloud ACI for AWS, lets users configure inter-site connectivity, define policies and monitor the health of network infrastructure across hybrid environments, Cisco said.

Cisco Cloud ACI for AWS brings a suite of capabilities to extend customer on-premises data centers into true multi-cloud architectures, helping to drive policy and operational consistency, independent of where applications or data reside, Cisco said. The service uses the native AWS constructs for policy translation and gives end-to-end visibility into customers' multi-cloud workloads and connectivity, Cisco said.

The companies have also worked on AWS Kubernetes integration and a cloud services router.

Cisco has similar [Cloud ACI integration][8] with Azure as well as other offerings.

Cisco has worked with [Google][9] to integrate customers in that cloud environment as well. For example, earlier this year Cisco and Google announced a turnkey package that lets customers mesh SD-WAN connectivity with applications running in a private data center, Google Cloud or another cloud or SaaS application. The jointly developed platform, called Cisco SD-WAN Cloud Hub with Google Cloud, combines Cisco’s SD-WAN policy-, telemetry- and security-setting capabilities with Google’s software-defined backbone to ensure that application service-level agreement, security and compliance policies are extended across the network.

Cisco and Google have been collaborated since October 2017, when the companies said they were working on an open hybrid-cloud platform that bridges on-premises and cloud environments. That package, [Cisco Hybrid Cloud Platform for Google Cloud][10], has been available since 2018.

Join the Network World communities on [Facebook][11] and [LinkedIn][12] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3576002/cisco-extends-sd-wan-options-with-aws-azure-hybrid-cloud-integration.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3031279/sd-wan-what-it-is-and-why-you-ll-use-it-one-day.html
[2]: https://www.networkworld.com/article/3323407/sd-wan/how-to-buy-sd-wan-technology-key-questions-to-consider-when-selecting-a-supplier.html
[3]: https://www.networkworld.com/article/3328488/backup-systems-and-services/how-to-pick-an-off-site-data-backup-method.html
[4]: https://www.networkworld.com/article/3250664/lan-wan/sd-branch-what-it-is-and-why-youll-need-it.html
[5]: https://www.networkworld.com/article/3285728/sd-wan/what-are-the-options-for-securing-sd-wan.html
[6]: https://www.networkworld.com/article/3268449/what-is-dns-and-how-does-it-work.html
[7]: https://www.networkworld.com/article/3487563/cisco-goes-deep-into-aws-hybrid-cloud-with-sd-wan-security-outposts-data-center-support.html
[8]: https://www.networkworld.com/article/3545396/cisco-fortifies-aci-for-amazon-microsoft-integration-and-multicloud-management.html
[9]: https://www.networkworld.com/article/3539252/cisco-integrates-sd-wan-connectivity-with-google-cloud.html
[10]: https://cloud.google.com/cisco/
[11]: https://www.facebook.com/NetworkWorld/
[12]: https://www.linkedin.com/company/network-world
