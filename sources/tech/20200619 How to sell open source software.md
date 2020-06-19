[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to sell open source software)
[#]: via: (https://opensource.com/article/20/6/sell-open-source-software)
[#]: author: (John Mark Walker https://opensource.com/users/johnmark)

How to sell open source software
======
A case study from Glyptodon, Inc., an open source remote desktop
solution.
![A dollar sign in a network][1]

In 2010-2011, Mike Jumper started the [Guacamole project][2], a multi-protocol gateway that allowed admins to securely serve up desktops remotely. The client interface ran in the browser, so it was a lightweight, easy-to-use replacement for some older remote access solutions. The project immediately started to grow, resulting in a number of incoming requests for support and help.

This led Mike to start a consulting and support business, Glyptodon, the success of which allowed him to quit his day job and work on Guacamole full-time by 2013. Along the way, they contributed Guacamole to the Apache Software Foundation, where it officially became the Apache Guacamole project. After a few years, Mike and his business partners, James Muehlner and Frank La, began to think about ways to scale the business. By the beginning of 2017, they realized that their services and support model would be difficult to scale out and decided to transition to a subscription licensing model. The result of this was Glyptodon Enterprise, a packaged, supported version of Apache Guacamole. Within two years, they had successfully transitioned 90% of their customer base to the new model and were increasing the number of customers and subscriptions. Here's how they're evolving into a sellable open source option.

### What is Glyptodon's core value?

Every business must answer the question—what is the thing of value to offer that customers will pay for? Businesses built on open source software face additional questions around how they simultaneously serve free users while still building a customer base. Stephen Walli often likes to comment that a user community is a group of people with excess time but no money, and customers are people with money but no time. A business that makes its money on open source software should find a way to incorporate both groups into its model.

So the real question is, what can you offer that saves customers time and effort, making their lives easier, while still building out a community of users and contributors that are the lifeblood for sustaining the project? Apache Guacamole is robust and easy for the end user, but an admin needs to understand some of the finer points of networking and remote access in order to successfully use the technology. This is where Glyptodon Enterprise comes in—it saves the customer time and effort by providing a pre-built solution that is easier for admins to incorporate into their environment than if they started from scratch with Apache Guacamole.

Deciding what to sell was relatively easy because the pain point was obvious—installing and maintaining the software. But how would the commercial effort relate to the open source project? How does one flow into the other, and how can you ensure the success of both? And can you really build a business selling something that can be obtained for free? The answers, in order: the open source upstream flows into the commercial downstream; by creating a commercial space and maintaining it separately from the open source community space; and yes, as I will demonstrate.

### The open source product model

One of my favorite reference points for building a business on open source software is Red Hat, and how they built out a model for commercial solutions that sell, while still supporting the upstream communities that sustain the technology innovation. As a long-time proponent of this model, I'm happy to report that it is gaining traction elsewhere. There is a misunderstanding that goes way back about this particular model that it is a support and services business, which is simply not true. Selling subscription licenses for software products is functionally the same, regardless of the origin of the source code, whether it is proprietary, open source, or otherwise. The reason that so many misunderstand this model is that they overvalue source code and mistake it for a product. In this reading, anyone selling a solution built solely with open source software must be selling support, because why would anyone pay for what they can obtain for free? As Red Hat and others have demonstrated, customers will pay for solutions that save them time, regardless of the origins of the technology.

Let's imagine a potential customer that looks at an open source product, scoffs, and decides they're going to build their own version. In truth, there are a number of options:

  * Use the same open source components to assemble a distribution resembling the product (a functionally similar solution, but not a byte-for-byte reproduction)
  * Use the same source code as the product and simply rebuild/respin it yourself (a fork)
  * Use a similar distribution from a competitor, sometimes also available for free



You may look at the list and think, why on earth would someone buy from a vendor of open source with all of these free alternatives available? It turns out there's a lot that goes into building a successful product that doesn't involve source code. There's the management of several instances and their automated, scalable upgrades. There are network services that feed into this management, making use of aggregated data from across the customer base. There's patent and license indemnification. There's HIPPA, PCI, and other compliance. There's a promise to resolve issues within an allotted time, as well as subject matter experts to consult, many of whom built the software you're using. The key finding from this model is that source code often doesn't matter to the customer. Customers care about saving time and effort, and if your solution does that, they will buy it. In the end, Glyptodon decided to emulate this model, making Apache Guacamole the upstream community, and Glyptodon Enterprise the downstream product.

### Create a commercial product

One of the key decisions to make in this process is where the open source project begins and ends, and where the commercial product picks up.

What are the differentiating factors? One of the findings from the Fedora-to-RHEL model is that branding and identity are important to both parts. The Fedora community must feel ownership of its identity, and paying customers must feel some affinity to the RHEL brand.

The bottom line is—the open source community, when it works well, provides the innovative force that sustains product development. Some companies decide that they will develop proprietary pieces of their commercial product not available to the upstream community. Other companies add further restrictions to their upstream community, essentially enforcing that all innovation comes from the downstream product development group. In the case of Glyptodon, they looked at four different models. All of these are valid, but there are tradeoffs to each.

  1. Open Source upstream community, proprietary downstream product—This is the model chosen by a number of companies, including Confluent, Databrix, Cloudera, and a host of others. The basic idea is to build a commercial proprietary product on a successful open source platform, usually with a viable community in its own right, separate from any commercial effort. This has become an especially popular model for data analytics solutions companies, who are able to differentiate products based on the management control plane. The core data analytics technologies are freely available and open source, while the management control plane software is only available at a cost. The downside is that it's difficult to build a user community around the downstream product, although that doesn't matter as much for certain industry segments.
  2. Limited upstream open source community, proprietary downstream product—This was the most popular model back when the first commercial open source companies received attention from investors. The model was simple: put out a limited version of the commercial product under an open source license and try to upsell on the proprietary features only available in the commercial version. The result is that the parent company is ultimately responsible for sustaining product development, and there's very little lift from an outside community. The communities in these cases never develop an identity outside of the parent company, limiting their growth and value to the parent company. This is a viable model in cases where the technology is more end-user app-focused. For these businesses, the tradeoff is worth it if what you're trying to build is mass adoption of a freemium product that you offer premium services for down the road. In cases where you require more input on product development, as is the case for many infrastructure solutions, this hasn't proved to be a suitable model.
  3. Upstream open source community, downstream licensed product built with open source software—This is the Red Hat model, and it's been proven to work well for others, too. For vendors who sell infrastructure solutions, there are some advantages. By developing and devoting resources to the upstream community, you help to ensure that your technology is used by a large number of people, many of whom are highly skilled admins who need to employ solutions that will allow them to be more efficient. By making a downstream product that has the same feature set, you allow these admins to do much of your selling for you, without having to explain why features are in one version but not the other. The downside is that the prospective customer can choose not to buy from you at all, but that gets us back to the original point about time vs. money. If you're able to save them time and the headache of maintenance, they have a compelling reason to buy from you.
  4. Upstream open source community, downstream SaaS product—This is a relatively new model that is easier for some vendors (and customers) to grok than the idea of selling open source software. Take an open source community, make it successful, and then offer to run it as a service for customers who don't want the headache of operating software themselves. There are tremendous benefits to this model: it's easy to explain, there's an obvious benefit to the customer, and you don't have to worry so much about delineating between the user and customer communities. But there are downsides: by taking on the daily operations of customers, you need to have the internal expertise to efficiently and securely run these services for your customers. This can be quite challenging, especially if you've never run a SaaS business before. MongoDB, to use one example, has made great progress with this model recently.



After considering these options, Glyptodon decided on option #3, for a host of reasons:

  * If the core value proposition is helping customers be successful with the technology, saving them time and resources, then the origin of the source code was irrelevant.
  * If the target audience consists of admins tasked with setting up and maintaining their remote access solutions, it was essential that they be able to get their hands on the software as easily as possible.
  * Apache Guacamole was a highly successful project with an active community. Its user base was by far the largest source of potential paying customers. Therefore, it didn't make sense to differentiate too much from the open source releases.
  * While SaaS is an option they continue to evaluate, the fact is that Glyptodon doesn't have experience with this model and would need to invest in additional resources to create a viable solution.



### So what happened?

The results have been an unqualified success. The assumptions Glyptodon made above have proven to be valid and the business sustainable and growing. Customers don't care where the software comes from; they just want a solution that works. By building a commercial brand around a solution for remote desktop access in the cloud, Glyptodon has set itself on a path towards a scalable business that will grow for years.

Some figures to consider:

![Glyptodon revenue growth graph][3]

  * While transitioning the customer base to the new model, Glyptodon's revenue has continued to hit an average growth rate of &gt;30%.
  * Glyptodon's cost for supporting customers has declined, which is to be expected when transitioning to a product licensing model vs. services and support.
  * Glyptodon's revenue breakdown in 2017 was &gt;95% support and services.
  * By the end of 2019, that had flipped, with 70+% of revenue coming from license subscriptions.



### The COVID effect

It would be disingenuous to discuss Glyptodon's success without mentioning that remote access software, like Glyptodon Enterprise, has seen a surge ever since remote working due to quarantine became part of the story starting in March 2020. Like other companies that provide solutions for remote working and learning, Glyptodon has certainly seen an influx of interest as many companies have had to suddenly shift to a remote model. However, it's important to note that its trajectory was positive before the quarantine. While the heightened interest in remote working has certainly led to an increase in customers and overall interest, it's too early to predict what the ultimate impact will be.

### Conclusion: yes, you can sell open source software

Every business model has its tradeoffs, with pros and cons. In the case of Glyptodon, they made a bet that they could build a viable commercial brand with 100% open source software. That bet has paid off, and it has allowed the Glyptodon founders to build a business without outside funding. The hope is that their story helps other entrepreneurs who are struggling with how to build a sustainable business selling open source software. For every company founder who was told it couldn't be done, Glyptodon wants you to know it is absolutely possible—you can build and sell open source products. The key is to establish a trusted commercial brand and sell the overall solution. Don't focus on feature comparisons; focus on what your commercial solution enables the customer to do. If what you're selling is higher efficiency based on less time and effort, then build around that. It's all about operations, and you are an essential part of a customer's successful business.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/sell-open-source-software

作者：[John Mark Walker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/johnmark
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/osdc_whitehurst_money.png?itok=ls-SOzM0 (A dollar sign in a network)
[2]: https://guacamole.apache.org/
[3]: https://opensource.com/sites/default/files/uploads/glyptodon_selling_open_source_software.png (Glyptodon revenue growth graph)
