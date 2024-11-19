[#]: subject: "Benchmarking Your Linux System: What, Why and How"
[#]: via: "https://itsfoss.com/benchmark-tools-linux/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Benchmarking Your Linux System: What, Why and How
======

[![Warp Terminal][1]][2]

If you are using Linux on your system, it is a rare phenomenon that your system is not performing well.

But, " _how fast?_ " is a question that we often ask ourselves or wonder when thinking to compare our experiences.

The easy and effective solution to know that is to **benchmark your Linux system**.

_So, how do you do that?_ **Using some benchmarking tools.** _And, what are the benchmarking tools available on Linux?_

Fret not, in this article, I shall guide you with the tools with which you can perform a Linux system benchmark for all kinds of use-cases.

✋

Benchmarking is not the complete story. But, only a part of it when comparing or evaluating the performance of a system.

To ensure your system runs the best, you need the correct drivers, up-to-date software, performance-focused desktop environment, a stable kernel, and a few other things.

### How to evaluate the benchmark results?

With every benchmark tool, you end up getting a final score.

The score alone is not meaningful unless you have a comparison in mind.

You can either perform benchmarks on two different systems to measure the performance gap. Or, you can benchmark the same system at different time intervals to check if a configuration/system update impacted the performance in any way.

![Geekbench scores for a laptop with AMD Ryzen 3 5300U \(Ubuntu\) vs desktop with an Intel i5-11600k \(Archcraft\)][3]

For example, you benchmark the system right after you set it up for the first time, and then after a few months.

Some tools also provide you with access to a leaderboard chart, where you can see scores of systems with various hardware configurations. You may also find them mention a " **baseline** " which is a reference score of a particular hardware.

For instance, Geekbench utilizes 2500 as baseline score, which is for an i7-12700 processor. You can know if your CPU performs better or worse accordingly.

In either case, you can check the Geekbench website that [ranks all processors][4], and then compare it against your score.

![][5]

**It is recommended to use the same benchmark test/tool when comparing multiple systems.**

### 4 tools that can help you benchmark your Linux computer

Some benchmarking tools are open source, while a few are not. Some are available as a standalone tool for a quick check, and some help you take an in-depth analysis of your system (which is not needed for everyone).

I list the best ones to help you get the job done.

📋

Most of the benchmarking tools are CLI-based.

#### 1\. UnixBench

![][6]

****Key Features:****

• Traditional test
• Open Source
• Easy to Use

One of the most traditional open source benchmark suite is [UnixBench][7].

It is derived from the original BYTE UNIX benchmark app built back in 1983, and has been maintained over the years with several revisions. It may not be the most modern solution out there, but it performs essential tests that have been long proven to be indicators of performance.

You get around ten different tests which include **basic 2D/3D graphics** , **process creation** , **string handling** , **floating-point operations** , **file copy** , and a couple of others.

It is alright if you do not understand the meaning of the tests it performs. All you need to know is that it performs a type of stress test of your entire system ( _not just a part of it_ ). So, the results will depend on the operating system, libraries, hardware, and compiler.

Once installed, you just have to run it by typing the following command:

```

    ubench

```

Here's how the results look:

![Click on the images to expand][8]

As you can see in the screenshots, as the test progresses (and completes), you can head to the mention directory ( _usr/lib/unixbench/results_ ) to get the details. You should find HTML and log files, access what you are comfortable with.

![][9]

You can install it via [AUR for Arch Linux][10]. And, for Ubuntu-based distros, it is available as a [Snap][11].

💭

UnixBench could be an older generation of benchmarking tests, but it has its benefits of technical testing and being an open source tool. No options to fiddle around, just type in one command after installation to start benchmarking, it is that easy!

[UnixBench][7]

#### 2\. Geekbench

![][12]

****Key Features:****

• Modern benchmark suite
• Cross-Platform
• Proprietary
• Uploads results to Geekbench website directly

If you want a modern tool to benchmark your entire system and do not mind if it is not open source, [Geekbench][13] is one of the most popular option.

There is no binary available for Linux distros. However, you just have to download a **tar.gz** file and run the executable via the terminal ( _no need of sudo_ ) using the following command inside the extracted folder:

```

    ./geekbench_x86_64

```

It worked like charm for me.

![][14]

It will automatically start running single-core, and multicore tests like Ray Tracer, File Compression, HTML5 browser test, PDF Renderer, and several others. In my testing, it took around 2–5 minutes to complete.

All you have to do is click on the URL provided to check your results.

💭

Geekbench testing requires an active internet connection unless you have its Pro edition. So, it uploads the results to its website, and gives you a URL to check the result. It is a neat experience if you do not mind uploading your results.

[Geekbench][13]

#### 3\. Hardinfo2

![][15]

****Key Features:****

• Graphical User Interface
• Open Source
• Easy to Use

[Hardinfo2][16] is a multipurpose tool with which you can [get essential information on your system's network, firmware, and hardware][17]. And, of course, it lets you run benchmarks.

Unlike the above two tools, it does not perform a complete benchmark, but allows you to choose what to test (CPU/Memory/Storage/Graphics).

![Click to expand images][18]

And, it is a complete GUI program. So, you do not need type any commands. Just head to the test you want to perform, and once it is done, it will show you the result along with a reference ranking compared to other hardware.

You can decide to generate a report for all the benchmarks you perform (HTML file) and access it separately.

I installed it via AUR on Arch Linux. You can find it in your default Linux repositories. In either case, you can build it from source using the instructions on its GitHub page.

💭

Hardinfo2 is a wondering GUI-focused benchmarking tool. The tests finish up fast, and it is easy to test all kinds of parts in your system. Not to forget, you can get essential system information with this tool, so you will want to keep it around after testing.

[Hardinfo2][16]

**Suggested Read 📖**

![][19]

#### 4\. Phoronix Test Suite

![][20]

****Key Features:****

• Cross-Platform
• Open Source
• Comprehensive tests for advanced users

One of the most advanced (and useful) benchmark applications is the [Phoronix Test Suite][21]. While it is available for all platforms, you can expect the full feature-set on Linux, for which it is tailored for.

It has a massive collection of tools that are installable, as per your requirements. For instance, you can install Geekbench from within the Phoronix Test Suite. Of course, that is a bit redundant in our use-case.

I had to install the suite first, then the test(s) I wanted to perform, and then run them.

The command for installing a test and running it looks like ( _ignore words with #_ ):

```

    phoronix-test-suite install pts/sysbench #installing
    phoronix-test-suite run pts/sysbench #running

```

![][22]

Unfortunately, some tests like pts/browsers failed, while [**pybench**][23] ( _benchmark inspired by geekbench_ ) and [**sysbenc**][24] **h** ( _open source benchmark_ ) tests worked like charm. If you wish to test various aspects of your system using a set of tools (not just limited to one), Phoronix Test Suite is for you.

Moreover, it makes use of [OpenBenchmarking.org][25] to which you can upload your test results, and compare it with great details with other combination of hardware.

You can install the suite via AUR for Arch Linux with **phoronix-test-suite** as the package name or download the deb package from its [GitHub releases][26] for Ubuntu-based distros.

💭

Unlike hardinfo2, it is CLI-based. But, it gives you all kinds of interactive options when you start a test. Things like __if you want to save a report__ , __the name of your system__ , and more. If you follow its documentation correctly, you can perform a comprehensive analysis of your system.

### Do you really need benchmarking?

It depends on what you are looking for but benchmarking could give you some ideas about how your computer is performing with the operating system.

For instance, when [I switched from Ubuntu to Archcraft][27], and I noticed a few performance improvements. In my case, there were visual indicators for me to say that.

But, in many scenarios, you cannot easily gauge the difference unless you extensively use/keep track of file extraction times, boot times, CPU performance, and other resource efficiency/usage stats.

Similarly, maybe you are switching to another distro, and want to check the performance difference. Or, perhaps, you just built a new computer, and want to test the waters before you start using it.

Benchmarking Linux can be helpful in such cases.

💬 _Do you perform a system benchmark? Let me know your thoughts in the comments below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/benchmark-tools-linux/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/11/hp-laptop-benchmark-1.png
[4]: https://browser.geekbench.com/processor-benchmarks
[5]: https://itsfoss.com/content/images/2024/11/geekbench-processor-benchmarks.jpg
[6]: https://itsfoss.com/content/images/2024/11/unixbench-home.png
[7]: https://github.com/kdlucas/byte-unixbench
[8]: https://itsfoss.com/content/images/2024/11/unixbench-results.png
[9]: https://itsfoss.com/content/images/2024/11/unixbench-result-files.png
[10]: https://itsfoss.com/aur-arch-linux/
[11]: https://snapcraft.io/install/unixbench/ubuntu
[12]: https://itsfoss.com/content/images/2024/11/geekbench-scores.png
[13]: https://www.geekbench.com/
[14]: https://itsfoss.com/content/images/2024/11/geekbench.png
[15]: https://itsfoss.com/content/images/2024/11/hardinfo2.png
[16]: https://github.com/hardinfo2/hardinfo2
[17]: https://itsfoss.com/hardinfo/
[18]: https://itsfoss.com/content/images/2024/11/hardinfo2-benchmark.png
[19]: https://itsfoss.com/content/images/icon/android-chrome-192x192-109.png
[20]: https://itsfoss.com/content/images/2024/11/phoronix-test-suite.png
[21]: https://www.phoronix-test-suite.com/
[22]: https://itsfoss.com/content/images/2024/11/phoronix-sys-bench-run.png
[23]: https://github.com/lucianmarin/pybench
[24]: https://github.com/akopytov/sysbench
[25]: http://openbenchmarking.org/
[26]: https://github.com/phoronix-test-suite/phoronix-test-suite/releases
[27]: https://news.itsfoss.com/archcraft-experience/
