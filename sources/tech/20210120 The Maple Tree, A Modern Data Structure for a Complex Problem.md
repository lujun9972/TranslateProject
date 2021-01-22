[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (The Maple Tree, A Modern Data Structure for a Complex Problem)
[#]: via: (https://www.linux.com/news/the-maple-tree-a-modern-data-structure-for-a-complex-problem/)
[#]: author: (Guest Author https://blogs.oracle.com/linux/the-maple-tree)

The Maple Tree, A Modern Data Structure for a Complex Problem
======

In recent years, processors have experienced growth in core counts which have pushed software to be multi-threaded and increased contention in the virtual memory data structure. The memory management subsystem uses the mmap_sem lock for write protection of the VMAs. Optimizing the mmap_sem lock into a rw-semaphore helped contention but did not solve the underlying issue. Even with a single threaded program and a well-intended system admin, contention does arise through proc file accesses for application monitoring.

In this blog, we introduce a new data structure that can track gaps, store ranges, and be implemented in an RCU compatible manner. This is the Maple Tree.
Click to [Read More][1] at Oracle Linux Kernel Development

--------------------------------------------------------------------------------

via: https://www.linux.com/news/the-maple-tree-a-modern-data-structure-for-a-complex-problem/

作者：[Guest Author][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://blogs.oracle.com/linux/the-maple-tree
[b]: https://github.com/lujun9972
[1]: https://blogs.oracle.com/linux/the-maple-tree
