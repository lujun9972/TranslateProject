[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Secure Work from Home by Applying Zero-Trust Best Practices to VPN Infrastructure)
[#]: via: (https://www.networkworld.com/article/3563869/secure-work-from-home-by-applying-zero-trust-best-practices-to-vpn-infrastructure.html)
[#]: author: (Mr. Larry Lunetta )

Secure Work from Home by Applying Zero-Trust Best Practices to VPN Infrastructure
======

iStock

As the security world rotated to a Zero-Trust model for securing the enterprise, tried-and-true technologies such as VPN seemed to fall by the wayside. Yes, many organizations simply assumed VPN credentials were enough to have access to corporate resources, and in fact, this perimeter view gave rise to a Zero-Trust philosophy where no user or device is allowed access without authentication and authorization.

But the idea that you need to choose between VPN and Zero Trust ignores the fact that how products and technologies are implemented will ultimately dictate an organization’s level of protection. “VPN or Zero Trust” is a false choice. With the home as the current employee workplace, organizations are rapidly implementing a range of software and hardware VPN connectivity solutions to support work from home connectivity. But with an eye towards Zero Trust, they are enhancing VPN security with key Zero-Trust components to ensure the organization is protected.

While there are several different definitions for Zero Trust (including NIST’s), the basic principle is that no user or device can gain network access without authenticating and being assigned application layer access rights. As a result, most Zero-Trust implementations will provide:

  * A method for collecting and validating user or device credentials using a variety of techniques, from 802.1x to multi-factor authentication. Typically the authentication process involves using a protocol such as Radius to interface with corporate identity systems such as Active Directory.
  * The second key component is a Trust Broker—essentially a policy manager that will take validated credentials and assign IT access rights based on pre-determined corporate policies. If the Trust Broker is designed for enterprise environments, then the role-based access policy is independent of the type of access (e.g., wired, wireless, remote), which means that when an employee gains VPN access, the appropriate access policies are automatically applied.
  * Next is enforcement. Enforcement can be done in a variety of network locations, but the optimal placement is at the point of VPN termination. Some organizations will install a separate firewall for this purpose, but scalable VPN termination along with routing and other functions can easily provide the policy enforcement necessary to restrict access once the traffic is inside the corporate network.
  * Finally, there is adaptive trust. Trust is not a permanent condition and based on what happens to the user or endpoint after initial access will determine what level of trust is provided on an ongoing basis. This means that status from across the security ecosystem must be sent and processed by both the Trust Broker and the corresponding enforcement point.



As organizations are overnight standing up thousands of new remote connections there is no need to sacrifice security for convenience. VPN is a foundational Zero-Trust element. By combining it with Zero-Touch setup, cloud management, seamless identity-based access control and head-end policy enforcement, employees will operate in a Zero-Trust environment no matter how or where they connect. We dive into topics on Zero-Trust Security at [ATM Digital,][1] our free event for our community of customers, partners, and networking/security influencers. Hope to see you there!

Learn more about [Aruba VPN Services.][2]

Read my blog, ["Cutting Through the Security Mist: Wi-Fi That Works Has Zero Trust Built In—From the Edge to the Cloud."][3]

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3563869/secure-work-from-home-by-applying-zero-trust-best-practices-to-vpn-infrastructure.html

作者：[Mr. Larry Lunetta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.arubanetworks.com/atmosphere
[2]: https://www.arubanetworks.com/products/security/vpn-services/
[3]: https://blogs.arubanetworks.com/spectrum/cut-through-the-security-mist-wi-fi-that-works-has-zero-trust-built-in-from-the-edge-to-the-cloud/
