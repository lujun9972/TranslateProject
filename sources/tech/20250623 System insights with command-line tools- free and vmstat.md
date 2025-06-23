[#]: subject: "System insights with command-line tools: free and vmstat"
[#]: via: "https://fedoramagazine.org/system-insights-with-command-line-tools-free-and-vmstat/"
[#]: author: "Andreas Haerter https://fedoramagazine.org/author/andreashaerter/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

System insights with command-line tools: free and vmstat
======

![][1]

Photo by [Hunter Harritt][2] on [Unsplash][3] cropped

In this fifth article of the “[System][4] [insights][5] [with][6] [command-line tools][7]” series we explore _free_ and _vmstat_ , two small utilities that reveal a surprising amount about your Linux system’s health. _free_ gives you an instant snapshot of how RAM and swap are being used. _vmstat_ (the virtual memory statistics reporter) reports a real-time view of memory, CPU, and I/O activity.

By the end of this article you will be able to translate buffers and cache into “breathing room”, read the mysterious _available_ column with confidence, and spot memory leaks or I/O saturation.

### A quick tour of _free_

#### Basic usage

```

    $ free -h
           total    used    free   shared  buff/cache  available
    Mem:    23Gi    14Gi   575Mi    3,3Gi        12Gi      8,8Gi
    Swap:  8,0Gi   6,6Gi   1,4Gi

```

_free_ parses _[/proc/meminfo][8]_ and prints totals for physical memory and swap, along with kernel buffers and cache. Use _-h_ for human-readable units, _-s 1_ to refresh every second, and _-c N_ to stop after N samples which is handy to get a trend when doing something in parallel. For example, free -s 60 -c 1440 gives a 24-hour CSV-friendly record without installing extra monitoring daemons.

**Free memory** refers to RAM that is entirely unoccupied. It isn’t being used by any process or for caching. On server systems, I tend to view this as wasted since unused memory isn’t contributing to performance. Ideally, after a system has been running for some time, this number should remain low.

**Available memory** , on the other hand, represents an estimate of how much memory can be used by new or running processes without resorting to swap. It includes free memory plus parts of the cache and buffers that the system can reclaim quickly if needed.

In essence, the distinction in Linux lies here: _free_ memory is idle and unused, while _available_ memory includes both truly free space and memory that can be readily freed up to keep the system responsive without swapping. **It is not a problem to have a low free memory, available memory is usually what to be concerned about**.

A healthy system might even show _used ≈ total_ yet _available_ remains large; that mostly reflects cache at work. Fedora’s kernel will automatically drop clean cache pages whenever an application needs the space, so cached memory is not wasted. Think of it as a working set that just hasn’t been reassigned yet.

#### Spotting problems with _free_

  * **Rapidly shrinking _available_ combined with rising _swap used_** indicates real memory pressure.
  * **Large swap-in/out spikes** point to thrashing workloads or runaway memory consumers.



### _vmstat_ – Report virtual memory statistics

_vmstat_ (virtual memory statistics) displays processes, memory, paging, block-I/O, interrupts, context switches, and CPU utilization in a single line. Run it with an interval and count to watch trends (output shown below has been split into three sections for better readability):

```

    $ vmstat 1 3
    procs -----------memory----------
     r  b   swpd   free   buff  cache
     2  0 7102404 1392528     36 12335148
     0  0 7102404 1392560     36 12335188
     0  0 7102404 1373640     36 12349928

     ---swap-- -----io----
      si   so    bi    bo
       8   21   130   724
       0    0     0     0
       0    0     8    48

     -system-- -------cpu-------
     in     cs us sy id wa st gu
     2851   19 15  7 77  0  0  0
     5779 7246 14 10 77  0  0  0
     5141 6525 12  9 79  0  0  0

```

#### Anatomy of the output

From the vmstat(8) manpage:

```

    Procs
        r: The number of runnable processes (running or waiting
           for run time).
        b: The number of processes blocked waiting for I/O to
           complete.

    Memory
        These are affected by the --unit option.
        swpd: the amount of swap memory used.
        free: the amount of idle memory.
        buff: the amount of memory used as buffers.
        cache: the amount of memory used as cache.
        inact: the amount of inactive memory.  (-a option)
        active: the amount of active memory.  (-a option)

    Swap
        These are affected by the --unit option.
        si: Amount of memory swapped in from disk (/s).
        so: Amount of memory swapped to disk (/s).

    IO
        bi: Kibibyte received from a block device (KiB/s).
        bo: Kibibyte sent to a block device (KiB/s).

    System
        in: The number of interrupts per second, including
            the clock.
        cs: The number of context switches per second.

    CPU
        These are percentages of total CPU time.
        us: Time spent running non-kernel code.  (user time,
            including nice time)
        sy: Time spent running kernel code.  (system time)
        id: Time spent idle.  Prior to Linux 2.5.41, this
            includes IO-wait time.
        wa: Time spent waiting for IO.  Prior to Linux 2.5.41,
            included in idle.
        st: Time stolen from a virtual machine.  Prior to
            Linux 2.6.11, unknown.
        gu: Time spent running KVM guest code (guest time,
            including guest nice).

```

#### Practical diagnostics

Section | Key Fields | What to watch
---|---|---
**Procs** | **r** (run-queue),
**b** (blocked) | _r_ > CPU cores = contention
**Memory** | **swpd, free, buff, cache** | Rising _swpd_ with falling _free_ = pressure
**Swap** | **si, so** | Non-zero _so_ means the kernel is swapping out
**IO** | **bi, bo** | High _bo_ \+ high _wa_ hints at write-heavy workloads
**System** | **in, cs** | Sudden spikes may indicate interrupt storms
**CPU** | **us, sy, id, wa, st** | High _wa_ (I/O wait) = storage bottleneck


#####

Catching a memory leak

Run _vmstat 500_ in one terminal while your suspect application runs in another. If _free_ keeps falling and _si/so_ climb over successive samples, physical RAM is being exhausted and the kernel starts swapping, which is classic leak behavior.

##### Finding I/O saturation

When _wa_ (CPU wait) and _bo_ (blocks out) soar while _r_ remains modest, the CPU is idle but stuck waiting for the disk. Consider adding faster storage or tuning I/O scheduler parameters.

##### Detecting CPU over-commit

A sustained _r_ that is double the number of logical cores with low _wa_ and plenty of _free_ means CPU is the bottleneck, not memory or I/O. Use _top_ or _htop_ to locate the busiest processes, or scale out workloads accordingly.

### Conclusion

Mastering _free_ and _vmstat_ gives you a lens into memory usage, swap activity, I/O latency, and CPU load. For everyday debugging: start with _free_ to check if your system is truly out of memory, then use _vmstat_ to reveal the reason, whether it’s memory leaks, disk bottlenecks, or CPU saturation.

Stay tuned for the next piece in our “System insights with command-line tools” series and happy Fedora troubleshooting!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/system-insights-with-command-line-tools-free-and-vmstat/

作者：[Andreas Haerter][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/andreashaerter/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/06/insights_via_cli-free-vmstat-816x345.jpg
[2]: https://unsplash.com/@hharritt?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/red-and-blue-lights-from-tower-steel-wool-photography-Ype9sdOPdYc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/system-insights-with-command-line-tools-lscpu-and-lsusb/
[5]: https://fedoramagazine.org/system-insights-command-line-dmidecode-lspci/
[6]: https://fedoramagazine.org/system-insights-with-command-line-tools-lsof-and-lsblk/
[7]: https://fedoramagazine.org/system-insights-command-line-lslogins-lsmod/
[8]: https://www.kernel.org/doc/html/latest/filesystems/proc.html#meminfo
