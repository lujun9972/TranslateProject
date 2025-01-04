[#]: subject: "Managing IPv4 Address Conflict Detection with NetworkManager"
[#]: via: "https://fedoramagazine.org/managing-ipv4-address-conflict-detection-with-networkmanager/"
[#]: author: "Maurizio Garcia https://fedoramagazine.org/author/malgnuz/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Managing IPv4 Address Conflict Detection with NetworkManager
======

![][1]

Photo by [Denny Müller][2] on [Unsplash][3]

This article describes address conflict detection with NetworkManager, providing examples to demonstrate the new features.

Detecting any potential address conflict in IP networks is paramount to avoid issues such as:

  * Intermittent connectivity.
  * Transmission errors.
  * Downtime.



The mechanisms to avoid IP address conflicts vary depending on the IP protocol version, and are valid for both static and dynamic IP.

[RFC 4862][4], published in 2007, defines a Duplicate Address Detection (DAD) procedure as a mechanism to avoid duplicated IPv6 addresses.

In 2008, [RFC 5227][5] established the IPv4 Address Conflict Detection (ACD). This mechanism broadcasts ARP probe packets to detect duplicated IPv4 addresses.

Fedora 40 introduced an important [change][6] for NetworkManager. Since that release, the ACD mechanism is enabled by default, waiting up to **200ms** for a duplicated IP in the network.

With this feature, when an IP address is already in use, NetworkManager won´t configure the interface and it will notify the MAC address currently linked to that IP address.

The following section shows the ACD mechanism in action.

### Testing the feature in Fedora 41:

We have two systems with Fedora 41 where we’ll configure the interfaces **enp0s8** with the same IP address: 10.0.0.2/24. These are named VM1 and VM2.

#### Fedora system VM1:

The device enp0s8 appears as disconnected:

```

    # cat /etc/fedora-release
    Fedora release 41 (Forty One)
    # nmcli dev
    DEVICE  TYPE      STATE                   CONNECTION
    enp0s3  ethernet  connected               enp0s3
    lo      loopback  connected (externally)  lo
    enp0s8  ethernet  disconnected            --

```

Now acquire the MAC address of enp0s8 for later checks:

```

    # nmcli -f general.hwaddr dev show enp0s8
    GENERAL.HWADDR:                         08:00:27:09:58:BA

```

Now start a packet capture (in background) over enp0s8 to verify the behavior when NetworkManager tries to configure the network interface:

```

    # tcpdump -i enp0s8 &
    [1] 1789
    tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
    listening on enp0s8, link-type EN10MB (Ethernet), snapshot length 262144 bytes

```

Through NetworkManager CLI (nmcli) the following command will configure the IP address 10.0.0.2/24 in enp0s8 in VM1:

```

    # nmcli con add con-name enp0s8 ifname enp0s8 type ethernet ip4 10.0.0.2/24 ipv6.method disabled
    Connection 'enp0s8' (78af198d-a052-456c-9f69-17bb50dabf60) successfully added.

```

The results of the last command shows the ARP request sent by broadcast to verify the IP address 10.0.0.2 is available.

```

    00:18:09.030677 ARP, Request who-has 10.0.0.2 tell 0.0.0.0, length 28
    00:18:09.056795 ARP, Request who-has 10.0.0.2 tell 0.0.0.0, length 28
    00:18:09.114868 ARP, Request who-has 10.0.0.2 tell 0.0.0.0, length 28

```

There is no answer to that query, so the IP address is successfully configured in enp0s8:

```

    # nmcli dev
    DEVICE  TYPE      STATE                   CONNECTION
    enp0s3  ethernet  connected               enp0s3
    enp0s8  ethernet  connected               enp0s8
    lo      loopback  connected (externally)  lo

    # ip -br addr show enp0s8
    enp0s8           UP             10.0.0.2/24

```

#### Fedora system VM2:

The device enp0s8 appears as disconnected:

```

    # cat /etc/fedora-release
    Fedora release 41 (Forty One)

    # nmcli dev
    DEVICE  TYPE      STATE                   CONNECTION
    enp0s3  ethernet  connected               enp0s3
    lo      loopback  connected (externally)  lo
    enp0s8  ethernet  disconnected            --

```

Now acquire the MAC address of enp0s8 at VM2:

```

    # nmcli -f general.hwaddr dev show enp0s8
    GENERAL.HWADDR:                         08:00:27:EF:CE:FD

```

Before configuring the IP address in enp0s8, capture packets in the interface:

```

    # tcpdump -i enp0s8 &
    [1] 1342
    dropped privs to tcpdump
    tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
    listening on enp0s8, link-type EN10MB (Ethernet), snapshot length 262144 bytes

```

Now, configure the same IP address 10.0.0.2/24 that was set in VM1:

```

    # nmcli con add con-name enp0s8 ifname enp0s8 type ethernet ip4 10.0.0.2/24 ipv6.method disabled
    Connection 'enp0s8' (62f5b868-097b-4c7f-85ac-d4aa70f1db68) successfully added.

```

From the tcpdump the ARP requests asking for the MAC linked to 10.0.0.2 can be seen. This time the replies are pointing to MAC address of enp0s8 at VM1: **08:00:27:09:58:BA**

```

    00:32:16.787092 ARP, Request who-has 10.0.0.2 tell 0.0.0.0, length 28
    00:32:16.791156 ARP, Reply 10.0.0.2 is-at 08:00:27:09:58:ba (oui Unknown), length 46
    00:32:17.026120 ARP, Request who-has 10.0.0.2 tell 0.0.0.0, length 28
    00:32:17.030038 ARP, Reply 10.0.0.2 is-at 08:00:27:09:58:ba (oui Unknown), length 46
    00:32:17.236314 ARP, Request who-has 10.0.0.2 tell 0.0.0.0, length 28
    00:32:17.240817 ARP, Reply 10.0.0.2 is-at 08:00:27:09:58:ba (oui Unknown), length 46

```

As the IP is already used by VM1, the NetworkManager will not configure enp0s8 in VM2. The device will still appear as disconnected without IP address set:

```

    # nmcli dev
    DEVICE  TYPE      STATE                   CONNECTION
    enp0s3  ethernet  connected               enp0s3
    lo      loopback  connected (externally)  lo
    enp0s8  ethernet  disconnected            --

    # ip -br addr show enp0s8
    enp0s8           UP

```

Now check the NetworkManager´s logs from the system´s journal:

```

    # journal -xe
    ... output omitted ...
    vm2 NetworkManager[809]: <info>  [1733739965.4208] device (enp0s8): state change: config -> ip-config (reason 'none', managed-type: 'full')
    vm2 NetworkManager[809]: <warn>  [1733739965.4400] device (enp0s8): IP address 10.0.0.2 cannot be configured because it is already in use in the network by host 08:00:27:09:58:BA
    vm2 NetworkManager[809]: <info>  [1733739965.4403] device (enp0s8): state change: ip-config -> failed (reason 'ip-config-unavailable', managed-type: 'full')
    vm2 NetworkManager[809]: <warn>  [1733739965.4406] device (enp0s8): Activation: failed for connection 'enp0s8'

```

The output above describes the default behavior for Fedora 40 and later. However, it introduces up to 200 ms delay in performing the duplicate IPv4 check as mentioned above.

#### Can the IPv4 Conflict Detection be tailored for particular use cases?

Yes. Sometimes, the delay for a specific use cases can be reduced or the ACD mechanism may be turned off. This is possible to achieve through the **ipv4.dad-timeout** property. When this property is set to 0, the IP duplicated check is disabled. This can be set globally or per network interface.

Getting back to the previous example, we can turn off the ACD mechanism in the enp0s8 interface at VM 2 when configuring the IP address 10.0.0.2/24:

```

    # nmcli con add con-name enp0s8 ifname enp0s8 type ethernet ip4 10.0.0.2/24 ipv6.method disabled ipv4.dad-timeout 0
    Connection 'enp0s8' (ff6bfee8-8562-44a0-8584-ec1a4eaef704) successfully added.

```

This time, the network interface will appear with the IP address successfully set:

```

    # nmcli con show
    NAME    UUID                                  TYPE      DEVICE
    enp0s3  592c6372-3025-3daa-8c3f-9209022d61ed  ethernet  enp0s3
    enp0s8  ff6bfee8-8562-44a0-8584-ec1a4eaef704  ethernet  enp0s8
    lo      cfda4123-c93a-40c1-a4b6-f7fd3e06db1f  loopback  lo

    # ip -br addr show enp0s8
    enp0s8           UP             10.0.0.2/24

```

As was seen above, disabling ACD will allow configuring a duplicated IPv4 address in the network. This is something to avoid unless the configuration approach followed can guarantee an IPv4 address duplication is unlikely or impossible to occur in the network.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/managing-ipv4-address-conflict-detection-with-networkmanager/

作者：[Maurizio Garcia][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/malgnuz/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/12/managing_ipv4_addr_conflicts-816x345.jpg
[2]: https://unsplash.com/@redaquamedia?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/white-and-blue-light-on-dark-room-JyRTi3LoQnc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://www.rfc-editor.org/rfc/rfc4862
[5]: https://www.rfc-editor.org/rfc/rfc5227
[6]: https://fedoraproject.org/wiki/Changes/Enable_IPv4_Address_Conflict_Detection
