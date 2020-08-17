[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to make sure data that should be backed up gets backed up)
[#]: via: (https://www.networkworld.com/article/3571435/how-to-make-sure-data-that-should-be-backed-up-gets-backed-up.html)
[#]: author: (W. Curtis Preston )

How to make sure data that should be backed up gets backed up
======
Using selective exclusion to determine what data gets backed up may result in storing some useless data, but it avoids having no backup for the important stuff.
Baranozdemir / Getty Images

There is no sadder moment in the backup world than finding out the file or database you need to restore has never been backed up. Understanding how systems, directories, and databases are included in the backup system is the key to making sure this never happens to you.

The first step toward this goal is making sure that servers and services you want backed up are registered with your backup-and-recovery system.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

For example, if you start using a new SaaS such as Salesforce, no backup system will automatically notice that addition and start backing it up for you. If you are fully virtualized on VMware, the systems will automatically notice if you add a new node to the configuration. But if you start using Hyper-V or KVM, no backup system will automatically notice there is a new hypervisor in the data center and start backing it up. And of course your backup system will not notice you installed a new physical server.

### Selective inclusion vs selective exclusion

There are two very broad categories of how items can be included in a backup system: selective inclusion and selective exclusion.

Selective inclusion is where the administrator individually specifies which filesystems, databases, or objects the backup system will back up. For example, if an administrator says they want to back up just the D:\ drive, or just the Apollo database, they are practicing selective inclusion.

Selective exclusion, or automatic inclusion, is when an administrator specifies to back up everything on the server, except for what is specifically excluded. For example, an administrator might select to back up all filesystems except for /tmp on a Linux system or a user's iTunes or Movies directories on a Windows laptop.

It's very common for administrators to think they administer systems in such a way that there is no point in backing up the operating system. They know they want to back up C:\Users on a Windows laptop, /Users on a Macbook, or something like /data or /home on a Linux system. They see no point in backing up the operating system or applications, and so they manually select just the filesystems they want to backup. The same is true of databases. They might not want your backup test databases, so they selectively include which databases to backup.

### Selective inclusion downside

The problem with selective inclusion is configuration changes. Every time a new database or file system with data is added to a system, someone needs to change the backup configuration, otherwise, the new resource will never get backed up.

This is why selective exclusion is the safest backup-selection method. The worst possible side effect is you might backup some worthless data. Compare this to the worst possible side effect of selective inclusion, which is important data gets completely excluded from the backup system. There is simply no comparison between the two. Selective inclusion may appear to save money because less data is stored, but it’s not worth the risk.

It is easy to exclude data that you know to be worthless, such as  /tmp or /temp on a Linux system. If you see no reason to backup the operating system, you might also exclude /, /user, /usr, /var, and /opt. On a Windows system, you could exclude C:\Windows and C:\Program Files if you really don't want to backup that data.

One thing to consider, though, is the effect that deduplication might have on this decision. It's one thing to know you are backing up hundreds or thousands of filesystems that have no value and waste valuable storage space on your disk array or tape library. But what if the operating system that you are spending so much time excluding is actually only stored once? Deduplication would ensure that only one copy of a Windows or Linux operating system is actually stored in your backup system. Considering this, perhaps you could just leave the backup system at its default configuration and not worry about excluding the operating system, as the cost to your backup system will be very small.

### Tag-based inclusion

Another way to automatically add backup data to the backup system is via tag-based inclusion. This has become popular in the virtualization world, where each new VM or database that is created can be given one or more tags that can be used to classify the type of VM or database. For example, all new database servers might be given the database tagging, indicating to multiple other processes that it is a database-related VM. This might tell certain monitoring systems to monitor whether the database is available. It might also automatically apply certain security rules and firewalls to that VM. And in most backup systems it can also automatically apply a database-centric backup policy to that VM as well.

One important thing to note when using tag-based inclusion: You need a default backup policy. You should create a backup policy that your backup software automatically uses if no appropriate tags are found. Then make sure to monitor that default policy for any new systems that show up, because it means that the data on those systems might not be getting properly backed up. If your backup software product does not support a default backup policy when used with tag-based inclusion, it might be best not to use this functionality, because it comes with the risk of new VMs or databases not being backed up.

### Just be safe

Default to the safest methods of backup inclusion, which is automatic or selective inclusion. Spend your valuable time on other administrator activities, without having to worry whether your new database is being backed up. Backup priorities should always be safety and protection first, cost second. No one ever got fired because their backup system backed up some worthless data.

Join the Network World communities on [Facebook][2] and [LinkedIn][3] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3571435/how-to-make-sure-data-that-should-be-backed-up-gets-backed-up.html

作者：[W. Curtis Preston][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/newsletters/signup.html
[2]: https://www.facebook.com/NetworkWorld/
[3]: https://www.linkedin.com/company/network-world
