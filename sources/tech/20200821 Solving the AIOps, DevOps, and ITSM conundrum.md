[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Solving the AIOps, DevOps, and ITSM conundrum)
[#]: via: (https://opensource.com/article/20/8/aiops-devops-itsm)
[#]: author: (Will Kelly https://opensource.com/users/willkelly)

Solving the AIOps, DevOps, and ITSM conundrum
======
Quickly shifting to remote work has enterprises looking to meet the ops
needs of a suddenly distributed team, and there are open source options
to get them there.
![two women kanban brainstorming and brainmapping with post-it notes on a whiteboard ][1]

The recent mad rush to scale to remote work may prove to be a key chapter in DevOps and AIOps evolution. This need for rapid, widescale change is creating a real conundrum concerning AIOps, DevOps, and ITSM, as organizations seek the best monitoring and incident response solution for their now distributed enterprises.

The key question both the DevOps and IT service management (ITSM) communities need to answer is how quickly they can pivot and adapt to increasing demands for operational intelligence.

### What's AIOps?

Artificial intelligence for IT Operations (AIOps) brings together artificial intelligence (AI), analytics, and machine learning (ML) to automate the identification and remediation of IT operations issues.

An AIOps system learns from your data and adapts how your application works. These systems won't do the same thing each time. AIOps systems can also run through all workable solutions to a problem, including solutions that some developers may miss in their human analysis of an infrastructure issue. However, we aren't at a place where AIOps systems—open source or proprietary—can replace experienced [systems administrators][2] and other operations team members.

Some better known open source contributions to AIOps include:

  * [Prometheus][3] is the first tool that comes to mind when discussing open source monitoring solutions. It's a graduate of a [Cloud Native Computing Foundation][4] (CNCF) project which focuses on monitoring for site reliability engineering (SRE). It simplifies pulling numerical metrics from a metrics endpoint.
  * [Grafana][5] is an open source metric analytics and visualization suite. As a data visualization tool, Grafana is popular among Prometheus users to visualize the metrics.
  * [Elastic Stack][6] is a suite of open source products from Elastic designed to help users search, analyze, and visualize data from any type of source, in any format, in real time. When you run Elastic Stack with Elastic Search, it provides monitoring and logging solutions.



All three of these technologies do not use AI to resolve issues but are still foundational to the practice of AIOps since consistent, structured data is required to inform decisions. A skilled engineering team, SRE or otherwise, could add open source technologies like [TensorFlow][7] or tooling from the [SciPy toolkit][8] to get to automated and statistically relevant conclusions about infrastructure.

### AIOps and DevOps

AIOps complements but doesn't replace DevOps. You may find this distorted in some marketing messaging. What AIOps actually does is [infuse AI][9] into DevOps monitoring, offering DevOps teams more powerful tooling and views into their toolchain and systems. AIOps still drives a need for culture change in the same ways that DevOps does because organizations are viewing their infrastructure as a whole rather than individual layers of their technology stack. AIOps supercharges the traditional DevOps cultural transformation through the proliferation of data. The culture needs to create processes and frameworks to infuse data effectively across the DevOps toolchain.

AIOps systems run continuously. You can run AIOps systems as part of your CI/CD toolchain and across hybrid development, test, and production systems.

Augmenting your DevOps toolchain with AIOps gives you a new tool to support uninterrupted product availability, leading to a superior end-user experience. For example, the quick jump to remote work when COVID-19 struck taught some major websites and CSPs that internet traffic patterns can change overnight. Such a situation can repeat itself if a similar crisis happens again. Using AIOps to augment DevOps gives you a powerful tool to remove data silos and analyze the data your IT infrastructure generates.

### AIOps + DevOps outpace ITSM

AIOps and DevOps together provide speed, agility, and improved monitoring for hybrid environments supporting the operational continuity that enterprises need right now.

Remote work at the modern scale response requires [unclear what this means, please rephrase] was never part of the ITSM concept. AIOps and DevOps are cloud-first and hybrid-friendly, making them quite adaptable to business and technology change. Operations organizations can use DevOps and AIOps principles and technologies to adapt to rapid changes in infrastructure and working environments. Furthermore, they have the tools, frameworks, and actionable data to make changes iteratively and quickly. The analytics and monitoring tools AIOps offers support cloud cost controls and dynamic checking of your public cloud utilization.

On a positive note, some proprietary AIOps tools are making their way into the ITSM toolchain, such as new monitoring tools and cloud-based service desks. We need to see how the bodies governing ITSM capitalize on the next-generation problem-solving capabilities that AIOps ushers in soon. Waiting eight years to respond to AIOps like they did with the cloud could prove detrimental to them in a world where actionable data is a must-have for frontline DevOps teams and their stakeholders.

The DevOps community faces a similar challenge in dealing with a sudden influx of operational intelligence. However, DevOps practitioners pride themselves on responding to rapid changes with agility.

### Finding the solution

Enterprises face a conundrum following the rapid changes in infrastructure, endpoint security, and workflow brought about by COVID-19—namely, determining the processes, frameworks, and best practices to manage the influx of actionable data that AIOps can deliver. DevOps is built by design for extreme change. ITSM is experiencing some AIOps inroads but lacks a history of responding meaningfully to a significant technology market change.

Is the prospect of AIOps altering your DevOps or ITSM strategies? Share your thoughts in the comments.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/aiops-devops-itsm

作者：[Will Kelly][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/willkelly
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/whiteboard-brainstorming-brainmapping-design-thinking-postits-kanban.png?itok=Is2Tg1Jk (Brainstorming with post-it notes on a whiteboard)
[2]: https://opensource.com/tags/sysadmin
[3]: https://prometheus.io/
[4]: https://www.cncf.io/
[5]: https://grafana.com/
[6]: https://www.elastic.co/elastic-stack
[7]: https://www.tensorflow.org/
[8]: https://www.scipy.org/
[9]: https://thenewstack.io/aiops-is-devops-ready-for-an-infusion-of-artificial-intelligence/#:~:text=AIOps%20requires%20the%20same%20kind%20of%20culture%20change%20as%20DevOps,a%20high%20level%20of%20automation.
