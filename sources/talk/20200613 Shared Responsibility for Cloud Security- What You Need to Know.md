[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Shared Responsibility for Cloud Security: What You Need to Know)
[#]: via: (https://www.networkworld.com/article/3562377/shared-responsibility-for-cloud-security-what-you-need-to-know.html)
[#]: author: (CIS )

Shared Responsibility for Cloud Security: What You Need to Know
======
Check out CIS Controls for best practice guidance
metamorworks

The COVID-19 pandemic changed business practices worldwide. The traditional workplace transformed; for many, the “new norm” is now a home office and a virtual workplace with employees holding meetings via video teleconferencing tools and communicating through email and applications like Slack, Microsoft Teams, and Google Hangouts. The cloud is busier than ever, making cloud security more important than ever.

In the public cloud, there’s a shared responsibility between the Cloud Service Provider (CSP) and the user (you). Security for things like data classification, network controls, and physical security need clear owners. The division of these responsibilities is known as the shared responsibility model for cloud security. Check out this chart to see where the responsibilities lie within different cloud environments.

[][1] CIS

Sources:
1\. [Microsoft Azure][2] [
2.][2] [Amazon Web Services][3]

## **Doing Your Part in the Shared Responsibility Model**

Holding up your end of the bargain with the shared responsibility model is easier said than done. That's because your responsibilities will vary depending on the cloud environment you’re operating in. No matter which cloud service you use (IaaS, PaaS, SaaS, or FaaS), protection of your organization's data is always up to you. That’s a big responsibility! According to Gartner, over the next three years, “at least 95% of cloud security failures will be the customer’s fault.” CIS is here to help your organization avoid becoming one of those statistics. Below are three ways you can help fulfill your security responsibilities using CIS resources.

## **Prevent Common Cyber-Attacks**

Before diving into the granular details like verifying that your GPG keys are configured properly to avoid malware, your organization should assess your overall cyber hygiene. Measuring your organization against a security best practice, such as the CIS Controls, will help you take stock of your cybersecurity health.

The CIS Controls are a free, internationally-recognized set of cybersecurity best practices. Prioritized and prescriptive in nature, they are the definition of "how" to achieve an effective cybersecurity program; they serve as a starting point for organizations seeking to improve their cyber defense.

For organizations in the cloud to use CIS Controls, we have the CIS Controls Cloud Companion Guide. The guide outlines the four main types of cloud environments and maps them to the CIS Controls: Infrastructure as a Service (IaaS), Software as a Service (SaaS), Platform as a Service (PaaS), and Function as a Service (FaaS).

The guide also examines unique risks (vulnerabilities, threats, consequences, and security responsibilities) to cloud environments. These risks drive the priority of enterprise security requirements (e.g., availability, integrity, and confidentiality of data).

The CIS Controls Cloud Companion Guide will help consumers tailor the CIS Controls to their cloud environment. It’s an essential starting point for those who wish to conduct a security improvement assessment. In addition to the free pdf guide, CIS provides a downloadable spreadsheet to track conformance to these recommendations.

[Download the guide here][4]

## **Implement a Secure Standard**

Whether you're operating on-prem or in the cloud, one thing remains constant: your systems operate software and hardware under different assumed security responsibilities than what’s actually expected of you. This is one of many reasons why you should review all of your system's configurations and implement secure recommendations, such as the CIS Benchmarks.

The CIS Benchmarks are the only vendor-agnostic cybersecurity configuration guidelines both developed and accepted by academia, government, and business. They’re designed to safeguard endpoint devices and systems against today’s evolving cyber threats. CIS provides foundational security benchmarks for three of the major CSPs:

  * [CIS Amazon Web Services (AWS) Foundations Benchmark][5]
  * [CIS Azure Foundations Benchmark][6]
  * [CIS Google Cloud Platform (GCP) Foundations Benchmark][7]



These CIS Benchmarks provide prescriptive guidance to help with identity and access management, logging and monitoring, and networking for each of the major cloud platforms.

## **Evolve with the Cloud**

Who's responsible for what can get more complicated as cloud services evolve. CSPs are constantly adding new services that come with new configuration and security tools to manage those services. While native security tools can be convenient, they may not cover all of your configuration management needs. You’ll also need to ensure that you apply all OS- and container-level security updates. To avoid a gap in protection, consider implementing third-party tools to harden systems in addition to the CSP’s native security tools. It’s better to have overlaps between third-party security tools and the CSP’s security services than to have gaps in your cloud security.

CIS Hardened Images are pre-configured virtual machine images that take the base image from your CSP and apply the security configuration guidelines of the CIS Benchmarks. They are independently hardened virtual machine images, and help ensure your organization's workloads are more secure than if they were on a base OS. CIS Hardened Images are used by thousands of organizations worldwide to secure OS and applications in the cloud. They’re regularly updated to ensure the latest security configurations are in place, giving you peace of mind while working on AWS, Microsoft Azure, Google Cloud Platform, or Oracle Cloud.

[View all CIS Hardened Images][8]

## **CIS Shared Responsibility Model Resource**

The shared responsibility model for cloud security provides clarity on security expectations for public cloud users and cloud service providers. However, an understanding of the expectation is just the first step. Users and CSPs must take action on these responsibilities by creating policies and procedures for their portion of cloud security. In order to do this, both parties should use cloud security tools and resources that directly address the needs of their cloud environment.

Used together or individually, CIS Controls, CIS Benchmarks, and CIS Hardened Images can help organizations moving to the cloud navigate the transition and the shared responsibility model more easily, transforming the virtual workplace into a secure “new norm.” In this white paper, we provide a deep dive into the shared responsibility model for cloud security, the division of user and CSP responsibilities, and how CIS resources help meet those responsibilities.

[**Download the White Paper**][9]

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3562377/shared-responsibility-for-cloud-security-what-you-need-to-know.html

作者：[CIS][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://images.idgesg.net/images/article/2020/06/12-image-1-100848679-orig.jpg
[2]: https://docs.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility
[3]: https://aws.amazon.com/compliance/shared-responsibility-model/
[4]: https://www.cisecurity.org/white-papers/cis-controls-cloud-companion-guide/?utm_source=NetworkWorld
[5]: https://www.cisecurity.org/benchmark/amazon_web_services/?utm_source=NetworkWorld
[6]: https://www.cisecurity.org/benchmark/azure/?utm_source=NetworkWorld
[7]: https://www.cisecurity.org/benchmark/google_cloud_computing_platform/?utm_source=NetworkWorld
[8]: https://www.cisecurity.org/cis-hardened-image-list/?utm_source=NetworkWorld
[9]: https://learn.cisecurity.org/shared-responsibility-white-paper?utm_source=NetworkWorld
