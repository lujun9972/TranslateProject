[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Improve Linux system performance with noatime)
[#]: via: (https://opensource.com/article/20/6/linux-noatime)
[#]: author: (Jim Hall https://opensource.com/users/jim-hall)

Improve Linux system performance with noatime
======
Turning off atime is a small but effective way to improve system
performance. Here's what it is and why it matters.
![Penguin driving a car with a yellow background][1]

Whenever I upgrade Linux on my home computer, I have a list of tasks I usually do. They've become habits over the years: I back up my files, wipe the system, reinstall from scratch, restore my files, then reinstall my favorite extra applications. I also make a few system tweaks. I've been making some of these tweaks for so long that I recently wondered if I still needed to do them.

One tweak is `atime`, which is one of the three timestamps on every file on Linux (more on that later). Specifically, I wondered if it's still worth it to disable `atime` in more recent Linux systems. Since `atime` is updated every time the file is accessed, my understanding was that it had a significant impact on system performance.

I recently upgraded my computer to Fedora 32 and turned off `atime` on my upgraded system out of habit. But did I still need to? I decided to look into it further. Here's what I found.

### A bit about file timestamps

To understand `noatime`, you need to take a step back and understand a few things about Linux filesystems and how the kernel applies timestamps to files and directories. You probably are already aware of the Last Modified date on files and directories; you can see that in an `ls -l` (long) directory listing or if you look at file details in a file manager. But behind the scenes, the Linux kernel tracks several timestamps on files and directories:

  1. When the file was last modified (`mtime`)
  2. When the file was last changed (`ctime`)
  3. When the file was last accessed (`atime`)



You can use the `stat` command to see these details for a file or directory. Here's an example of the `/etc/fstab` file on one of my test servers:


```
$ stat fstab
  File: fstab
  Size: 261             Blocks: 8          IO Block: 4096   regular file
Device: b303h/45827d    Inode: 2097285     Links: 1
Access: (0664/-rw-rw-r--)  Uid: (    0/    root)   Gid: (    0/    root)
Context: system_u:object_r:etc_t:s0
Access: 2019-04-25 21:10:18.083325111 -0500
Modify: 2019-05-16 10:46:47.427686706 -0500
Change: 2019-05-16 10:46:47.434686674 -0500
 Birth: 2019-04-25 21:03:11.840496275 -0500
```

From the output, you can see this file was created on April 25, 2019, when I installed the system. My `/etc/fstab` file was last modified on May 16, 2019, and any other attributes were changed at around the same time.

If I copy `/etc/fstab` to a new file, the dates change, indicating that this is a new file:


```
$ sudo cp fstab fstab.bak
$ stat fstab.bak
  File: fstab.bak
  Size: 261             Blocks: 8          IO Block: 4096   regular file
Device: b303h/45827d    Inode: 2105664     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Context: unconfined_u:object_r:etc_t:s0
Access: 2020-05-12 17:53:58.442659986 -0500
Modify: 2020-05-12 17:53:58.443659981 -0500
Change: 2020-05-12 17:53:58.443659981 -0500
 Birth: 2020-05-12 17:53:58.442659986 -0500
```

But if I just rename the file without changing its contents, Linux only updates the Change time for the file:


```
$ sudo mv fstab.bak fstab.tmp
$ stat fstab.tmp
  File: fstab.tmp
  Size: 261             Blocks: 8          IO Block: 4096   regular file
Device: b303h/45827d    Inode: 2105664     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Context: unconfined_u:object_r:etc_t:s0
Access: 2020-05-12 17:53:58.442659986 -0500
Modify: 2020-05-12 17:53:58.443659981 -0500
Change: 2020-05-12 17:54:24.576508232 -0500
 Birth: 2020-05-12 17:53:58.442659986 -0500
```

These timestamps are very useful for certain Unix programs. For example, [biff][2] is a program that notifies you when you have a new email message. You don't see many people using biff these days, but in the days when mailboxes were local to your system, biff was quite common.

How does a program know if you have new mail in your inbox? Biff compares the Last Modified time (when the inbox file was updated with a new email message) and the Last Accessed time (the last time you read your email). If Modified is more recent than Accessed, then biff knows an email message has arrived since you last read email and lets you know. The [Mutt][3] email client does something similar to alert you when new messages arrive.

That Last Accessed time is also useful if you need to do filesystem statistics and performance tweaking. On large Linux systems, administrators may need to know what's being accessed so they can tune the filesystem appropriately.

But most modern programs no longer need the Last Accessed time, so there's been some argument to not use it. In 2007, Linus Torvalds and several other kernel developers discussed `atime` and its performance issues. Linux kernel developer Ingo Molnár made this [observation][4] about `atime` and the ext3 filesystem:

> It's kind of weird that every Linux desktop and server is hurt by a noticeable IO performance slowdown due to the constant atime updates, while there's just two real users of it: tmpwatch [which can be configured to use ctime so it's not a big issue] and some backup tools. (Ok, and mail-notify too i guess.) Out of tens of thousands of applications.

But people still use some programs that need it, and removing `atime` would break those user programs. And the rule in Linux kernel development is not to break userspace.

### The relatime compromise

Linux distributions include a lot of software applications, and users can download and install other programs to suit their particular needs. That's the key benefit of an open source operating system! But that makes things more difficult in tuning your filesystem performance. Do you need `atime`, or will removing it break something on your system?

As a compromise, Linux kernel developers implemented a new method: `relatime` is a slightly different performance measure that is meant to balance performance with compatibility. The `mount` man page says this about `relatime`:

> Access time is only updated if the previous access time was earlier than the current modify or change time. … Since Linux 2.6.30, the kernel defaults to the behavior provided by this option (unless noatime was specified) … In addition, since Linux 2.6.30, the file's last access time is always updated if it is more than 1 day old.

In short: modern Linux systems (since Linux 2.6.30, released in 2009) already use `relatime`, which should give you a really fast performance boost. That means you don't need to tweak your `/etc/fstab` file and can rely on the `relatime` kernel default.

### Tweaking system performance with noatime

But if you're looking to tweak your system to get maximum performance, disabling `atime` is still a valid option in 2020.

This performance tweak might not be very noticeable on very fast modern drives (like NVME or a fast SSD), but there's still a little boost there.

If you know you don't use software that requires `atime`, then you can get a slight performance boost by setting `noatime` in your `/etc/fstab` file. This tells the kernel not to track the Last Accessed time, avoiding that tiny performance hit to continually update `atime` in the filesystem. Add `noatime` as an option to your Linux filesystems, usually after the defaults entry:


```
/dev/mapper/fedora_localhost--live-root /          ext4   defaults,noatime,x-systemd.device-timeout=0 1 1
UUID=be37c451-915e-4355-95c4-654729cf662a /boot    ext4   defaults,noatime        1 2
UUID=C594-12B1                          /boot/efi  vfat   umask=0077,shortname=winnt 0 2
/dev/mapper/fedora_localhost--live-home /home      ext4   defaults,noatime,x-systemd.device-timeout=0 1 2
/dev/mapper/fedora_localhost--live-swap none       swap   defaults,x-systemd.device-timeout=0 0 0
```

This will take effect the next time you reboot.

David Both shares his favorite system monitoring tools for understanding what is going on in any...

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/linux-noatime

作者：[Jim Hall][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/jim-hall
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/car-penguin-drive-linux-yellow.png?itok=twWGlYAc (Penguin driving a car with a yellow background)
[2]: https://en.wikipedia.org/wiki/Biff_(Unix)
[3]: https://opensource.com/life/15/8/top-4-open-source-command-line-email-clients
[4]: http://web.archive.org/web/20110427023154/http://kerneltrap.org/node/14148
