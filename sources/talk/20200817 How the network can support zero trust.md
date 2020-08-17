[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How the network can support zero trust)
[#]: via: (https://www.networkworld.com/article/3571453/how-the-network-can-support-zero-trust.html)
[#]: author: (Scott Hogg )

How the network can support zero trust
======
Zero trust architecture calls for granting just enough access to network resources so individuals can accomplish their work tasks – nothing more – and the network itself can help.
Getty Images

Simply stated, zero trust calls for verifying every user and device that tries to access the network and enforcing strict access-control and identity management that limits authorized users to accessing only those resources they need to do their jobs.

[Zero trust][1] is an architecture, so there are many potential solutions available, but this is a look at those that fit in the realm of networking.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][2]

### Least privilege

One broad principle of zero trust is least privilege, which is granting individuals access to just enough resources to carry out their jobs and nothing more. One way to accomplish this is network segmentation, which breaks the network into unconnected sections based on authentication, trust, user role, and topology. If implemented effectively, it can isolate a host on a segment and minimize its lateral or east–west communications, thereby limiting the "blast radius" of collateral damage if a host is compromised. Because hosts and applications can reach only the limited resources they are authorized to access, segmentation prevents attackers from gaining a foothold into the rest of the network.

Entities are granted access and authorized to access resources based on context: who an individual is, what device is being used to access the network, where it is located, how it is communicating and why access is needed.

There are other methods of enforcing segmentation. One of the oldest is physical separation in which physically separate networks with their own dedicated servers, cables and network devices are set up for different levels of security. While this is a tried-and-true method, it can be costly to build completely separate environments for each user's trust level and role.

### Layer-2 Segmentation

Another method is Layer 2 segmentation where end users and their devices are isolated via inline security filtering between the device and the access-switch. But installing a firewall between each user and the switch could get very expensive. An alternative is port-based network access control that grants access and assigns each node to a Layer 3 virtual LAN (VLAN) based on authentication or a supplicant certificate.

These types of methods are commonly used on wired and wireless access networks via [the 802.1x standard][3] and [extensible authentication protocol][4]. However, enterprises may not be leveraging vendors’ full suites of end-user role, authentication credentials, device profile, and advanced traffic filtering to segment users based on their level of trustworthiness. Users may be able to boost security if they do.

### Layer-3 Segmentation

A common method of creating application enclaves involves separating access cables and ports into Layer 3 subnets – VLANs – and performing inline filtering.  The filtering could be performed by a network device like a router or by a stateful firewall or proxy server that has some awareness of users’ identities and roles.  A typical example is a standard three-tier web-application architecture in which web servers, app servers, and database servers are in separate subnets. 

Along these lines is network slicing, the [software-defined networking][5] approach where the network is logically separated into slices, similar to virtual routing and forwarding contexts.

A modern take on this would be assigning each server its own IPv4 subnet or IPv6/64 prefix and having it advertise its subnet to network routers as described [here][6]. All the traffic within that server subnet is local to within that server, and no other infiltration could occur on that virtual network inside that host.

Encapsulating traffic in overlay tunnels that run on top of an IP network can separate network segments as well, and this can be done in many ways. These include [virtual extensible LAN][7], [network virtualization using generic routing encapsulation][8], [generic network virtualization encapsulation][9], [stateless transport tunneling][10], and [TCP segmentation offload][11].

Packet tagging – marking packets with internal identifiers – can be used to create trusts between interfaces and so sequester packets from end-user devices based on their identity and authorization. It’s possible to tag in protocols including [MPLS][12], [802.1ad Q-in-Q][13], [802.1AE  MACsec][14], and [Cisco TrustSec][15]. A modern take on this is [segment routing][16] where a special routing header is used in an IPv6 packet to control the communications path over MPLS or IPv6 networks.

### NIST recommendations

The National Institute of Standards and Technology (NIST) has [enumerated the logical components of a zero-trust architecture][17] and provided definitions of some of the deployment styles. This includes validating and authenticating users based on policy decision points and policy enforcement points. This is similar to how the Cloud Security Alliance first conceived of a [software-defined perimeter][18] (SDP).

This method involves an SDP controller that authenticates users, then notifies an SDP gateway to permit access to a specific application based on the user's role and authorization. The process can use an old-school username and password or the new-school method of multi-factor authentication (MFA) with a one-time password, software token, hard token, mobile app, or text message. An alternative method called [single packet authorization][19] or [port knocking][20] uses the client browser or application to send a set of packets to the SDP controller that identifies the user and their device.

There is a wide variety of micro-segmentation, host-isolation, and zero-trust networking methods.  Some are implemented in the network devices, in the servers themselves, within identity and access control systems, or in middleboxes such as proxy servers and firewalls.  There is a broad array of zero trust methods that can be implemented in the host operating system, in the software container virtual networks, in the hypervisor, or in virtual cloud infrastructure with SDP or an IAP.

Many zero trust methods also involve a software agent on the end-user node along with X.509 certificates, mutual TLS (mTLS), single-packet authentication (SPA), and MFA.  Not all of these can be fully implemented by the network or the server or security administrators solely on their own.  To achieve a robust zero-trust network architecture, these techniques may be implemented in concert through collaboration with an interdisciplinary IT team.

Join the Network World communities on [Facebook][21] and [LinkedIn][22] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3571453/how-the-network-can-support-zero-trust.html

作者：[Scott Hogg][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3487720/the-vpn-is-dying-long-live-zero-trust.html
[2]: https://www.networkworld.com/newsletters/signup.html
[3]: https://www.networkworld.com/article/2216499/wireless-what-is-802-1x.htmlhttps:/www.networkworld.com/article/2216499/wireless-what-is-802-1x.html
[4]: https://www.networkworld.com/article/2223672/which-eap-types-do-you-need-for-which-identity-projects.html
[5]: https://www.networkworld.com/article/3209131/what-sdn-is-and-where-its-going.html
[6]: https://tools.ietf.org/html/rfc8273
[7]: https://tools.ietf.org/html/rfc7348
[8]: https://tools.ietf.org/html/rfc7637
[9]: https://tools.ietf.org/html/draft-ietf-nvo3-geneve-16
[10]: https://tools.ietf.org/html/draft-davie-stt-08
[11]: https://en.wikipedia.org/wiki/Large_send_offload
[12]: https://en.wikipedia.org/wiki/Multiprotocol_Label_Switching
[13]: https://en.wikipedia.org/wiki/IEEE_802.1ad
[14]: https://en.wikipedia.org/wiki/IEEE_802.1AE
[15]: https://www.cisco.com/c/dam/en/us/solutions/collateral/borderless-networks/trustsec/C07-730151-00_overview_of_trustSec_og.pdf
[16]: https://tools.ietf.org/html/rfc8402
[17]: https://csrc.nist.gov/publications/detail/sp/800-207/draft
[18]: https://cloudsecurityalliance.org/research/working-groups/software-defined-perimeter/
[19]: https://www.cipherdyne.org/fwknop/
[20]: https://en.wikipedia.org/wiki/Port_knocking
[21]: https://www.facebook.com/NetworkWorld/
[22]: https://www.linkedin.com/company/network-world
