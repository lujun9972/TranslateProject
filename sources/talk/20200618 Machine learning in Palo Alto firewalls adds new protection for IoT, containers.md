[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Machine learning in Palo Alto firewalls adds new protection for IoT, containers)
[#]: via: (https://www.networkworld.com/article/3562705/machine-learning-in-palo-alto-firewalls-adds-new-protection-for-iot-containers.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

Machine learning in Palo Alto firewalls adds new protection for IoT, containers
======
With machine learning added to Palo Alto Networks' PAN-OS firewall operating system, the firewalls are better equipped to defend IoT devices and containers, whether on-prem or in the cloud.
Matejmo / Getty Images

Palo Alto Networks has released [next-generation firewall (NGFW)][1] software that integrates machine learning to help protect enterprise traffic to and from [hybrid clouds][2], [IoT][3] devices and the growing numbers of remote workers.

The machine learning is built into the latest version of Palo Alto's firewall operating system – PAN 10.0 –  to prevent real-time signatureless attacks and to quickly identify new devices – in particular  IoT products – with behavior-based identification.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][4]

NGFWs include traditional firewall protections like stateful packet inspection but add advanced security judgments based on application, user and content.

“Security attacks are continually morphing at rapid pace and traditional signature-based security approaches cannot keep up with the millions of new devices, running a variety of operating systems and software stacks coming on the network,” said Anand Oswal senior vice president and GM at Palo Alto. “IoT devices, which are growing exponentially, exacerbated that issue because they have so many of their own different agents, patches and OS’s it’s impossible to set security policies around them.”

Oswal said the ML in its new NGFW uses inline machine-learning models to identify variants of known attacks as well as many unknown cyberthreats  to prevent up to 95% of zero-day malware in real time. As it collects telemetry information from the network and combines it with existing Palo Alto data, the firewall can learn behaviors, recognize trends and recommend appropriate security policies, Oswal said.

In addition, PAN 10.0 features over 70 new features, including the ability to more fully deploy decryption, prevent DNS attacks and support Transportation Layer Security 1.3.

Supporting ML is key to staying ahead of the threat curve, experts said.

“It is very important for us to apply ML when you start collecting huge amounts of data about your network,” said Sreeni Kancharla, vice president and CISO of Cadence Design Systems, an electronic design-automation software and engineering-services company speaking at the Palo Alto PAN 10 introduction. It’s important to get a faster response time to threats without making the security environment more complex, Kancharla said.

### Support for IoT security

On the IoT front PAN 10.0 supports a subscription service that targets IoT systems.

“IoT devices present unique challenges for security teams. They are connected to an enterprise’s central network, yet they are generally unmanaged,” Oswal said. “For the most part, they are also unregulated, shipped with unknown or unpatched vulnerabilities, and often their useful life exceeds their supported life.”

Oswal noted that a recent [Palo Alto Unit 42][5] IoT threat report that said 57% of IoT devices are vulnerable to medium- or high-severity attacks, and 98% of all IoT-device traffic is unencrypted. Unit 42 is the vendor’s threat-research arm.

The IoT service is based on cloud-based IoT discovery, identity and security technology Palo Alto bought with [Zingbox][6] last year for $75 million. 

“We have enhanced Zingbox’s technology with Palo Alto Networks App-ID technology [which identifies applications traversing the firewalls], letting it automatically discover new IoT devices, assess risks and convert the learnings into policies that secure IoT,” Oswal said. 

### Protecting Kubernetes

PAN 10.0 also hones in on protecting another hot enterprise technology – Kubernetes containers.  A containerized version of the NGFW called the CN Series, is aimed at protecting container-based resources.

According to Palo Alto, the package includes container-protection technologies acquired from Twistlock, and microsegmentation capabilities from Aporeto. The CN Series offers Layer 7 visibility into container traffic and offers vulnerability protection to inbound, east-west and outbound traffic. In addition, URL filtering can be used to prevent cloud-native applications from connecting to potentially malicious websites or code repositories. 

CN-Series can deliver NGFW protection no matter where apps are hosted.

In an on-prem data center, this can be Kubernetes or Red Hat OpenShift. In a public cloud, protection includes Kubernetes and Red Hat OpenShift, but also Google Kubernetes Engine (GKE), Azure Kubernetes Service (AKS), and  Amazon’s Elastic Kubernetes Service (EKS), according to Palo Alto.

PAN-OS version 10.0 is expected to be available in mid-July and can be delivered as software, an appliance or a cloud service.  It is also part of Palo Alto’s overarching cloud-based security package, Prisma, which includes access control, advanced threat protection, user behavior monitoring and other services that promise to protect enterprise applications and resources.

Join the Network World communities on [Facebook][7] and [LinkedIn][8] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3562705/machine-learning-in-palo-alto-firewalls-adds-new-protection-for-iot-containers.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3230457/what-is-a-firewall-perimeter-stateful-inspection-next-generation.html
[2]: https://www.networkworld.com/article/3233132/what-is-hybrid-cloud-computing.html
[3]: https://www.networkworld.com/article/3207535/what-is-iot-the-internet-of-things-explained.html
[4]: https://www.networkworld.com/newsletters/signup.html
[5]: https://unit42.paloaltonetworks.com/iot-threat-report-2020/
[6]: https://www.networkworld.com/article/3168044/zingbox-launhces-iot-protection-for-business.html
[7]: https://www.facebook.com/NetworkWorld/
[8]: https://www.linkedin.com/company/network-world
