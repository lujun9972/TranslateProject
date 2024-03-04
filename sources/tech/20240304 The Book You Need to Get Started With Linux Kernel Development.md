[#]: subject: "The Book You Need to Get Started With Linux Kernel Development"
[#]: via: "https://itsfoss.com/linux-kernel-programming-review/"
[#]: author: "Pratham Patel https://itsfoss.com/author/pratham/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Book You Need to Get Started With Linux Kernel Development
======

[![Warp Terminal][1]][2]

I had always scoured the internet searching for a book that was in equivalence to books like the 'Linux Kernel Development' by Robert Love and 'Understanding the Linux Kernel' by Marco Cesati.

Both are amazing books, but are now sadly outdated by the fact that the Linux kernel's codebase moves fast.

I have had the fortune of receiving the second edition of Linux Kernel Programming early, while also owning my own copy of the first edition. Let's get to the review!

📋

I have met the book of this author in real life and have had a tiny, non-influential discussion about this book. ****But, this review, in no way tries to be in the "good grace" of the author, nor the publisher, who provided an early review copy. Every single word written here is my original thought and feedback on this book.****

If you find me sympathising with the author, it is because I understand that the Linux kernel is an unfathomably large project and has complexities unheard of.

### Linux Kernel Programming (Second Edition)

As the title mentions, this review is for the _second edition_ of [Linux Kernel Programming book][3], written by Kaiwan N. Billimoria. In this section, I will give you an overview of the second edition. The primary difference between the first and second edition is the upgrade from the 5.4 to the 6.1 version of the Linux kernel.

**This is a hands-on book and as such, you are expected to perform the exercises. That is how you will learn.** All the necessary code is provided in [this GitHub repository][4]. Fork at will!

The book is available on Amazon and Packt website.

[Linux Kernel Programming (2nd Edition)][3]

This book comes with assignments that you can solve to challenge your understanding and revisit topics that you find tough.

It starts with a gentle introduction to the Linux kernel, its source code and origins. It has **13 chapters** in total, each chapter covering more detail than the previous one and filling the gaps about questions you might have had.

While I won't copy-paste the book's index here, I will lay out the general flow that the author takes, to introduce you to the Linux kernel.

✋

The following sections are not how the author has structured his book. These are _****my interpretation****_ of the author's intention of the learning flow from this book.

#### Basic introduction to the Linux kernel

To introduce you to the Linux kernel, the author covers the following topics:

  1. Creating a dedicated virtual machine for Linux Kernel development and setting up the environment. You wouldn't want a bad kernel or kernel module crashing your main PC now, would you?
  2. Getting familiar with the Linux version nomenclature, including all the various trees that exist.
  3. Creating a simple custom menu entry in the Linux Kernel `Kconfig` (kernel configuration) file.
  4. Building the Linux kernel and installing it. This is done for native x86_64 targets as well as cross compilation for the 64-bit ARM targets like the Raspberry Pi 4.
  5. Understanding concepts like the kernel image, kernel modules. Also learning about initramfs and even how to manually generate the initramfs for your particular kernel.



![A section from the book that takes you through compiling the Linux kernel and modules][5]

As expected, the author does a good job of explaining these concepts to someone who might be new to kernel programming. Some topics like the Linux kernel modules are specific only to the Linux kernel. He covers them in a satisfactory manner, building up for the next chapter.

#### Writing code for the Linux kernel

Once you have a brief idea about the Linux kernel source tree and build process, the author then dives into writing code for the Linux kernel. You are highly encouraged to follow along on your physical/virtual machine in building and running this "out-of-tree" code.

To get you writing code for the Linux kernel, the author starts by making you familiar with the Linux kernel's module system. Topics like the following are covered:

  1. Understanding all the elements of writing a simple Linux kernel module. "Equivalents" of userspace programming conventions like the `main()` function in the kernel code (`init()` and `exit()` functions).
  2. Building these kernel modules. Loading and unloading them. Where to see their output.
  3. Experiments and approaches when you have multiple kernel modules and source files. How to make one source file "depend" on another?



![A figure showing how the simple kernel module works][6]

I will repeat this again. **Please follow along with the code examples.** They are for you to understand and are quite nice in explaining each topic at hand.

#### Linux kernel internals: overview

As the next step, the author then gives you an overview of Linux kernel internals. Foundational blocks that a kernel developer _must know_ , like the following, are covered:

  1. Processes and threads. Diving into the `task_struct` data structure of the Linux for tracking the processes.
  2. Internals of the Linux kernel memory management.
  3. Memory allocation for kernel module(s).
  4. Creating a custom slab cache.
  5. Kernel's "internal" APIs like `kmalloc()`, `kzalloc()`, `kfree()`, `vmalloc()` etc.



The author also goes above and beyond (in my opinion) by covering a necessary, but often ignored feature: KASLR (Kernel Address Space Layout Randomisation).

![Author explaining the task_struct structure of Linux kerne's scheduler.][7]

This section is finally concluded by learning about the Linux kernel out-of-memory (OOM) killer.

#### Linux kernel internals: scheduler

Once the topics that you might have encountered in the Operating Systems class are covered, the author then covers the final, most important task that all the kernels of every operating system in existence covers: **the task scheduler**.

Topics like the following are covered in this section:

  1. KSE and its purpose in scheduling tasks in the Linux kernel.
  2. CFS task scheduler that is part of the Linux kernel's v6.1.y release, that this book targets.
  3. Kernel synchronisation and techniques: spinlocks, locking, etc.
  4. Understanding Cgroups (v2).



![The author clarifies on which memory allocation API of the Linux kernel to use.][8]

By covering a majority of aspects of the Linux kernel's scheduler, the author concludes the end of this book.

💡

Though I did not yet mention it explicitly in any section so far, the author has obviously covered methods of debugging a given problem. :)

### Things I liked in the book

This book comes with a strong recommendation from me for being an excellent resource that is up-to-date with the Linux kernel's source code.

Following are _some_ aspects of this book that I personally liked:

  1. **Hands-on approach** : This book focuses a lot of code and a majority of the text (non-code) in this book is mostly about explaining the code, what it does, what can be done instead and some other ideas for you to explore.
  2. **Assignments** : This is in addition to the first point about a hands-on approach. The author has some fun assignments that you should at least try!
  3. **In-depth explanation** : Almost all of the topics covered have good, in-depth explanation. Those that don't, encourage you to explore further.
  4. **Highly technical content** : This book focuses very little on generic OS fundamentals--unlike your typical CS course book on OS. Instead, it dives straight into how stuff works in the Linux kernel. (I personally prefer this over generic fundamentals because you apply on a known base (Linux) and see the results immediately.)
  5. **Software licensing** : While many software developers don't _have to_ bother with a software license, it is important to know about software licensing as a kernel developer due to various restrictions (discussed in the book). This is a tiny, but important topic.



### Things I wish the book had covered

While this is a great resource, nothing is perfect and as such, I have a teeny tiny list of things that I would have loved to see included.

  1. Coverage of VFS, for a better understanding of file-system included in the Linux kernel codebase.
  2. A tiny section on driver development. Letting readers branch out other than "core" kernel development.
  3. Inclusion of some Rust code, but that would only come with a later kernel version, so I'm willing to let go of this.



Who knows? If you like it and end up purchasing this book, the author might be incentivised for a third edition! ;)

### Conclusion

The second edition of the 'Linux Kernel Programming' book, written by Kaiwan N. Billimoria is an excellent resource for someone seeking a book that helps you get started with Linux kernel programming. It has a lot of hand-holding and _rightfully so_ because the Linux kernel is a huge codebase.

[Linux Kernel Programming (2nd Edition)][3]

I know that many people these days prefer online and video content for programming and other tech related learnings but nothing beats the handiness of a good book. Not only you learn at your pace, revisiting a topic is much easier with books than videos. This is coming from someone who is in early 20s, so that says a lot.

--------------------------------------------------------------------------------

via: https://itsfoss.com/linux-kernel-programming-review/

作者：[Pratham Patel][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/pratham/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://packt.link/CiKha
[4]: https://github.com/PacktPublishing/Linux-Kernel-Programming_2E
[5]: https://itsfoss.com/content/images/2024/03/Screenshot-2024-03-02-at-22.09.48.png
[6]: https://itsfoss.com/content/images/2024/03/Screenshot-2024-03-02-at-22.19.19.png
[7]: https://itsfoss.com/content/images/2024/03/Screenshot-2024-03-02-at-22.21.28.png
[8]: https://itsfoss.com/content/images/2024/03/Screenshot-2024-03-02-at-22.26.50-1.png
