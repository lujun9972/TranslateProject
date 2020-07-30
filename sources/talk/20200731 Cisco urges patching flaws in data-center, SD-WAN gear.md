[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Cisco urges patching flaws in data-center, SD-WAN gear)
[#]: via: (https://www.networkworld.com/article/3569153/cisco-urges-patching-flaws-in-data-center-sd-wan-gear.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

Cisco urges patching flaws in data-center, SD-WAN gear
======
Cisco has issued a number of critical security advisories for its data center manager and SD-WAN offerings that customers should deal with now.
Thinkstock

Cisco has issued a number of critical security advisories for its data center manager and SD-WAN offering customers should deal with now.

On the data center side, the most critical – [with a threat score of 9.8 out of 10][1] – involves a vulnerability in the REST API of Cisco Data Center Network Manager (DCNM) could let an unauthenticated, remote attacker bypass authentication and execute arbitrary actions with administrative privileges on an affected device.

Cisco DCNM lets customers see and control network connectivity  through a single web-based management console for the company’s Nexus, Multilayer Director Switch, and Unified Computing System products.

“The vulnerability exists because different installations share a static encryption key. An attacker could exploit this vulnerability by using the static key to craft a valid session token. A successful exploit could allow the attacker to perform arbitrary actions through the REST API with administrative privileges,” Cisco stated. 

According to Cisco, this vulnerability affects all deployment modes of all Cisco DCNM appliances that were installed using .ova or .iso installers and Cisco DCNM software releases 11.0, 11.1, 11.2, and 11.3.

The company issued eight other security warnings in the DCNM package, one of the worst being a [8.2-rated][2] High vulnerability in REST API endpoints of DCNM could let an authenticated, remote attacker inject arbitrary commands on the underlying operating system with the privileges of the logged-in user.

The vulnerability is due to insufficient validation of user-supplied input to the API. An attacker could exploit this vulnerability by sending a crafted request to the API. A successful exploit could allow the attacker to inject arbitrary commands on the underlying operating system, Cisco said.

[Other high-rated][3] REST API security holes in DCNM were revealed as well.

As for the SD-WAN warnings, Cisco deemed two of them critical.  The [first][4], with a security-threat rating of 9.9, describes a weakness in the web-based management interface of Cisco SD-WAN vManage Software that could let an authenticated, remote attacker bypass authorization, enabling them to access sensitive information, modify the system configuration, or impact the availability of the affected system.

The vulnerability is due to insufficient authorization checking on the affected system. An attacker could exploit this weakness by sending crafted HTTP requests to the web-based management interface of an affected system, Cisco stated. A successful exploit could allow the attacker to gain privileges beyond what would normally be authorized for the configured user-authorization level. The attacker may be able to access sensitive information, modify the system configuration, or affect system availability, Cisco stated.

The second critical warning, with a security threat rating of 9.8, is a [vulnerability in Cisco SD-WAN Solution][5] Software that could let an unauthenticated, remote attacker cause a buffer overflow on an affected device.

The vulnerability is due to insufficient input validation. An attacker could exploit this vulnerability by sending crafted traffic to an affected device. A successful exploit could allow the attacker to gain access to information that they are not authorized to access, make changes to the system that they are not authorized to make, and execute commands on an affected system with privileges of the root user, Cisco said.

Vulnerable products include: IOS XE SD-WAN Software, SD-WAN vBond Orchestrator Software, SD-WAN vEdge Cloud Routers, SD-WAN vEdge Routers, SD-WAN vManage Software, and SD-WAN vSmart Controller Software.

Cisco said there were no workarounds that address these vulnerabilities and that it had [released software updates][6] that address all of the weaknesses.

Join the Network World communities on [Facebook][7] and [LinkedIn][8] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3569153/cisco-urges-patching-flaws-in-data-center-sd-wan-gear.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-dcnm-bypass-dyEejUMs
[2]: https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-dcnm-rest-inj-BCt8pwAJ
[3]: https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-dcnm-improper-auth-7Krd9TDT
[4]: https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-uabvman-SYGzt8Bv
[5]: https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-sdbufof-h5f5VSeL
[6]: https://www.cisco.com/c/en/us/about/legal/cloud-and-software/end_user_license_agreement.html
[7]: https://www.facebook.com/NetworkWorld/
[8]: https://www.linkedin.com/company/network-world
