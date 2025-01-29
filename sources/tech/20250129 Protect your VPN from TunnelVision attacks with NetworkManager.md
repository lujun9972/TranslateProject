[#]: subject: "Protect your VPN from TunnelVision attacks with NetworkManager"
[#]: via: "https://fedoramagazine.org/protect-your-vpn-from-tunnelvision-attacks-with-networkmanager/"
[#]: author: "Íñigo Huguet https://fedoramagazine.org/author/ihuguet/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Protect your VPN from TunnelVision attacks with NetworkManager
======

![][1]

Photo by [Redd Francisco][2] on [Unsplash][3] (modified)

Many users trust in a variety of VPN solutions to securely protect their privacy or access to personal or company’s resources when connecting from an untrusted network. This may be an airport or cafe’s WiFi network. This article describes how to use NetworkManager to improve that security.

Some months ago, researchers disclosed the [TunnelVision][4] vulnerability with ID [CVE-2024-3661][5]. The CVE describes a way to redirect traffic outside of the encrypted channel of a large number of VPN solutions. The attack is trivial for malicious agents with access to the network to which the user connects. They don’t even need to exploit any obscure bug or hidden vulnerability. They only need to reconfigure one standard feature of the DHCP protocol.

The attack is based on DHCP installing some routes to your system. Let’s begin by investigating what DHCP and routing are and how the attack makes use of them. If you only wish to know the solution, jump to the “[Policy routing to the rescue][6]” section, below. Jump to the “[Configure NetworkManager”][7] section to see how to effectively apply the mitigation in your system when configuring your VPN with NetworkManager.

### DHCP

DHCP stands for _Dynamic Host Configuration Protocol_. It is a protocol to automatically assign IP addresses and other IP related configurations to hosts that connect to a network. When you connect to your home network and automatically get a private IP address, instead of having to configure it manually, it is very likely that it is thanks to a _DHCP server_ running in your router, as DHCP is the most widely used method for this purpose.

The typical pieces of configuration that a host gets from DHCP are the host’s IP address, the network mask, and the gateway. These three settings are normally enough to figure out how to reach other hosts in the same private network and to the Internet.

SLAAC normally replaces DHCP for IPv6, but it works similarly.

### Basic explanation about routing

Routing is how your host decides where to send each packet depending on the destination IP address. With the ip route command you can see some of the routes that your system is using. They look something like this (simplified):

```

    192.168.1.0/24 dev eth0 src 192.168.1.10
    172.16.0.0/16 dev eth1 src 172.16.1.2
    10.0.0.0/8 via 192.168.1.25 dev eth0 src 192.168.1.10
    default via 192.168.1.1 dev eth0 src 192.168.1.10

```

_Note: the definition of subnets in the format 192.168.1.0/24 is following the CIDR notation. See[here][8] if you don’t know what does it mean_.

First we see a _direct route_ instructing to send packets directed to IP addresses within the 192.168.1.0/24 subnet through _eth0_. Then, a _direct route_ instructing to send packets directed to IP addresses within the 172.16.0.0/16 subnet through _eth1_. _Direct routes_ are used for packets directed to the same subnet as the host, since they are directly reachable. The kernel uses the routes to decide what the right device to send the packet is. It would be a mistake to send a packet directed to 192.168.1.20 by the _eth1_ interface, which is connected to a different physical network.

The third route contains _via 192.168.1.25_. This is a _next hop_ , and is used to send packets to destinations not directly reachable by our system. Instead they are sent via an intermediate device with the IP address 192.168.1.25. This must be a router with capability to forward the packet to other networks where the destination is reachable.

The last one is known as a _default route_. The kernel uses it to send packets that didn’t match any other route. They are typically used to configure the _gateway_ , the _next hop address_ to which to route all the packets that we don’t explicitly know the route to. This is how our packets reach the Internet.

![][9]

### How the attack works

Most of the VPN clients are routing-based VPNs. This type of clients establish a tunnel to the VPN network by creating a virtual device. This is typically named _tun0_ or something similar. The VPN program encrypts all the traffic routed through that virtual device and sends it to the other end of the tunnel. The idea is that, although the traffic still goes through the potentially compromised network, it now does so as encrypted data.

To select what traffic to send through the tunnel interface, some routes are added to your system. At a minimum, a route similar to _10.0.0.0/8 dev tun0_ is created. This routes the traffic directed to other systems inside the same VPN. For those who want to route all the traffic through the VPN, a default route similar to _default via 10.11.12.13 dev tun0_ is added, as well.

When you connect to a network using DHCP or SLAAC, the received IP configuration might contain some routes to install in your system. This has legitimate uses that we won’t dig into in this article, but it is also what attackers use to bypass the VPN’s configurations.

What happens when 2 routes overlaps in a way that a destination IP address matches with both of them? For example, the address 10.0.0.1 is within both subnets 10.0.0.0/8 and 10.0.0.0/24. Then, the route with the greater prefix wins. In this case, 10.0.0.0/24. This is because it is a more specific route, as it defines a smaller range of addresses, so they are a subset of the other which is more general.

Malicious agents with access to the network can take advantage of this. They can configure their DHCP server to send 2 routes with greater prefix than those configured by your VPN. This makes your system use the higher prefix and not send the traffic through the virtual tunnel device, so it goes unencrypted.

```

    10.0.0.0/8 dev tun0   <-- route from VPN client
    10.0.0.0/9 dev eth0   <-- route from DHCP
    10.128.0.0/9 dev eth0 <-- route from DHCP

```

![][10]

A _default route_ can also be shadowed. _Default_ is equivalent to 0.0.0.0/0, so the routes for 0.0.0.0/1 and 128.0.0.0/1 would overrule it, as they have a greater prefix. This means that the attacker can redirect all the traffic.

### Policy routing to the rescue

We can use policy routing to mitigate the TunnelVision attack and other similar attacks like [TunnelCrack][11]. Policy routing is a technique for making routing decisions based on custom policies. In Linux based distros like Fedora we can see the policies with the command ip rule*.*

To prevent the attack, we can use policy routing to move the VPN routes to a dedicated routing table with higher priority than the table that contains the routes configured by DHCP.

Do this by creating a _policy rule_ that looks up a custom routing table, for example table 75, for all the outgoing packets. Use a lower priority value than the main table, which is 32766, to ensure that our routes match first. Note that lower values mean higher priority.

```

    ip rule add to all table 75 pref 32000

```

Then recreate the same routes as the VPN in the new table.

```

    ip route add 10.0.0.0/8 dev tun0 table 75
    ...(etc)...

```

Check that the rule is in place with the ip rule command. Inspect that the routes have really been added to the table with ip route list table 75.

That’s it. If any route from our custom table is applicable, it is used. Otherwise, the main table is checked as usual. Since routes from DHCP are added to the main table by default, they are unable to override the VPN’s routes.

### Configure NetworkManager

At this point, most readers might have already noticed that manually configuring this every time is going to be very tedious and error prone. Also, non expert users might have lot of difficulties to determine which are the VPN routes among all the others. Moreover, routes for a device that doesn’t exist cannot be added, so we need to wait until the VPN device (i.e. _tun0_ ) is created. Once created, it is normally brought up immediately. This presents the risk of leaking data before the policy routing is configured.

If you are managing the VPN connection with NetworkManager, you can instruct it to configure the policy routing. The following command will perform the configuration. You only need to run it once and it will set this as a permanent configuration (even after a reboot).

```

    nmcli connection modify MY_VPN_CONNECTION_NAME \
        ipv4.route-table 75 \
        ipv4.routing-rules "priority 32000 from all table 75" \
        ipv6.route-table 75 \
        ipv6.routing-rules "priority 32000 from all table 75"

```

**Tip:** find what the connection name is with the nmcli connection command.

Now deactivate and reactivate the connection. With these settings, NetworkManager will add the rules and put the routes in the specified table.

These are pretty advanced configurations, thus they are normally not available in your desktop’s GUI settings panel.

_**Note:** Due to a bug in NetworkManager, these settings were partially ignored for VPN connections. This_ _is fixed in_ _development version 1.51.6. The newest versions in Fedora 40 and 41 also contain the fix. Update Fedora and ensure that you have at least NetworkManager version 1.46.6-1 or 1.50.2-1._

### Possible side effects

People use VPN to securely access resources inside the VPN itself. Optionally, they use it to route all the traffic through the VPN, mainly for privacy reasons. This behavior can be enabled with the “use only for resources in this connection” option (called _never-default_ in _nmcli_ ).

When the VPN is used to route all the traffic, the explained policy routing configuration routes **all** the traffic through the VPN. Even the traffic directed to the local network (i.e. to 192.168.1.20) that, as a consequence, will stop working. Captive portals like those used to login to hotels’ WiFi network won’t work, either. This is because a default route like _default via VPN_ADDRESS_ is added to the new table with higher priority. If this happens, you might need to disable this configuration. If you are experienced enough, you may add some custom routes to the table to fix it.

Any other connection that also needs to add routes might stop working, and you will need to tweak its _route-table_ and _routing-rules_ configurations to create a rule with higher priority than the other.

Even with the potential drawbacks, this is a very robust configuration that should protect you from any data leak based on these kinds of routing attacks.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/protect-your-vpn-from-tunnelvision-attacks-with-networkmanager/

作者：[Íñigo Huguet][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ihuguet/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/01/tunnelvision_attacks-816x345.jpg
[2]: https://unsplash.com/@reddfrancisco?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/grayscale-photo-train-subway-fdvTTpkAKkY?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://www.tunnelvisionbug.com/
[5]: https://nvd.nist.gov/vuln/detail/cve-2024-3661
[6]: tmp.IiGNrfBaAr#routing
[7]: tmp.IiGNrfBaAr#configure
[8]: https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation
[9]: https://fedoramagazine.org/wp-content/uploads/2025/01/routes.png
[10]: https://fedoramagazine.org/wp-content/uploads/2025/01/attack.png
[11]: https://tunnelcrack.mathyvanhoef.com/
