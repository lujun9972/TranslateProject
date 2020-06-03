[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Building a Managed SD-WAN Service Starts with Selecting the Right Solution)
[#]: via: (https://www.networkworld.com/article/3546342/building-a-managed-sd-wan-service-starts-with-selecting-the-right-solution.html)
[#]: author: (Nirav Shah )

Building a Managed SD-WAN Service Starts with Selecting the Right Solution
======

iStock

The need for [SD-WAN][1] is a foregone conclusion. The need for fast and reliable access to applications and critical resources by all users is essential for competing in today’s digital marketplace. As a result, many organizations are now at a crossroads in their decision to implement SD-WAN. For most, it is not a question of if, but how. Should they jump in and build a solution themselves, or wait for a managed service provider to offer a service?

### The challenges of early adopters

Early adopters, while lauding the benefits of an SD-WAN strategy, quickly ran into a number of critical challenges early on. Implementing an SD-WAN solution isn’t always as easy as it looks. SD-WAN solutions designed for one use case, say, connecting branch offices located in a specific metro area, don’t always translate to other use cases, such as then trying to support a global deployment.

But the biggest problem was how to secure these new, highly dynamic connections. Traditional traffic routed through an MPLS and WAN router configuration receives all of the security inspection and protection provided by the core network. But that all disappears when a branch office connects directly to cloud and internet services. And once an organization realizes that the basic VPN and firewall that came with their new SD-WAN device will not be able to adequately protect critical data and applications, they are forced to build – and try to deploy – an overlay security solution. Selecting, integrating, and deploying a security solution that not only provides a full stack of protection, but that is also agile enough to keep up with dynamically changing connections, is not only expensive upfront but also requires significant overhead throughout its life cycle.

### The need for a managed SD-WAN solution

Those smart enough to see these challenges are increasingly turning to managed services partners to solve the problem for them. This is why SD-WAN has one of the fastest predicted annual growth rates of any solution for managed services providers. [According][2] to Gartner, managed SD-WAN services are expected to grow at an astounding 76% CAGR through 2023.

However, there is still a lot of churn in the vendor space as a growing number of solutions compete for market share. Some only offer a limited set of functions or only support very narrow use cases. Others rely on complex systems of cloud-based connectors to enable access to applications. Most do not offer any sort of integrated security solution. And far too many are unlikely to still be around in a year or so, either due to acquisition, consolidation of the marketplace, or simply because they will have had to close their doors.

### Selecting an SD-WAN vendor

This makes it especially crucial that MSPs have a specific strategy for their managed SD-WAN offering, including any value-add services they would like to provide as a market differentiator. And that they carefully analyze all potential SD-WAN partners they may consider building a new managed service around.

_**APIs and standards**_

One key consideration is to prioritize those vendors that have invested in the development and adoption of open APIs and adherence to critical standards and certifications around security and interoperability. MEF (Metro Ethernet Forum), with a membership that currently includes over 130 service providers worldwide as well as vendor partners, provides industry guidance and standards bodies that define the interoperability standards that need to be implemented.

These standards not only ensure reliable connectivity and security functionality within an SD-WAN solution, but also enable service providers to build hooks between SD-WAN solutions and their orchestration and automated workflow services, as well as connections into devices for enhanced management, configuration, and coordination. They also need these solutions to support a wide range of transport options, including broadband, MPLS, and LTE/4G/5G.

_**Performance and cloud on-ramp**_

Another critical consideration is performance. [SD-WAN solutions][1] use a variety of strategies to ensure high-speed access to SaaS applications and multi-cloud resources. The most common is to embed controllers in the cloud that all of their SD-WAN devices connect to. This controller identifies the application being used and then searches for the optimum path to its location in the cloud. Because traditional network management tools, such as BGP, are unable to identify and direct applications around congested traffic, this optimum path almost always involves connecting to a third-party POP. This cloud on-ramp function moves traffic onto a private, fiber optic network backbone directly connected to all major cloud providers.

The problem is that this extra hop between the MSP’s co-location site and the on-ramp POP in the cloud can introduce time delays and latency into a process where application delivery and SLAs are measured in microseconds. MSPs are much better served selecting a solution where the controller is embedded in the SD-WAN device itself rather than out in the cloud.

_**Security**_

But the biggest issue for MSPs, as well as for their clients, is security. In a recent survey conducted by [MEF][3], security was the number one value-add service wanted by managed service providers. However, they face the same challenges that enterprises face when trying to implement security as an overlay. The underlying SD-WAN functionality is too dynamic for most security solutions, which means they are often functioning in a perpetual state of trying to catch up. The security implications are obvious.

Another challenge is that most security devices function as independent siloes, which can make it very difficult to integrate them into the MSP’s environment, let alone into the SD-WAN device. And they are slow. Most network security devices designed using traditional hardware cannot keep up with the demands of today's applications – especially those that provide rich streaming services such as teleconferencing.

As a result, MSPs need to build their service around an SD-WAN device that has already integrated a full stack of enterprise-class security into its core functionality. And the management interface used to control both connectivity and security also needs to scale across multiple devices, as well as be SP-ready by providing tiered support for clients who want a hybrid management solution right out of the box.

### The best solutions start with the right partners

As professionals in this space already know, the key to launching a successful managed service is to start with a solution that already contains all of the elements that their customers need. It also needs to be easily integrated into their existing managed services environment to reduce the ratio of engineers to customers. And it needs to provide reliability, functionality, and performance so that SLAs can be guaranteed. And perhaps most importantly, it has been designed by a vendor that already understands how to sustain and support an MSP partner.

_Take a security-driven approach to networking to improve user experience and simplify operations at the WAN edge with _[_Fortinet’s Secure SD-WAN_][4]_ solution._

_Read these customer case studies to see how _[_De Heus_][5]_ and _[_Burger King Brazil_][6]_ implemented Fortinet’s Secure SD-WAN to alleviate network complexity, increase bandwidth, and reduce security costs._

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3546342/building-a-managed-sd-wan-service-starts-with-selecting-the-right-solution.html

作者：[Nirav Shah][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.fortinet.com/products/sd-wan.html?utm_source=pr&utm_campaign=2019-q3-sd-wan
[2]: https://www.gartner.com/teamsiteanalytics/servePDF?g=/imagesrv/media-products/pdf/fortinet/fortinet-1-5VG5OU4.pdf
[3]: https://img.lightreading.com/downloads/SDWan-Strategies-Survey-Report-2019.pdf?p_redirone=yes&piddl_promo=2239
[4]: https://www.fortinet.com/products/sd-wan.html?utm_source=blog&utm_campaign=2018-q2-sd-wan-web
[5]: https://www.fortinet.com/customers/deheus.html
[6]: https://www.fortinet.com/customers/burger-king.html
