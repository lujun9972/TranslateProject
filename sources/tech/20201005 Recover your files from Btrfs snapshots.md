[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Recover your files from Btrfs snapshots)
[#]: via: (https://fedoramagazine.org/recover-your-files-from-btrfs-snapshots/)
[#]: author: (Alessio Ciregia https://fedoramagazine.org/author/alciregi/)

Recover your files from Btrfs snapshots
======

![][1]

Photo by [Malcolm Lightbody][2] on [Unsplash][3]

As you have seen [in a previous article][4], Btrfs snapshots are a convenient and fast way to make backups. Please note that these articles do not suggest that you avoid backup software or well-tested backup plans. Their goals are to show a great feature of this file system, snapshots, and to inspire curiosity and invite you to explore, experiment and deepen the subject. Read on for more about how to recover your files from Btrfs snapshots.

### A subvolume for your project

Let’s assume that you want to save the documents related to a project inside the directory _$HOME/Documents/myproject_.

As you have seen, a Btrfs subvolume, as well as a snapshot, looks like a normal directory. Why not use a Btrfs subvolume for your project, in order to take advantage of snapshots? To create the subvolume, use this command:

```
btrfs subvolume create $HOME/Documents/myproject
```

You can create an hidden directory where to arrange your snapshots:

```
mkdir $HOME/.snapshots
```

As you can see, in this case there’s no need to use _[sudo][5]_. However, _sudo_ is still needed to list the subvolumes, and to use the _send_ and _receive_ commands.

Now you can start writing your documents. Each day (or each hour, or even minute) you can take a snapshot just before you start to work:

```
btrfs subvolume snapshot -r $HOME/Documents/myproject $HOME/.snapshots/myproject-day1
```

For better security and consistency, and if you need to send the snapshot to an external drive as shown in the previous article, remember that the snapshot must be read only, using the _-r_ flag.

Note that in this case, a snapshot of the _/home_ subvolume **will not** snapshot the _$HOME/Documents/myproject_ subvolume.

### How to recover a file or a directory

In this example let’s assume a classic error: you deleted a file by mistake. You can recover it from the most recent snapshot, or recover an older version of the file from an older snapshot. Do you remember that a snapshot appears like a regular directory? You can simply use the _cp_ command to restore the deleted file:

```
cp $HOME/.snapshots/myproject-day1/filename.odt $HOME/Documents/myproject
```

Or restore an entire directory:

```
cp -r $HOME/.snapshots/myproject-day1/directory $HOME/Documents/myproject
```

What if you delete the entire _$HOME/Documents/myproject_ directory (actually, the subvolume)? You can recreate the subvolume as seen before, and again, you can simply use the _cp_ command to restore the entire content from the snapshot:

```
btrfs subvolume create $HOME/Documents/myproject
cp -rT $HOME/.snapshots/myproject-day1 $HOME/Documents/myproject
```

Or you could restore the subvolume by using the btrfs snapshot command (yes, a snapshot of a snapshot):

```
btrfs subvolume snapshot $HOME/.snapshots/myproject-day1 $HOME/Documents/myproject
```

### How to recover btrfs snapshots from an external drive

You can use the _cp_ command even if the snapshot resides on an external drive. For instance:

```
cp /run/media/user/mydisk/bk/myproject-day1/filename.odt $HOME/Documents/myproject
```

You can restore an entire snapshot as well. In this case, since you will use the _send_ and _receive_ commands, you must use _sudo_. In addition, consider that the restored subvolume will be created as read only. Therefore you need to also set the read only property to _false_:

```
sudo btrfs send /run/media/user/mydisk/bk/myproject-day1 | sudo btrfs receive $HOME/Documents/
mv Documents/myproject-day1 Documents/myproject
btrfs property set Documents/myproject ro false
```

Here’s an extra explanation. The command _btrfs subvolume snapshot_ will create an exact copy of a subvolume in the same device. The destination has to reside in the same btrfs device. You can’t use another device as the destination of the snapshot. In that case you need to take a snapshot and use the _send_ and _receive_ commands.

For more information, refer to some of the online documentation:

```
man btrfs-subvolume
man btrfs-send
man btrfs-receive
```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/recover-your-files-from-btrfs-snapshots/

作者：[Alessio Ciregia][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/alciregi/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/09/btrfs-snapshot-restore-816x345.jpg
[2]: https://unsplash.com/@mlightbody?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/snapshot?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://fedoramagazine.org/btrfs-snapshots-backup-incremental/
[5]: https://fedoramagazine.org/howto-use-sudo/
