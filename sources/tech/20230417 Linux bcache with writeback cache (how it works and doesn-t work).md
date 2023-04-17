[#]: subject: "Linux bcache with writeback cache (how it works and doesn’t work)"
[#]: via: "https://fedoramagazine.org/linux-bcache-with-writeback-cache-how-it-works-and-doesnt-work/"
[#]: author: "Giuseppe Della Bianca https://fedoramagazine.org/author/giusdbg/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Linux bcache with writeback cache (how it works and doesn’t work)
======

![][1]

Photo by [Andrey Matveev][2] on [Unsplash][3]

bcache is a simple and good way to have large disks (typically rotary and slow) exhibit performance quite similar to an SSD disk, using a small SSD disk or a small part of an SDD.

In general, bcache is a system for having devices composed of slow and large disks, with fast and small disks attached as a cache.

This article will discuss performance and some optimization tips as well as configuration of bcache.

The following terms are used in bcache to describe how it works and the parts of bcache:

_backing device_ | slow and large disk (disk intended to actually hold the data)
---|---
_cache device_ | fast and small disk (cache)
_dirty cache_ | data present only in the cache device
_writeback_ | writing to the cache device and later (much later) to the backing device
_writeback rate_ | cache write speed in the backing device

A disk data cache has always existed, it is the free RAM in the operating system. When data is read from the disk it is copied to RAM. If the data is already in RAM, it is read from RAM rather than being read from disk again. When data is written to the disk, it is written to RAM and after a few moments written to the disk as well. The time data spends only in RAM is very short since RAM is volatile.

bcache is similar, only it has various modes of cache operation. The mode that is faster in writing data is writeback. It works the same as for RAM, only instead of RAM there is a SATA or NVME SSD device. The data may reside only in the cache for much longer, even forever, so it is a bit riskier (if you break the SSD, the data that resided only in the cache is lost, with a good chance that the whole filesystem becomes inaccessible).

### Performance Comparison

It is very difficult to gather reliable data from any tests, either with real cases or with special programs. They always give extremely variable, different, unstable values. The various caches present and the type of filesystem (btrfs, journaled, etc.), make the values very variable. It is advisable to ignore small differences (say 5-10%).

The following performance data refers to the test below (random and multiple reads/writes), trying to always maintain the same conditions and repeating three times in immediate sequence.

```

    $ sysbench fileio --file-total-size=2G --file-test-mode=rndrw --time=30 --max-requests=0 run

```

The tables below show the performance of the separate devices:

**Performance of the backing device (RAID 1 with 1TB rotary disks)**

Throughput: |  |
---|---|---
read, MiB/s: 0.22 | read, MiB/s: 0.23 | read, MiB/s: 0.19
written, MiB/s: 0.15 | written, MiB/s: 0.16 | written, MiB/s 0.13
Latency (ms): |  |
max: 174.92 | max: 879.59 | max: 1335.30
95th percentile: 87.56 | 95th percentile: 87.56 | 95th percentile: 89.16

RAID 1 with 1TB rotary disks

**Performance of the cache device (SSD SATA 100GB)**

Throughput: |  |
---|---|---
read, MiB/s: 7.28 | read, MiB/s: 7.21 | read, MiB/s: 7.51
written, MiB/s: 4.86 | written, MiB/s: 4.81 | written, MiB/s 5.01
Latency (ms): |  |
max: 126.55 | max: 102.39 | max: 107.95
95th percentile: 1.47 | 95th percentile: 1.47 | 95th percentile: 1.47

Cache device (SSD SATA 100GB)

The theoretical expectation that a bcache device will be as fast as the cache device is (physically) impossible to achieve. On average, bcache is significantly slower and only sometimes approaches the same performance as the cache device. Improved performance almost always requires various compromises.

Consider an example assuming there is a 1TB bcache device and a 100GB cache. When writing a 1TB file, the cache device is filled, then partially emptied to the backing device, and refilled again, until the file is fully written.

Because of this (and also because part of the cache also serves data when reading) there is a limit on the length of the file’s sequential data that are written to the cache. Once the limit is exceeded, the file data is written (or read) directly to the backing device, bypassing the cache.

bcache also limits the response delay of the disks, but disproportionately so, especially for SSD SATA, degrading the performance of the cache.

The dirty cache should be emptied to decrease the risk of data loss and to have cache available when it is needed. This should only be done when the devices exhibit little or no activity, otherwise the performance available for normal use collapses.

Unfortunately, the default settings are too low, and the writeback rate adjustment is crude. To improve the writeback rate adjustment it is necessary to write a program (I wrote a script for this).

The following commands provide the necessary optimizations (required at each startup) to get better performance from the bcache device.

```

    # echo 0 > /sys/block/bcache0/bcache/cache/congested_write_threshold_us
    # echo 0 > /sys/block/bcache0/bcache/cache/congested_read_threshold_us
    # echo 600000000 > /sys/block/bcache0/bcache/sequential_cutoff
    # echo 40 > /sys/block/bcache0/bcache/writeback_percent

```

The following tables compare the performance with the default values and the optimization results.

**Performance with default values**

Throughput: |  |
---|---|---
read, MiB/s: 3.37 | read, MiB/s: 2.67 | read, MiB/s: 2.61
written, MiB/s: 2.24 | written, MiB/s: 1.78 | written, MiB/s 1.74
Latency (ms): |  |
max: 128.51 | max: 102.61 | max: 142.04
95th percentile: 9.22 | 95th percentile: 10.84 | 95th percentile: 11.04

Default values (SSD SATA 100GB)

**Performance with optimizations**

Throughput: |  |
---|---|---
read, MiB/s: 5.96 | read, MiB/s: 3.89 | read, MiB/s: 3.81
written, MiB/s: 3.98 | written, MiB/s: 2.59 | written, MiB/s 2.54
Latency (ms): |  |
max: 131.95 | max: 133.23 | max: 117.76
95th percentile: 2.61 | 95th percentile: 2.66 | 95th percentile: 2.66

Optimization (SSD SATA 100GB)

**Performance with the writeback rate adjustment script**

Throughput: | ﻿ | ﻿
---|---|---
read, MiB/s: 6.25 | read, MiB/s: 4.29 | read, MiB/s: 5.12
written, MiB/s: 4.17 | written, MiB/s: 2.86 | written, MiB/s 3.41
Latency (ms): | ﻿ | ﻿
max: 130.92 | max: 115.96 | max: 122.69
95th percentile: 2.61 | 95th percentile: 2.66 | 95th percentile: 2.61

Writeback rate adjustment (SSD SATA 100GB)

In single operations (without anything else happening in the system) on large files, adjusting the writeback rate becomes irrelevant.

### Prepare the backing, cache and bcache device

To create a bcache device you need to install the bcache-tools. The command for this is:

```

    # dnf install bcache-tools

```

bcache devices are visible as _/dev/bcacheN_ (for example _/dev/bcache0_ ). Once created, they are managed like any other disk.

More details are available at <https://docs.kernel.org/admin-guide/bcache.html>

CAUTION: Any operation performed can immediately destroy the data on the partitions and disks on which you are operating. Backup is advised.

In the following example _/dev/md0_ is the backing device and _/dev/sda7_ is the cache device.

**WARNING:** _bcache device cannot be resized._
**NOTE:** _bcache refuses to use partitions or disks with a filesystem already present._

```

    To delete an existing filesystem you can use:
    # wipefs -a /dev/md0
    # wipefs -a /dev/sda7

```

#### Create the backing device (and therefore the bcache device)

```

    # bcache make -B /dev/md0
    if necessary (device status is inactive)
    # bcache register /dev/md0

```

#### Creating the cache device (and hooking the cache to the backing device)

```

    # bcache make -C /dev/sda7
    if necessary (device status is inactive)
    # bcache register /dev/sda7

```

```

    # bcache attach /dev/sda7 /dev/md0

```

```

    # bcache set-cachemode /dev/md0 writeback

```

#### Check the status

```

    # bcache show

```

The output from this command includes information similar to the following:
(if the status of a device is inactive, it means that it must be registered)

Name | Type | State | Bname | AttachToDev
---|---|---|---|---
/dev/md0 | 1 (data) | clean(running) | bcache0 | /dev/sda7
/dev/sda7 | 3 (cache) | active | N/A | N/A

bcache show

#### Optimize

```

    # echo 0 > /sys/block/bcache0/bcache/cache/congested_write_threshold_us
    # echo 0 > /sys/block/bcache0/bcache/cache/congested_read_threshold_us
    # echo 600000000 > /sys/block/bcache0/bcache/sequential_cutoff
    # echo 40 > /sys/block/bcache0/bcache/writeback_percent

```

### In closing

Hopefully this article will provide some insight on the benefits of bcache if it suits your needs.

As always, nothing fits all cases and all people’s preferences. However, understanding (even roughly) how things work, and especially how they don’t work, as well as how to adapt them, makes the difference in having satisfactory results or not

* * *

### Addendum

The following charts show the performance with a SSD NVME cache device rather than SSD SATA as shown above.

**Performance of the cache device (SSD NVME 100GB)**

Throughput: | ﻿ | ﻿
---|---|---
read, MiB/s: 16.31 | read, MiB/s: 16.17 | read, MiB/s: 15.77
written, MiB/s: 10.87 | written, MiB/s: 10.78 | written, MiB/s 10.51
Latency (ms): | ﻿ | ﻿
max: 17.50 | max: 15.30 | max: 46.61
95th percentile: 1.10 | 95th percentile: 1.10 | 95th percentile: 1.10

Cache device (SSD NVME 100GB)

**Performance with optimizations**

Throughput: |  |
---|---|---
read, MiB/s: 7.96 | read, MiB/s: 6.87 | read, MiB/s: 7.73
written, MiB/s: 5.31 | written, MiB/s: 4.58 | written, MiB/s 5.15
Latency (ms): |  |
max: 50.79 | max: 84.40 | max: 108.71
95th percentile: 2.00 | 95th percentile: 2.03 | 95th percentile: 2.00

Optimization (SSD NVME da 100GB)

**Performance with the writeback rate adjustment script**

Throughput: | ﻿ | ﻿
---|---|---
read, MiB/s: 8.43 | read, MiB/s: 7.52 | read, MiB/s: 7.34
written, MiB/s: 5.62 | written, MiB/s: 5.02 | written, MiB/s 4.89
Latency (ms): | ﻿ | ﻿
max: 72.71 | max: 78.60 | max: 50.61
95th percentile: 2.00 | 95th percentile: 2.03 | 95th percentile: 2.11

Writeback rate adjustment (SSD NVME 100GB)

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/linux-bcache-with-writeback-cache-how-it-works-and-doesnt-work/

作者：[Giuseppe Della Bianca][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/giusdbg/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/04/bcache-816x345.jpg
[2]: https://unsplash.com/fr/@zelebb?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/ssm-and-hdd?orientation=landscape&utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
