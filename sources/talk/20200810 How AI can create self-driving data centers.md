[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How AI can create self-driving data centers)
[#]: via: (https://www.networkworld.com/article/3568354/how-ai-can-create-self-driving-data-centers.html)
[#]: author: (Neal Weinberg )

How AI can create self-driving data centers
======
Early adopters are driving the use of AI to optimize power and cooling systems, automate predictive maintenance, and improve workload distribution in enterprise data centers.
Just_Super / Getty Images

Most of the buzz around artificial intelligence (AI) centers on autonomous vehicles, chatbots, [digital-twin][1] technology, robotics, and the use of AI-based 'smart' systems to extract business insight out of large data sets. But AI and machine learning (ML) will one day play an important role down among the server racks in the guts of the enterprise data center. 

AI's potential to boost [data-center][2] efficiency – and by extension improve the business – falls into four main categories:

  * **Power management**: AI-based power management can help optimize heating and cooling systems, which can cut electricity costs, reduce headcount, and improve efficiency. Representative vendors in this area include Schneider Electric, Siemens, Vertiv and Eaton Corp.
  * **Equipment management:** AI systems can monitor the health of servers, [storage][3], and networking gear, check to see that systems remain properly configured, and predict when equipment is about to fail. According to Gartner, vendors in the AIOps IT infrastructure management (ITIM) category include OpsRamp, Datadog, Virtana, ScienceLogic and Zenoss.
  * **Workload management:** AI systems can automate the movement of workloads to the most efficient infrastructure in real time, both inside the data center and, in a [hybrid-cloud][4] environment, between on-prem, cloud and [edge][5] environments. There are a growing number of smaller players offering AI-based workload optimization, including Redwood, Tidal Automation and Ignio. Heavyweights like Cisco, IBM and VMware also have offerings.
  * **Security:** AI tools can 'learn' what normal network traffic looks like, spot anomalies, prioritize which alerts require the attention of security practitioners, help with post-incident analysis of what went wrong, and provide recommendations for plugging holes in enterprise security defenses. Vendors offering this capability include VectraAI, Darktrace, ExtraHop and Cisco.



Put it all together and the vision is that AI can help enterprises create highly automated, secure, self-healing data centers that require little human intervention and run at high levels of efficiency and resiliency.

### Tech Spotlight: [AI and machine learning][6]

  * [5 machine learning success stories: An inside look][7] (CIO)
  * [AI at work: Your next co-worker could be an algorithm][8] (Computerworld)
  * [How secure are your AI and machine learning projects?][9] (CSO)
  * [How to choose a cloud machine learning platform][10] (InfoWorld)



"AI automation can scale to interpret data at levels beyond human capacity, gleaning imperative insights needed for optimizing energy use, distributing workloads and maximizing efficiency to achieve higher data-center asset utilization," explains Said Tabet, distinguished engineer in the global CTO office at [Dell Technologies][11].

Of course, much like the promise of self-driving cars, the self-driving data center isn't here yet. There are significant technical, operational, and staffing barriers that stand in the way of AI breakthroughs in the data center. Adoption is nascent today, but the potential benefits will keep enterprises looking for opportunities to move the needle.

## Power management taps into server workload management

Data centers are estimated to consume 3% of the global electric supply and cause about 2% of greenhouse gas emissions, so it's no surprise that so many enterprises are taking a hard look at data-center power management, both to save money and to be environmentally responsible.

Daniel Bizo, senior analyst at [451 Research][12], says AI-based systems can help data-center operators understand current or potential cooling issues, such as insufficient cold air delivery due to, for example, a high-density cabinet that's blocking the air flow, an underperforming HVAC unit, or inadequate air containment between hot and cold aisles.

AI promises to deliver benefits "beyond what's possible with simply good facilities design," Bizo says. AI systems "can learn a facility by correlating HVAC systems data and environmental sensory readings" on the data-center floor.

Power management is the low-hanging fruit, adds Greg Schulz, founder of IT advisory and consultancy firm [StorageIO][13]. "Today, it's about productivity, about getting more work done per BTU, more work done per watt of energy, which means working smarter and getting the equipment to work smarter."

There's also a capacity planning angle. In additional to looking for hot spots and cool spots, AI systems can make sure data centers are powering the right number of physical servers and also have the available capacity to spin up (and spin down) new physical servers if there's a temporary burst in demand.

Schulz adds that power management tools are developing hooks up into the systems that manage equipment and workloads. If sensors detect that a server is running too hot, for example, the system might quickly and automatically move workloads to an underutilized server in order to avoid a potential outage that might impact mission critical applications. The system could then investigate the cause of the server overheating – it might be a fan that failed (an HVAC issue), a physical component that is about to crash (an equipment issue), or maybe the server has just been overloaded (a workload issue). 

## AI-driven health monitoring, configuration management oversight

Data centers are full of physical equipment that needs regular maintenance. AI systems can go beyond scheduled maintenance and help with the collection and analysis of telemetry data that can pinpoint specific areas that require immediate attention. "AI tools can sniff through all of that data and spot patterns, spot anomalies," Schulz says.

"Health monitoring starts with checking if equipment is configured correctly and performing to expectations," Bizo adds. With hundreds or even thousands of IT cabinets with tens of thousands of components, such mundane tasks can be labor intensive, and thus not always performed in a timely and thorough fashion."

He points out that predictive equipmen- failure modeling based on vast amounts of sensory data logs can "spot a looming component or equipment failure and assess whether it needs immediate maintenance to avoid any loss of capacity that might cause a service outage."

Michael Bushong, vice president of enterprise and cloud marketing at [Juniper Networks][14], argues that enterprise data-center operators should ignore some of the overpromises and hype associated with AI, and focus on what he calls "boring innovations."

Yes, AI systems may one day "tell me what's wrong and fix it," but at this point, many data-center operators would settle for "if something goes wrong, tell me where to look," Bushong says.

Dependency mapping is also an important, but not especially exciting area where AI can be useful. If data-center managers are making policy changes to firewalls or other devices, what might the unintended consequences be? "If I propose a change, it's useful to know what might be inside the blast radius," Bushong says.

Another important aspect of keeping equipment running smoothly and safely is controlling something called configuration drift, a data-center term for the way that ad hoc configuration changes over time can add up to create problems. AI can be used as "an additional safety check" to identify impending configuration-based data-center issues, Bushong says.

## AI and security

According to Bizo, AI and machine learning "can simplify event handling (incident response) by performing rapid classification and clustering of events to identify important ones and separate them from the noise. Quicker root-cause analysis helps human operators make informed decisions and act on them."

AI can be particularly useful in real-time intrusion detection, adds Schulz. AI-based systems can detect, block and isolate threats and can then go back and conduct a forensic investigation to determine exactly what happened and what vulnerabilities the hacker was able to exploit.

Security professionals working in a security operations center (SOC) are oftentimes overloaded with alerts, but AI-based systems can scan through vast amounts of telemetry data and log information, clearing mundane tasks off the deck, so that security pros are freed up to handle deeper types of investigations.

## AI-based workload optimization

At the application layer, AI has the potential to automate the movement of workloads to the appropriate landing spot, whether that's on-premises or in the cloud. "AI/ML should in the future make real-time decisions on where to place workloads against the multitude of specifications for performance, cost, governance, security, risk and sustainability," Bizo says.

For example, workloads could be automatically moved to the most power-efficient servers, while making sure that the servers operate at peak efficiency, which would be 70-80% utilization. AI systems could integrate performance data into the equation, so time-sensitive apps are running on the high-efficiency servers, while at the same time making sure that excess energy is not being burned on applications that don't require fast execution, Bizo says.

AI-based workload optimization has caught the eye of MIT researchers, who announced last year that they had developed an AI system that automatically learns how to schedule data-processing operations across thousands of servers.

But, as Bushong points out, the reality is that workload optimization today is the province of the [hyperscalers][15] like Amazon, Google and Azure, not the average enterprise data center. And there are a number of reasons for that.

## The challenges of implementing AI

Optimizing and automating the data center is an integral part of ongoing digital transformation initiatives. Dell's Tabet adds that "with COVID-19, many companies are now looking at further automation, pushing the ideas of 'digital data centers' that are AI-driven and capable of self-healing."

Google announced in 2018 that it had turned control of its cooling systems in several of its hyperscale data centers to an AI program, and the company reported that the recommendations provided by the AI algorithm delivered a 40% reduction in energy usage.

But, for companies not named Google, AI in the data center is "largely aspirational," Bizo says. "Some AI/ML features are available in event handling, infrastructure health and cooling optimization. But it will take more years before AI/ML models achieve more visible breakthroughs beyond what's possible with standard Data Center Infrastructure Management ([DCIM][16]) today. Much like with autonomous vehicle development, early stages may be interesting, yet far from the breakthrough economics/business case it ultimately promises."

Some of the barriers, according to Tabet, are that "the right people need to either be hired or trained to manage the system. Another issue to be aware of is the need for data standards and relevant architectures."

Gartner puts it this way: "AIOps platform maturity, IT skills and operations maturity are the chief inhibitors. Other emerging challenges for advanced deployments include data quality, and lack of data science skills" within IT infrastructure and operations teams.

Bushong adds that the biggest barrier is always the people. He points out that going out and hiring data scientists is a challenge for many enterprises, and training existing employees is also a hurdle.

Plus, there's a long history of employees resisting technologies that take control out of their hands, Bushong says. He notes that software-defined networking ([SDN][17]) has been around for a decade, yet more than three-fourths of IT operations are still CLI-driven.

"We have to believe that operators across all manner of infrastructure are prepared to give up control to AI," Bushong says. "If a group of people don't yet trust controllers to make decisions, how do you train, educate, and comfort a group of people to make a transition of this magnitude when the prevailing attitude in the industry is that, if I do this, I will lose my job?'"

That's why Bushong suggests that enterprises take those small, boring steps toward AI and not get caught up in the hype that so often surrounds a new technology.

Join the Network World communities on [Facebook][18] and [LinkedIn][19] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3568354/how-ai-can-create-self-driving-data-centers.html

作者：[Neal Weinberg][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3280225/what-is-digital-twin-technology-and-why-it-matters.html
[2]: https://www.networkworld.com/article/3223692/what-is-a-data-centerhow-its-changed-and-what-you-need-to-know.html
[3]: https://www.networkworld.com/article/3256312/what-is-a-san-and-how-does-it-differ-from-nas.html
[4]: https://www.networkworld.com/article/3233132/what-is-hybrid-cloud-computing.html
[5]: https://www.networkworld.com/article/3224893/what-is-edge-computing-and-how-it-s-changing-the-network.html
[6]: https://www.cio.com/article/3570613/ai-and-machine-learning-the-new-enterprise-reality.html
[7]: https://www.cio.com/article/3225445/machine-learning-success-stories.html
[8]: https://www.computerworld.com/article/3568642/ai-at-work-your-next-co-worker-could-be-an-algorithm.html
[9]: https://www.csoonline.com/article/3434610/how-secure-are-your-ai-and-machine-learning-projects.html
[10]: https://www.infoworld.com/article/3568889/how-to-choose-a-cloud-machine-learning-platform.html
[11]: https://www.delltechnologies.com/en-us/index.htm
[12]: https://451research.com/
[13]: https://storageio.com/index.html
[14]: https://www.juniper.net/us/en/
[15]: https://www.networkworld.com/article/3541228/supply-chain-woes-put-the-brakes-on-hyperscale-data-centers.html
[16]: https://www.networkworld.com/article/3269265/data-center-management-what-does-dmaas-deliver-that-dcim-doesnt.html
[17]: https://www.networkworld.com/article/3209131/what-sdn-is-and-where-its-going.html
[18]: https://www.facebook.com/NetworkWorld/
[19]: https://www.linkedin.com/company/network-world
