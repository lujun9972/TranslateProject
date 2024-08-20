[#]: subject: "Now CockroachDB Ditches Open-Source License"
[#]: via: "https://news.itsfoss.com/cockcroachdb-no-open-source/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Now CockroachDB Ditches Open-Source License
======
In the time when companies are embracing open-source, we have some doing
the opposite.
[![][1]][2]

Regrettably, it's becoming a common occurrence to see well-performing open-source projects shifting towards a more closed-door approach, with weird [vanity licenses][3] being deployed that make the code less open.

Many usually opt for a “ _source available_ ” policy, where the code is publicly accessible, available for anyone to view, while restricting any form of commercial usage. The debate on [open-source vs. source available][4] is a never-ending one, but one that divides the community of software developers as a whole.

In a similar type of situation, [CockroachDB][5], a popular distributed SQL database management system developed by Cockroach Labs, recently [announced][6] that they were changing their licensing terms.

### CockroachDB: The Same Old Story?

![][7]

Come November 2024, **the free CockroachDB Core offering will be no more** , and a new enterprise licensing system will take its place to cater to users. Cockroach Labs asserts that they have taken this measure to encourage established organizations to utilize the full capabilities of the platform without any compromises by opting for one of the new plans.

There are **two enterprise plans** individuals/organizations can choose from:

  * The first is the free **CockroachDB Enterprise Free** plan, meant for individuals, organizations, researchers, etc. with an annual revenue below $10 million. They will be provided with annual renewal ( _subject to eligibility check_ ) and community support.
  * The second one is the paid **CockroachDB Enterprise** plan with all the features as Free, but with dedicated support, and the flexibility to opt for a 30-day self-service trial ( _with only community support_ ).



The second plan is meant for large-scale commercial businesses with more than $10 million in revenue, and government use.

Following this change, **the code for CockroachDB will just be source available** , with restrictions on commercial use or redistribution without a license by Cockroach Labs.

CockroachDB was originally offered under the [Apache License 2.0][8], with a subsequent switch to the [Business Source License][9] (BSL), and finally, settling on their in-house [Cockroach Community License][10] (CCL) for their enterprise offerings.

However, there's **another concerning aspect** with this situation. In the licensing comparison table below, do you see the section about Telemetry? The bit around the end of the table. 👇

![][11]

On the free trial of the paid enterprise plan, and on the free enterprise plan of CockroachDB, **users cannot opt out of Telemetry** , which makes the latter a mandatory requirement to deploy CockroachDB on non-paid self-hosted plans.

I am sure many of the people reading this won't like that, but, it is what it is. You can check out what kind of telemetry system is in use by going through [their blog][12] on it.

When announcing these changes, CEO at Cockroach Labs, [Spencer Kimball][13] added that:

> With the introduction of version 24.3 in November, we are retiring our Core offering and introducing a new Enterprise licensing structure for self-hosted users, also applied to new patch releases of versions 23.1 and later.

> This new structure will provide all users with the robust database capabilities found previously only in the self-hosted Enterprise license. CockroachDB will remain entirely source code available.

You can take a closer look at the updated licensing of CockroachDB on the [official website][14].

#### The Community Sees What's Going On

As expected, the conversation over this move has gained traction on [Hacker News][15], with one of the [community members][16], saying that:

> I understand the goal, and the perceived abuse of the Core edition. But the problem with the Enterprise edition is that it's quite expensive, "contact us" salesy, and it feels like taking a bite of this edition is possibly getting into bed with a future Oracle/landlord type of relationship where you end up squeezed by your database vendor.

I agree with what they have said, **this change has created the perfect stage for vendor lock-in**. Organizations and individuals who are drawn towards CockroachDB for its features and scalability, **will inevitably end up paying increasing amounts of money** as they grow.

This begs the question, should anyone integrate such restrictive options into core parts of their IT infrastructure? I leave you to answer that question, feel free to add your thoughts in the comments below.

**Suggested Read** 📖

![][17]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/cockcroachdb-no-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/License_proliferation#:~:text=%5B16%5D-,Vanity%20licenses,-%5Bedit%5D
[4]: https://news.itsfoss.com/open-source-source-available/
[5]: https://www.cockroachlabs.com/
[6]: https://www.cockroachlabs.com/blog/enterprise-license-announcement/
[7]: https://news.itsfoss.com/content/images/2024/08/CockroachDB_a.jpg
[8]: https://www.apache.org/licenses/LICENSE-2.0
[9]: https://en.wikipedia.org/wiki/Business_Source_License
[10]: https://www.cockroachlabs.com/cockroachdb-community-license/
[11]: https://news.itsfoss.com/content/images/2024/08/CockroachDB_b.jpg
[12]: https://www.cockroachlabs.com/blog/opentelemetry-collector-cockroachdb-datadog/
[13]: https://www.linkedin.com/in/spencerwkimball
[14]: https://www.cockroachlabs.com/enterprise-license-update/
[15]: https://news.ycombinator.com/item?id=41256222
[16]: https://news.ycombinator.com/user?id=AYBABTME
[17]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
