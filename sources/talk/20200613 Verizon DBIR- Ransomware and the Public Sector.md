[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Verizon DBIR: Ransomware and the Public Sector)
[#]: via: (https://www.networkworld.com/article/3562475/verizon-dbir-ransomware-and-the-public-sector.html)
[#]: author: (CIS )

Verizon DBIR: Ransomware and the Public Sector
======
How a basic cyber hygiene program can limit impact
CIS

Verizon's Data Breach Investigations Report ([DBIR][1]) provides an annual analysis of security incidents and data breaches. The information and analysis are categorized by sector. Public sector organizations are key contributors to the report each year.

The report highlights that "the Public Administration sector is an illustration of what good partner visibility into an industry looks like. The bulk of our data in this vertical comes from partners inside the United States federal government who have a finger on the pulse of data breaches inside Public Administration."

The 2020 DBIR found that ransomware continues to be a top cyber-attack and that this type of attack disproportionately affects the public administration sector (60% of malware vs. 27% of malware in all sectors). Fortunately, it's possible to limit the success of ransomware attacks through good cyber hygiene and defensive strategies.

## **Ransomware Results from the Verizon DBIR**

The DBIR contains results from an analysis of 157,525 cybersecurity incidents. Of the incidents analyzed, 3,950 were confirmed data breaches. Ransomware is the third most common malware breach variety and the second most common malware incident variety.

A total of 16 industries were covered, including public administration, healthcare, and information. The report found:

  * 60% of malware affecting public entities was ransomware
  * 40% of breaches affecting public entities involved web-based applications
  * 70% of breaches were perpetrated by external actors
  * 55% of breaches were assessed to be directly linked to organized criminal actors
  * 22% of breaches included social attacks



## **Defensive Strategies Against Ransomware**

It's possible to limit the impact of ransomware by improving your organization's cyber hygiene. In fact, many of the safeguards covered in [CIS Controls Implementation Group 1][2] support the basic cyber hygiene program that can limit the impact of ransomware attacks. The following three steps are a few core defensive measures your organization should consider implementing.

  1. ## **Patching and Updates**




According to the DBIR, "unpatched vulnerabilities in your web application infrastructure may lead to them being found by someone with a set of tools to exploit them in an automated fashion. Keeping your infrastructure patches up to date is certainly a security best practice."

Safeguards found in CIS Controls Implementation Group 1 confirm this recommendation:

  * CIS Control 3.4: Deploy Automated Operating System Patch Management Tools
  * CIS Control 3.5: Deploy Automated Software Patch Management Tools



Applying the latest updates and making sure all of your organization’s operating systems, applications, and software are updated regularly will help close the security gaps that attackers are looking to exploit.

  2. ## **Backups (Maintain Offsite or Out-of-Band)**




The MS-ISAC recommends that recurring backups, as part of your organization's disaster recovery plan, are the single most effective way of limiting the impact of ransomware attacks and recovering from a ransomware infection. Backup files should be protected and stored separately offsite or out-of-band from the source production files to avoid your backup files being targeted by attackers. Using cloud services could help mitigate a ransomware infection, as many retain previous versions of files allowing you to roll back to an unencrypted version.

[7 Steps to Help Prevent and Limit the Impact of Ransomware][3]

  3. ## **Leverage an Intrusion Detection System (IDS)**




According to the DBIR, "at least one piece of ransomware was blocked by 18% of organizations through the year." Additionally, ransomware "presented a fairly good detection rate of 82% in simulated incident data."

An Intrusion Detection System (IDS) looks for malicious activity by comparing network traffic logs to signatures that detect known malicious activity. When ransomware strikes, it’s important for your organization to be notified and investigate quickly. According to data from Crowdstrike, it should take mature organizations 10 minutes to investigate an intrusion. However, only 10% of organizations are able to meet this benchmark. ([Source][4])

[][5] CIS

[Albert Network Monitoring][6] is an IDS solution tailored to U.S. State, Local, Tribal, and Territorial (SLTT) government organizations. The custom signature set utilized by Albert enables it to be very effective in detecting ransomware. Organizations using Albert that are affected by ransomware are typically notified within six minutes of malicious activity.

## **Takeaways from the DBIR**

Ransomware threats continue to increase, especially for the public sector. Basic cyber hygiene is an effective strategy for limiting the success of ransomware attacks.

[**Learn more about Albert**][7]

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3562475/verizon-dbir-ransomware-and-the-public-sector.html

作者：[CIS][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.verizon.com/dbir
[2]: https://www.cisecurity.org/controls/cis-controls-implementation-groups/?utm_source=NetworkWorld
[3]: https://www.cisecurity.org/blog/7-steps-to-help-prevent-limit-the-impact-of-ransomware/?utm_source=NetworkWorld
[4]: https://subscriber.politicopro.com/cybersecurity/whiteboard/2019/11/crowdstrike-report-paints-dire-picture-of-breach-response-capabilities-3974144
[5]: https://images.idgesg.net/images/article/2020/06/dbir-image-100848675-orig.jpg
[6]: https://www.cisecurity.org/services/albert-network-monitoring/?utm_source=NetworkWorld
[7]: https://learn.cisecurity.org/albert?utm_source=NetworkWorld
