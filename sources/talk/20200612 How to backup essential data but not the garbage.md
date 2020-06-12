[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to backup essential data but not the garbage)
[#]: via: (https://www.networkworld.com/article/3562348/how-to-backup-essential-data-but-not-the-garbage.html)
[#]: author: (W. Curtis Preston )

How to backup essential data but not the garbage
======
There’s lots of ways to sort out what to back up and what not to, but the goal should always be to back up everything that needs to survive a crash.
danielsbfoto / Getty Images

Something as simple as how you tell your backup product which files and databases to backup can have a massive impact on your recoverability. Proper backup selection is essentially a balance between ensuring that everything that should be backed up is indeed backed up, while also trying not to backup worthless data.

### Physical server inclusion

Virtually all backup products require some initial installation and configuration at the level of a physical server. This means that for any of the tactics mentioned in this article to work, one must first install the appropriate software and authorization on each physical server in the data center. This means every VMware or Hyper-V server (not to be confused with each VM on those servers), every physical UNIX or Windows server, and any cloud services that are being backed up. Someone must make that initial connection and authentication before the backup system can perform its magic.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

### Selective inclusion

The most common method of including files, objects, or databases in a backup system is to manually select them when configuring the backups of a given system. Here are three examples of selective inclusion:

  * Clicking through the vCenter or Hyper-V control panel and manually selecting which VMs to backup
  * Manually selecting one or more databases from a list of all databases
  * Manually selecting one or more filesystems or subdirectories



The reason this is the most common method is that it fits the way people think; they want to perform backups, so they specify what they want to back up. It also helps minimize the amount of data backed up that has no value, because very few people would select a test VM or database, or a file system such as /tmp on UNIX.

The concern with selective inclusion is what happens over time. If only systems you manually select will be backed up, what happens when the configuration changes? For example, what happens when you add new VMs to a given VMware server? What happens if you move a given VM from VMware to Hyper-V, or even the cloud? If you manually selected it in VMware, it will not automatically start getting backed up when it moves to another configuration. Backup experts generally warn against this type of backup selection method because the risk of data loss is simply too high.

### Automatic inclusion

Once a given VM or database server has been added to the backup configuration, another very common method is to simply specify that all VMs, databases, or filesystems found therein should be backed up. This is the safest method of backup inclusion because it ensures that every new data source will be backed up. It addresses the concern about selective inclusion because VMs – or a VM that was moved from one type of configuration to another – would automatically get backed up without anyone having to be notified.

Some say this method virtually ensures it will back up worthless data. While this is true, it also ensures that you will automatically be backing up important data. The worst-case scenario with selective inclusion is that a really important file system, database, or VM doesn’t get backed up. With an automatic inclusion system, the worst-case scenario is that you are also backing up garbage.

### Selective exclusion

This technique is typically used in conjunction with an automatic-inclusion system. A customer configures their backup systems to backup every VM, database, or file system except those that are specifically called out on a list of exclusions. Selective exclusion is a way to have your cake and eat it, too, as it allows you to use automatic inclusion as a way to ensure all important data is backed up, while also automatically excluding known worthless data.

This can be done in a UI, where a customer clicks through and manually selects drives or databases that he or she knows hold no value. An administrator trying to save space might add test databases or BMs, or filesystems like /tmp to the exclusion list to ensure that space is not wasted on them.

Another way to set up selective exclusion is to use wildcards or regular expressions to identify what should not be backed up. For example, one could specify *.tmp, *.bak, *.cache as wildcard exclusion patterns;  any files found with those extensions would not be backed up. Those familiar with regular expressions can get very creative with them in order to exclude particular types of files no matter where they are found.

### Tag-based inclusion

A very modern way of including data in a backup is to use tags, which are quite prevalent in the VM world. This allows you to specify not only that VMs with a certain tag should be backed up, but also how they should be backed up. For example, you could specify that VMs with a #database tag should be backed up with the database backup policy that will handle those VMs in a particular way. The same is true for VMs with hashtags like #fileserver, #test, etc. You can create several different types of backup policies that behave in particular ways, and then apply those policies to different VM's via hashtags.

This is a form of automatic inclusion, as any new VMs would be automatically added to the appropriate backup policy based on the hashtag. You can also continue to use automatic exclusion system to ensure that garbage data doesn't get backed up.

### Default inclusion

Whenever using automatic inclusion or tag-based inclusion, you need some kind of catch-all mechanism. For example, if a VM or database is not automatically selected via some type of hashtag or other mechanism, you want to make sure that it is still backed up. The more you use intelligent systems like tag-based inclusion, the more important a default inclusion system becomes.

If your backup system supports it, it works like this: Any VM or database that is not already selected by an automatic policy or a tag-based policy will be backed up by this policy. Obviously, the policy will not be tailored to the needs of that particular system, but at least some kind of backups are happening. You could then monitor this particular policy to see if any systems are ever backed up using a default inclusion system. If they are, perhaps you should examine why that is happening and solve that by putting them in the appropriate type of backup configuration.

Remember this fundamental rule of backup-system design: You cannot restore that which has not been backed up. No one ever got fired because they backed up too much data, but many people have been fired because they didn't backup enough data. Do your best to eliminate wasted backups, but try to err on the side of caution. Be more concerned with data that is not being backed up than with worthless data being backed up. That should help keep you from creating what many people call a resume-producing event.

Join the Network World communities on [Facebook][2] and [LinkedIn][3] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3562348/how-to-backup-essential-data-but-not-the-garbage.html

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
