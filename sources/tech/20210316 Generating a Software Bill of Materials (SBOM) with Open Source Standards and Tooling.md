[#]: subject: (Generating a Software Bill of Materials (SBOM) with Open Source Standards and Tooling)
[#]: via: (https://www.linux.com/news/generating-a-software-bill-of-materials-sbom-with-open-source-standards-and-tooling/)
[#]: author: ( https://www.linux.com/author/)
[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )

Generating a Software Bill of Materials (SBOM) with Open Source Standards and Tooling
======

Every month there seems to be a new software vulnerability showing up on social media, which causes open source program offices and security teams to start querying their inventories to see how FOSS components they use may impact their organizations. 

Frequently this information is not available in a consistent format within an organization for automatic querying and may result in a significant amount of email and manual effort. By exchanging software metadata in a standardized software bill of materials (SBOM) format between organizations, automation within an organization becomes simpler, accelerating the discovery process and uncovering risk so that mitigations can be considered quickly. 

In the last year, we’ve also seen standards like [OpenChain][1] (ISO/IEC 5320:2020) gain adoption in the supply chain. Customers have started asking for a bill of materials from their suppliers as part of negotiation and contract discussions to conform to the standard. OpenChain has a focus on ensuring that there is sufficient information for license compliance, and as a result, expects metadata for the distributed components as well. A software bill of materials can be used to support the systematic review and approval of each component’s license terms to clarify the obligations and restrictions as it applies to the distribution of the supplied software and reduces risk. 

Kate Stewart, VP, Dependable Embedded Systems, The Linux Foundation, will host a complimentary mentorship webinar entitled **Generating Software Bill Of Materials** on Thursday, March 25 at 7:30 am PST. This session will work through the minimum elements included in a software bill of materials and detail the reasoning behind why those elements are included. To register, [please click here][2]. 

[Register for webinar][2]

There are many ways this software metadata can be shared. The common SBOM document format options ([SPDX][3], [SWID][4], and [CycloneDX][5]) will be reviewed so that the participants can better understand what is available for those just starting. 

This mentorship session will work through some simple examples and then guide where to find the next level of details and further references. 

At the end of this session, participants will be on a secure footing and a path towards the automated generation of SBOMs as part of their build and release processes in the future. 

The post [Generating a Software Bill of Materials (SBOM) with Open Source Standards and Tooling][6] appeared first on [Linux Foundation][7].

--------------------------------------------------------------------------------

via: https://www.linux.com/news/generating-a-software-bill-of-materials-sbom-with-open-source-standards-and-tooling/

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linux.com/author/
[b]: https://github.com/lujun9972
[1]: https://www.openchainproject.org/
[2]: https://linuxfoundation.org/webinars/generating-software-bill-of-materials/
[3]: https://github.com/spdx
[4]: https://csrc.nist.gov/projects/software-identification-swid/
[5]: https://cyclonedx.org/
[6]: https://www.linuxfoundation.org/en/blog/generating-a-software-bill-of-materials-sbom-with-open-source-standards-and-tooling/
[7]: https://www.linuxfoundation.org/
