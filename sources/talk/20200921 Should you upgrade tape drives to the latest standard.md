[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Should you upgrade tape drives to the latest standard?)
[#]: via: (https://www.networkworld.com/article/3575810/should-you-upgrade-tape-drives-to-the-latest-standard.html)
[#]: author: (W. Curtis Preston )

Should you upgrade tape drives to the latest standard?
======
A recently released standard for linear tape-open—LTO-9—sets the scene for faster drives with more capacity, but are they a must-have?
Vladimir Timofeev / Getty Images

With the recent release of the linear tape–open 9 (LTO-9) standard, tape drives with increased capacity and speed should be available soon, but that doesn’t mean users of tape drives should rush to buy them.

Here are some of the pros and cons to weigh when considering whether an upgrade is in order.

Tape drives are a very reliable way to write data to storage, and are very good at holding onto data for multiple decades. They make an excellent medium for long-term storage and for shipping large amounts of data across long distances (a FedEx truck has unlimited bandwidth).

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

What tape is not good at is going slow. LTO-8 has a compressed transfer speed of 900MB/s, which is significantly faster than most any backup you're going to send to it. It's definitely faster than any incremental backup that will be sent to it, and that comprises most backups. That makes tapes as the initial target of backups problematic.

It’s OK to use tape to copy your backups for off-site purposes, because your disk-based backup system can be used as a cache for your tape drive, which should allow it to stream at a decent rate during the copy process. But it is next to impossible these days to properly design a backup system that sends incremental backups across the network directly to tape.

### Why to upgrade your tape drive

There are three reasons that could justify upgrading your tape drive. The first would be if you have a task that uses large amounts of tape on a regular basis and upgrading to a faster tape drive would increase the speed of that process.

For example, it might make sense for a movie producer using cameras that produce petabytes of data a day who want to create multiple copies and send them to several post-production companies. Copying 1PB to tape takes 22 hours at LTO-7 speeds, and LTO-9 would roughly halve that time. (The three companies behind the standard have not advertised the speed part of the spec yet, but it should be somewhere around 1200-1400 MB/s.) If the difference between 22 and 11 hours changes your business, then by all means upgrade to LTO-9.

Second, LTO-9 offers a 50% capacity increase over LTO-8 and a 200% capacity increase over LTO-7. If you are currently paying by the tape for shipping your tapes or storing them in a vault, a financial argument could be made for upgrading to LTO-9 and copying all of your existing tapes to newer, bigger tapes. You might be able to significantly reduce those monthly costs if you’re using LTO-8 tapes and reduce them even more if you’re using LTO-7.

The final good reason to upgrade is if your current tape drives are so old you can no longer obtain service for them or that, because of their age, require prohibitively expensive service contracts. It is possible that replacing your old tape drives with newer LTO-9 drives might actually be less expensive than maintaining a service contract on your older tape drives.

### Risks of upgrading

Upgrading your tape drives is not without risks. The first only applies if you are still sending very slow backups directly to tape without caching them with a disk target before copying them to tape. In that case, upgrading your tape drive is likely to exacerbate the problem. If you are not making a 900 MB/s tape drive happy with your design, upgrading to a 1200-1400 MB/s tape drive will make that situation worse.

LTO standards are read-compatible to two previous generations, and write-compatible to one previous generation. That means that the oldest tapes that LTO-9 drives will be able to read are LTO-7 and LTO-8 but not tapes older than that. If you have older drives you will be forced to do one of two things: Keep some of your older tape drives or transfer all of your older tapes onto newer tapes.

If the reason you are upgrading is because your current tape drives are too old and not serviceable, the first option really isn't available to you. That is unless you keep them around just in case and take them off a service contract.

The second option is more likely, and a good backup or archive product should be able to help you consolidate all of your older backup tapes onto newer tapes. This will also be required if the reason you are upgrading is to reduce your monthly cost of storing the tapes.

Realize that although tape drives are very good at writing data, such a process is never risk free. One bad bit in 1019 bits is still more than zero, so recognize that this kind of error exists and work it into your process. One thing you might do is consolidate all of the older tapes onto newer tapes, but then safely store the older tapes somewhere just in case one of the copies went bad. Or you could create two copies on newer tape because the odds of a bit error in the same place during both copies is 1019 X1019.

### Risks of not upgrading

There are risks involved in not upgrading, the biggest of which have to do with the lifespan of your current tape drives. Can you still buy additional new tape drives of the model that you are using? If so, your risks of not upgrading at this point are relatively low. Even if you can no longer buy new tape drives of your current model, you can still probably get the ones you own serviced. As long as your current tape drives are serviceable with parts and technicians that know how to service them, there shouldn't be too much of a risk of holding onto them. But remember the cost of the service contract may be too steep for your budget.

### It's your call

The most important point is that many people upgrade their tape drives because they think that buying faster tape drives will make the backup or archive system faster. That is not a reason to upgrade unless you know for a fact that you are already maxing out the transfer rate of your current tape drives, which is unlikely. (I have never seen that happen in production.) Take a look at the reasons for upgrading and the risks, and weigh them against the risks of not upgrading. In the end, it's your company's data and money, so it's your call.

Join the Network World communities on [Facebook][2] and [LinkedIn][3] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3575810/should-you-upgrade-tape-drives-to-the-latest-standard.html

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
