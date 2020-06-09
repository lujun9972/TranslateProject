[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Huawei Helps Innovate Server Value with BSST)
[#]: via: (https://www.networkworld.com/article/3561759/huawei-helps-innovate-server-value-with-bsst.html)
[#]: author: (Written by Huawei )

Huawei Helps Innovate Server Value with BSST
======

Huawei

In terms of operating system acceleration, low-capacity boot storage media have evolved from USB flash drive to SD card, to SATADOM, and to M.2 SSD. Serial Advanced Technology Attachment (SATA) interface-based M.2 solid-state drives (SSDs) feature mature storage technologies, high reliability, high speed, and wide application support. In a scenario where the capacity of a boot disk is low, an M.2 SSD that occupies less space can be used to increase the server space, especially the storage space (for example, two 2.5-inch or 3.5-inch hard drive slots can be added). In addition, M.2 SSDs do not use power cables, simplifying cabling design. Therefore, the M.2 SSD is very suitable for installing an OS.

A current trend among enterprises is to separate the OS boot disk from the data disks and use hardware Redundant Array of Independent Disks (RAIDs) mirroring (RAID 1) for their services. This is especially applicable to those deploying new services oriented to hyper-converged infrastructure (HCI) and software-defined storage (SDS). Although this type of RAID architecture offers high OS reliability, it is not perfect without a solid system in place. The Huawei FusionServer Pro V5 server introduces new Boot Speedup Storage Technology (BSST). This technology enables independent deployment of the OS and data on the server in a simpler, more economical, and more reliable manner.

The Huawei BSST technology is equipped with a RAID controller card within a PCIe card to support two M.2 SSDs with SATA 3.0 ports. The BSST works in either pass-through or RAID group (RAID 0/1) modes, implementing fault-tolerant data storage for supercharged system performance. It supports data storage in multiple hard drive partitions and read/write operations on multiple hard drives at the same time, helping to slash data access delays.

Huawei

_Figure 1 Huawei BSST (dual M.2 SSDs supporting hardware RAID and hot plug)_

In a conventional deployment, an M.2 SSD is connected to a connector parallel to the motherboard, and the other end of the connector is secured to the card using a screw. This design is simple and inexpensive; however, it is inconvenient for most environments because users need to stop services and power off the server before replacing a component, greatly impacting system availability and O&amp;M efficiency.

Huawei prides itself on the ability to find a technology for common industry pain points. For this scenario, Huawei provides the BSST technology using the PCIe card in the standard PCIe slot of server. By setting the two M.2 SSDs to the hardware RAID 1 mirroring mode before installing the OS, the SSDs can store and back up OS data synchronously, improving the reliability of boot disk data. More importantly, Huawei BSST supports the industry-unique hot plug function. In the event that one SSD needs to be replaced, you can easily remove and replace it without shutting down the system or cutting off the power supply. This improves the system disaster recovery capability, scalability, and flexibility, and slashes the unplanned downtime.

Effective management and real-time monitoring are crucial to those deploying M.2 SSDs in their system. Huawei intelligent Baseboard Management Controller (iBMC) is management software that interacts with the RAID controller card to run out-of-band management for SSDs. This means iBMC can query and monitor the working status of the SSDs, RAID controller card, physical disks, and logical disks. In addition, it displays the disk capacity, online status, and remaining service life immediately in the event of an exception. To prevent any service interruption caused by SSD faults, iBMC provides an early warning function. When the remaining service life of an SSD is less than 5%, the iBMC generates a major alarm to instruct maintenance personnel to replace the SSD immediately. In this way, service faults can be avoided.

The modular design better supports more servers. Huawei BSST adopts common components to integrate multiple functions into a PCIe card that is decoupled from the entire system. The PCIe card as a common component can be installed on all Huawei FusionServer Pro intelligent servers. The BSST offers a wide range of capacity options of 32 GB, 64 GB, 240 GB and 480 GB, of which the latter two options are widely used due to their large capacity and solid reliability.

Over the past 18 years, Huawei has continuously invested in server technologies for technology and product innovation. Huawei is a technological enterprise that digs into customer and industry problems to provide products and solutions tailored to specific scenarios. According to the _ITIC 2018 Global Server Hardware, Server OS Reliability Report_, Huawei servers meet enterprise requirements by delivering 99.99% uptime and 99.999% availability.

Huawei

_Figure 2 Source:_ _ITIC 2018 Global Server Hardware, Server OS Reliability Report_

Huawei next-generation servers are designed to meet diversified enterprise requirements of green, better performance. They provide intelligent management and high energy efficiency to reduce O&amp;M costs.

[Learn more][1] about FusionServer Pro.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3561759/huawei-helps-innovate-server-value-with-bsst.html

作者：[Written by Huawei][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://e.huawei.com/topic/fusion-server/en/index.html?utm_campaign=4MHQHQ20W6V1N&utm_medium=pm-display&utm_source=google&source=SEM&utm_object=NA&utm_content=FSP
