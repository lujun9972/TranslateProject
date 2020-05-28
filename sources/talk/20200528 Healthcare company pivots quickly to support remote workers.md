[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Healthcare company pivots quickly to support remote workers)
[#]: via: (https://www.networkworld.com/article/3545533/healthcare-company-pivots-quickly-to-support-remote-workers.html)
[#]: author: (Maria Korolov )

Healthcare company pivots quickly to support remote workers
======
TrialCard rolls out secure access service edge (SASE), which combines SD-WAN capabilities with network security services.
Getty Images

Security and performance concerns made it challenging for TrialCard to enable its employees to work from home when the COVID-19 pandemic hit.

Customer service agents use a voice-over-IP phone and thin-client computer, both of which were designed to work in an on-premises office environment. "They need those systems to do their day-to-day job," says Ryan Van Dynhoven, director of infrastructure at [TrialCard][1], a Morrisville, N.C.-based company that helps pharmaceutical manufacturers connect with patients, including providing patient support and clinical trial services.

**READ MORE:** [Enterprises look to SASE to bolster security for remote workers][2]

To maintain sufficient voice quality over residential Internet connections and keep those interactions secure, TrialCard looked to deploy a new technology: secure access service edge. SASE, pronounced "sassy," combines elements of SD-WAN and network security in a cloud-based service.

Research firm Gartner started talking about SASE last year, citing the need for greater scalability, flexibility, low latency, and pervasive security at the WAN edge than a legacy network and security architecture can provide. Services that might be wrapped into SASE include [SD-WAN][3], secure web gateway (SWG), cloud access security broker (CASB), DNS protection, and cloud-based firewall.

"SASE offerings will provide policy-based 'software defined' secure access from an infinitely tailorable network fabric in which enterprise security professionals can precisely specify the level of performance, reliability, security, and cost of every network session based on identity and context," Gartner wrote in its [report][4] introducing SASE.

With more SaaS applications in use and more employee traffic destined for cloud services, SASE takes a different approach than the legacy method of routing all traffic through the enterprise data center for inspection. Instead, access decisions are based on the identity of the entity that's at the source of the connection – whether that's a user, device, branch office, IoT device, edge-computing location, or a combination of these factors, according to Gartner. Security decisions are enforced at the endpoint while policies are defined and managed in the cloud.

At TrialCard, the decision to fast-track an untested SASE solution to hundreds of users was made easier by going with one of the company's existing networking vendors, Silver Peak. "We were already using Silver Peak in our internal networks," Van Dynhoven says. "We also used them for a connection from a data center to one of our external partners."

Silver Peak's SASE product is its Unity EdgeConnect SD-WAN edge platform, which includes end-to-end encryption and [microsegmentation][5] capabilities to isolate sensitive medical or payments data. Other cloud security features are provided by partners, which include Check Point Software, Netskope and Zscaler, and the platform can connect to multiple points-of-presence providers.

"It's very similar to a VPN, except that it's building multiple tunnels to multiple data centers for multiple purposes," Van Dynhoven says. "And we classify voice traffic as the most critical data, so we can sustain 30-to-40% packet loss on the connection, and they can still have a good connection."

TrialCard did a proof-of-concept in a single day, borrowing a Silver Peak edge device, configuring it, and sending it home with an employee. The company placed its first order for the Unity EdgeConnect ultra small SD-WAN appliances on Friday, March 13. The first devices arrived on Tuesday, March 17, and the first group of agents started working from home the following day. By Friday, March 20, 300 users were working from home, and another 300 were outfitted over the next few days.

"The agents would come into the office, work their normal shift, and at the end of their shift we would give them equipment to take home, and they would start their shift the next day from home," says Tommy Walker, vice president of IT operations at TrialCard. "In terms of productivity, it was entirely seamless."

TrialCard had to preconfigure the SASE edge devices for its employees, but software tools made it possible to do each device configuration in just 15 to 20 minutes. A bigger task was handling the hardware. "Unboxing 100 units at a time is no small feat in terms of packing material and cables," Van Dynhoven says. "We have pictures of boxes packed floor to ceiling down our hallways."

With the Silver Peak devices for security, employees can work from home using the same exact setup they have at the office. To get set up, each employee plugs a preconfigured SD-WAN appliance into their home router, then plugs the thin-client device and voice-over-IP phone that they brought home from work into the Silver Peak gear. All the agents were able to use their existing residential broadband connections and did not require new connections or upgrades.

TrialCard has three entry-level technicians handing tech support calls, but after the initial rollout, calls have been few. "The solution does not require a lot of TLC," Van Dynhoven says.

Changes in the data center were minimal, since TrialCard had already deployed Silver Peak devices for other user cases. "We just made some changes in our firewall posturing, to make it more secure end-to end," Van Dynhoven says.

After a few weeks in production, the results have been extremely positive. "We have not had any change in any of the business metrics we track for calls and productivity," Van Dynhoven says. "It's been completely seamless. Our customers have said a few nice things about how fast we were able to mobilize to do this. In the future, we're not sure at what scale we'll remain at work from home, but from a technical standpoint, there's no reason why it couldn't continue."

**READ MORE ABOUT SASE**

  * [SASE might be better than VPNs for quickly ramping up remote access][6]
  * [How SD-WAN is evolving into Secure Access Service Edge][7]
  * [SASE is more than a buzzword for BioIVT][8]
  * [Know the benefits of cloud-native networking for SASE][9]
  * [IT pros need to weigh in on that ‘sassy’ security model][10]
  * [SASE: A reflection of our times][11]
  * [SASE: Redefining the network and security architecture][12]



Join the Network World communities on [Facebook][13] and [LinkedIn][14] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3545533/healthcare-company-pivots-quickly-to-support-remote-workers.html

作者：[Maria Korolov][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://corp.trialcard.com/
[2]: https://www.networkworld.com/article/3545778/enterprises-look-to-sase-to-bolster-security-for-remote-workers.html
[3]: https://www.networkworld.com/article/3031279/sd-wan-what-it-is-and-why-you-ll-use-it-one-day.html
[4]: https://www.gartner.com/doc/3956841
[5]: https://www.networkworld.com/article/3247672/what-is-microsegmentation-how-getting-granular-improves-network-security.html
[6]: https://www.networkworld.com/article/3534501/sase-might-be-better-than-vpns-for-quickly-ramping-up-remote-access.html
[7]: https://www.networkworld.com/article/3449136/how-sd-wan-is-evolving-into-secure-access-service-edge.html
[8]: https://www.networkworld.com/article/3453030/sase-is-more-than-a-buzzword-for-bioivt.html
[9]: https://www.networkworld.com/article/3534720/know-the-benefits-of-cloud-native-networking-for-sase.html
[10]: https://www.networkworld.com/article/3516503/it-pros-need-to-weigh-in-on-that-sassy-security-model.html
[11]: https://www.networkworld.com/article/3442941/secure-access-service-edge-sase-a-reflection-of-our-times.html
[12]: https://www.networkworld.com/article/3481519/sase-redefining-the-network-and-security-architecture.html
[13]: https://www.facebook.com/NetworkWorld/
[14]: https://www.linkedin.com/company/network-world
