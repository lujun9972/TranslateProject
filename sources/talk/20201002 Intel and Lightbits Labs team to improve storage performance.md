[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Intel and Lightbits Labs team to improve storage performance)
[#]: via: (https://www.networkworld.com/article/3584409/intel-and-lightbits-labs-team-to-improve-storage-performance.html)
[#]: author: (Andy Patrizio https://www.networkworld.com/author/Andy-Patrizio/)

Intel and Lightbits Labs team to improve storage performance
======
The collaboration is designed to speed up Lightbits NVMe/TCP storage, reducing enterprise reliance on Fibre Channel and improving storage hardware utilization.
[Quest Software][1]

Intel has partnered with Lightbits Labs, as well as taken a financial stake in the startup, to improve the performance of storage systems in data centers. The two companies plan to develop disaggregated storage solutions designed to reduce the total cost of ownership (TCO) in storage systems due to extraneous hardware and "stranded disk capacity."

Stranded disk capacity refers to storage that has been allocated but is unused or unavailable for use by applications for any number of reasons, including problems with a connection. The result is that storage systems are burning electricity but not being used.

**READ MORE:** [NVMe over Fabrics creates data-center storage disruption][2]

Another way Lightbits aims to improve TCO is by eliminating the need for specialized hardware. Lightbits is the developer of LightOS [NVMe][3] over Fabrics TCP (NVMe-oF/TCP), a software-defined block storage platform that pools NVMe storage across multiple storage devices via TCP/IP networking rather than more expensive specialized storage networking gear such as Fibre Channel.

Intel is probably not the first name you think of when it comes to storage, but it has many products in that market. The company claims that LightOS, while being fully optimized for Intel hardware, will give customers improved storage efficiency, reduce underutilization, and maintain compatibility with existing infrastructure without compromising performance.

"The data center is being transformed, with disaggregation and composability of resources being essential to meet the efficiency requirements needed to address the explosion of data," said Remi EL-Ouazzane, vice president and data platforms group chief strategy &amp; business development officer at Intel, in a statement. "Our differentiated hardware capabilities coupled with Lightbits innovative NVMe over Fabrics software gives our joint customers an exceptional economic solution to address this strategic inflection point."

The LightOS storage solution has been tested with Intel's Ethernet 800 network adapter series with Application Device Queues (ADQ), which is designed to achieve faster, more predictable Ethernet.

ADQ enables NVMe-oF/TCP to achieve distributed storage performance in the same range as RDMA-based protocols, while NVMe-oF/TCP enables broad adoption because of its ease of deployment and scalability. Intel says LightOS with ADQ on the Ethernet 800 card shows up to 30% improvement in response time predictability as measured by P99.99 tail latency, up to 50% reduction in average latency, and up to 70% throughput increase as measured in IOPS when using ADQ vs. without ADQ.

In addition to the Intel Ethernet adapter, LightOS will also be tuned to work with Intel's Optane memory persistent storage and 3D NAND SSDs based on QLC, as well as Intel Xeon processors.

Intel also is investing in Lightbits Labs, but it did not disclose the financial details of its investment.

Join the Network World communities on [Facebook][4] and [LinkedIn][5] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3584409/intel-and-lightbits-labs-team-to-improve-storage-performance.html

作者：[Andy Patrizio][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Andy-Patrizio/
[b]: https://github.com/lujun9972
[1]: https://www.quest.com/whitepaper/storage-switzerland-paper-on-qorestor8134538/
[2]: https://www.networkworld.com/article/3394296/nvme-over-fabrics-creates-data-center-storage-disruption.html
[3]: https://www.networkworld.com/article/3280991/what-is-nvme-and-how-is-it-changing-enterprise-storage.html
[4]: https://www.facebook.com/NetworkWorld/
[5]: https://www.linkedin.com/company/network-world
