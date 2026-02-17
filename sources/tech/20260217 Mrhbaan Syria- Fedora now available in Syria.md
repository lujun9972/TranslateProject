[#]: subject: "Mrhbaan Syria! Fedora now available in Syria"
[#]: via: "https://fedoramagazine.org/fedora-syria/"
[#]: author: "Justin Wheeler https://fedoramagazine.org/author/jflory7/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Mrhbaan Syria! Fedora now available in Syria
======

![A dark grey banner featuring the Syrian Independence flag alongside the text "Now available in Syria", "Fedora", and the Syrian Arabic phrase "في داركم" below it. The background has a subtle triangular pattern.][1]

CC BY-SA 4.0 © Justin Wheeler

Mrhbaan, Fedora community! 👋 **I am happy to share that as of 10 February 2026, Fedora is now available in Syria.** Last week, the Fedora Infrastructure Team [lifted the IP range block][2] on IP addresses in Syria. This action restores download access to Fedora Linux deliverables, such as ISOs. It also restores access from Syria to Fedora Linux RPM repositories, the Fedora Account System, and Fedora build systems. Users can now access the various applications and services that make up the Fedora Project. This change follows a recent [update to the Fedora Export Control Policy][3]. Today, anyone connecting to the public Internet from Syria should once again be able to access Fedora.

This article explains why this is happening now. It also covers the work behind the scenes to make this change happen.

### Why Syria, why now?

You might wonder: what happened? Why is this happening now? I cannot answer everything in this post. However, the story begins in December 2024 with the fall of the Assad regime in Syria. A new government took control of the country. This began a new era of foreign policy in Syrian international relations.

Fast-forward to 18 December 2025. The United States signed the [National Defense Authorization Act for Fiscal Year 2026][4] into law. This law [repealed the 2019 Caesar Act sanctions][5]. This action removed Syria from the list of [OFAC embargoed countries][6]. The U.S. Department of the Treasury maintains this list.

This may seem like a small change. Yet, it is significant for Syrians. Some U.S. Commerce Department regulations remain in place. However, the U.S. Department of the Treasury’s policy change now allows open source software availability in Syria. The Fedora Project updated its stance to welcome Syrians back into the Fedora community. This matches actions taken by other major platforms for open source software, [such as Microsoft’s GitHub][7].

### Syria & Fedora, behind the scenes

Opening the firewall to Syria took seconds. However, months of conversations and hidden work occurred behind the scenes to make this happen. The story begins with a ticket. Zaid Ballour ([@devzaid][8]) opened [Ticket #541][9] to the Fedora Council on 1 September 2025. This escalated the issue to the Fedora Council. It prompted a closer look at the changing political situation in Syria.

Jef Spaleta and I dug deeper into the issue. We wanted to understand the overall context. The United States repealed the 2019 Caesar Act sanctions in December 2025. This indicated that the [Fedora Export Policy Control][10] might be outdated.

During this time, Jef and I spoke with legal experts at Red Hat and IBM. We reviewed the situation in Syria. This review process took time. We had to ensure compliance with all United States federal laws and sanctions. The situation for Fedora differs from other open source communities. Much of our development happens within infrastructure that we control. Additionally, Linux serves as digital infrastructure. This context differs from a random open source library on GitHub.

However, the path forward became clear after the repeal of the 2019 Caesar Act. After several months, we received approval. Fedora is accessible to Syrians once again.

#### Opening the door to Syria

Some folks may have noticed the [Fedora Infrastructure ticket][2] last week. It requested the removal of the firewall block. We also submitted a [Fedora Legal Docs Merge Request][3] to change the [Fedora Export Control Policy][10].

We wanted to share this exciting announcement now. It aligns with our commitment to the [Fedora Project vision][11]:

> “The Fedora Project envisions a world where everyone benefits from free and open source software built by inclusive, welcoming, and open-minded communities.“

We look forward to welcoming Syrians back into the Fedora community and the wider open source community at large. Mrhbaan!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-syria/

作者：[Justin Wheeler][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jflory7/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/02/fedora-syria-816x345.png
[2]: https://forge.fedoraproject.org/infra/tickets/issues/13135
[3]: https://gitlab.com/fedora/legal/fedora-legal-docs/-/merge_requests/348
[4]: https://en.wikipedia.org/wiki/National_Defense_Authorization_Act_for_Fiscal_Year_2026
[5]: https://sana.sy/en/politics/2284409/
[6]: https://ofac.treasury.gov/sanctions-programs-and-country-information
[7]: https://github.blog/company/github-is-enabling-broader-access-for-developers-in-syria-following-new-government-trade-rules/
[8]: https://discussion.fedoraproject.org/u/devzaid
[9]: https://discussion.fedoraproject.org/t/fedora-council-tickets-ticket-541-request-to-update-export-control-policy-after-us-sanctions-has-been-lifted-on-syria/163366
[10]: https://docs.fedoraproject.org/en-US/legal/export/
[11]: https://docs.fedoraproject.org/en-US/project/#_our_vision
