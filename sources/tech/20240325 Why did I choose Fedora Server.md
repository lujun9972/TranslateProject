[#]: subject: "Why did I choose Fedora Server?"
[#]: via: "https://fedoramagazine.org/why-did-i-choose-fedora-server/"
[#]: author: "Daniel Mendizabal https://fedoramagazine.org/author/sigulete/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Why did I choose Fedora Server?
======

![][1]

Photo by [Kyle Glenn][2] on [Unsplash][3]

I thought it would be a good idea to share my experience implementing servers for personal use. It wasn’t easy to know the best fit for my workload and it has been a moving target, so it was critical to understand and update my needs before taking one route or another.

There are plenty of articles discussing which OS is more appropriate, some will warn against _Fedora Server_ or even _CentOS Stream_ regarding stability, but all it comes down to the use case. So the context is what makes the difference.

### RHEL is predictable with Insights as a bonus

I started using a _RHEL_ (developer license) to implement my services. At the time it was the obvious choice, because I needed a predictable package versioning. I implemented various services using _PHP_ and Databases which needed a consistent versioning of dependencies.

_RHEL_ also gave me the additional bonus of _Insights_ which is a convenient tool to see CVE’s, patches, and other interesting data. But apart from the initial hype while learning its capabilities, I stopped using it almost completely because my server was always up to date, and there wasn’t anything to see in the dashboard. I concluded, therefore, that despite the potential of _Insights_ , it wasn’t something I really needed.

### CentOS Stream brings you upgrades ahead of time

_RHEL_ versioning helps cases where staying in one minor version for a long time is paramount to keep applications working. But it wasn’t my case. I was always upgrading through minor versions as soon as they were available. So I looked at _CentOS Stream_ as an appealing alternative. It would give me the same stability with the additional benefit of getting the upgrades ahead of time. I made the move and migrated to _CentOS Stream_.

I was reluctant to use containers, in those days, thinking that having my workload installed directly in the server was more efficient. The presumption was that I was running _Apache_ , _MariaDB_ , _Postgress_ , _PHP_ , etc. only once. But there is a caveat with this simplified view because some of those services fork different instances to support the various requests anyway.

### Moving services into containers

A realization came when one of the services needed a newer _PHP_ version which wasn’t available in the standard repo. So I reverted to Modules to install the newer version. Unfortunately, I encountered some issues with dependencies on _EPEL_ that wouldn’t work with some of the newer _PHP_ packages. Also, not all my services worked well with the latest _PHP_ , and so on, and so forth. Long story short; I scraped all services and implement them as containers.

It was like being born again. Each service running in their own optimized environment happened to be the perfect solution and I just kept _Apache Server_ as reverse proxy.

I run my server in the cloud so resources were pretty limited. Surprisingly, the CPU and RAM consumption didn’t jump as I thought they would meaning that I didn’t have to upgrade my cloud service plan.

### Fedora Server turned out to be the best fit

Everything was good until I started using _Quadlet_ to implement my containers. _Quadlet_ is an amazing tool that replaces the deprecated _podman-generate-systemd_ to create _systemd_ units to handle containers’ lifecycle.

_Quadlet_ is available starting with _Podman 4.6_ , but it is limited to single containers. The implementation of Pods will be only available starting with _Podman 5.0_. The plan is to include _Podman 5.0_ in _Fedora 40_ which in turn will branch out _CentOS Stream 10_. This means that if I stay on _CentOS Stream_ , I will need to wait approximately 8 months to enjoy this new feature.

I was also looking for _DNF5_ , but unfortunately it didn’t make on time to _Fedora 4_ 0\. This means it will only be available on _CentOS Stream 11_ in another 4 years. Who knows what other cool upgrades I may be missing or will miss in the future.

After the move to _CentOS Stream_ , I came to another realization. I didn’t need a server with a predictable package versioning anymore. So you see where I’m going. On one hand, I’m not getting any particular benefit running _CentOS Stream_ (or _RHEL_ ), because all my workload is containerized. On the other hand, I’m missing the latest software to make my life easier and more enjoyable. So moving to _Fedora Server_ is a no brainier.

Another factor I didn’t think of before is the upgraded workflow. Staying with _CentOS Stream_ doesn’t guarantee a pathway between major versions, so it is likely that I will need to do a fresh install. Whereas using _Fedora Server_ guarantees a pathway and workflow to move between major releases.

So, all and all, the change makes so much sense for my use case. And I’m assuming this is a common scenario.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/why-did-i-choose-fedora-server/

作者：[Daniel Mendizabal][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/sigulete/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/03/why_did_i_choose_fedora_server-816x345.jpg
[2]: https://unsplash.com/@kylejglenn?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-yellow-and-black-sign-sitting-on-the-side-of-a-road-IFLgWYlT2fI?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
