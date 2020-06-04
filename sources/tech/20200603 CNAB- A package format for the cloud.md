[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (CNAB: A package format for the cloud)
[#]: via: (https://www.linux.com/featured/cnab-a-package-format-for-the-cloud/)
[#]: author: (Linux.com Editorial Staff https://www.linux.com/author/linuxdotcom/)

CNAB: A package format for the cloud
======

_By [Matt Butcher][1], special to Linux.com_

### Introduction

Installing a new app on your phone is simple. So is installing one on your Mac, Linux box, or PC. It should be just as simple to install a distributed application into your cloud — this is the goal of the Cloud Native Application Bundles (CNAB) project. We believe we can achieve this goal without requiring another cloud service or tying the user to only one cloud provider.

Over the last few months, we have witnessed first-hand how much the cloud has to offer. As everything from our daily meetings to our kids’ classrooms has gone online, we are reminded daily of what a potent boon cloud technologies have become.

For those responsible for building and maintaining our cloud presence, we know that some formidable issues are not yet resolved. One of those is how we install, upgrade, and delete applications in the cloud. Using containers, a bit of JSON, and some best-of-breed security infrastructure, we have created a package management standard for the cloud.

### A Package Format for the Cloud

While the core cloud technologies like virtual machines and object storage have been around for over a decade, and a rich tapestry of cloud infrastructure exists, managing cloud applications remains a challenge. Two years ago, my team sat down and asked a straightforward question: Why is installing, upgrading, and deleting applications from the cloud is such a challenge? True, there are specific services (like PaaS) that make this manageable for a small segment of the ecosystem. But when it comes to a high-level solution, we are still left doing the orchestration of things either by hand or with bespoke tools.

This led us to one straightforward question:

_What if we could find a way to make package management work for the cloud the same way that it works for a local operating system?_

This domain was not entirely new ground for us. After all, we’d built the enormously successful Helm package manager for Kubernetes. But we were well aware that Helm is inextricably bound to Kubernetes. While we believe Kubernetes has many attractive features, we do not think it will replace the rest of the cloud landscape.

Enumerating the big features, we started to list things we would want to be able to do:

  *     * Install virtual machines
    * Set up object storage and cloud databases databases
    * Load containerized workloads onto clusters like Kubernetes, but perhaps not only Kubernetes
    * Manage virtual networks and resources like load balancers
    * Interoperate with policy and identity control tools
    * Make it possible and even easy for developers to introduce support for new services and tools



The list went on in a similar vein for a while. And then came the two killer features:

  *     * Make it extremely easy to use, just like a regular package manager.
    * Make it completely cloud-agnostic. It should run just as smoothly on Azure, AKS, on-prem OpenStack, and everything else.



The feature list was looking daunting until a rather elegant solution presented itself: Today’s packages are moved around in self-contained bundles of code and supporting resources. And then the host environment executes that bundle. What if we just used a Docker container as the primary package technology? In that case, we can reuse a considerable amount of cloud infrastructure, easily moving packages around–even across air-gapped boundaries.

This was the critical insight that became Cloud Native Application Bundles (CNAB). With Docker, Datadog, and Pivotal (before their acquisition by VMware), we wrote a specification that described how to build cloud-centric packages that are captured in Docker containers.

Initially announced at DockerCon EU in December of 2018, our combined team has continued to work on the specifications, build tools, and explore better ways of delivering an easy-to-use cloud packaging experience.

### Today’s Tools

Since our initial announcement of CNAB, Docker Apps has rolled CNAB into its production release. Microsoft has built Porter–an open source CNAB builder–and Datadog has led the charge on a CNAB security specification that provides not just a quick verification scheme, but deep software supply chain security.

Docker initially announced their CNAB support for Docker Apps with [a great architectural introduction][2]. At the end of last year, they explained how CNAB worked with application templates in [Docker Desktop][3]. For Docker, CNAB provides a convenient way to encapsulate applications built using core Docker technology, without requiring the user to learn yet another technology stack. And right now, the newly released Docker [Compose specification][4] is supported in Porter, providing a new avenue for integrating Docker’s excellent developer tooling with other cloud technologies.

Microsoft created the Porter project. We had already written a CNAB reference implementation (Duffle) designed to exercise the specification. But it was not necessarily designed to provide a great user experience. Porter, on the other hand, is a user-first design. Through mixins, Porter can support a vast range of cloud technologies, from Terraform to Helm to Docker Compose, making it easy to tailor a CNAB bundle to your preferred target cloud or technology stack.

Finally, thanks to the diligent work of Datadog, the CNAB group is preparing to publish a second specification: The CNAB Security 1.0 Specification. The initial security model for CNAB was designed alongside the core specification. But we wanted to make sure we did our due diligence. We have spent an extra year diving deeper into scenarios and vetting and collaborating popular security products so that it could be accomplished with existing solutions. 

Along with covering distribution security, this specification also provides a software supply chain security model. This means that from development through testing, and finally on into release, each step can be verified according to a robust security process. We believe CNAB represents a new generation of security tooling that reduces risk and increases the fidelity of cloud technologies.

### Tomorrow’s Goals

CNAB is designed to operate well in enterprise environments. And the CNAB group has two more standards in flight. We are eagerly pushing these toward completion.

One of CNAB’s target environments is the “disconnected cloud.” From physically remote environments, such as research stations and oil rigs, to secure compartmentalized facilities, cloud technologies provide a robust platform even when disconnected from the internet. CNAB is intended to work well in these environments as well. And this means that CNAB must have a robust “air gap” story.

From day one, this has been a goal. Over the last two years, we have refined our model, goals, and features to meet this scenario best. The core specification is written with air-gapped environments in mind, as is the security specification. But our third specification, the CNAB Registry 1.0 Specification, is the last puzzle piece.

This specification describes how CNAB bundles (packages) are stored, discovered, downloaded, and moved. Utilizing the OCI Registry standard, this specification describes how users and tools will share packages. But it also provides details on how bundles can be moved across network boundaries in a high-fidelity manner. With this specification, CNAB becomes a compelling method for transporting sophisticated cloud-native applications from network to network–without sacrificing security or requiring copious amounts of manual labor.

Finally, we have one more specification in the works. The CNAB Claims 1.0 Specification describes how CNAB tools can share a common description of their deployed applications. For example, one tool can “claim” ownership over an application deployment, while another tool can access the shared information about that application and how it was deployed. This brings together distributed management, audit trails, and long-term tool interoperability.

Porter and Duffle already support claims, but we are excited to get a formal standard that enables information sharing across all of the tools in the CNAB ecosystem.

### How to Get Involved

The CNAB specification is developed under an open source model. You can dive right in at [cnab.io][5]. There you will find not only the specifications, the common source libraries (like [cnab-go][6]), and our full command-line reference implementation [duffle][7].

[Porter][8] is also open source and is a great starting point if you wish to work with a user-friendly CNAB tool immediately.

We have even experimented with a graphical [CNAB installer][9], and have some [VS Code extensions][10] to improve the development process.

### Conclusion

Our goal with CNAB is to provide a package management story for the cloud. Just as it is easy to run an installer on our laptops or put a new app on our phone, it should be easy to install a new cloud application. That is the vision that CNAB relentlessly pursues.

We’d love to have you join up, take it for a test drive, and explore the possibilities.

--------------------------------------------------------------------------------

via: https://www.linux.com/featured/cnab-a-package-format-for-the-cloud/

作者：[Linux.com Editorial Staff][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linux.com/author/linuxdotcom/
[b]: https://github.com/lujun9972
[1]: mailto:matt.butcher@microsoft.com
[2]: https://www.docker.com/blog/docker-app-and-cnab/
[3]: https://www.docker.com/blog/powering-docker-app-next-steps-for-cnab/
[4]: https://www.compose-spec.io/
[5]: https://cnab.io/
[6]: https://github.com/cnabio/cnab-go/
[7]: https://duffle.sh/
[8]: https://porter.sh/
[9]: https://github.com/deislabs/duffle-coat
[10]: https://github.com/deislabs/duffle-vscode
