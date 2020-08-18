[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Why Linux’s biggest ever kernel release is really no big deal)
[#]: via: (https://www.linux.com/news/why-linuxs-biggest-ever-kernel-release-is-really-no-big-deal/)
[#]: author: (Linux.com Editorial Staff https://www.linux.com/author/linuxdotcom/)

Why Linux’s biggest ever kernel release is really no big deal
======

When the Linux 5.8 Release Candidate opened for testing recently, the big news wasn’t so much what was in it, but its [size][1]. As Linus Torvalds himself [noted][2], _“despite not really having_ _any single thing that stands out … 5.8 looks to be one of our biggest releases of all time.”_

True enough, RC 5.8 features over 14,000 non-merge commits, some 800,000 new lines of code, and added around a hundred new contributors. It might have gotten that large simply because few have been traveling thanks to COVID-19, and we’ve all been able to get more work done in a release window than usual. But from the perspective of this seasoned Linux kernel contributor and maintainer, what is particularly striking about the 5.8 RC release is that its unprecedented size just was not an issue for those that are maintaining it. That, I’d argue, is because Linux has the best workflow process of any software project in the world.

What does it mean to have the best workflow process? For me, it comes down to a set of basic rules that Linux kernel developers have established over time to allow them to produce relentlessly steady and reliable progress on a massive scale.

### One key factor is git

It’s worth starting with a little Linux history. In the project’s early days (1991–2002), people simply sent patches directly to Linus. Then he began pulling in patches from sub-maintainers, and those people would be taking patches from others. It quickly became apparent that this couldn’t scale. Everything was too hard to keep track of, and the project was at constant risk of merging incompatible code.

That led Linus to explore various change management systems including BitKeeper, which took an unusually decentralized approach. Whereas other change management systems used a check-out/modify/check-in protocol, BitKeeper gave everyone a copy of the whole repo and allowed developers to send their changes up to be merged. Linux briefly adopted BitKeeper in 2002, but its status as a proprietary solution proved incompatible with the community’s belief in open source development, and the relationship ended in 2005. In response, Linus disappeared for a while and came back with [git][3], which took decentralized change management in a powerful new direction and was the first significant instantiation of the management process that makes Linux development work so well today.

Here are seven best practices — or fundamental tenets — that are key to the Linux kernel workflow:

#### Each commit must do only one thing

A central tenet of Linux is that all changes must be broken up into small steps. Every commit that you submit should do only one thing. That doesn’t mean every commit has to be small in size. A simple change to the API of a function that is used in a thousand files can make the change massive but is still acceptable as it is all part of performing one task. By always obeying this single injunction, you make it much easier to identify and isolate any change that turns out to be problematic. It also makes it easier for the patch reviewer only to need to worry about a single task that the patch accomplishes. 

#### Commits cannot break the build

Not only should all changes be broken into the smallest possible increments, but they also can’t break the kernel. Every step needs to be fully functional and not cause regressions. This is why a change to a function’s prototype must also update every file that calls it, to prevent the build from breaking. So every step has to work as a standalone change, which brings us to the next point:

#### All code is bisectable

If a bug is discovered at some point, you need to know which change caused the problem. Essentially, a bisect is an operation that allows you to find the exact point in time where everything went wrong.

You do that by going to the middle of where the last known working commit exists, and the first commit known to be broken, and test the code at that point. If it works, you go forward to the next middle point. If it doesn’t, you go back to the middle point in the other direction. In that way, you can find the commit that breaks the code from tens of thousands of possible commits in just a dozen or so compiles/tests. Git even helps in automating this process with the **git bisect** functionality. 

Importantly, this only works well if you abide by the previous rules: that each commit does just one thing. Otherwise, you would not know which of the many changes in the problem commit caused the issue. If a commit breaks the build or does not boot, and the bisect lands on that commit, you will not know which direction of the bisect to take. This means that you should never write a commit that depends on a future commit, like calling a function that doesn’t exist yet, or changing the parameters of a global function without changing all its callers in that same commit.

#### Never rebase a public repository

The Linux workflow process won’t allow you to rebase any public branch used by others. Once you rebase, the commits that were rebased will no longer match the same commits in the repositories based on that tree. A public tree that is not a leaf in a hierarchy of trees must not rebase. Otherwise, it will break the trees lower in the hierarchy. When a git repository is based on another tree, it builds on top of a commit in that tree. A rebase replaces commits, possibly removing a commit that other trees are based on.** **

#### Git gets merging right

Getting merging right is far from a given. Other change management systems are a nightmare to merge code from different branches. It often ends up with hard to figure out conflicts and takes a huge amount of manual work to resolve. Git was structured to do the job effortlessly, and Linux benefits directly as a result. It’s a huge part of why the size of the 5.8 release wasn’t really a big deal. The **5.8-rc1** release averaged 200 commits a day, with 880 total merges from 5.7. Some maintainers noticed a bit more of a workload, but nothing was too stressful or would cause burnout.

#### Keep well-defined commit logs

Unfortunately, this may be one of the most essential best practices that are skipped over by many other projects. Every commit needs to be a stand-alone, and that includes its commit log. Everything required to understand the change being made must be explained in the change’s commit log. I found that some of my most lengthy and descriptive changelogs were for single line commits. That’s because a single line change may be for a very subtle bug fix, and that bug fix should be thoroughly described in the changelog.

A couple of years after submitting a change, it is highly unlikely that anyone would know why that change was made. A **git blame** can show what commits changed the code of a file. Some of these commits may be very old. Perhaps you need to remove a lock, or make a change to some code and do not precisely know why it exists. A well-written changelog for that code change can help determine if that code can be removed or how it can be modified. There have been several times I was glad I wrote detailed changelogs on code as I had to remove code, and the changelog description let me know that my changes were fine to make. 

#### Run continuous testing and integration

Finally, an essential practice is running continuous testing and continuous integration. I test every one of my pull requests before I send them upstream. We also have a repro called **linux-next** that pulls in all the changes that maintainers have on a specific branch of their repositories and tests them to assure that they integrate correctly. Effectively, **linux-next** runs a testable branch of the entire kernel that is destined for the next release. This is a public repo so anyone can test it, which happens pretty often – people now even release bug reports on code that’s in **linux-next**. But the upshot is that code that’s been in **linux-next** for a couple of weeks is very likely to be good to go into mainline.

### Best practices exemplified

All of these practices enable the Linux community to release incredibly reliable code on a regular 9-week schedule at such a massive scale (average of 10,000 commits per release, and over 14,000 for the last release).  

I’d point to one more factor that’s been key to our success: culture. There’s a culture of continuous improvement within the kernel community that led us to adopt these practices in the first place. But we also have a culture of trust. We have a clear pathway via which people can make contributions and demonstrate over time that they are both willing and able to move the project forward. That builds a web of trusted relationships that have been key to the project’s long term success.

At the kernel layer, we have no choice but to follow these practices. All other applications run on top of the kernel. Any performance problem or bug in the kernel becomes a performance problem or bug for the applications on top. All error paths must exit peacefully; otherwise, the entire system will be compromised. We care about every error because the stakes are so high, but this mindset will serve any software project well.

Applications can have the luxury of merely crashing due to a bug. It will annoy users, but the stakes are not as high. Quality software should not take bugs lightly. This is why the Linux development workflow is considered the golden standard to follow.

_About the author: Steven Rostedt ([@srostedt][4]) is a Linux kernel contributor and an Open Source Engineer at VMware. You can learn more about Steven’s work at [blogs.vmware.com/opensource][5] or [@VMWopensource][6] on Twitter_

--------------------------------------------------------------------------------

via: https://www.linux.com/news/why-linuxs-biggest-ever-kernel-release-is-really-no-big-deal/

作者：[Linux.com Editorial Staff][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linux.com/author/linuxdotcom/
[b]: https://github.com/lujun9972
[1]: https://9to5linux.com/linus-torvalds-kicks-off-development-of-linux-kernel-5-8-as-biggest-release-of-all-time
[2]: https://lore.kernel.org/lkml/CAHk-=whfuea587g8rh2DeLFFGYxiVuh-bzq22osJwz3q4SOfmA@mail.gmail.com/
[3]: https://git.kernel.org/pub/scm/git/git.git/
[4]: https://twitter.com/srostedt
[5]: https://blogs.vmware.com/opensource
[6]: https://twitter.com/vmwopensource
