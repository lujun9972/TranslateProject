[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Enterprises look to SASE to bolster security for remote workers)
[#]: via: (https://www.networkworld.com/article/3545778/enterprises-look-to-sase-to-bolster-security-for-remote-workers.html)
[#]: author: (Maria Korolov )

Enterprises look to SASE to bolster security for remote workers
======
Surge in telework drives interest in secure access service edge (SASE), which combines SD-WAN capabilities with network security services.
Cybrain / Getty Images

The coronavirus pandemic has accelerated some companies' plans to adopt secure access service edge (SASE).

Last summer, Gartner estimated SASE adoption at less than 1% of enterprises and said it would take five to 10 years before the technology [reaches mainstream][1]. But today, SASE is one of the [main topics][2] of client interest, according to Gartner analyst John Wheeler.

**READ MORE:** [How SD-WAN is evolving into Secure Access Service Edge][3]

Gartner coined the term SASE, pronounced "sassy," to describe a technology category that converges network and security services, including [SD-WAN][4], secure web gateway (SWG), cloud access security broker (CASB), DNS protection, and cloud-based firewall. COVID-19 has boosted interest in SASE as enterprises scramble to support a suddenly remote workforce. The surge in telework has taxed legacy network architectures that depend on traffic being routed through the enterprise data center for inspection. With SASE, access decisions are based on user identity and enforced at the endpoint, while policies are centrally defined and managed in the cloud. (Read more about how SASE works [here][3])

"Companies that were on the fence about whether to upgrade to SASE, they're falling over to the 'adopt now' side," says Zeus Kerravala, founder and principal analyst at [ZK Research][5]. "If I'm trying to move to a modernized application infrastructure, why am I still using a network architecture designed for client-server from 30 years ago? A lot of my apps are now in the cloud, I've got people working from everywhere. This transition would have happened with or without the pandemic, but the pandemic has accelerated it."

While it's too early to tell if adoption spikes will continue after the pandemic abates, individual SASE vendors are reporting dramatic changes so far. Versa Networks, for example, saw remote user traffic increase by 800% to 900% since the pandemic hit. "Around March 22 is when we began to see these stats appear at this level," says Mike Wood, [Versa Networks][6]' CMO.

Sanjay Uppal, senior vice president and general manager of the VeloCloud business unit at [VMware][7], says that use of the company's SASE network has gone up five-fold since the pandemic hit. "It's a dramatic increase," he says. "We had one company that has deployed 5,000 employees at home in less than one week. Another customer called up and said they had to send 500 nurses and diagnosticians [to work from] home."

Anand Oswal, senior vice president of product management and engineering for firewall as a platform at [Palo Alto Networks][8], says that more than 1,000 trials have been activated of the company's Prisma Access SASE platform in response to the pandemic.

### Networking without new hardware

For new SASE customers, the biggest delay is typically on the hardware side. Employees may need new SASE edge devices to handle networking and security in employee homes. In addition, corporate data centers may need new hardware to connect to the SASE networks.

But there are also ways to deploy SASE without any new hardware. [CloudCheckr][9], a 200-person software company that makes cloud management tools, uses Zscaler's SASE platform to connect its employees to the cloud services they need to do their jobs, including AWS infrastructure, in a secure way.

CloudCheckr is entirely cloud-based, says Travis Rehl, senior director of product at the Rochester, N.Y.-based company. "We have no servers, no routers, nothing in our offices," he says.

Meanwhile, when at home, employees don't require any additional network or security devices either. "We don't use printers or other devices much," Rehl says. "Besides laptops, the only other thing people brought home was monitors, but that isn't a network device."

So, on the user side, the SASE client could be all software.

Before the pandemic hit, half of CloudCheckr's employees were working remotely, using the [Zscaler][10] SASE platform for the only home SASE connection. Teleworkers used laptops that had the Zscaler client installed on the machine, with no additional hardware necessary.

Traffic would be routed from the employee directly to the Zscaler network. "We did not go through the corporate network," Rehl says.

Zscaler would then route the traffic directly to the cloud apps that the employees were accessing.

Because the SASE infrastructure was already in place, the transition to a fully work-from-home workplace was seamless. The employees already had company-issued laptops, and all that was needed was the client software. Other than an additional authentication step when signing in from home for the first time, employees get the same exact work environment as they would in the office, Rehl says. "We had zero downtime for our teams because we were all set up already," he says. "People just went home."

When first logging into the network, the employees would need to authenticate once to the Zscaler system, which then controlled the traffic flow to the applications specific to each particular employee, he says. That's the same as the process that was in place before the pandemic.

### SASE enables agility

Speed of deployment has been a big draw for companies that turned to SASE as COVID-19 disrupted work patterns.

"One organization we work with had 95% of their employees coming into an office, sitting in a cubicle, and working on premises," says Jeremy Nelson, director of networking services at Tempe, Ariz.-based [Insight][11], a technology consulting and system-integration firm. "They had to go to only 5% of the workforce in the office, the ones with essential functions that require them to come on-premises. Now we have people trying to access applications that they never had to access remotely before."

That company didn't have the broadband capacity in their traditional data center to handle the increase in remote traffic, and it would have taken several weeks to provision new circuits from their service providers. By deploying SASE, they were able to leverage the infrastructure of their vendor's cloud-based platform. "It was highly flexible, scales based on user access, and would only route traffic to the destinations it needed to go," Nelson says. And the deployment took about two weeks, he says.

Nelson warns, however, that not all SASE platforms are created equal. "There are gaps in each individual offering," Nelson says. "You'll hear that they have the entire SASE thing solved end to end, but it's still very much a best-of-breed approach, as opposed to being wholly holistic."

**READ MORE ABOUT SASE**

  * [SASE might be better than VPNs for quickly ramping up remote access][12]
  * [How SD-WAN is evolving into Secure Access Service Edge][3]
  * [SASE is more than a buzzword for BioIVT][13]
  * [Know the benefits of cloud-native networking for SASE][14]
  * [IT pros need to weigh in on that ‘sassy’ security model][15]
  * [SASE: A reflection of our times][16]
  * [SASE: Redefining the network and security architecture][17]



Join the Network World communities on [Facebook][18] and [LinkedIn][19] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3545778/enterprises-look-to-sase-to-bolster-security-for-remote-workers.html

作者：[Maria Korolov][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.gartner.com/doc/reprints?id=1-6QW0Z4A&ct=190528&st=sb
[2]: https://blogs.gartner.com/john-wheeler/top-ten-gartner-client-topics-for-emerging-technologies-q1-2020/
[3]: https://www.networkworld.com/article/3449136/how-sd-wan-is-evolving-into-secure-access-service-edge.html
[4]: https://www.networkworld.com/article/3031279/sd-wan-what-it-is-and-why-you-ll-use-it-one-day.html
[5]: https://zkresearch.com/
[6]: https://www.versa-networks.com/
[7]: https://www.vmware.com/
[8]: https://www.paloaltonetworks.com/
[9]: https://cloudcheckr.com/
[10]: https://www.zscaler.com/
[11]: https://www.insight.com/en_US/home.html
[12]: https://www.networkworld.com/article/3534501/sase-might-be-better-than-vpns-for-quickly-ramping-up-remote-access.html
[13]: https://www.networkworld.com/article/3453030/sase-is-more-than-a-buzzword-for-bioivt.html
[14]: https://www.networkworld.com/article/3534720/know-the-benefits-of-cloud-native-networking-for-sase.html
[15]: https://www.networkworld.com/article/3516503/it-pros-need-to-weigh-in-on-that-sassy-security-model.html
[16]: https://www.networkworld.com/article/3442941/secure-access-service-edge-sase-a-reflection-of-our-times.html
[17]: https://www.networkworld.com/article/3481519/sase-redefining-the-network-and-security-architecture.html
[18]: https://www.facebook.com/NetworkWorld/
[19]: https://www.linkedin.com/company/network-world
