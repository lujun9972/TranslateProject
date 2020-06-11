[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Huawei iBMC Supercharges Intelligent Management of Servers)
[#]: via: (https://www.networkworld.com/article/3562369/huawei-ibmc-supercharges-intelligent-management-of-servers.html)
[#]: author: (Written by Huawei )

Huawei iBMC Supercharges Intelligent Management of Servers
======

iStock

A server is a high-performance computer that provides external services in a network environment. To provide quality services, servers need to deliver and maintain high performance for a long time using effective management. Currently, most mainstream servers run on the x86 architecture, but more people are realizing that a single architecture fails to meet today’s soaring computing requirements. With more enterprises accelerating their digital transformation, the demand for computing power is higher than ever, and this trend is generating tremendous market activity.

According to IDC, the global market space of computing power in 2016 was 9.5 million servers, and this figure is estimated to reach 14.2 million by 2023. When tens of thousands of high-performance servers are deployed in data centers, conventional manual maintenance cannot detect and resolve issues in a timely manner. As a result, it is imperative for enterprises to achieve efficient and intelligent O&amp;M management for their mass cloud-based services. This has impacted the server industry, which in recent years has undergone huge changes. High performance and low cost are no longer the only concerns for enterprises. Instead, enterprises are also looking to intelligent and efficient device O&amp;M to ease pressure on O&amp;M personnel and reduce running costs.

Throughout the lifecycle of a server—starting from deployment, O&amp;M and upgrade management, fault prevention and diagnosis, to intelligent energy saving and security management—the Huawei-proprietary Intelligent Baseboard Management Controller (iBMC) plays a key role, ensuring continuous and stable services at a lower cost. As a basis for cluster and cloud management, the iBMC is an independent out-of-band management system that contributes to the energy saving and device O&amp;M in data centers. The iBMC supports various industry protocols and interfaces that implement basic system management functions, such as local and remote diagnosis, remote console, configuration management, hardware management, and troubleshooting.

Starting in 2002 originally to fill the demand in the carrier industry, the Huawei server business line has expanded its scope to new, more demanding industries. In 2008, the Huawei server debuted in the Internet industry, and has provided services for enterprises worldwide since 2012. Thanks to the past 18 years' experience, Huawei has innovated a wide range of server technologies and products, including the engineering, architecture, application solution, and management software. Now let's take a deeper look at the iBMC.

  * **Multiple remote management tools**



The iBMC supports server deployment, configuration, and upgrade using multiple remote management tools, such as the Kernel-based Virtual Machine (KVM), SOL, virtual media, and web access. More importantly, the iBMC achieves zero-touch O&amp;M, addressing a prominent pain point of the industry.

Huawei

Figure 1 Various remote management tools

The iBMC offers a wide variety of remote O&amp;M tools and capabilities that allow O&amp;M personnel to access to servers anytime, anywhere, for any operation, such as configuration, upgrade, and alarm handling.

  * **Mainstream management protocols and software**



The Huawei iBMC complies with IPMI 1.5/2.0, SNMP, and Redfish protocols, and is compatible with mainstream management software, allowing enterprises to integrate different interfaces into their servers for automatic and intelligent management.

Huawei

Figure 2 Mainstream management protocols and software

The iBMC provides various user interfaces, such as the CLI, web-based user interface, IPMI integration interface, SNMP integration interface, and Redfish integration interface. All user interfaces adopt the authentication mechanism and high-security encryption algorithm to enhance access and transmission security.

  * **Intelligent fault diagnosis and management**



The Huawei Fault Diagnosis &amp; Management (FDM) is an in-house developed set of diagnosis technologies and tools that monitor the health of hardware devices. It is embedded in the iBMC by default and provides intelligent and precise fault diagnosis independent of the operating system, ensuring system stability and reliability.

Huawei

Figure 3 Comprehensive fault diagnosis and management

The FDM supports the in-depth fault diagnosis and generates alarms for key server components, such as CPUs, DIMMs, drives, buses, and PSUs on motherboard and card. It can also predict a fault, such as system breakdown, 7 to 30 days in advance, with a fault locating accuracy of up to 93%.

In addition to the automatic fault diagnosis, the FDM provides a great variety of functions that assist O&amp;M personnel in fault analysis and locating, such as breakdown video recording, screen video recording and snapshot, fault reporting, black box, and serial port data recording. The technology perfectly combines manual and intelligent fault diagnosis, helping O&amp;M personnel to determine the fault cause and provide targeted solutions, thereby preventing the same fault in the future.

  * **Intelligent energy saving technology**



Based on the input parameters such as the CPU load and ambient temperature, the Huawei-patented Dynamic Energy Management Technology (DEMT) intelligently adjusts the power consumption of each component in real time, helping a single server consume 15% less power without compromising its performance. The DEMT boasts three highlight technologies: frequency modulation and hibernation, Proportional Integral and Differential (PID), and Digital Thermal Sensor 2.0 (DTS 2.0).

  * Frequency modulation and hibernation: adjusts the running status of core components based on service loads.
  * PID: quickly adjusts the fan module speed according to the CPU temperature, reducing power consumption loss caused by misplaced adaptation.
  * DTS 2.0: uses the margin relationship between CPU performance and temperature to control the fan module speed within the margin range, reducing the power consumption of the entire server.
  * **Ultimate energy efficiency in tests**



Huawei FusionServer series has proven to offer high performance and ultimate energy efficiency in authoritative tests, such as the SPECpower-ssj2008, designed to measure the server energy efficiency, and specifically that of unit power consumption. The Huawei FusionServer Pro V5 series servers running on the DEMT have broken the world record of the SPEC energy consumption test multiple times.

For example, in 2018, the Huawei FusionServer Pro 2288H V5 scored 13,398 to rank No. 1 in the SPECpower-ssj2008 test for 2-socket servers.

Huawei

Figure 4 SPECpower-ssj2008 test data in April 2018 [http://www.spec.org][1]

To show the strength of the series instead of individual products, another FusionServer product, the Pro 1288H V5, scored 14,209 to top the 2019 SPECpower-ssj2008 test for 2-socket servers.

Huawei

Figure 5 SPECpower-ssj2008 test data in April 2019 <http://www.spec.org>

Current data suggests that power costs account for half of the OPEX of a data center. As a result, customers across industries are looking for ways to add green computing power to fuel their services. Huawei is an enterprise that focuses on answering industry pain points. Huawei servers are equipped with state-of-the-art energy saving technologies to unleash superior computing at a lower power consumption, making them a must in this digital age.

  * **Security protection at three layers**



The iBMC ensures the management system security at the hardware, data, and access layers. Specifically, the security is enhanced using the protection, monitoring, and recovery security mechanisms.

Huawei

Figure 6 Security protection at three layers

The Huawei iBMC harnesses the carrier-grade firmware dual-image backup technology to improve system reliability. For example, in the event of a flash misoperation or damaged storage blocks, the system automatically switches to the backup image to ensure continuous operations. Meanwhile, an alarm is generated, indicating that the original active image changes to the standby one.

Data centers with solid device management can supercharge their everyday business operations. What are normally manual, time-consuming operations, such as device deployment and fault locating and diagnosis, are now automated, accelerated, and enhanced. Digital O&amp;M offers near-perfect fault prediction, low power consumption, and minimized O&amp;M costs, making it essential for any enterprise running huge data volumes. Huawei servers are fueled by the self-developed management chip and intelligent iBMC management system, and these technologies have propelled Huawei as a major player of competitive computing platforms. Looking forward, Huawei will continue to innovate and collate premium technologies designed to make intelligent, simple computing.

[Learn more][2] about FusionServer Pro.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3562369/huawei-ibmc-supercharges-intelligent-management-of-servers.html

作者：[Written by Huawei][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: http://www.spec.org/
[2]: https://e.huawei.com/topic/fusion-server/en/index.html?utm_campaign=4MHQHQ20W6V1N&utm_medium=pm-display&utm_source=google&source=SEM&utm_object=NA&utm_content=FSP
