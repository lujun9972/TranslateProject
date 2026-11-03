[#]: subject: "Migrating away from unmaintained NetworkManager VPN plugins (vpnc and fortisslvpn)"
[#]: via: "https://fedoramagazine.org/migrating-away-from-unmaintained-networkmanager-vpnpluginsvpnc-and-fortisslvpn/"
[#]: author: "Aoife MoloneyBeniamino Galvani https://fedoramagazine.org/author/amoloney/https://fedoramagazine.org/author/bengal/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Migrating away from unmaintained NetworkManager VPN plugins (vpnc and fortisslvpn)
======

![][1]

Two legacy NetworkManager VPN plugins— **NetworkManager-vpnc** and **NetworkManager-fortisslvpn** —are retiring and will be obsolete, starting in **Fedora Linux 45**. This is part of ongoing system maintenance and security cleanup.

If you use Virtual Private Networks (VPNs) to connect to remote workplace or enterprise networks, take note of this upcoming change in NetworkManager package availability.

This article contains information about what you need to know. It covers why these plugins are being retired, how this affects your current setup, and how to migrate your VPN connections to actively supported alternatives.

## **Why retire these plugins?**

Both NetworkManager-vpnc and NetworkManager-fortisslvpn are unmaintained. Furthermore, the published issues allow LPE through malicious VPN profiles as well as legacy privilege-handling bugs in older VPN helper scripts, which pose security risks to local systems. Further information is available in this [blog post][2].

To ensure Fedora Linux users remain secure and backed by active upstream maintainers, the Fedora Engineering and Steering Committee (FESCo) and NetworkManager maintainers agreed to retire these unmaintained plugins in favor of modern, secure alternatives already available in Fedora repositories.

## **Overview of changes and migration paths**

**Retired Plugin** | **Protocol / Network Type** | **Migration Target** | **Status & Recommendation**
---|---|---|---
**NetworkManager-fortisslvpn** | Fortinet SSLVPN | **NetworkManager-openconnect** | openconnect supports the older PPP-based Fortinet protocols natively and is actively maintained.
**NetworkManager-vpnc** | Cisco IPsec (IKEv1) | **NetworkManager-libreswan** | libreswan handles the same IKEv1 protocol family and is directly maintained by the NetworkManager team.

## **Step-by-Step Migration Guide**

### **1\. Fortinet SSLVPN Users (fortisslvpn → openconnect)**

If you currently rely on Fortinet SSLVPN tunnels, switch to the NetworkManager-openconnect plugin.

  1. Install the OpenConnect NetworkManager plugin:
Bash
sudo dnf install NetworkManager-openconnect
  2. Open **Settings** → **Network** (or **KDE System Settings** → **Connections** ).
  3. Click **+** to add a new connection and select **Multi-protocol VPN client (openconnect)**.
  4. Set the protocol dropdown to **Fortinet SSL VPN** , input your gateway address and authentication details, and save the profile.
  5. Once verified, remove the legacy package:
Bash
sudo dnf remove NetworkManager-fortisslvpn



### **2\. Cisco IPsec / IKEv1 Users (vpnc → libreswan)**

If you use legacy Cisco IPsec VPN tunnels, migrate your connections to NetworkManager-libreswan.

  1. Install the Libreswan NetworkManager plugin:
Bash
sudo dnf install NetworkManager-libreswan
  2. You may need to create file _/etc/ipsec.d/ikev1.conf_ with this content:
config setup
ikev1-policy=accept
This enables the deprecated IKEv1 protocol. Then restart ipsec.service. Note that the ipsec.service must be running, or the activation will fail.
  3. In your desktop network settings, add a new **IPsec based VPN** connection and select Type=IKEv1.
  4. Enter your gateway IP/domain, the group name enclosed in square brackets (e.g ‘[group]’), group password (pre-shared key), and user credentials corresponding to your previous vpnc configuration. You might have to tune IKE/ESP proposals, DH/PFS settings and routing requirements, which can be obtained from the gateway’s configuration and old vpnc logs.
  5. Test the connection, then remove the legacy package:
Bash
sudo dnf remove NetworkManager-vpnc



## **What happens during upgrades?**

  * **Fedora 43 & 44:** Current installations retain their installed plugins so active connections will not abruptly break. However, there will be no further feature or security updates issued for vpnc or fortisslvpn.
  * **Fedora 45+:** The legacy packages are officially obsoleted by NetworkManager. An upgrade to Fedora 45 automatically removes NetworkManager-vpnc and NetworkManager-fortisslvpn, if they are installed.



We strongly encourage all users relying on these VPN types to test and migrate their connection profiles to **openconnect** or **libreswan** as soon as possible!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/migrating-away-from-unmaintained-networkmanager-vpnpluginsvpnc-and-fortisslvpn/

作者：[Aoife MoloneyBeniamino Galvani][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/amoloney/https://fedoramagazine.org/author/bengal/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/11/migrating_from_unsupported_VPN_plugins-816x345.jpg
[2]: https://blogs.gnome.org/mcatanzaro/2026/09/15/privilege-escalation-vulnerabilities-in-networkmanager-plugins/
