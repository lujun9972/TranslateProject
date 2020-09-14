[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (4 essential edge-computing use cases)
[#]: via: (https://www.networkworld.com/article/3573587/4-essential-edge-computing-use-cases.html)
[#]: author: (Ann Bednarz )

4 essential edge-computing use cases
======
Placing processing power and storage at the edge of enterprise networks takes many forms but delivers faster response times and can reduce the need for WAN bandwidth.
Structuresxx / Getty Images

[Edge computing][1] means different things to different players. But one thing is constant: Location matters.

Edge computing enables autonomous mining equipment to react to unexpected conditions a mile below the surface, even when disconnected from a network. When a hotel guest places a food order from a mobile phone and wants to have it delivered poolside, [edge computing][1] makes it possible to steer servers to the guest's lounge chair.

### Tech Spotlight: [Edge Computing][2]

  * [Edge computing's epic turf war][3] (CIO)
  * [Securing the edge: 5 best practices][4] (CSO)
  * [Edge computing and 5G give business apps a boost][5] (Computerworld)
  * [Amazon, Google, and Microsoft take their clouds to the edge][6] (InfoWorld)



Sensors, smart devices, and mobile users are proliferating across all industries. Enterprises are investing in edge deployments to combat growing amounts of decentralized data that need to be processed in place. When low latency is essential, edge setups take the delay out of moving data to a data center or public cloud for processing.

Another factor is the cost of backhauling data to a central location. Processing and analyzing locally can translate to less need for expensive bandwidth.

When more immersive interactions are sought, edge computing can put real-time data production closer to where people and machines exist. By 2022, more than 50% of enterprise-generated data will be created and processed outside the [data center][7] or cloud, according to Gartner.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][8]

At the same time, edge deployments are not islands. Edge infrastructure is typically managed centrally, via an enterprise data center or the cloud. Edge services might be delivered by content-delivery networks, [colocation providers][9], and cloud service providers that are extending their footprints with regional data centers, local [micro data centers][10], and compute capacity tacked onto telecom towers. Enterprise IT is tasked with integrating all the pieces – sensors, mobile devices, access points, gateways, edge servers, storage and networking gear – and managing operations that extend from the edge to on-prem and cloud data centers.

With edge computing, enterprises tend to start with a single, narrow use case, led by a vendor or system integrator, according to Gartner. But that's just the beginning. Over the next few years, enterprises are expected to expand to a wide range of edge-computing use cases. By the end of 2023, more than 50% of large enterprises will deploy at least six edge-computing use cases for [IoT][11] or immersive experiences, compared to less than 1% in 2019, Gartner predicts.

Four enterprises in different industries shared their edge-computing endeavors and how they're realizing gains in employee safety, productivity, customer service and revenue. Here's what we learned.

## AI at the edge speeds freight-train maintenance

Idle time is the enemy of freight-train operations.

Railroad companies measure freight-train performance in terms of average velocity, which generally hovers in the 35-37 mph hour range, according to Scott Carns, COO at [Duos Technologies][12]. "If they can gain one mile-per-hour in velocity, that equates to about $10 million in profitability. So there's a huge push to invest in technologies that make them more efficient."

One thing that slows freight trains is inspections. As freight trains cross the rail lines in North America, operators have to make time for mandatory car inspections. Historically, that would require people to conduct visual and physical examinations of mechanical components on the cars while they sit idle in a railyard. Duos is working to streamline that process using sensors, imaging and analytics deployed in the field.

The Jacksonville, Fla.-based company is building rail-inspection portals that stand like giant industrial carports. Instead of getting a physical examination in an inspection yard, a train passes through a Duos portal and undergoes an automated inspection without having to slow its speed. The portals are outfitted with high-powered LED lights to illuminate the trains and with cameras that can capture images at high speeds.

"We build these big portals, and trains go through at 40, 50, 60 miles per hour. We image the entire train from all sides, and then we run AI algorithms to look for what we call use cases, or mechanical defects, on the rail car," Carns says. The system can detect oil leaks, damaged parts, and missing hatches, for example, and pinpoint the issues that need fixing.

"We capture every rail car from nine different camera perspectives," Carns says. Each camera generates about 1GB of data, so a single car generates 9GB. An average train is about 120 cars, which puts the data tally at about 1TB per train. The high volume of data, combined with the inconsistency of available WAN bandwidth at remote track-side sites around the country, makes it impractical to send the data for processing in a central data center.

Adjacent to the portal is a small hut for IT systems. Two 45U racks contain ruggedized [Dell XR2 servers][13] and PowerVault storage. "We essentially build a small data center on the track side to process all that data at the edge," Carns says.

AI processing starts immediately. To comply with rail safety regulations, the inspections have to be conducted quickly so that any needed repairs can be made when the trains arrive at the nearby railyard. "We have to do it in near real-time, because the train has to be inspected before it gets to its destination."

In addition, depending on the location of the portal, there might be 30 to 40 trains that pass through each day. "You have to be done processing before the next train comes through," Carns says. "That's a huge, high-data operation that takes place track-side."

Duos migrated from Dell's PowerEdge VRTX blade servers to the XR2s about 18 months ago. The XR2 platform is enabling Duos to make its systems more modular, Carns says. The ruggedized aspect is also critical, given the environmental conditions the servers have to withstand. For example, one of the Duos portals is deployed in Winnipeg, Canada, where temperatures can climb to 90 degrees in the summer and plunge to minus 40 in the winter.

"One of our biggest challenges is maintenance and serviceability," Carns says. "Outside of the military and marine applications, the railroad is probably about as far to the edge as you can get."

Looking ahead, Duos plans to continue to expand its buildout of portals. Over the next few years, the company expects to have 60 or 70 systems in production, Carns says.

On the development side, the company continues to expand the range of its AI applications. Most recently, Duos began prototyping an application that uses thermal imaging to capture and analyze how electrical traction motors, which are mounted under the train cars, operate at different temperatures. The goal is to improve predictive maintenance for these costly parts that tend to break and burn out, Carns says. "Nobody had this data point before."

## Location-aware apps add to hotel room smarts

Sometimes, doing more at the edge can mean subtracting hardware. At [Nobu Hotels][14], an upgraded wireless infrastructure is enabling more [IoT][11] and AI-driven applications with less proprietary hardware.

Nobu is standardizing on network infrastructure for its hotels that will allow it to converge Wi-Fi access with a range of applications for guests and employees, including content delivery, lighting controls, door locks, and safety alarms. At the same time, it's enabling Nobu to streamline its onsite hardware requirements, which saves time and money, says Rodney Linville, global corporate director of IT at Nobu Hospitality.

"To simplify opening a hotel and to be able to integrate the technologies at the property – I needed to make sure that the technology chosen was able to do that," Linville says. Not sometime in the future, but right out of the gate. "Aruba had their foot forward."

Nobu deployed [Aruba][15] gear beginning with three new hotels in Chicago, Warsaw and London. It's using Aruba edge and core switches, [ClearPass Policy Manager][16] for role- and device-based secure network access control, and location-ready access points with support for IoT devices running [Wi-Fi][17], Zigbee, Bluetooth, and third-party protocols.

The network infrastructure supports administrative applications, such as the hotel's mobile point-of-sale (POS) and property-management systems, as well as guest applications. It delivers all the technology within the rooms – door locks, climate control, hospitality services, and more. Using their own mobile devices, guests can check in or out of the property, order room service, request linens, or raise the blinds. Employees can monitor room access, reprogram locks, or call for help if there's an emergency.

"Being able to have that connectivity anywhere in the room and being able to control those services in the room – that's where our rooms are going," Linville says. The goal is to allow guests to use their own phones or wireless devices to manage not only hotel-wide services such as hospitality but also in-room, location-dependent systems such as the door lock, TV or air conditioner.

To make that happen, the IT team is pairing the Bluetooth beacon and Zigbee radio technology that's built into Aruba's access points with IoT and analytics applications that generate, analyze and act upon data in real time.

Nobu initiated the integration of Aruba's infrastructure with access-control technology from ASSA ABLOY Global Solutions, for example. The [ASSA ABLOY][18] technology lets guests use their smartphones for contactless check-in and to unlock their rooms. In the past, Nobu had to deploy dedicated in-room gateways for the ASSA ABLOY contactless entry systems. With the integration, Nobu can use the Aruba access points, rather than separate Zigbee gateways, to secure communications between the in-room smart door locks and the centralized lock-management software.

Linville pushed for ASSA ABLOY to use the Aruba hardware instead of the proprietary gateways. "They would have, almost, another network inside the hotel just to control the locks," Linville says. "I don't want to pay for that when I have the technology already at the hotel. Why can't you guys just talk?"

Another key project was getting the Aruba gear to work with a third-party employee-safety application. [React Mobile][19] makes portable panic buttons that are designed to alert security personnel if a hotel employee encounters a dangerous or threatening situation such as an abusive guest or a medical emergency. The alarm system incorporates location-based services, and in the past, it required IT to deploy and maintain a separate overlay network with proprietary Bluetooth beacons installed in the rooms.

By integrating the systems, Nobu can use Aruba's IoT-enabled access points to provide the necessary connectivity: If a worker presses the "help" button on the React Mobile smartphone app, Bluetooth beacons in the Aruba access points enable the app to determine the user's location, which is sent via Wi-Fi to summon help.

Again at Nobu's prompting, the vendors worked together to integrate their systems in time for the opening of the hotel's new Chicago facility. It required some trial and error to deploy it, Lineville says, but the effort paid off the next time. "In Warsaw it was flawless."

Aruba's willingness to invest in R&amp;D and explore AI possibilities was a big draw, Linville says. "One of the reasons we chose Aruba is because they are as eager to do these types of integration as I am. They see the value in it."

Another feature that drew Nobu to the Aruba platform is security. The Aruba gear has integrated role-based [firewall][20] and intrusion prevention capabilities, which help Nobu stay compliant with Payment Card Information (PCI) data-security requirements for its wireless point-of-sale application, for example. Other enterprise vendors can offer that kind of security, but it would require another appliance in the network, Linville says. "If I can utilize that in their product, I'd rather use that than add another piece of hardware."

## HCI at the edge streamlines grocery store IT

A trade-show demonstration of a [hyperconverged infrastructure][21] (HCI) platform caught Jeff Miller's eye several years ago, but the size of the system was a dealbreaker. "I thought, 'that's perfect, except I need it about 10 times smaller,'" Miller recalls. He stayed in contact with the vendor, Scale Computing, and kept tabs on his options until a form factor that worked for his needs became available.

Miller is director of IT at [Jerry's Foods][22], a retailer with 50 grocery, liquor and hardware stores in Minnesota and Florida. In the past, each location had virtual servers and a SAN. The legacy systems were expensive and difficult to manage. Now, Jerry’s Foods is nearing the end of a project to deploy [Scale Computing's][23] HE150 edge devices in its locations – a move that's enabling the company to rearchitect its whole in-store IT strategy, Miller says.

The HE150 is an all-flash, [NVMe][24] storage-based compute appliance that's built off the Intel NUC mini PC. It measures roughly the size of three smartphones stacked on top of each other. It includes disaster recovery, high-availability clustering, rolling upgrades and integrated data protection, "all local and in a very small footprint," Miller says.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3573587/4-essential-edge-computing-use-cases.html

作者：[Ann Bednarz][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3224893/what-is-edge-computing-and-how-it-s-changing-the-network.html
[2]: https://www.networkworld.com/article/3574910/edge-computing-the-next-generation-of-innovation.html
[3]: https://www.cio.com/article/3574928/edge-computings-epic-turf-war.html
[4]: https://www.csoonline.com/article/3572338/securing-the-edge-5-best-practices.html
[5]: https://www.computerworld.com/article/3573769/edge-computing-and-5g-give-business-apps-a-boost.html
[6]: https://www.infoworld.com/article/3575071/amazon-google-and-microsoft-take-their-clouds-to-the-edge.html
[7]: https://www.networkworld.com/article/3223692/what-is-a-data-centerhow-its-changed-and-what-you-need-to-know.html
[8]: https://www.networkworld.com/newsletters/signup.html
[9]: https://www.networkworld.com/article/3407756/colocation-facilities-buck-the-cloud-data-center-trend.html
[10]: https://www.networkworld.com/article/3445382/10-hot-micro-data-center-startups-to-watch.html
[11]: https://www.networkworld.com/article/3207535/what-is-iot-the-internet-of-things-explained.html
[12]: https://www.duostechnologies.com/
[13]: https://www.dell.com/en-us/work/shop/povw/poweredge-xr2
[14]: https://www.nobuhotels.com/
[15]: https://www.arubanetworks.com/
[16]: https://www.arubanetworks.com/products/security/network-access-control/
[17]: https://www.networkworld.com/article/3560993/what-is-wi-fi-and-why-is-it-so-important.html
[18]: https://www.assaabloyglobalsolutions.com/en/
[19]: https://www.reactmobile.com/
[20]: https://www.networkworld.com/article/3230457/what-is-a-firewall-perimeter-stateful-inspection-next-generation.html
[21]: https://www.networkworld.com/article/3207567/what-is-hyperconvergence.html
[22]: https://www.jerrysfoods.com/
[23]: https://www.scalecomputing.com/
[24]: https://www.networkworld.com/article/3280991/what-is-nvme-and-how-is-it-changing-enterprise-storage.html
