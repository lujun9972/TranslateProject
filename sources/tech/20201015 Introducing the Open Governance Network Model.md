[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Introducing the Open Governance Network Model)
[#]: via: (https://www.linux.com/news/introducing-the-open-governance-network-model/)
[#]: author: (The Linux Foundation https://www.linuxfoundation.org/blog/2020/10/introducing-the-open-governance-network-model/)

Introducing the Open Governance Network Model
======

![][1]

### Background

The Linux Foundation has long served as the home for many of the world’s most important open source software projects. We act as the vendor-neutral steward of the collaborative processes that developers engage in to create high quality and trustworthy code. We also work to build the developer and commercial communities around that code to sponsor each project’s members. We’ve learned that finding ways for all sorts of companies to benefit from using and contributing back to open source software development is key to the project’s sustainability.

Over the last few years, we have also added a series of projects focused on lightweight open standards efforts — recognizing the critical complementary role that standards play in building the open technology landscape. Linux would not have been relevant if not for POSIX, nor would the Apache HTTPD server have mattered were it not for the HTTP specification. And just as with our open source software projects, commercial participants’ involvement has been critical to driving adoption and sustainability.

On the horizon, we envision another category of collaboration, one which does not have a well-established term to define it, but which we are today calling “Open Governance Networks.” Before describing it, let’s talk about an example.

Consider ICANN, the agency that arose after demands emerged from evolving the global domain name system (DNS) from its single-vendor control by Network Solutions. With ICANN, DNS became something more vendor-neutral, international, and accountable to the Internet community. It evolved to develop and manage the “root” of the domain name system, independent from any company or nation. ICANN’s control over the DNS comes primarily through its establishment of an operating agreement among domain name registrars that establishes rules for registrations, guarantees your domain names are portable, and a uniform dispute resolution protocol (the UDRP) for times when a domain name conflicts with an established trademark or causes other issues.

ICANN is not a standards body; they happily use the standards for DNS developed at the IETF. They also do not create software other than software incidental to their mission, perhaps they also fund some DNS software development, but that’s not their core. ICANN is not where all DNS requests go to get resolved to IP addresses, nor even where everyone goes to register their domain name — that is all pushed to registrars and distributed name servers. In this way, ICANN is not fully decentralized but practices something you might call “minimum viable centralization.” Its management of the DNS has not been without critics, but by pushing as much of the hard work to the edge and focusing on being a neutral core, they’ve helped the DNS and the Internet achieve a degree of consistency, operational success, and trust that would have been hard to imagine building any other way.

There are similar organizations that interface with open standards and software but perform governance functions. A prime example of this is the CA Browser Forum, who manages the root certificates for the SSL/TLS web security infrastructure.

Do we need such organizations? Can’t we go completely decentralized? While some cryptocurrency networks claim not to need formal human governance, it’s clear that there are governance roles performed by individuals and organizations within those communities. Quite a bit of governance is possible to automate via smart contracts (and repairing damage from exploiting them), promoting the platform’s adoption to new users, onboarding new organizations, or even coordinating hard fork upgrades still require humans in the mix. And this is especially important in environments where competitors need to participate in the network to succeed, but do not trust one competitor to make the decisions.

### Network governance is not a solved problem

Network governance is not just an issue for the technical layers. As one moves up the stack into more domain-specific applications, it turns out that there are network governance challenges up here as well, which look very familiar.

Consider a typical distributed application pattern: supply chain traceability, where participants in the network can view, on a distributed database or ledger, the history of the movement of an object from source to destination, and update the network when they receive or send an object. You might be a raw materials supplier, or a manufacturer, or distributor, or retailer. In any case, you have a vested interest in not only being able to trust this distributed ledger to be an accurate and faithful representation of the truth. You also want the version you see to be the same ledger everyone else sees, be able to write to it fairly, and understand what happens if things go wrong. Achieving all of these desired characteristics requires network governance!

You may be thinking that none of this is strictly needed if only everyone agreed to use one organization’s centralized database to serve as the system of record. Perhaps that is a company like eBay, or Amazon, Airbnb, or Uber. Or perhaps, a non-profit charity or government agency can run this database for us. There are some great examples of shared databases managed by non-profits, such as Wikipedia, run by the Wikimedia Foundation. This scenario might work for a distributed crowdsourced encyclopedia, but would it work for a supply chain?

This participation model requires everyone engaging in the application ecosystem to trust that singular institution to perform a very critical role — and not be hacked, or corrupted, or otherwise use that position of power to unfair ends. There is also a trust the entity will not become insolvent or otherwise unable to meet the community’s needs. How many Wikipedia entries have been hijacked or subject to “edit wars” that go on forever? Could a company trust such an approach for its supply chain? Probably not.

Over the last ten years, we’ve seen the development of new tools that allow us to build better-distributed data networks without that critical need for a centralized database or institution holding all the keys and trust. Most of these new tools use distributed ledger technology (“DLT”, or “blockchain”) to build a single source of truth across a network of cooperating peers, and embed programmatic functionality as “smart contracts” or “chaincode” across the network.

The Linux Foundation has been very active in DLT, first with the launch of Hyperledger in December of 2015. The launch of the [Trust Over IP Foundation earlier this year][2] focused on the application of self-sovereign identity, and in many examples, usually using a DLT as the underlying utility network.

As these efforts have focused on software, they left the development, deployment, and management of these DLT networks to others. Hundreds of such networks built on top of Hyperledger’s family of different protocol frameworks have launched, some of which (like the Food Trust Network) have grown to hundreds of participating organizations. Many of these networks were never intended to extend beyond an initial set of stakeholders, and they are seeing very successful outcomes.

However, many of these networks need a critical mass of industry participants and have faced difficulty achieving their goal. A frequently cited reason is the lack of clear or vendor-neutral governance of the network. No business wants to place its data, or the data it depends upon, in the hands of a competitor; and many are wary even of non-competitors if it locks down competition or creates a dependency on a market participant. For example, what if the company doesn’t do well and decides to exit this business segment? And at the same time, for most applications, you need a large percentage of any given market to make it worthwhile, so addressing these kinds of business, risk, or political objections to the network structure is just as important as ensuring the software works as advertised.

In many ways, this resembles the evolution of successful open source projects, where developers working at a particular company realize that just posting their source code to a public repository isn’t sufficient. Nor even is putting their development processes online and saying “patches welcome.”

To take an open source project to the point where it becomes the reference solution for the problem being solved and can be trusted for mission-critical purposes, you need to show how its governance and sustainability are not dependent upon a single vendor, corporate largess, or charity. That usually means a project looks for a neutral home at a place like the Linux Foundation, to provide not just that neutrality, but also competent stewarding of the community and commercial ecosystem.

### Announcing LF Open Governance Networks

To address this need, today, we are announcing that the Linux Foundation is adding “Open Governance Networks” to the types of projects we host. We have several such projects in development that will be announced before the end of the year. These projects will operate very similarly to the Linux Foundation’s open source software projects, but with some additional key functions. Their core activities will include:

  * Hosting a technical steering committee to specify the software and standards used to build the network, to monitor the network’s health, and to coordinate upgrades, configurations, and critical bug fixes
  * Hosting a policy and legal committee to specify a network operating agreement the organizations must agree to for connecting their nodes to the network
  * Running a system for identity on the network, so participants to trust other participants who they say they are, monitor the network for health, and take corrective action if required.
  * Building out a set of vendors who can be hired to deploy peers-as-a-service on behalf of members, in addition to allowing members’ technical staff to run their own if preferred.
  * Convene a Governing Board composed of sponsoring members who oversee the budget and priorities.
  * Advocate for the network’s adoption by the relevant industry, including engaging relevant regulators and secondary users who don’t run their own peers.
  * Potentially manage an open “app store” approach to offering vetted re-usable deployable smart contracts of add-on apps for network users.



These projects will be sustained through membership dues set by the Governing Board on each project, which will be kept to what’s needed for self-sufficiency. Some may also choose to establish transaction fees to compensate operators of peers if usage patterns suggest that would be beneficial. Projects will have complete autonomy regarding technical and software choices – there are no requirements to use other Linux Foundation technologies.

To ensure that these efforts live up to the word “open” and the Linux Foundation’s pedigree, the vast majority of technical activity on these projects, and development of all required code and configurations to run the software that is core to the network will be done publicly. The source code and documentation will be published under suitable open source licenses, allowing for public engagement in the development process, leading to better long-term trust among participants, code quality, and successful outcomes. Hopefully, this will also result in less “bike-shedding” and thrash, better visibility into progress and activity, and an exit strategy should the cooperation efforts hit a snag.

Depending on the industry that it services, the ledger itself might or might not be public. It may contain information only authorized for sharing between the parties involved on the network or account for GDPR or other regulatory compliance. However, we will certainly encourage long term approaches that do not treat the ledger data as sensitive. Also, an organization must be a member of the network to run peers on the network, required to see the ledger, and particularly write to it or participate in consensus.

Across these Open Governance Network projects, there will be a shared operational, project management, marketing, and other logistical support provided by Linux Foundation personnel who will be well-versed in the platform issues and the unique legal and operational issues that arise, no matter which specific technology is chosen.

These networks will create substantial commercial opportunity:

  * For software companies building DLT-based applications, this will help you focus on the truly value-delivering apps on top of such a shared network, rather than the mechanics of forming these networks.
  * For systems integrators, DLT integration with back-office databases and ERP is expected to grow to be billions of dollars in annual activity.
  * For end-user organizations, the benefits of automating thankless, non-differentiating, perhaps even regulatorily-required functions could result in huge cost savings and resource optimization.



For those organizations acting as governing bodies on such networks today, we can help you evolve those projects to reach an even wider audience while taking off your hands the low margin, often politically challenging, grunt work of managing such networks.

And for those developers concerned before about whether such “private” permissioned networks would lead to dead cul-de-sacs of software and wasted effort or lost opportunity, having the Linux Foundation’s bedrock of open source principles and collaboration techniques behind the development of these networks should help ensure success.

We also recognize that not all networks should be under this model. We expect a diversity of approaches that will be long term sustainable, and encourage these networks to find a model that works for them. Let’s talk to see if it would be appropriate.

LF Governance Networks will enable our communities to establish their own Open Governance Network and have an entity to process agreements and collect transaction fees. This new entity is a Delaware nonprofit, a nonstock corporation that will maximize utility and not profit. Through agreements with the Linux Foundation, LF Governance Networks will be available to Open Governance Networks hosted at the Linux Foundation.

If you’re interested in learning more about hosting an Open Governance Network at the Linux Foundation, please contact us at [**governancenetworks@linuxfoundation.org**][3]

Thanks!

Brian

The post [Introducing the Open Governance Network Model][4] appeared first on [The Linux Foundation][5].

--------------------------------------------------------------------------------

via: https://www.linux.com/news/introducing-the-open-governance-network-model/

作者：[The Linux Foundation][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linuxfoundation.org/blog/2020/10/introducing-the-open-governance-network-model/
[b]: https://github.com/lujun9972
[1]: https://www.linuxfoundation.org/wp-content/uploads/2020/10/GovernanceNetwork-100620_V3.png
[2]: https://www.linuxfoundation.org/press-release/2020/05/cross-industry-coalition-advances-digital-trust-standards/
[3]: mailto:governancenetworks@linuxfoundation.org
[4]: https://www.linuxfoundation.org/blog/2020/10/introducing-the-open-governance-network-model/
[5]: https://www.linuxfoundation.org/
