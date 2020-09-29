[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Streaming telemetry challenges SNMP in large, complex networks)
[#]: via: (https://www.networkworld.com/article/3575837/streaming-telemetry-gains-interest-as-snmp-reliance-fades.html)
[#]: author: (John Edwards )

Streaming telemetry challenges SNMP in large, complex networks
======
As big, complicated enterprises seek more efficient ways to monitor and troubleshoot their networks, a growing number are looking to streaming network telemetry
Gremlin / Getty Images

Network telemetry is far from new, but its importance is growing as data volume and network size relentlessly snowball. Streaming network telemetry gathers operational data from various network devices, combines the information, and then forwards it for inspection and study.

Growing scale and the increasing use of automation in next-generation enterprise networks require a modern, more efficient approach to network data capture and analytics, says Bo Lane, vice president of global engineering for [Kudelski Security][1], a cybersecurity technology provider. "Streaming telemetry allows enterprises to track network state, identify network problems and optimize network performance," Lane says. "In modern software-defined networks, problems or bottlenecks may be identified and autonomously remediated in near-real time."

**READ MORE:** [4 essential edge-computing use cases][2]

Streaming telemetry uses a push-based mechanism that allows data to be transmitted automatically and continuously from various remote sources, such as routers, switches or firewalls, to one or more centralized platforms for storage and analysis using formats such as XML, JSON and Protocol Buffers.

In contrast, SNMP and other methods are pull-based, meaning they only get information from a device when it's requested. Gaps in the frequency of asking for this data can hinder problem detection. "Streaming telemetry has the advantage of generating a real-time flow of high-resolution data that not only can help detect problems early, but also can generate actionable network intelligence to optimize network performance," says Justin Ryburn, head of global engineering at [Kentik][3], a network intelligence platform developer.

The variety and volume of metrics that network devices can now generate are increasing, and streaming telemetry offers a means to improve how that data is collected and shared, Ryburn says. An enterprise-class telemetry architecture addresses issues such as security, scaling, polling gaps, and resource utilization of polled devices to safeguard the sending and receiving of streaming telemetry data.

The granular data provided by streaming telemetry opens the door to greatly improved visibility. "When you combine the network data with additional data pulled from application and business systems, you get a much deeper insight into understanding the impact of network issues on the business and a faster, more automated way to respond to them," says Charles Nebolsky, global network practice lead at [Accenture Technology Services][4].

Clear visibility into the network to reveal the root causes of delays, developing threats and the impact of new business applications and exchanges is essential not only for the success of the networking group but the entire enterprise, says Mark Leary, network analytics research director at technology research firm [IDC][5]. "Telemetry boosts visibility, and it does so across the IT organization—from NetOps to SecOps to DevOps to AIOps," he says.

### Streaming network telemetry vs. SNMP

For many years, SNMP has served as the go-to method for enterprise network monitoring. Yet SNMP has also long been dogged by a series of flaws and shortcomings, including limited filtering and data retrieval options, unreliable transport, and inconsistent encoding between versions.

Streaming telemetry is viewed by most observers as a more efficient data-transfer method that imposes a lower network load. "It's considered more secure than SNMP, which is rather weak on authentication," says Shamus McGillicuddy, vice president of research at IT research and consulting firm [Enterprise Management Associates][6]. Streaming telemetry also enables more reliable data collection. "SNMP packet drops are a frequent problem, impacting visibility," McGillicuddy says.

A key difference between SNMP and streaming telemetry is the method of data collection.

SNMP polls network devices to collect information or set configuration properties. The approach, while generally reliable, can also lead to delays as long as five to 10 minutes before information is received from a device—veritable eons in today's networks. Streaming telemetry flips and streamlines the process. Instead of the pull model used by SNMP, streaming telemetry uses a push model to continuously stream data from network devices to one or more network monitoring systems.

Streaming telemetry packages data straight from the device into YANG (Yet Another Next Generation), an IETF standards based-model, making it easier to aggregate devices across complex systems into a useful picture of the state of IT infrastructure, says John Annand, research director for [Info-Tech Research Group][7].

"Simply put, streaming telemetry offers a closer-to-real-time view that contains fewer misleading artifacts, which are the result of the very act of monitoring," Annand says. SNMP polling data doesn't always arrive at the monitoring system in the same order it was requested from the target system. "This is due to network lag and a lack of timestamp on the data when it leaves the network element," Annan explains. "The result is that the monitoring data, when presented in a time series, can have odd blips that require significant creative interpretation to correctly understand."

SNMP-based monitoring, by its mere existence, has the potential to impact—usually in a bad way—the network element being observed. "You can actually induce and observe poor performance of an element with improper SNMP usage," Annand says. "The result ... would be a false positive, kicking off an investigation about faulty configuration or hardware when the true root cause was the poor attempt to monitor the device in the first place."

Another problem with SNMP is that it generally runs on the CPU located inside the switch, router or other network device, slowing performance. "In streaming telemetry, the ability to collect data happens at a lower level, off the CPU, basically, and on the ASICs, on the switching fabric, on the switching chips and so forth," explains Mike Fratto, a senior analyst at [S&amp;P Global Market Intelligence][8]. As a result, there's no impact to the CPU during data collection. "All the CPU has to do at that point is package [the data] up and spit it out," Fratto says.

SNMP's viability has been questioned by enterprise network vendors and users for nearly a decade. Microsoft dealt the first crippling blow to SNMP in 2012, when it stopped supporting the technology for server monitoring, Annand says. By 2016, Cisco, Juniper Networks and other top network players began discussing telemetry as a serious successor to SNMP. Google, meanwhile, pronounced SNMP dead in 2018, Annand says.

Today's enterprise network environment has become far less homogenous over the past few years. "There are too many black boxes for SNMP to be effective," Annand says.

An explosion in the number of IoT devices has also eroded SNMP's usefulness. "Manufacturing and energy sector IoT deployments scale out to tens or hundreds of thousands of devices very quickly," he says. "SNMP wasn't designed for that scale."

Further depleting SNMP's value is the fact there's a significant amount of useful data tucked into many existing infrastructure assets that the aging protocol simply doesn't support. "No one wants to build a single-purpose object-identifier (OID), but structured data is the heart blood of DevOps, and streaming telemetry uses those same data models," Annand says.

### Telemetry standardization remains nascent

By now, virtually all major network vendors have announced at least some type of streaming telemetry capability. Cisco, Juniper Networks and [Arista][9] all support streaming telemetry, McGillicuddy notes. "Cisco primarily enables it in custom ASICs to stream data at very high levels of granularity," he says. Additional vendors, notably Arista, execute the capability primarily in software on commercial silicon. "Many other vendors, including some of the open networking software vendors, like [Arrcus][10] and [Kaloom][11], also support streaming telemetry," McGillicuddy says.

The problem is, streaming telemetry standards efforts are numerous and "a bit disjointed" at this point, with select camps focusing on certain pieces to the puzzle, Leary says. Cisco and Juniper, for example, are following separate model paths for telemetry collection services. "Cisco for Pipeline; Juniper for OpenNTI," he notes.

Any way you look at it, telemetry standardization remains nascent at this point. Most implementations are proprietary, McGillicuddy says, but use standard protocols like NETCONF and gRPC for data transport. "Many implementations also comply with the pseudo-standard defined by [OpenConfig][12], an informal working group formed by engineers from web giants and hyperscale companies, such as Google and Facebook," he reports.

Meanwhile, despite streaming telemetry's many advantages, SNMP isn't showing any signs of imminent death. "There are plenty of use cases where SNMP is fully sufficient for the business objectives and network operation needs," Annand says. "Justifying the effort required to switch would be "more art than science," he notes. "As those systems naturally lifecycle out, so too will the SNMP use cases dry up—but that's a longer process."

In any event, SNMP isn't robust enough for systems that enterprise IT doesn't fully own, Annand contends. "You generally can't get SNMP data from as-a-service or external elements, he notes. "Even in the best case, you end up with a piecemeal solution with different visibilities from different elements."

SNMP is also not fast enough for "real-time" response required of most modern systems. For example, if a device were polled once every5 minutes to see if it was up, it could be down for 4 out of those 5 minutes every interval, but the report would say 100% system health.

Despite its shortcomings, SNMP remains a mainstay in many network management and monitoring systems, as well as in numerous infrastructure monitoring environments, Fratto says. "SNMP will still be used for a long time," he says.

McGillicuddy says his organization's research reveals that 71% percent of network managers are interested in using streaming telemetry. "But more than two-thirds of those who are interested in the technology told us they expect to use streaming telemetry to complement SNMP," he states. "They do not have plans to eliminate SNMP from their networks."

The same holds true for most network giants. "Google and several other high-profile companies have publicly stated that they would like to eliminate SNMP from their networks, but mainstream companies are not moving in that direction—at least for now," McGillicuddy says.

While SNMP was never able to live up to its anticipated potential, streaming telemetry is raising the bar. "Management of network assets was accomplished more by proprietary vendor command line than an open management and configuration protocol," Annand says. "Streaming telemetry is the chance for a modern approach and to laser focus on just one thing: visibility."

Streaming telemetry will continue to grow in popularity, McGillicuddy predicts. "Network managers should be asking their network management tool vendors what plans they have in this area," he says. "It's not essential to have it now, but in a few years, I think it will be quite mainstream.”

Join the Network World communities on [Facebook][13] and [LinkedIn][14] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3575837/streaming-telemetry-gains-interest-as-snmp-reliance-fades.html

作者：[John Edwards][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.kudelskisecurity.com/
[2]: https://www.networkworld.com/article/3573587/4-essential-edge-computing-use-cases.html
[3]: https://www.kentik.com/
[4]: https://www.accenture.com/us-en/about/technology-index
[5]: https://www.idc.com/
[6]: https://www.enterprisemanagement.com/
[7]: https://www.infotech.com/
[8]: https://www.spglobal.com/marketintelligence/en/
[9]: https://www.arista.com/en/
[10]: https://www.arrcus.com/
[11]: https://www.kaloom.com/
[12]: https://openconfig.net/
[13]: https://www.facebook.com/NetworkWorld/
[14]: https://www.linkedin.com/company/network-world
