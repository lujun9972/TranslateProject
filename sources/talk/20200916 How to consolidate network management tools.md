[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to consolidate network management tools)
[#]: via: (https://www.networkworld.com/article/3574852/how-to-consolidate-network-management-tools.html)
[#]: author: (Neal Weinberg )

How to consolidate network management tools
======
Enterprise IT shops are getting serious about winnowing the tools they use for network capacity planning, monitoring, event correlation, configuration management and more.
Sorayut / MF3D / Getty Images

Network executives are making strides in their ongoing efforts to reduce network management tool sprawl, but there's still plenty of room for improvement on the road to a consolidated, platform-based toolset.

Nearly two-thirds of enterprises (64%) in EMA's [Network Management Megatrends 2020][1] report indicated they use between four and 10 tools, and another 17% use more than 10 tools. And that's just the tools that companies will admit to.

In the same way that individual business units go out and acquire their own productivity applications without telling anyone (shadow IT), network managers have their own bags of tricks, which include open source tools as well as tools developed in-house. The true number of tools in a large enterprise, if you include every advanced script written in-house, could hit triple digits, suggests Mark Leary, research director for network analytics at [IDC][2].

**READ MORE:** [Are new Cisco certs too much? Network pros react][3]

The problem is that having a patchwork of multiple, siloed tools can be expensive and leads to "fragmented workloads, inefficient data collection and sharing, and difficulty in escalating problems," according to EMA.

Network execs have gotten the message. The number of enterprises using 16-20 tools to monitor and troubleshoot their networks dropped from 8% to 5% between 2018 and 2020, and those using 11-15 declined from 12% to 9%, according to EMA survey. The sweet spot appears to be 4-5 tools, with 41% of respondents indicating that's how many separate tools they're using, a significant uptick from 25% in 2018.

When asked about their purchasing strategies, 35% of respondents said the goal was fully integrated, multi-function platforms, while only 27% cited best of breed from multiple vendors. However, the EMA report also notes that "for many companies a unified tool strategy is an aspiration, not a reality."

One major hurdle for network execs is that they are being asked to maintain uptime and performance amid the increasing complexity of the network, which now has to accommodate [IoT][4] devices, cloud traffic, SDN, [SD-WAN][5], more people working from home, [5G][6], you name it.

All of these new demands fuel the temptation to acquire additional tools.

### How did we get here?

You can't fix a problem until you figure out the root cause. In the case of network management, the problem is that there are many tools that do one or two things really well but no tool that does everything well.

There are tools that discover and [map the network][7]. There are tools that monitor network traffic. There are tools that troubleshoot. Tools that perform root cause analysis and event correlation. Tools that focus on configuration management and change management. Tools for application performance management. Tools that do [capacity planning][8].

"There are tools that do multiple things, but they still don't do everything," says EMA analyst Shamus McGillicuddy. Not only that, each tool has its own strengths and weaknesses. "Maybe your configuration tool can do basic flow analysis, but then maybe they don't have change control. If you want to do configuration management in a more sophisticated way, or the tool doesn't scale, maybe you buy a second flow monitor tool that scales more."

Then there are dozens of open source tools that are tempting to download because they're free. "I'm not getting everything I need from what I have, so I'll just download an open source tool," McGillicuddy says. The downside is not only lack of integration but also the time and effort it takes to patch and update the open source tool.

Leary adds that one of the major trends in networking is that network managers are [becoming programmers][9], building their own tools in order to automate specific network management functions. The proliferation of custom tools only exacerbates the problem in the long run.

### What you can do

There are several best practices and guiding principles to help organizations consolidate and optimize their network management toolsets.

  * **Conduct an inventory of vendor, open source and in-house tools.** Try to identity overlap, tools that may have been used by a single network manager who may have left the company, cases in which two network engineers each use their pet tool for the same functionality, or where a redundant tool is being used only as a backup.
  * **Consider timing.** Once candidates for consolidation have been identified, the best time to make a move is when licenses are expiring or when vendors come out with a new version that might have additional functionality, allowing the organization to eliminate even more tools.
  * **Look for platforms, not point products.** Identify vendors that are putting together a broad suite of integrated tools.
  * **Identify vendors that are building a cross-vendor ecosystem.** Before doing business with a vendor, ask them to walk you through the ways that you can take data from their tool and integrate it with data from other vendors on a single management platform.
  * **Set up formal best practices and processes for managing the toolset.**
  * **Look for ways to consolidate toolsets across other IT groups. **Consider tools used by security and DevOps, for example.
  * **Automate as many processes as possible.**
  * **Consider data-sharing and correlation capabilities.** Look for vendors that enable their log data to be consumed by AIOps tools that use machine learning to perform event correlation and other network management functions.



Consolidation is an ongoing effort and takes time, training and planning. At Guardian Life Insurance, it took more than a year for the company to replace six disparate tools with the SaaS-based Zenoss platform.

### Guardian slashes costs, improves cross-IT tool integration

When Avronil Chatterjee arrived at [Guardian][10] as technical manager for enterprise monitoring five years ago, he encountered multiple point solutions, decentralized monitoring by the network team, and a lack of correlation among the networking, server, security and application development teams.

He began investing in agent-less systems that could help the company monitor and troubleshoot its network of more than 1,000 network devices and more than 4,000 servers in both on-premises and cloud environments.

Chatterjee settled on the [Zenoss][11] platform. "We were looking for one platform that could do it all," Chatterjee says. He is using Zenoss for network monitoring, application performance management and event correlation.

The move enabled him to slash his $1 million annual licensing expenditure for network management tools by 70% right off the bat. "That was a pretty big win from a cost perspective," Chatterjee says.

But the consolidation is paying dividends in other areas as well. Operational efficiency is much better, he doesn't have to manage relationships with as many vendors as before, and he doesn't need as many staffers to manage the tools, so he can cross-train his team to perform other tasks.

Of course, no large enterprise can get by with only one tool. While the move to Zenoss enabled Chatterjee to replace some legacy HP networking tools, plus several additional point products, he is streaming security and application log data into a tool from [Splunk][12] for advanced performance and capacity planning.

He is also using [AppDynamics][13] for application performance management, particularly when it comes to optimizing the response time and overall performance of the company's ecommerce site. And he is using an AIOps tool from [Resolve][14] in order to increase IT automation and orchestration.

Chatterjee says the transition entailed "a lot of heavy lifting." One aspect of the transition was training staffers. "Change is always difficult, and there was a little bit of apprehension. It took some time for users to get comfortable with the new tool and really get on board. But it worked out well," he says.

The plan was to roll out the new system in "phases and waves" with a combination of soft launches, as well as operating the two systems in parallel for a period of time. Looking ahead, Chatterjee says his goals are to increase the level of automation and to introduce natural language processing so that senior managers can ask an answer-bot "who are the top talkers?" rather than have to navigate dashboards, menus, and command lines.

### Consolidation becoming even more imperative

While it would be ideal to get down to one magic tool that can do it all, realistically enterprises will continue to have multiple network management tools for the foreseeable future. McGillicuddy says companies shouldn't get too hung up on the number of tools. Instead, they should focus more on getting the best functionality from each tool and making sure that tools are integrated within the networking team, and, if possible, across security, server, DevOps and other groups.

"While EMA advises a consolidated approach to network management, large toolsets are not necessarily a harbinger of doom. However, EMA believes that enterprises with large toolsets can find opportunities to integrate those toolsets for unified workflows and better integration," McGillicuddy says.

Leary points out that one of the lessons learned from the current pandemic is that network teams need to be ready for anything that comes along that could significantly alter network traffic patterns.

Toward that end, network managers should look for products that can do more than one thing, products that provide automation, that are part of a larger platform and that have the ability to provide a common set of data points in order to enable analysis of that data, Leary says.

Join the Network World communities on [Facebook][15] and [LinkedIn][16] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3574852/how-to-consolidate-network-management-tools.html

作者：[Neal Weinberg][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://nam05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.enterprisemanagement.com%2Fresearch%2Fasset.php%2F3899%2FNetwork-Management-Megatrends-2020&data=02%7C01%7C%7Cbade00007e4e4dd3fb8408d83571942f%7C3aedb78fc8e04326888a74230d1978ff%7C0%7C0%7C637318109226550621&sdata=daCUOACULU5qjW5OJcRObJLvwblONg65sqH2OElOQ8M%3D&reserved=0
[2]: https://www.idc.com/
[3]: https://www.networkworld.com/article/3446044/are-new-cisco-certs-too-much-network-pros-react.html
[4]: https://www.networkworld.com/article/3207535/what-is-iot-the-internet-of-things-explained.html
[5]: https://www.networkworld.com/article/3031279/sd-wan-what-it-is-and-why-you-ll-use-it-one-day.html
[6]: https://www.networkworld.com/article/3203489/what-is-5g-fast-wireless-technology-for-enterprises-and-phones.html
[7]: https://www.networkworld.com/article/2924320/8-free-wi-fi-stumbling-and-surveying-tools-for-windows-and-mac.html
[8]: https://www.networkworld.com/article/3338100/using-ai-to-improve-network-capacity-planning-what-you-need-to-know.html
[9]: https://www.networkworld.com/article/3332923/software-cloud-lead-in-demand-skills-for-network-pros.html
[10]: https://www.guardianlife.com/
[11]: https://www.zenoss.com/
[12]: https://www.splunk.com/
[13]: https://www.appdynamics.com/
[14]: https://resolve.io/aiops
[15]: https://www.facebook.com/NetworkWorld/
[16]: https://www.linkedin.com/company/network-world
