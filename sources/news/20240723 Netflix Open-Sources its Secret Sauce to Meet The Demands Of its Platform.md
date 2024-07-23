[#]: subject: "Netflix Open-Sources its Secret Sauce to Meet The Demands Of its Platform"
[#]: via: "https://news.itsfoss.com/netflix-maestro-open-source/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Netflix Open-Sources its Secret Sauce to Meet The Demands Of its Platform
======
Netflix bets on open-source!
[![][1]][2]

Every company relies on some form of workflow organization, where they devise a mechanism or tool that helps them utilize the resources to the best of their ability, meet customer demands, facilitate easy software development, and more.

Not just big companies like Netflix, but every company has its unique set of problems and ideas to handle them. So, there is never a " _one solution fits all_ " approach here.

However, if a company invests a significant amount of money to build their own workflow engines, and then they are open-sourcing it, that's good news! 🥳

### Meet Netflix's Workflow Orchestrator 'Maestro'

![][3]

If you are a cloud computing enthusiast, the term orchestrator may remind of Kubernetes or microservices. But, Maestro is not that.

As the official blog describes:

> Maestro is a general-purpose, horizontally scalable workflow orchestrator designed to manage large-scale workflows such as data pipelines and machine learning model training pipelines.

Companies like Netflix need to collect data, process it, store it, transform it, verify, and monitor it. Anything that deals with data engineering, the same processes are involved.

In other words, the decisions to recommend you of your favorite shows, analyzing what works best, what doesn't, management of media, and any back-end trick, everything is data-driven (heaps of it). And, that is facilitated by using such a tool.

One could say Maestro is at the core of Netflix's platform, making all the gears work in sync together for its engineers to work comfortably, partners to get all insights needed, and customers to access the service seamlessly.

Netflix used Meson (another of its orchestrator) before it [introduced Maestro in 2022][4] to address the scalability issue. But, it was not open-sourced.

Now, Netflix seems to be confident that its solution can help others, and in return, use the help of the open-source community to improve it further. So, they decided to open-source the entire code and make it available on [GitHub][5] under **the Apache 2.0 license.**

[Maestro GitHub][5]

Some users in the [Hacker News discussions][6] seem to think that this is purely a PR move, and they did not need to re-invent the wheel when there are options like [Apache Airflow.][7]

Some are skeptical if Netflix would maintain it or abandon it later for something else, like [Conductor][8] (Netflix's older tech).

While others believe that this is a good move, and it could help the open-source community re-purpose the code to individual use-cases for different business logic.

I am not a data engineer, so I am not aware of how this is technically beneficial over existing solutions. So, I would let you find that out from their detailed [announcement blog post][9].

_💭 What do you think about Netflix's decision to open-source their latest workflow engine? Let me know your thoughts in the comments below!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/netflix-maestro-open-source/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/content/images/2024/07/netflix-opensource-maestro-1.png
[4]: https://netflixtechblog.com/orchestrating-data-ml-workflows-at-scale-with-netflix-maestro-aaa2b41b800c
[5]: https://github.com/Netflix/maestro
[6]: https://news.ycombinator.com/item?id=41037745
[7]: https://airflow.apache.org/
[8]: https://github.com/Netflix/conductor
[9]: https://netflixtechblog.com/maestro-netflixs-workflow-orchestrator-ee13a06f9c78
