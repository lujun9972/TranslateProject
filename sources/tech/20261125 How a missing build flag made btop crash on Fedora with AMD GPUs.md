[#]: subject: "How a missing build flag made btop crash on Fedora with AMD GPUs"
[#]: via: "https://fedoramagazine.org/how-a-missing-build-flag-made-btop-crash-on-fedora-with-amd-gpus/"
[#]: author: "Igor Giamoniano https://fedoramagazine.org/author/igorgbr/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How a missing build flag made btop crash on Fedora with AMD GPUs
======

![][1]

In July 2026, I opened btop on my Fedora 44 machine and the program died before drawing the first screen. The terminal returned this line:

```

    btop: src/rocm_smi.cc:136: uint64_t get_multiplier_from_str(char): Assertion `false' failed.
    Aborted (core dumped)

```

This article tells the story about how an ordinary user carried a fix into Fedora, and how you can do the same.

If you haven't used it, [btop][2] is a terminal resource monitor. It reads GPU information through the ROCm SMI library (packaged in Fedora as rocm-smi), which exposes data from the amdgpu driver. The error came from inside that library, not from btop, and the message made that clear. The strangest part: the same version of btop worked fine on Ubuntu and Arch with the same GPU.

Almost three months passed between my first crash and the stable update reaching users. The pull request sat unreviewed for almost eight weeks. Along the way, I found a [two-year-old report][3] closed as “not a bug,” a build flag that nobody was defining, and a direct email that finally unblocked the process.

### A two-year-old bug, closed as NOTABUG

In February 2024, Jerry James installed btop on Fedora 39 and hit the same crash on first run. The automatic report from ABRT (Fedora’s tool for capturing program crashes) pointed to rocm-smi. [In Bugzilla, he identified the exact function][4]: freq_string_to_int was receiving a line from sysfs that it could not parse.

Two things are worth explaining here. sysfs is the kernel’s virtual filesystem, where each file under /sys exposes a piece of the hardware state. An assert is a check used during development. If the tested condition is false, the program aborts immediately instead of continuing with an invalid state.

Tom Rix, from AMD, replied in Bugzilla arguing that if sysfs was malformed, the problem was in the kernel. Jerry posted the contents of the file and pointed to the kernel code that prints that format on purpose. This information was added in a [2020 commit][5]. It was not a formatting error: it was a case the rocm-smi parser did not know how to read. The discussion stalled and in November 2024 the [report was closed as NOTABUG][3], near the end of life of Fedora 39.

Two parties, each certain the problem was on the other side.

### The bug returns, and where I come in

On November 28, 2025, Russell Odom [opened a new report][6] on Fedora 43. Jerry returned to the case, disagreed with the NOTABUG, and took the problem upstream, opening [issue #231][7] in the rocm_smi_lib repository.

In July 2026, I hit the same crash on Fedora 44 and [published my analysis in Bugzilla][8]. The conclusion: these were two independent problems.

The first, already tracked upstream, was the parser that did not understand the line. The second, and the real cause of the abort, was in Fedora’s packaging. Nobody replied to my comment.

### The four-link chain

To understand the crash, it helps to follow the data’s path from the kernel to btop. There are four links.

**First link: the kernel prints an unusual format.** btop asks for the GPU memory frequency, and the library reads the file /sys/class/drm/card0/device/pp_dpm_mclk. The normal format is a list of levels, with the current one marked with an asterisk:

```

    0: 400Mhz
    1: 1067Mhz *

```

When the current frequency does not match any defined level, the kernel prints an extra line without an index, on purpose, since the 2020 commit. This is common on APUs, AMD processors with integrated graphics:

```

    2: 400Mhz
    3: 1067Mhz
       1066Mhz *

```

**Second link: the parser does not understand that line.** When splitting the number from the unit, the unit string ends up empty, and the get_multiplier_from_str function receives a null character. It falls into the default case, which is:

```

    assert(false);
    throw amd::smi::rsmi_exception(RSMI_STATUS_UNEXPECTED_DATA, ...);

```

**Third link: the assert.** This is where a build flag called

NDEBUG

comes in. When it is defined, every assert() compiles to nothing. When it is not, they stay active.

**Fourth link: the Fedora package never defined NDEBUG.** The result: the assert fired, called abort(), and the whole process died. btop did not receive an error code; it was taken down together with the library.

The upstream intent is clear: with NDEBUG, the assert disappears, the throw runs, the library’s public functions catch the exception, and they return an error code. btop logs a warning and keeps running. If the assert were meant to stay active in production, the throw right after it would be dead code.

### Why the problem was Fedora-specific

Fedora’s %cmake macro defines CMAKE_CXX_FLAGS_RELEASE="-DNDEBUG", but it does not define CMAKE_BUILD_TYPE, and the rocm-smi spec does not either. CMake only adds per-configuration flags such as CMAKE_CXX_FLAGS_RELEASE when CMAKE_BUILD_TYPE selects that configuration. Without a build type, the flag is defined and never used.

The proof came from a measurement. In September 2026, I took the case to the [devel@ list][9] after five weeks without a review on the pull request. Florian Weimer, from Red Hat, [asked][10] whether NDEBUG shouldn’t already be active, since %cmake defines the Release flag. [I replied by measuring][11]: on Rawhide, with the original spec, 0 out of 34 compile lines had -DNDEBUG.

AMD’s own packages and Arch’s build use -DCMAKE_BUILD_TYPE=Release. That is why the abort was specific to Fedora.

### The one-line fix

My first attempt was to use CMAKE_BUILD_TYPE=Release. It compiled and fixed the crash, but the build failed with Empty %files file debugsourcefiles.list. The reason: the upstream CMakeLists.txt has a rule that, only in Release, runs strip on the library right after linking. Without the symbols, Fedora cannot generate the debug source package.

The solution was to inject NDEBUG through the compile flags, without touching the build type:

```

    %build
    export CXXFLAGS="%{build_cxxflags} -DNDEBUG"
    %cmake \

```

That one line was the whole fix.

### From pull request to stable update

Opening the PR in dist-git, the Fedora repository that holds the spec and patches for each package, was not the easy part. I spent hours trying to push over SSH before discovering that non-packagers need to use [HTTPS with an OIDC token][12] or the fork’s web editor. The path to users was even longer:

  * 2026-07-28: [PR opened][13] against Rawhide, tested in mock, with debuginfo and debugsource intact.
  * 2026-09-01: rebased onto the updated Rawhide, tested again.
  * 2026-09-10: [email to devel@][9] asking for review.
  * 2026-09-11: [reply to Florian][11] with the measurement. Then silence again.
  * 2026-09-20: Tom updated the package to 10.0, and my PR conflicted again. I realized he was active; he just wasn’t seeing dist-git PRs.
  * 2026-09-23: direct email to him. Reply the same day.
  * 2026-09-24: I rebased, and [Tom merged it][13] the same day.



After the merge, Tom Rix submitted the updates in Bodhi, Fedora’s update system, which moves builds from testing to stable. The [Fedora 45 update][14] became stable on October 6; the [Fedora 44][15] [u][15][pdate][15] became stable on October 7. I tested the F44 update and gave it a +1, which brought it to the minimum karma.

On October 8, I [confirmed in Bugzilla][16]: on my Ryzen 5 5600G, btop, which used to crash on startup, now runs with GPU monitoring, including under load.

### Check your system

If you use Fedora 44 or 45 with an AMD GPU, you can verify whether the fix is on your system:

```

    rpm -q rocm-smi

```

The minimum version is 7.1.1-4 on F44 and 7.2.1-4 on F45. To see the sysfs format that caused the crash:

```

    cat /sys/class/drm/card*/device/pp_dpm_mclk

```

If a line without an index appears, such as 1066Mhz *, that is the case the parser still does not handle. With the patch, btop no longer crashes, but the GPU clock may briefly disappear from the screen until the parser is fixed upstream.

### How to do the same

If you run into a similar crash, here is the path.

Start with systemd’s crash log:

```

    coredumpctl list btop
    coredumpctl info btop

```

The second command shows the signal (SIGABRT, in my case) and the backtrace. (On systems where ABRT handles crashes, coredumpctl may show nothing; ABRT’s report has the same backtrace.) Look for the first function outside the program that crashed. In my case, get_multiplier_from_str was in librocm_smi64. Find out which package it comes from:

```

    rpm -qf /usr/lib64/librocm_smi64.so*

```

The answer was rocm-smi. Before investigating further, search Bugzilla for the function name: someone may have seen the problem already. If not, clone the package and run a test build:

```

    fedpkg clone -a rocm-smi
    cd rocm-smi
    fedpkg mockbuild

```

The mock build writes its log to results_rocm-smi/<version>/<release>/build.log. Search it for the compile lines and count how many carry the flag:

```

    grep '/usr/bin/g++' results_rocm-smi/*/*/build.log | grep -c DNDEBUG

```

If the number is zero, as it was for me, you have found the packaging link. Test the spec change and check that the debug packages are still generated. Then fork the repository on src.fedoraproject.org, create a branch, open the PR against Rawhide, and link it in Bugzilla.

If the PR sits idle, check whether the maintainer is active on the package. If they are, write to them directly. Keep it short: the link, one line of context, and an offer to do the work. That email, on September 23, is what unblocked mine.

### What remains open

The upstream parser is still broken. [Issue #231][7] remains open, and in June 2026 someone else reported the same assert on IBM Power machines, which shows the parser problem is neither Fedora-specific nor APU-specific.

But the main point of this article is not the parser. It is that a shared library should not take down the process that calls it. Kernel, library, and packaging can disagree about the sysfs format for years; the user should not pay for that with a program that crashes on startup.

Jerry James diagnosed the parser side in 2024. My part was spotting the packaging side and fixing it.

### _**AI note**_

_I used AI to help read the C++ code and suggest tests. I ran the tests, confirmed the cause, and made the fix._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-a-missing-build-flag-made-btop-crash-on-fedora-with-amd-gpus/

作者：[Igor Giamoniano][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/igorgbr/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/11/debug_feature_image-816x345.jpg
[2]: https://github.com/aristocratos/btop
[3]: https://bugzilla.redhat.com/show_bug.cgi?id=2264343
[4]: https://bugzilla.redhat.com/show_bug.cgi?id=2264343#c13
[5]: https://github.com/torvalds/linux/commit/ae7b32e7c30268196e1b3c61e0dcb50b4e842f39
[6]: https://bugzilla.redhat.com/show_bug.cgi?id=2417737
[7]: https://github.com/ROCm/rocm_smi_lib/issues/231
[8]: https://bugzilla.redhat.com/show_bug.cgi?id=2417737#c14
[9]: https://lists.fedoraproject.org/archives/list/devel@lists.fedoraproject.org/thread/NFSNPFJY3WK3TAIMOULQ6GYDFULE3762/
[10]: https://lists.fedoraproject.org/archives/list/devel@lists.fedoraproject.org/message/VGSFSR67WWVDV6B2R45NFU6GBZCSP7QC/
[11]: https://lists.fedoraproject.org/archives/list/devel@lists.fedoraproject.org/message/FTIK5URZR3CVDCORVRFFAE3QPAJGZOJF/
[12]: https://fedoraproject.org/wiki/Infrastructure/HTTPS-commits
[13]: https://src.fedoraproject.org/rpms/rocm-smi/pull-request/4
[14]: https://bodhi.fedoraproject.org/updates/FEDORA-2026-cba5b025f8
[15]: https://bodhi.fedoraproject.org/updates/FEDORA-2026-69050651ef
[16]: https://bugzilla.redhat.com/show_bug.cgi?id=2417737#c16
