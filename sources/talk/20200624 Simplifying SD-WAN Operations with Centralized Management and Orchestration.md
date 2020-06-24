[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Simplifying SD-WAN Operations with Centralized Management and Orchestration)
[#]: via: (https://www.networkworld.com/article/3563880/simplifying-sd-wan-operations-with-centralized-management-and-orchestration.html)
[#]: author: (Nirav Shah )

Simplifying SD-WAN Operations with Centralized Management and Orchestration
======

iStock

Software-defined wide-area networking (SD-WAN) is rapidly replacing the traditional WAN for remote office and branch deployments. [SD-WAN][1] was designed to provide a wide range of benefits to support digital innovation. However, far too many SD-WAN solutions lack critical networking and security features, requiring organizations to add complex and costly overlay solutions to manage and protect their SD-WAN deployments.

For example, one critical issue organizations face – especially when a large number of SD-WAN devices have been deployed – is orchestrating communications, workflows, and other traffic between branch offices. While a traditional WAN model is certainly inefficient from a bandwidth or application management perspective, its hub and spoke model for connecting remote environments is relatively simple to deploy and manage. Since SD-WAN enables direct connections to the internet, however, building a communications overlay requires a complex, fully meshed VPN solution that can be a nightmare to design, implement, and manage.

The best approach to addressing this and similar challenges, such as SD-WAN security, is through integration, [automation][2] and simplification. Eliminating the complexity of a disaggregated branch infrastructure not only reduces an organization’s attack surface but also simplifies network operations.

### Centralized Management for Distributed Organizations

One critical functionality that many SD-WAN solutions lack is an [integrated management system][3] designed to consolidate all of its essential functions into a single console. Centralized SD-WAN management needs to span all distributed branch environments, enabling administrators to deliver and orchestrate configurations and policies, and quickly identify and correct errors that may lead to cyber-risk exposure and network outages.

At the same time, a central orchestrator allows organizations to simplify centralized deployment and establish automation to save time and respond more quickly to business demands. One effective strategy that a central orchestrator can provide is the distribution of applications, workflows, and other traffic across and between branch offices. Most SD-WAN solutions offer VPN functionality, but a meshed VPN, especially in larger SD-WAN deployments, requires significant processing overhead and ongoing management.

By using an orchestrator to group branch offices into regions, the majority of branch offices can be designated as edge environments attached to one of more regional hubs. These edge offices require minimal management other than local connectivity and security. Management overhead can then be focused on a handful of regional hubs, which are used to move data between branch offices within the region, as well as coordinate traffic between regions.

In such a complex environment, a central orchestration tool can more easily manage traffic loads. It can also automatically designate additional hubs when and where needed to prevent bottlenecks while keeping the number of control points that need to be configured and managed to a minimum. This, in turn, eliminates VPN overhead.

### SD-WAN Analytics &amp; Reporting

With the addition of centralized analytics, network engineering and operations teams can also more efficiently find and mitigate human errors, improve functionality, and reduce security risks. Enhanced analytics for WAN link availability, performance SLAs and application traffic in runtime, and historical stats allow the infrastructure team to troubleshoot and quickly resolve network issues.

To make this possible, centralized SD-WAN management needs to include telemetry for application visibility and network performance, enabling SD-WAN management teams to achieve faster resolution of issues and reduce the number of IT support tickets. On-demand SD-WAN reports should provide further insight into the threat landscape, trust level, and asset access – all of which are mandated for best practice compliance purposes.

Compliance reporting is also critical, as organizations need reports and tools to help validate compliance to their auditors. The challenge is that compliance management has traditionally been a costly, labor-intensive process for teams—often requiring multiple full-time staff from both networking and InfoSec teams to aggregate and normalize data across multiple point security products. This is because compliance is enabled by Networking, but implemented by InfoSec. And most SD-WAN solutions don’t make it any easier as they lack insight into critical compliance elements such as security.

Simplifying the security infrastructure, for example, not only eliminates the need for many manual processes but also makes it easier to demonstrate compliance to auditors. However, an effective compliance management system needs to include customizable regulatory templates, as well as canned reports for standards such as Payment Card Industry Data Security Standard (PCI DSS), Security Activity Report (SAR), Center for Internet Security (CIS), and National Institute of Standards and Technology (NIST).

It should also run audit checks to help security and networking teams identify critical vulnerabilities and configuration weaknesses in their setup, and implement best- practice recommendations. And ideally, it should provide a benchmark so network leaders can compare their organization’s security posture score against those of their industry or regional peers.

### Integration and Automation

To be effective, security must become seamlessly integrated across every part of the distributed organization, including every branch and remote office location. Network engineering and operations leaders need full visibility across the entire attack surface from a single location. Then, they need automated responses to reduce the window of time from detection to remediation and to alleviate the burdens of manual tasks from their staff.

However, the lack of security built into the vast majority of SD-WAN solutions has been another critical lapse in SD-WAN development. It has forced organizations to add an overlay of point security products to their SD-WAN technology to address the threat exposures and compliance requirements that used to be handled by the security solutions deployed at the core. This creates two serious problems. First, these point security products generally do not interoperate with each other, which can reduce visibility while leading to acute management and logistical burdens and overhead. And second, point security solutions are too disconnected from SD-WAN functions to do much more than react to connectivity changes after the fact, creating critical defensive gaps at the network edge.

An integrated management solution that takes a [security-driven networking][4] approach and weaves SD-WAN and security functionality into a single console can decrease threat remediation time from months to minutes. It does this by coordinating policy-based automated responses across the distributed security architecture, unlocking security workflows, and threat intelligence gathering and implementation. As a result, any detected incident alert sent with contextual awareness data from a branch allows a network administrator to quickly determine a course of action to protect the entire enterprise against a potential coordinated attack.

But because cyber events happen at digital speeds, certain events should also trigger automatic changes to device configurations to close the loop on attack mitigation in an instant, reducing risk while reducing the burden on staff resources. Naturally, this solution should also integrate with third-party tools, such as [security information and events management][5] (SIEM), IT service management (ITSM), and [DevOps][6] (e.g., Ansible, Terraform.) This will enable organizations to preserve existing workflows while leveraging investments in other security and networking tools.

### Centralized SD-WAN Orchestration and Management Delivers Real Value

Blending enterprise-class security and branch networking capabilities into a single, centralized management and orchestration system provides critical benefits, the most important of which is decreasing cyber risk. But by consolidating the number of networking and security tools required, it can also significantly lower total cost of ownership. Capital expenditures can be effectively managed, while operating expenses can be significantly reduced through simplified management and workflow automation. The net benefit, however, is a faster, more productive, and more secure organization that can safely and quickly leverage digital innovation to compete more effectively in today's digital marketplace.

_Take a security-driven approach to networking to improve user experience and simplify operations at the WAN edge with _[_Fortinet’s Secure SD-WAN_][7]_ solution._

Join the Network World communities on [Facebook][8] and [LinkedIn][9] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3563880/simplifying-sd-wan-operations-with-centralized-management-and-orchestration.html

作者：[Nirav Shah][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.fortinet.com/products/sd-wan.html?utm_source=pr&utm_campaign=2019-q3-sd-wan
[2]: https://www.fortinet.com/solutions/enterprise-midsize-business/automate-security.html?utm_source=pr&utm_campaign=2019-q3-automate-security
[3]: https://www.fortinet.com/solutions/enterprise-midsize-business/fabric-management-center.html?utm_source=pr&utm_campaign=2020-q2-fabric-management-center
[4]: https://www.fortinet.com/solutions/enterprise-midsize-business/network-security?utm_source=pr&utm_campaign=2020-q2-network-security
[5]: https://www.fortinet.com/products/siem/fortisiem.html?utm_source=pr&utm_campaign=2019-q3-fortisiem
[6]: https://www.fortinet.com/partners/partnerships/alliance-partners/devops.html?utm_source=pr&utm_campaign=2019-q3-devops
[7]: https://www.fortinet.com/products/sd-wan.html?utm_source=blog&utm_campaign=2018-q2-sd-wan-web
[8]: https://www.facebook.com/NetworkWorld/
[9]: https://www.linkedin.com/company/network-world
