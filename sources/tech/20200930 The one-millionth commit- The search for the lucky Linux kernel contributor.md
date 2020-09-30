[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (The one-millionth commit: The search for the lucky Linux kernel contributor)
[#]: via: (https://www.linux.com/news/the-one-millionth-commit-the-search-for-the-lucky-linux-kernel-contributor/)
[#]: author: (The Linux Foundation https://www.linuxfoundation.org/blog/2020/09/the-one-millionth-commit-the-search-for-the-lucky-linux-kernel-contributor/)

The one-millionth commit: The search for the lucky Linux kernel contributor
======

![][1]

This week has been “a week of millions” for the Linux Foundation, with our announcement that [over 1 million people][2] have taken our free [Introduction to Linux][3] course. As part of the research for our recently published [2020 Linux Kernel History Report][4], the Kernel Project itself determined that it had surpassed one million code commits. Here is how we established the identity of this lucky Kernel Project contributor.

### Methodology:

The historical repo of BitKeeper (converted to Git) has 63,428 commits. We then found the merge at which Linus Torvalds’ repo has at least 936,572 commits (his repo has at least this many commits).

At commit **92c59e126b21fd212195358a0d296e787e444087** the repo had 936,456 commits (116 shy of the million)

```
>git checkout 92c59e126b21fd212195358a0d296e787e444087

>git log --oneline | wc

 936456 7483489 62991540
```

The next merge **2f3fbfdaf77f3ac417d0511fac221f76af79f6fc** passed that number, with 937,105

```
> git checkout 2f3fbfdaf77f3ac417d0511fac221f76af79f6fc

> git log --oneline | wc

 937105 7489456 63037625
```

So on merge **2f3fbfdaf77f3ac417d0511fac221f76af79f6fc** Linus’ repo passed the 1M mark (to be precise, 1,000,533 including BitKeeper commits):

```
commit 2f3fbfdaf77f3ac417d0511fac221f76af79f6fc 92c59e126b21fd212195358a0d296e787e444087 f510ca05271b6f71bd532fe743b39f628110223f (HEAD)

Merge: 92c59e126b21 f510ca05271b

Author: Linus Torvalds <torvalds@linux-foundation.org>

Date:   Mon Aug 3 19:19:34 2020 -0700


Merge tag 'arm-dt-5.9' of git://git.kernel.org/pub/scm/linux/kernel/git/soc/soc
```

At this point, we can simply list the 936,572nd commit in the log:

```
>git log --oneline | tail -936572 | head -1

85b23fbc7d88 x86/cpufeatures: Add enumeration for SERIALIZE instruction
```

### And the committer is…

```
git log -1 85b23fbc7d88

commit 85b23fbc7d88f8c6e3951721802d7845bc39663d

Author: Ricardo Neri <ricardo.neri-calderon@linux.intel.com>

Date:   Sun Jul 26 21:31:29 2020 -0700

    x86/cpufeatures: Add enumeration for SERIALIZE instruction
```

Ricardo’s momentous commit to the Kernel was to add enumeration support for the SERIALIZE instruction, supported in Intel’s forthcoming Sapphire Rapids and Alder Lake microarchitectures for their 10-nanometer server and workstation chips. Ricardo is a software engineer who has been working on Linux feature support for Intel’s microprocessors for 12 years as part of the company’s CPU enabling team.

For more about Intel Corporation’s Ricardo Neri, the one-millionth Linux Kernel code committer, [please read and watch our interview, conducted by Swapnil Bhartiya on Linux.com.][5]

The post [The one-millionth commit: The search for the lucky Linux kernel contributor][6] appeared first on [The Linux Foundation][7].

--------------------------------------------------------------------------------

via: https://www.linux.com/news/the-one-millionth-commit-the-search-for-the-lucky-linux-kernel-contributor/

作者：[The Linux Foundation][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linuxfoundation.org/blog/2020/09/the-one-millionth-commit-the-search-for-the-lucky-linux-kernel-contributor/
[b]: https://github.com/lujun9972
[1]: https://www.linuxfoundation.org/wp-content/uploads/2020/09/million.png
[2]: https://training.linuxfoundation.org/announcements/free-intro-to-linux-course-surpasses-one-million-enrollments/
[3]: https://training.linuxfoundation.org/training/introduction-to-linux-2/
[4]: https://www.linuxfoundation.org/blog/2020/08/download-the-2020-linux-kernel-history-report/
[5]: http://www.linux.com/featured/meet-the-one-millionth-committer-to-linux-ricardo-neri
[6]: https://www.linuxfoundation.org/blog/2020/09/the-one-millionth-commit-the-search-for-the-lucky-linux-kernel-contributor/
[7]: https://www.linuxfoundation.org/
