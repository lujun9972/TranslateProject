[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Use dnsmasq to provide DNS & DHCP services)
[#]: via: (https://fedoramagazine.org/dnsmasq-provide-dns-dhcp-services/)
[#]: author: (Andy Mott https://fedoramagazine.org/author/amott/)

Use dnsmasq to provide DNS & DHCP services
======

![Provide DNS & DHCP with dnsmasq][1]

Many tech enthusiasts find the ability to control their [host name resolution important][2]. Setting up servers and services usually requires some form of fixed address, and sometimes also requires special forms of resolution such as defining Kerberos or LDAP servers, mail servers, etc. All of this can be achieved with dnsmasq.

dnsmasq is a lightweight and simple program which enables issuing DHCP addresses on your network and registering the hostname &amp; IP address in DNS. This configuration also allows external resolution, so your whole network will be able to speak to itself and find external sites too.

This article covers installing and configuring dnsmasq on either a virtual machine or small physical machine like a Raspberry Pi so it can provide these services in your home network or lab. If you have an existing setup and just need to adjust the settings for your local workstation, read the previous article which covers [configuring the dnsmasq plugin in NetworkManager.][3]

### **Install dnsmasq**

First, install the dnsmasq package:

```
sudo dnf install dnsmasq
```

Next, enable and start the dnsmasq service:

```
sudo systemctl enable --now dnsmasq
```

### Configure dnsmasq

First, make a backup copy of the _dnsmasq.conf_ file:

```
sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf.orig
```

Next, edit the file and make changes to the following to reflect your network. In this example, mydomain.org is the domain name, 192.168.1.10 is the IP address of the dnsmasq server and 192.168.1.1 is the default gateway.

```
sudo vi /etc/dnsmasq.conf
```

Insert the following contents:

```
domain-needed
bogus-priv
no-resolv
server=8.8.8.8
server=8.8.4.4
local=/mydomain.org/
listen-address=::1,127.0.0.1,192.168.1.10
expand-hosts
domain=mydomain.org
dhcp-range=192.168.1.100,192.168.1.200,24h
dhcp-option=option:router,192.168.1.1
dhcp-authoritative
dhcp-leasefile=/var/lib/dnsmasq/dnsmasq.leases
```

Test the config to check for typos and syntax errors:

```
$ sudo dnsmasq --test
dnsmasq: syntax check OK.
```

Now edit the _hosts_ file, which can contain both statically- and dynamically-allocated hosts. Static addresses should lie outside the DHCP range you specified earlier. Hosts using DHCP but which need a fixed address should be entered here with an address within the DHCP range.

```
sudo vi /etc/hosts
```

The first two lines should be there already. Add the remaining lines to configure the router, the dnsmasq server, and two additional servers.

```
127.0.0.1   localhost localhost.localdomain
::1         localhost localhost.localdomain
192.168.1.1    router
192.168.1.10   dnsmasq
192.168.1.20   server1
192.168.1.30   server2
```

Restart the dnsmasq service:

```
sudo systemctl restart dnsmasq
```

Next add the services to the firewall to allow the clients to connect:

```
sudo firewall-cmd --add-service={dns,dhcp}
sudo firewall-cmd --runtime-to-permanent
```

### Test name resolution

First, install _bind-utils_ to get the _nslookup_ and _dig_ packages. These allow you to perform both forward and reverse lookups. You could use ping if you’d rather not install extra packages. but these tools are worth installing for the additional troubleshooting functionality they can provide.

```
sudo dnf install bind-utils
```

Now test the resolution. First, test the forward (hostname to IP address) resolution:

```
$ nslookup server1
Server:       127.0.0.1
Address:      127.0.0.1#53
Name:         server1.mydomain.org
Address:      192.168.1.20
```

Next, test the reverse (IP address to hostname) resolution:

```
$ nslookup 192.168.1.20
20.1.168.192.in-addr.arpa    name = server1.mydomain.org.
```

Finally, test resolving hostnames outside of your network:

```
$ nslookup fedoramagazine.org
Server:       127.0.0.1
Address:      127.0.0.1#53
Non-authoritative answer:
Name:    fedoramagazine.org
Address: 35.196.109.67
```

### **Test DHCP leases**

To test DHCP leases, you need to boot a machine which uses DHCP to obtain an IP address. Any Fedora variant will do that by default. Once you have booted the client machine, check that it has an address and that it corresponds to the lease file for dnsmasq.

From the machine running dnsmasq:

```
$ sudo cat /var/lib/dnsmasq/dnsmasq.leases
1598023942 52:54:00:8e:d5:db 192.168.1.100 server3 01:52:54:00:8e:d5:db
1598019169 52:54:00:9c:5a:bb 192.168.1.101 server4 01:52:54:00:9c:5a:bb
```

### **Extending functionality**

You can assign hosts a fixed IP address via DHCP by adding it to your hosts file with the address you want (within your DHCP range). Do this by adding into the _dnsmasq.conf_ file the following line, which assigns the IP listed to any host that has that name:

```
dhcp-host=myhost
```

Alternatively, you can specify a MAC address which should always be given a fixed IP address:

```
dhcp-host=11:22:33:44:55:66,192.168.1.123
```

You can specify a PXE boot server if you need to automate machine builds

```
tftp-root=/tftpboot
dhcp-boot=/tftpboot/pxelinux.0,boothost,192.168.1.240
```

This should point to the actual URL of your TFTP server.

If you need to specify SRV or TXT records, for example for LDAP, Kerberos or similar, you can add these:

```
srv-host=_ldap._tcp.mydomain.org,ldap-server.mydomain.org,389
srv-host=_kerberos._udp.mydomain.org,krb-server.mydomain.org,88
srv-host=_kerberos._tcp.mydomain.org,krb-server.mydomain.org,88
srv-host=_kerberos-master._udp.mydomain.org,krb-server.mydomain.org,88
srv-host=_kerberos-adm._tcp.mydomain.org,krb-server.mydomain.org,749
srv-host=_kpasswd._udp.mydomain.org,krb-server.mydomain.org,464
txt-record=_kerberos.mydomain.org,KRB-SERVER.MYDOMAIN.ORG
```

There are many other options in dnsmasq. The comments in the original config file describe most of them. For full details, read the man page, either locally or [online][4].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/dnsmasq-provide-dns-dhcp-services/

作者：[Andy Mott][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/amott/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/09/dnsmasq-dhcp_dns-816x345.png
[2]: https://tldp.org/LDP/nag/node35.html
[3]: https://fedoramagazine.org/using-the-networkmanagers-dnsmasq-plugin/
[4]: http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html
