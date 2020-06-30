[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Test and review of 4 Wi-Fi 6 routers: Who's the fastest?)
[#]: via: (https://www.networkworld.com/article/3541759/test-and-review-of-4-wi-fi-6-routers-whos-the-fastest.html)
[#]: author: (Eric Geier )

Test and review of 4 Wi-Fi 6 routers: Who's the fastest?
======
We tested Wi-Fi 6 routers from Extreme, Cisco, EnGenius and Meraki to find out whether these access points deliver on the latest standard's promise of better throughput, and we reviewed each device.
RoyalFive / Getty Images

One of the most anticipated features of Wi-Fi 6 wireless routers is improved throughput over their Wi-Fi 5 predecessors, and we wanted to check whether they deliver.

Four vendors – Extreme, Cisco, EnGenius and Meraki (owned by Cisco) – provided access points (AP) for our test. Since the routers support both Wi-Fi 5 (802.11ac) and Wi-Fi 6 (802.11ax), we tested them against two Wi-Fi 5 and two Wi-Fi 6 clients and recorded the average throughput and the peak throughput during one-minute tests.

The results give a sense of the performance boost you might expect by upgrading to Wi-Fi 6, and the Wi-Fi 5 number is important because some Wi-Fi 5 clients are likely to be in use for a while after upgrading to Wi-Fi 6 APs.

When you read on past the results, we've got in-depth reviews and a comparison of important features of each of the APs – the Extreme (Aerohive) AP-650, Cisco Catalyst C9115, EnGenius EWS377 and Meraki MR55.

### How we tested

We used network-performance software platform [IxChariot][1] (from Ixia, a [Keysight Technologies][2] business) to run throughput tests on the APs with four different wireless clients: Two Wi-Fi 5 – TP-Link AC600 USB Adapter and Galaxy S5 Phone – and two Wi-Fi 6 - Ubit AX200 PCI Adapter and Apple iPhone 11.

The IxChariot High_Performance_Throughput.scr script was installed on a test PC, on the phones and on the PCI/USB adapters. We simultaneously tested the TCP uplink (from the wireless client through the test AP to the test PC) and the TCP downlink (from the test PC through the test AP to the wireless client).

Each AP was tested against each client, and the Ixia software recorded the results.

During the testing, the distance between the APs and wireless test clients was about 20 feet with a hollow wooden door blocking the line of sight. We enabled WPA2/AES security on the APs and set the 5Ghz channel-width to 80MHz and TX power to 17dBm. The APs were powered with a Gigabit 802.3at PoE injector and linked to the test PC with a Gigabit Ethernet connection.

### Test results

We tallied the results from the tests and arranged them in the chart below:

[][3] Network World / IDG

Throughput test: The throughput speeds between Wi-Fi 6 routers and Wi-Fi 5 (802.11ac) and Wi-Fi 6 (802.11ax) clients as measured in megabits per second.

The average throughput result across Wi-Fi 6 clients, when averaged, was 44.85% higher than with Wi-Fi 5 clients, and the maximum throughput, on average, was 47.44% higher. So it seems that Wi-Fi 6 access points do deliver significantly better throughput.

### And the winners are…

Within this test, the EnGenius EWS377 had both the fastest average throughput and the fastest maximum throughput numbers with both Wi-Fi 6 clients, so it is the clear winner in that category.

As for performance with Wi-Fi5 clients, the Extreme AP had the best throughput in three of the four categories: average and maximum throughput with the TP-Link USB adapter and maximum throughput with the Galaxy S5 phone client, so it is the winner for Wi-Fi 5 throughput. The EnGenius AP outperformed it in one category – average throughput with the Galaxy S5 client – with a throughput of 498.5Mbps vs Extreme’s 485.45Mbps.

With the Wi-Fi 5 clients the lowest recorded average throughput was 122.17Mbps when the Cisco router was paired with the TP-Link adapter client. The highest result in that category was 498.5Mbps between the Engenius AP and the Galaxy phone.

With the Wi-Fi 6 clients, the lowest maximum throughput was 226.74Mbps between the Cisco AP and the Ubit PCI adapter, and the highest was 929.37Mbps between the Engenius AP and the iPhone 11 client.

The biggest outlier in the test was the Cisco AP. Its best score in any test was its average throughput with the Galaxy S5 Wi-Fi 5 client, not with one of the Wi-Fi 6 clients as might be hoped for.

Cisco suggested testing upstream and downstream throughput separately, but we felt doing both at the same time stressed the APs more and represented more of a real-world load. Cisco also suggested running the tests again with a newer version of firmware, but that would have required doing the same for all the other APs, and time didn’t allow. That raises an important point: These results for all the access points are snapshots, not only of the available firmware, but also the very specific testing conditions. With different conditions, any of the access points could do better or they could do worse.

### Feature comparison

Throughput was the only test we ran on the four access points, so while we had them we also checked out each one to note its key features and gauge how easy it is to configure. Again, this is a snapshot, and vendors upgrade their devices over time.

Some of the features we looked for include orthogonal frequency-division multiple access ([OFDMA][4]) that greatly increases the number of radio-frequency subchannels an AP and so can reduce contention among multiple devices by transmitting simultaneously to them or dedicating subchannels to each.

We also looked for multiuser multiple input multiple output ([MU-MIMO][5]), technology that enables multiple devices to access a Wi-Fi router at the same time, effectively sharing the available capacity. Options for routers include 4x4 MU-MIMO and 8x8 MU-MIMO, where the numbers indicate how many simultaneous streams the router can support.

Wi-Fi Protected Access ([WPA3][6]) is another feature on the list, the first major Wi-Fi security upgrade in 15 years, which boosts cryptographic strength for networks transmitting sensitive data.

We also looked for Simultaneous Authentication of Equals (SAE), which provides better protection of transmissions even if passwords aren’t up to recommended security standards.

At the bottom of this article is a chart that compares all the APs against all 14 criteria, but here’s a chart that highlights some of the pros and cons of each device:

### Pros and cons overview

Now, reviews of the four APs.

### Extreme (Aerohive) AP650

The [AP650][7] is one of many Wi-Fi 6 APs Extreme has out, and we evaluated it using their [cloud-based management platform][8]. Packed inside are two Wi-Fi radios (one 5GHz-only and one dual-band that supports 5GHz and 2.4GHz as well) and a Bluetooth radio. This is one of the two APs that utilizes WPA3 security. Though we tested with the internal antenna version, they do offer a version of this same model with external antennas.

[][9] [Aerohive][10]

Aerohive AP650

 

The AP650 weighs just over 2.5 pounds, measures about 9 inches square and 1.5 inches high. On the front/top surface it has one LED status light. On one side it has a reset button, USB port IoT and proximity/location-oriented services, and an RJ45 console port for command-line-interface access. Right around the corner from that it has the DC power input, 2.5G Ethernet LAN port, and an alternative 1G Ethernet LAN port. Both LAN ports are 802.3at [PoE][11] compatible, and also 802.3af PoE with reduced operation. The AP comes with simple mounting hardware.

Using Extreme Networks’ ExtremeCloud IQ automation software, you can create different network policies for each location. (Extreme bought Aerohive in August 2019.) On the top of the GUI is the main menu. The first shortcut takes you to the onboarding process.

On the Manage tab of the menu you can see lists and stats of devices, clients, and users. You can also view logs for events, alarms, security, and applications. There’s also troubleshooting tools to help solve client or AP issues.

[][12] Network World

_**The Devices page of the Manage menu gives you a table of the basic stats, which is customizable with the data you want to see.**_

The Configure tab on the menu allows you to configure network policies such as the SSIDs and wireless security. You can configure the applications, like HTTP/HTTPS, TCP, and UDP connections, that you want to track usage for. You can access the settings for common objects, for instance policies, VLANs, security, QoS, and authentication.

From the Configure tab you can also manage users and groups for standard RADIUS 802.1X authentication or for Extreme's unique Private Pre-shared Key (PPSK) functionality. With PPSK certain users can be given their own WPA/WPA2 password to use on the Wi-Fi.

[][13] Network World

_Extreme's PPSK feature is useful for giving visitors and non-employees encrypted Wi-Fi access without having to hand them your main Wi-Fi credentials._

Within the ML Insights tab on the menu you’ll find a neat feature they call Network 360. It allows you to import floor plans to create a network topology map for documentation and monitoring, plus you can place simulated APs to see a visual prediction of the Wi-Fi coverage. Part of the ML Insights is also Client 360 to give you an idea of client performance.

Comparative Analytics is also a simple but neat feature where you can see how your bandwidth, number of unique client devices, and average number of clients with poor health compare to other Extreme Wi-Fi networks within your industry type.

On the Dashboard tab of the menu you can see more stats about network health, and you can generate customizable reports. On the Cloud View tab, you can see yet more stats, but these are about traffic, clients, events, and usage across the globe for all Extreme networks. This doesn’t have any real value but is neat to see. The last tab on the menu is A3, which is Extreme’s cloud-based Network Access Control (NAC) service, which requires separate licensing.

[][14] Network World

_Extreme offers great reporting functionality for network, PCI, WIPS, and wireless stats._

Throughout Extreme’s cloud GUI there’s a help shortcut on the right side of each page that opens their documentation to the particular topic on the screen at that time. There are even some spots throughout the GUI with video icons that open up a video explanation.

While configuring our test AP, we found the process and GUI to be a bit complicated, especially for smaller networks. There are a lot of template and profile schemes to help customers with large numbers of APs, but it still seems like configuration could be simplified. One annoyance is that most of the default templates and profiles couldn’t be edited. We had to clone them, edit the cloned templates/profiles, and then find out where to apply them.

### Cisco Catalyst 9115

Here is a look at [Cisco’s Catalyst C9115AXI-B AP][15] with the [C9800-40-K9 wireless controller][16]. Housed inside the AP are two Wi-Fi radios (2.4GHz-only and 5GHz-only) and a Bluetooth radio. It is one of four Wi-Fi 6 AP models in the company’s portfolio, and we evaluated the version with internal antennas.

[][17] [Cisco][18]

Cisco Catalyst 9115

This Cisco AP weighs about two pounds and measures about 8-inch square and 1.5 inches high. On the top of the AP you’ll find an LED status light and a USB port, which will be enabled via future software. On bottom you’ll find the 1G/2.5G LAN port, an RG-45 console port, and a reset button. The LAN port supports 802.3at and 802.3af PoE, but reduces functionality with the latter option. The AP comes with standard mounting hardware as well.

On the left-hand side of the web GUI of the controller is the main menu. The first page is the Dashboard, where you can see the main stats and usage of the WLANs, APs, clients, and rogues and interferers. You also get details on the controller usage and specs.

[][19] Network World

_The Dashboard gives you some overview graphics and graphs of the main usage and stats of the APs._

 Network World

* *

In the Monitoring category you can view details and stats on everything, such as ports, system, AAA, services, and many wireless statistics. In the Configuration category you can configure the interfaces, layer2 settings, routing protocols, and services.

In the Radio Configurations tab you can setup interference detection called CleanAir and their radio resource management for detecting and adapting to noise and coverage issues. You can also configure data rates for high throughput, configure parameters for media/voice wireless traffic, and general network settings.

In the Security Configuration category you can configure the internal and external AAA servers, manage the ACL lists, manage guest users, and configure web authentication. Rogue AP detection and containment functionality is also configurable in the security category. Additionality, you can integrate the controller with Umbrella, Cisco’s enterprise network security platform.

Services Configuration manages application visibility, sets QoS, throttles bandwidth, connects Cisco cloud services, sets up mDNS, and configures multicast settings. Wireless Configuration category includes AP-specific settings, configuring air-time fairness, and manage mesh functionality.

[][20] Network World

_The Advanced Wireless features allow you to fine-tune the load balancing, band-steering, roaming, and density functionality._

 

* *

Administration gives access to best practices, to the CLI from the web GUI, and to configuration of the main device settings, DHCP pools, and DNS. It also provides the interface for performing backups/restores and accessing the file manager.

[][21] Network World

_The Troubleshooting page is where you can access the logs, dumps, and reports plus tools like packet capturing and ping and trace route._

 

* *

The controller’s web GUI didn’t have any tooltips or any explanation near the settings but did have a help icon up on the main menu. Clicking that brings up the documentation to the settings you’re currently viewing, but the explanation of help is very brief.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3541759/test-and-review-of-4-wi-fi-6-routers-whos-the-fastest.html

作者：[Eric Geier][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.ixiacom.com/products/ixchariot
[2]: https://www.keysight.com/
[3]: https://images.idgesg.net/images/article/2020/06/nw_wi-fi-5-vs.-wi-fi-6-throughput-chart_new-100849504-orig.jpg
[4]: https://www.networkworld.com/article/3315056/why-is-ofdma-a-magical-feature-in-the-802-11ax-standard.html
[5]: https://www.networkworld.com/article/3256905/13-things-you-need-to-know-about-mu-mimo-wi-fi.html
[6]: https://www.networkworld.com/article/3316567/what-is-wpa3-wi-fi-security-protocol-strengthens-connections.html
[7]: https://www.extremenetworks.com/product/ap650-650x/
[8]: https://www.extremenetworks.com/extremecloud-iq/
[9]: https://images.idgesg.net/images/article/2020/05/aerohive-product-100840873-orig.jpg
[10]: http://www.aerohiveworks.com/
[11]: https://www.networkworld.com/article/2328615/the-power-over-ethernet.html
[12]: https://images.idgesg.net/images/article/2020/05/aerohive-manage-100840986-orig.jpg
[13]: https://images.idgesg.net/images/article/2020/05/aerohive-ppsk-100840987-orig.jpg
[14]: https://images.idgesg.net/images/article/2020/05/aerohive-reports-100840988-orig.jpg
[15]: https://www.cisco.com/c/en/us/products/wireless/catalyst-9100ax-access-points/index.html
[16]: https://www.cisco.com/c/en/us/products/wireless/catalyst-9800-series-wireless-controllers/index.html
[17]: https://images.idgesg.net/images/article/2020/05/cisco-product-2-100841070-orig.jpg
[18]: http://www.networkworld.com/cms/article/www.cisco.com
[19]: https://images.idgesg.net/images/article/2020/05/cisco-dashboard-100840990-orig.jpg
[20]: https://images.idgesg.net/images/article/2020/05/cisco-advanced-wireless-100840991-orig.jpg
[21]: https://images.idgesg.net/images/article/2020/05/cisco-troubleshooting-100840993-orig.jpg
