[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Item-level vs. image-level backup: Why it’s best to use a combo)
[#]: via: (https://www.networkworld.com/article/3566128/item-level-vs-image-level-backup-why-it-s-best-to-use-a-combo.html)
[#]: author: (W. Curtis Preston )

Item-level vs. image-level backup: Why it’s best to use a combo
======
Two types of backup – item level and image level – have different strengths, and it’s possible to tap the best of both.
gorodenkoff / Getty Images

There are two very different ways to backup a computer: Item-level backup and image-level backup, and both methods have been used by IT pros for decades. Each comes with its own advantages and disadvantages, which is why most environments use a combination of the two.

### Item-level backup

An item-level backup backs up discrete collections of information that are addressed as individual items, and the most common type of item is a file. In fact, if this article were being written several years ago, this would most likely be called file-level backup.

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

The other type of item that might be included in an item-level backup is an object in an object storage system. For many environments, objects are similar to files in that most companies using object storage are simply using it to hold onto what would otherwise be files. But since they are being stored in an object storage system, they are not files, as files are stored in a file system. The contents are often the same, but they get a different name because they are stored differently.                                                

You typically perform item-level backup if you are backing up a file server, a Windows or Linux server, or a virtual machine where the backup agent is running inside the server/VM itself. The backup agent is deciding which files to backup by first looking at the file system, such as  C:\\. If you are performing a full backup, it will backup all the files in the file system. If you are performing an incremental backup, it will be backing up files that have changed since the last backup.

You are also performing an item-level backup if you are backing up your object storage system, such as Amazon S3, Azure Blob, or Google Cloud Storage. You may wonder why you’d want to backup these services since they are typically replicated to multiple locations for data resiliency. However, replication within object storage is typically designed to survive system outages but is not necessarily designed to survive an attack from the outside that deletes the object itself. If an object is deleted – whether on purpose, accidentally or maliciously – the deletion will be replicated across all copies. The only way to protect against this is to perform an item-level backup of your object storage to another account.

The advantage of an item-level backup is that it is very easy to understand. Install a backup agent in the appropriate place and it will examine your file or object storage system, find all of the items there and back them up at the appropriate time. Restoring the entire file or object storage system requires first restoring the full backup, and then performing restores from each subsequent incremental backup.

### Image-level backups

An image-level backup is the result of backing up either a physical or virtual device at the block level. This is why – depending on your frame of reference – image-level backups are also referred to as drive-level, volume-level, or VM-level backups. The device could be storing a variety of information types, including a standard file system, block storage for a database, or even the boot volume for a physical or virtual machine. Within an image-level backup, you're backing up the building blocks of the file system, rather than backing up the files themselves.

Prior to the advent of virtualization, image-level backups were rare because backing up the physical drive was a lot harder and required unmounting the filesystem while you backed up the blocks. Otherwise you risked a contaminated backup where some of the blocks are from one point in time and some of the blocks are from another point in time. Virtual snapshot technology, such as what is found in Windows Volume Shadow Services (VSS) or VMware snapshots, solved this underlying problem.

Backing up at the volume level became much more popular once VMs came on the scene. Image-level backups allow you to perform a backup of a VM at the hypervisor level, where your backup software runs outside the VM and sees the VM as one or more images (e.g. VMDK files in VMware).

Backing up at the image level has a number of advantages. First, it provides faster backups and much faster restores. Image-level backups avoid the overhead of the file- or object-storage system and go directly to the underlying storage. Restores can be much faster because file-level backups require restoring each file individually, which requires creating a file in the file system, a process that comes with quite a bit of overhead. This problem really rears its ugly head when restoring very dense filesystems with millions of files, where the process of creating the files during the restore actually takes longer than the process of transferring the data into the files. Image-level restores do not have this problem because they are laying the data straight down at the block level.

Once the changing block issue was addressed with snapshots, backup systems were presented with the second biggest challenge of image-level backups: incremental backups. When you are backing up at the drive, volume, or image level, every file is a full backup. For example, consider a VM represented by a VMDK file. If that VM is running and a single block in the VM changes, the modification time on that image will show that it has changed. A subsequent backup will then backup the entire VMDK file, even though only a few blocks of data might have changed.

This challenge has also been solved in the VM world via change-block tracking (CBT), which is a protocol to keep track of when a previous backup was created and the blocks that have changed since that last backup. This allows an image-level backup to perform a block-level incremental backup by using this protocol to ask which blocks have changed, and then copying only those blocks.

This leaves us with one final disadvantage of backing up at the image level, and that is the lack of item-level recovery. Customers do not typically want to restore an entire VM; they want to restore a file or two within that VM. How do you restore a single file from a VM when you backed up the entire VM as a single image? This is also a problem that has been solved by many backup software companies. For example, in the case of a VMware VM, they understand the format of VMDK files, which allows them to do a number of different things. Some backup products allow you to mount the original VMDK files as a virtual volume and grab the files that you need from there, where others can grab the appropriate blocks that are necessary to restore the file you've asked for.

### The best of both worlds

This means that at this point in the backup and recovery industry, most customers are performing image-level backups of all of their VMs while still retaining the ability to perform both incremental backups and item-level restores. It also supports block-level incremental backups, which are actually much more efficient than item-level incremental backups.

Backing up at the VM level also comes with the ability to easily restore the VM as a single image. This makes what we used to call bare-metal recovery so much easier than it used to be. You get all of the bare-metal recovery capabilities that you need without having to jump through hoops to address the changing block issue.

We even have image-level backups of physical Windows servers, since most people are using Windows VSS to create a snapshot of each file system prior to backing it up. This allows the backup software product to back up at the image-level without risking data corruption.

Now that you understand the advantages and disadvantages of each approach, you can make an educated decision as to which is appropriate for you. Most people backing up VMs choose image-level backups, and most people backing up file servers use item-level backups. Deciding what to do with physical servers might take a bit more research.

Join the Network World communities on [Facebook][2] and [LinkedIn][3] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3566128/item-level-vs-image-level-backup-why-it-s-best-to-use-a-combo.html

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
