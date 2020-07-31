[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Arista reinforces multi-cloud edge-networking software)
[#]: via: (https://www.networkworld.com/article/3569172/arista-reinforces-multi-cloud-edge-networking-software.html)
[#]: author: (Michael Cooney https://www.networkworld.com/author/Michael-Cooney/)

Arista reinforces multi-cloud edge-networking software
======
Arista has extended its CloudEOS software to ease cloud networking tasks.
Thinkstock

Arista has extended its connectivity software to better support [edge networking][1] with on-premises and [hybrid-cloud][2] resources.

The extensions enhance Arista's recently announced [CloudEOS software][3], which is meant to simplify cloud networking and let customers build and deploy applications faster.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][4]

In its initial form, CloudEOS included two components. The first, CloudEOS Multi Cloud, enables network connectivity to and between [private clouds][5] or public clouds. The package sets up a [virtual machine][6] and can redirect traffic across the most effective and efficient networking path using real-time topology data, in-band telemetry and other attributes, the company said. It also automatically encrypts all traffic on those paths.

The second package, CloudEOS Cloud Native, lets customers set up an instance of the network operating system in a Kubernetes container, offering a fully supported, enterprise-class networking stack within cloud-native environments.

CloudEOS can be set up and managed through Arista's [CloudVision][7] management software, which provides network-wide visibility, orchestration, provisioning and telemetry across the [data center][8] and campus. CloudVision's network information can be utilized by other Arista networking partners such as VMware, Microsoft and IBM's Red Hat.

To that product family, the company has now added CloudEOS Edge, new software that lets customers set up connectivity services to all major cloud providers at the network edge facing the internet, and multiple private and public carriers, such as Amazon Web Services, Microsoft Azure, and Google Cloud, according to Arista. 

"CloudEOS Edge standardizes enterprise edge connectivity into multi-region and multi-provider clouds, using open/standards-based protocols (VxLAN, BGP EVPN) for interoperability with native network services like AWS Transit Gateway, legacy WANs, and SD-WAN," said [Douglas Gourlay][9], Arista vice president and general manager of cloud-networking software.

"Additionally, CloudEOS implements dynamic path selection to select the best path for a given application based on real-time network performance (latency, throughput, drop rate) between a cloud provider region and the existing data center/campus/branch, whether it's going through Equinix Cloud Exchange, AWS Direct Connect, Azure Express Route, Google Cloud Interconnect or the public internet," Gourlay said.

CloudEOS Edge takes aim at the central challenges enterprises are facing with inter-connecting and monitoring networks running in multi-domain locations like data centers, campus, and public clouds, according to Gourlay. "The native network services from the cloud providers were never designed to interoperate across other cloud providers, [or to] understand provisioning, troubleshooting, and monitoring the networks in between," Gourlay said. **
**

Furthering that idea, CloudEOS Edge also integrates with AWS' Transit Gateway (TGW). According to AWS, the Transit Gateway is a service that lets customers connect their Amazon Virtual Private Clouds (VPC) and their on-premises networks to a single entryway to cloud resources. Transit Gateway acts as a hub that controls how traffic is routed among all the connected networks, Amazon stated.

CloudEOS Edge integration with TGW lets customers extend AWS TGW segmentation into Arista Cloud Network Private Segments in the data center, campus, and across multiple public clouds. And it enables AWS TGW with secure hybrid cloud, multi-cloud connectivity using Dynamic Path Selection with IPSec encryption. Customers can monitor TGW connectivity and traffic visibility with CloudVision, which has been upgraded to manage multicloud implementations, Gourlay said.

By supporting TGW, new virtual networks provisioned in Microsoft Azure and new VPCs provisioned in Google Cloud Platform can be immediately reachable from VPCs provisioned in AWS that are using AWS TGW as their primary inter-VPC connectivity fabric, Gourlay added.

In addition to setting up connectivity to multiple cloud services, CloudEOS lets customers set up a pay-as-you-go consumption of CloudEOS across AWS, Azure and Google Cloud.

CloudEOS is also now a [Terraform provider][10], which lets customers use software-defined provisioning for multi-cloud backbones through Hashicorp Terraform and Arista CloudVision.

Arista CloudEOS Edge and other enhancements are available now.

Join the Network World communities on [Facebook][11] and [LinkedIn][12] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3569172/arista-reinforces-multi-cloud-edge-networking-software.html

作者：[Michael Cooney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Michael-Cooney/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3224893/what-is-edge-computing-and-how-it-s-changing-the-network.html
[2]: https://www.networkworld.com/article/3233132/what-is-hybrid-cloud-computing.html
[3]: https://www.networkworld.com/article/3452357/arista-targets-cloud-networking-with-cloudeos-software-packages.html
[4]: https://www.networkworld.com/newsletters/signup.html
[5]: https://www.networkworld.com/article/2159885/cloud-computing-gartner-5-things-a-private-cloud-is-not.html
[6]: https://www.networkworld.com/article/3234795/what-is-virtualization-definition-virtual-machine-hypervisor.html
[7]: https://blogs.arista.com/blog/cloudvision-cognitive-management-plane
[8]: https://www.networkworld.com/article/3223692/what-is-a-data-centerhow-its-changed-and-what-you-need-to-know.html
[9]: https://www.linkedin.com/in/dgourlay/
[10]: https://www.terraform.io/docs/providers/index.html
[11]: https://www.facebook.com/NetworkWorld/
[12]: https://www.linkedin.com/company/network-world
