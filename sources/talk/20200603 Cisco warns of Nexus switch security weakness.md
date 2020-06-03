[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Cisco warns of Nexus switch security weakness)
[#]: via: (https://www.networkworld.com/article/3546341/cisco-warns-of-nexus-switch-security-weakness.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

Cisco warns of Nexus switch security weakness
======
Cisco Nexus NS-OS software could be exploited to create a DOS attack.
Filo / Getty

Cisco is telling customers of its Nexus core data-center switches to fix or work around a vulnerability that could leave the boxes open to a denial of service attack.

The [vulnerability, found in the Nexus NX-OS software][1] gets a 8.6 score out of 10 on the Common Vulnerability Scoring System, making it a “High” risk problem.

Cisco said the vulnerability is due to an affected device unexpectedly decapsulating and [processing IP-in-IP packets][2] that are destined to a locally configured IP address. IP in IP is a tunneling protocol that wraps an IP packet within another IP packet.

“A successful exploit could cause the affected device to unexpectedly decapsulate the IP-in-IP packet and forward the inner IP packet. This may result in IP packets bypassing input access-control lists (ACLs) configured on the affected device or other security boundaries defined elsewhere in the network,” Cisco stated.  “Under certain conditions, an exploit could cause the network stack process to crash and restart multiple times, leading to a reload of the affected device and a DoS condition.”

The vulnerability impacts a variety of Nexus switches from the Nexus 1000 Virtual Edge for VMware vSphere to the Nexus 9000 Series.

Cisco said a workaround is to configure infrastructure access-control lists (iACLs) to let only required management and control-plane traffic to reach the affected device, as recommended in the [Cisco Guide to Securing NX-OS Software Devices][3]

.“Customers may also consider explicitly denying all IP packets with protocol number 4 (corresponding to IP-in-IP packets) as part of their iACLs, if no legitimate IP-in-IP traffic is used in their network. A customized control-plane-policing (CoPP) policy may also be used to drop IP-in-IP traffic that is destined to an affected device; however, support for CoPP customization varies across different Nexus platforms and software releases.”

Customers are advised to contact their support organization for assistance evaluating the feasibility of a workaround and with implementing one on an affected device, Cisco stated. Cisco also said the [Cisco Software Checker][4] identifies Cisco Security Advisories that affect specific Cisco NX-OS Software releases and names the earliest release that fixes vulnerabilities that are described in each advisory, called “First Fixed.”

In addition the company said it has released [free software updates][5] that address the vulnerability.

Join the Network World communities on [Facebook][6] and [LinkedIn][7] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3546341/cisco-warns-of-nexus-switch-security-weakness.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-nxos-ipip-dos-kCT9X4
[2]: https://kb.cert.org/vuls/id/636397
[3]: https://tools.cisco.com/security/center/resources/securing_nx_os.html
[4]: https://tools.cisco.com/security/center/softwarechecker.x
[5]: https://www.cisco.com/c/en/us/about/legal/cloud-and-software/end_user_license_agreement.html
[6]: https://www.facebook.com/NetworkWorld/
[7]: https://www.linkedin.com/company/network-world
