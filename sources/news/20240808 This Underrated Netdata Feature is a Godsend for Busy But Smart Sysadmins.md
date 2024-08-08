[#]: subject: "This Underrated Netdata Feature is a Godsend for Busy But Smart Sysadmins"
[#]: via: "https://news.itsfoss.com/netdata-dynamic-configuration-manager/"
[#]: author: "Abhishek https://news.itsfoss.com/author/root/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Underrated Netdata Feature is a Godsend for Busy But Smart Sysadmins
======
Monitoring performance metrics is one thing, getting timely alerts is
another.
[![][1]][2]

I don't think of myself as a sysadmin. I am more of a self-hoster who has some experience hosting websites for me and my friends. That doesn't qualify me as a sysadmin, I think.

And yet, here I am suggesting a tool whose full potential can only be utilized by a seasoned sysadmin (or so I believe).

The tool I am talking about is [Netdata][3]. It is an open source network infrastructure monitoring tool. You can self-host it, use it on-prem or opt for their managed cloud service (data stays on your server but is displayed on the hosted dashboard).

![][4]

Netdata lets you collect all kinds of performance metrics and displays them beautifully in a dashboard. Yeah, dashboards! Who doesn't love them?

0:00

/0:21

1×

But I am not discussing the dashboard here.

### The feature I love the most: Alert configuration

Here's the thing about dashboards. They are good to look at but you are likely not going to look at them all the time.

The feature I like the most is the alert configuration.

CPU utilization going high? Alert me. Disk is about to run out of space? Notify me?

A timely alert can save the server from going down and thus avoid service disruption.

While Netdata comes with default alert configuration for several performance metrics, it is easy to change as per your preference.

For example, the default disk space utilization is set at 80% for warning and 90% for critical. But I prefer keeping the alert at 75%.

Configuring alerts is really simple. You can either to go the dedicated alert tab or just change them from the dashboard itself.

![][5]

The same goes for memory and CPU utilization and tons of other performance metrics that Netdata tracks.

💡

If you have more than one node, you can configure the same alert on all nodes simultaneously. Saves a lot of time that would have gone into the repeating the tasks.

More details on the alert configuration can be found here:

![][6]

Now, this could be a tiny feature but I like it and it has saved my servers, hosting Ghost CMS, a few times. Perhaps it will benefit you as well.

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/netdata-dynamic-configuration-manager/

作者：[Abhishek][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/root/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.netdata.cloud/
[4]: https://github.githubassets.com/assets/pinned-octocat-093da3e6fa40.svg
[5]: https://news.itsfoss.com/content/images/2024/08/netdata-alert-configuration-manager.png
[6]: https://learn.netdata.cloud/img/favicon-32x32.png
