[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Pros and cons of cloud storage)
[#]: via: (https://www.networkworld.com/article/3542038/pros-and-cons-of-cloud-storage.html)
[#]: author: (Neal Weinberg )

Pros and cons of cloud storage
======
Easy scalability and pay-per-usage pricing are two of the draws of enterprise cloud storage. Potential drawbacks include management complexity and security concerns.
Ivanastar / Getty Images / Sam Schooler

Everything seems to be moving to the cloud these days, so what about storage? Is it time to unplug those expensive data center storage appliances and migrate all of that data to the cloud?

The answer: It's more complicated than you might think.

While cloud storage offers many advantages over on-premises data storage – scalability at the push of a button (up or down), accessibility from any device at any location, pay-per-usage pricing – there are some potential drawbacks as well.

### Tech Spotlight:

[Cloud Computing][1]

  * [The 2020 IDG Cloud Computing Survey][2] (InfoWorld)
  * [Reskilling IT for the cloud][3] (CIO)
  * [3 big SaaS challenges for IT][4] (Computerworld)
  * [A 10-point plan to vet SaaS provider security][5] (CSO)
  * [How to make the most of AWS Lambda][6] (InfoWorld)



Security and privacy issues inevitably come up when enterprises consider whether to entrust a public cloud services provider with information that could be damaging to the company in the event of a data breach. Performance is another issue, particularly when it comes to applications that require low latency. Managing data when it's locked up in your data center is by definition easier than managing data scattered across multiple geographic availability zones of a single cloud storage provider, or even scattered across multiple providers. And vendor lock-in is certainly a concern when you're talking about moving terabytes of data.

David Friend, CEO and co-founder of cloud storage vendor [Wasabi Technologies][7], estimates that around 80% of enterprise storage is still on-premises, but he predicts that within 10 years, most data will be in the public cloud. "The business of running a storage farm yourself makes less and less sense," Friend says. IDC analyst Andrew Smith agrees. "The expectation is that more and more capacity will be stored in the public cloud," he says.

According to [Allied Market Research][8], the cloud storage market was $46 billion in 2019 and is expected to grow at more than 20% a year, topping $222 billion by 2027. Inkwood Research comes to a similar conclusion, predicting a growth rate of 19.75% between 2020 and 2028.

When it comes to the primary storage that is linked to specific workloads, storage follows the application, whether the app moves from an enterprise data center to a private cloud or public cloud environment, says Henry Baltazar, a storage analyst at [451 Research][9]. "At the end of the day, storage is a secondary element to the application," says Baltazar.

Where it gets interesting is the opportunity to migrate backup data, archived data and even disaster recovery functionality to the public cloud. For enterprises investigating a strategic move to cloud storage, here are some of the pros and cons that should be taken into consideration.

## Cloud storage advantages

**Cost cutting:** Acquiring cloud storage on an 'only-pay-for-what-you-use model' is cheaper than shelling out millions for your own storage hardware that you have to maintain and upgrade. In fact, Smith says that as the competition has heated up between the main cloud storage providers – Amazon, Microsoft, Google, IBM – prices have continued to plummet. "There's a pretty obvious race to the bottom on price in terms of public cloud storage."

**Scalability**: The ability to access more data storage capacity in times of unexpected or unplanned business need can be lifesaver for a company. Similarly, companies can quickly and easily scale back down. And the almost unlimited storage capacity of the public cloud comes into play when companies start to think about creating data lakes so they can apply artificial intelligence to IoT data or other large data sets. Smith says the data lake scenario is still "nascent," but he predicts that it will gain momentum over time.

**Accessibility**: Cloud storage enables end users to access and share data on any device no matter where they are working. This type of connectivity can boost collaboration, productivity and business agility.

**Offsite management/maintenance:** No matter how well you maintain your storage assets, disks crash, components fail, appliances go down. In an on-prem scenario, that's an emergency the IT department has to tackle. In a cloud scenario, it's Amazon's problem.

**Constant updates:** Organizations with on-prem storage hardware have to watch their devices age and become obsolete. Cloud storage companies are constantly providing updates as part of the normal course of business.

**Backup benefits:** Backing up data has always been important for business continuity, but it has taken on increased urgency in the age of ransomware attacks that encrypt data and demand money to unlock that data. Most large enterprises back up their data at a secondary data center, but cloud storage provides a low-cost alternative that eliminates the need for companies to maintain redundant facilities and enables companies to restore their data without paying a ransom.

**Disaster recovery:** DR involves maintaining a mirror image of the production environment at a different location, so that it can be activated in the event of a disaster. Instead of owning and operating a secondary DR site, which might never be needed, putting DR in the cloud is an enticing prospect. The tricky part is figuring out whether to do-it-yourself, to go with a DR-as-a-Service offering from cloud services providers like Azure and IBM, or to work with third-party DRaaS vendors like iLand or Recovery Point.

Baltazar says that once companies realize that they can stand up servers and storage at the touch of a button in the cloud, they can begin to use cloud-based DR as a way to run production workloads in cases where the main data center might be running out of capacity. And eventually, DR can provide workload mobility. "The future is going to be about choosing the right execution venue based on the requirements of the business," he says.

## Cloud storage challenges

**Pricing gotchas**: Yes, cloud storage is cheap, but nailing down exactly what your costs will be in order to do accurate budgeting and forecasting isn't all that easy. Storage falls into three large buckets, hot storage or active data that needs to be accessed frequently, cool storage or data that needs to be accessed infrequently, and cold storage, which is inactive archived data that is being kept for compliance or regulatory reasons.

The complexity comes in when organizations have to decide between Amazon's six storage tiers (Standard, Intelligent, Standard Infrequent Access, One-Zone Infrequent Access, Glacier and Glacier Deep Archive.) Similarly, Microsoft Azure has four tiers and Google has five tiers, with prices decreasing as one moves to the colder forms of storage.

Then there are additional costs that organizations might not have anticipated. For example, the cloud vendors charge for data access (get requests and put requests) and data movement (egress charges). Business requirements change all the time, so companies may find themselves needing to access data that they once thought was stagnant, which translates into additional fees that the company had not planned on, Smith says.

There are now third-party vendors who will help companies classify their data, make sure it ends up in the appropriate tier and even ‘prune' the data over time in a bid to control costs.

**Security and privacy concerns:** Cloud service providers have made a determined effort to assuage those concerns, but security is still the No. 1 worry among enterprise customers, according to IDC surveys. Smith points out that service providers are now offering a broad range of security-related features, including data encryption, SLAs, multiple ‘9s' of availability, the ability to track sensitive data, etc. But auditors and compliance officers remain wary, especially in regions subject to GDPR or similar regulations.

**Management complexity:** As companies begin to move data to the cloud, or to multiple clouds, they are faced with the task of managing across a hybrid cloud environment, which can be a challenge. First off, IT staffers might not have the right skills to be doing things like checking to see that SLAs are being met, or tracking the reasons for escalating usage costs. Smith says many enterprises end up buying third-party cloud storage management tools from vendors such as Veeam, Commvault and Zerto.

The good news is that the incumbent storage hardware vendors (NetApp, Dell/EMC, IBM, HPE, etc.) are offering software overlays that integrate an enterprise's on-prem storage with its cloud volumes in order to create a single management platform across a multi-cloud environment. "That model is resonating with customers," says Smith.

He adds that most enterprise have wisely decided not to spread their storage across multiple service providers, unless there's a specific use case. For example, companies might use AWS for their CRM applications and Azure for email. But they would be unlikely to have CRM data in more than one cloud.

**Vendor lock-in:** In practice, it could literally take months for an enterprise to move large volumes of data to the cloud over a typical Internet connection. "It's still painful to move a lot of data," Friend says. So, imagine that process in reverse, if an organization wanted to remove its data from a cloud storage provider. Not only that, in many cases companies are required to make a three-year commitment. And there are even monetary penalties for "early deletion" of cool and cold storage.

**Performance**: There's no way to get around it – accessing data housed in an on-prem data center, or even an edge data center, will always be faster than accessing data from the cloud. The question then becomes which applications absolutely require low latency and which can live with a bit of delay. Global companies also need to do their research to make sure that the cloud provider has availability zones in all of the geographic areas in which the company does business.

Bottom line: Storage requirements continues to increase, and most companies want to get off that costly storage hardware refresh cycle. But it's important to be aware of the complexities involved in moving storage to the public cloud.

**More about enterprise storage:**

  * [NVMe over Fabrics creates data-center storage disruption][10]
  * [How NVMe is changing enterprise storage][11]
  * [What is a solid-state drive? SSDs vs HDDs][12]
  * [How to pick an offsite data-backup method][13]
  * [Top storage skills to boost your salary][14]



Join the Network World communities on [Facebook][15] and [LinkedIn][16] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3542038/pros-and-cons-of-cloud-storage.html

作者：[Neal Weinberg][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.infoworld.com/article/3561329/the-state-of-cloud-computing-in-2020.html
[2]: https://www.infoworld.com/article/3561269/the-2020-idg-cloud-computing-survey.html
[3]: https://www.cio.com/article/3561249/reskilling-it-for-the-cloud.html
[4]: https://www.computerworld.com/article/3541829/3-big-saas-challenges-for-it.html
[5]: https://www.csoonline.com/article/3546316/a-10-point-plan-to-vet-saas-provider-security.html
[6]: https://www.infoworld.com/article/3539233/how-to-make-the-most-of-aws-lambda.html
[7]: https://wasabi.com/
[8]: https://alliedmarketresearch.com/cloud-storage-market
[9]: https://451research.com/
[10]: https://www.networkworld.com/article/3394296/nvme-over-fabrics-creates-data-center-storage-disruption.html
[11]: https://www.networkworld.com/article/3280991/what-is-nvme-and-how-is-it-changing-enterprise-storage.html
[12]: https://www.networkworld.com/article/3326058/what-is-an-ssd.html
[13]: https://www.networkworld.com/article/3328488/how-to-pick-an-off-site-data-backup-method.html
[14]: http://www.networkworld.com/article/3199310/storage/top-storage-skills-to-boost-your-salary.html
[15]: https://www.facebook.com/NetworkWorld/
[16]: https://www.linkedin.com/company/network-world
