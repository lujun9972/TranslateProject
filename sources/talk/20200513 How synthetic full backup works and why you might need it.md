[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How synthetic full backup works and why you might need it)
[#]: via: (https://www.networkworld.com/article/3543220/how-synthetic-full-backup-works-and-why-you-might-need-it.html)
[#]: author: (W. Curtis Preston )

How synthetic full backup works and why you might need it
======

Bridgestone

The invention of synthetic full backups is one of the most important advancements in backup technology in the last few decades, right up there witih disk-based backups, deduplication, continuous data protection (CDP), and the cloud.

Here’s how they came to be and an explanation of what benefits they might offer.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

### Traditional backup options

There are essentially two very broad categories of what the backup industry calls backup levels;

you are either backing up everything (full backup) or you are backing up only what has changed (incremental backup). There are different types of incremental backups, but that's really not relevant to this particular discussion. A typical set up runs incremental backups every night and full backups every week – or even less often than that.

The reason for periodic full backups is what happens when you perform a restore. Traditional backup software will restore all data found on the full backup – even if some of the data on that tape has been replaced by newer versions that will be found on incremental backups. The restore process will then begin restoring new or updated files from the various incremental backups, in the order that they were created.

This process of performing multiple restores, some of which are restoring data that will be overwritten, is inefficient to say the least. If the restores are coming from tape, you must also add the time required to insert and load each tape, seek to the appropriate place on the tape, and eject the tape once it is no longer needed. This process can take over five minutes per tape.

This means that with this type of configuration, the more frequent your full backups are, the faster your restores will be because they are wasting less time. (From a restore perspective, full backups every night would be ideal.) This is why it was very common to perform a full backup once a week on all systems. As systems got more automated, some practitioners moved to monthly or quarterly full backups.

However, performing a full backup on an active server or VM creates a significant load on that server. This gives an incentive for a backup administrator to decrease the frequency of full backups as much as possible, even if it results in restores that take longer. This push and pull between backup and restore efficiency is the main reason that synthetic backups came to be.

### What is a synthetic full backup?

A synthetic full backup is a backup that behaves as a full backup during restores, but does not do so during backups. In fact, in a typical synthetic full backup configuration, full backups are all but done away with. There are three main methods of accomplishing this.

The first, and probably the most common, method of creating a synthetic full backup is to create one from the available backups. The backup system keeps a catalog of all data it finds during each backup. So at any given point it knows all of the files – and which versions of those files – that would be on a full backup if it were to create one in the traditional way. It simply copies each of those files from one medium to another. This method will work with tape or disk, as long as multiple devices are available.

This method of performing a synthetic full backup can take quite some time; however, this process can be run any time of day without any impact to the systems being backed up. In fact, the servers or VMs being backed up are completely uninvolved. The resulting backup is in every sense a full backup and subsequent incremental backups can be based on that full backup. The only downside to this method is the time necessary to copy the full backup.

The second method is only possible when using disk as your primary backup target. It's also only possible if the backup system is storing each changed file or block as a separate object in its storage system. This is in contrast to the way backup systems have traditionally stored backups, where many files are put inside a container (e.g. tar or a proprietary backup format). If all changed files or blocks are stored as individual chunks of data, then a synthetic full backup can be created by simply creating a snapshot-like view to the current version of all of the current chunks that make up the full backup.

There are many advantages to this method, starting with the fact that it takes virtually no time to create the synthetic full backup, as there is no movement of data. This means that synthetic full backups can be created much more often, and in fact most systems that support this will do this after every backup. This means that, while the system performs only incremental backups, all of its backups behave as full backups. This is typically referred to as a block-level incremental forever backup system, as it never again requires a full backup to be created, either traditionally or using the copy method mentioned above.

Finally, there is an approach that is somewhat of a hybrid of these two approaches. This is only possible with target deduplication systems. Like the second approach mentioned above, all backups are stored as small chunks of data, resulting in each changed file or block being represented by many small chunks stored in the target deduplication system. This means that it is possible for this appliance to create a virtual full backup – similar to the incremental forever method mentioned above – in very little time. This process can also be controlled via a backup product, where the backup product tells the target deduplication system to create a synthetic full backup. Like the second approach mentioned above, this method is very efficient and happens nearly instantaneously.

### Does your system support synthetic full backups?

Whether it uses the copy method, block level incremental backups forever, or the virtual copy method used by target deduplication systems, a synthetic full backup has become quite common in most commercial backup systems. If you are not using this functionality it might be time to investigate whether it is possible with your hardware and software set up. If it is not possible, this could be an indication that your backup system is a little behind the times.

Join the Network World communities on [Facebook][2] and [LinkedIn][3] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3543220/how-synthetic-full-backup-works-and-why-you-might-need-it.html

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
