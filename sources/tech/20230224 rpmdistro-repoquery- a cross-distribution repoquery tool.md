[#]: subject: "rpmdistro-repoquery: a cross-distribution repoquery tool"
[#]: via: "https://fedoramagazine.org/rpmdistro-repoquery-a-cross-distribution-repoquery-tool/"
[#]: author: "Michel Alexandre Salim https://fedoramagazine.org/author/salimma/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

rpmdistro-repoquery: a cross-distribution repoquery tool
======

![][1]

Photo by [Paul Green][2] on [Unsplash][3]

This article showcases _rpmdistro-repoquery_ , and describes how to use it to simplify doing RPM-based package operations across multiple distributions. This does not require using SSH to log into another host or starting a container or VM.

### Introduction

Whether you’re a packager, system administrator, or a user of Fedora Linux, CentOS Stream, or their derivatives (RHEL, AlmaLinux, Rocky Linux etc.), you might already be familiar with _dnf repoquery_. This tool allows you to query the repositories configured on the system for information about available packages, whether or not they are currently installed on the local machine.

This is great, within limits. For instance, on Fedora Linux, you can query packages built for stable and branched Fedora Linux releases and, if you install fedora-repos-rawhide, packages in the development branch. Sufficient care is required to make sure you don’t enable repos meant for different Fedora Linux releases by default and thus accidentally upgrade the running system.

Enter [rpmdistro-repoquery][4]: it comes with a set of repo definitions for different RPM-based distributions, but instead of putting them in /etc/yum.repos.d with the repositories meant for actual use, put them in /usr/share/rpmdistro-repoquery (or, if you so choose, you can clone the repository and use definitions that come in the checkout). DNF is then invoked with a custom configuration file and a custom cache location that points at one of the repos for one of the distributions rather than the default location.

The various supported distributions come with the relevant repositories enabled by default. Some have additional repositories that need to be enabled explicitly. For example, source repos are off by default. Also, CentOS Stream configurations come with additional repos for SIG packages that are off by default.

This opens up a lot of use cases. I highlight some of them below.

Note: The primary author of this tool, [Neal Gompa][5], works on a lot of RPM-based Linux distributions. I became involved using it in ebranch.

### Real-life rpmdistro-repoquery use cases

#### Quickly seeing if a CentOS Stream update has made it to the mirrors

In Fedora’s build system, updates go through [Bodhi][6], and once they are marked testing or stable that means there is a compose containing those updates, and they tend to hit mirrors shortly after.

In CentOS Stream, the situation is more complicated, as the QA process is not visible to the public. Take _clang_ for example: given a [commit][7], and a matching [Koji build][8] on January 27th, can we be sure this is pushed out to the mirrors?

It turns out, as of February 9th, it’s not in the mirrors yet:

```

    $ rpmdistro-repoquery centos-stream 9 clang 2>/dev/null
    clang-0:14.0.0-1.el9.i686
    clang-0:14.0.0-1.el9.x86_64
    clang-0:14.0.5-1.el9.i686
    clang-0:14.0.5-1.el9.x86_64
    clang-0:14.0.6-1.el9.i686
    clang-0:14.0.6-1.el9.x86_64
    clang-0:15.0.1-2.el9.i686
    clang-0:15.0.1-2.el9.x86_64
    clang-0:15.0.7-2.el9.i686
    clang-0:15.0.7-2.el9.x86_64

```

#### Comparing what is packaged in different distributions

Scenario: you use / manage a heterogeneous fleet of different distributions. You want to find out if all the packages you need are available (because you might need to package what’s missing).

Let’s see if [myrepos][9] is available on openSUSE Tumbleweed (the rolling distribution):

```

    $ rpm -q myrepos
    myrepos-1.20180726-14.fc37.noarch

    $ rpmdistro-repoquery opensuse-tumbleweed 0 myrepos

    $ rpmdistro-repoquery opensuse-tumbleweed 0 /usr/bin/mr
    mr-0:1.20180726-1.9.noarch

```

Searching by the Fedora Linux package name yields nothing, but in this case, searching by the binary shows a match (since those are in the RPM metadata): myrepos is available, but you’ll need a different package name in your configuration management.

#### ebranch

This is a special case of the former. [ebranch][10] is a tool for branching Fedora Linux packages for EPEL.

Given that CentOS Stream (and its downstreams, such as Red Hat Enterprise Linux, AlmaLinux and Rocky Linux) only carries the subset of Fedora Linux packages that Red Hat is committed to supporting, EPEL provides a way for the community to maintain additional packages built against RHEL (or CentOS Stream).

A major problem here is dealing with dependency hell: a missing package might have several missing dependencies, which in turn have more missing dependencies… Getting [retsnoop in EPEL 9][11] involves branching 189 packages in total!

ebranch utilizes rpmdistro-repoquery to compare what is available in Rawhide (rpmdistro-repoquery fedora rawhide) with what is available in CentOS Stream + EPEL (rpmdistro-repoquery centos-stream-legacy 8 and rpmdistro-repoquery centos-stream 9) to build up a transitive closure of missing dependencies and report on any dependency loops. ebranch also computes a chain build order for the missing dependencies, grouping packages that can be built in parallel.

#### Checking the impact of a soname bump

Fedora’s [updates policy for stable releases][12] and EPEL’s [incompatible upgrades policy][13] both discourage ABI-breaking updates, but sometimes they are necessary, as in the case of [libkdumpfile][14] in EPEL.

With rpmdistro-repoquery, finding the delta between any two distribution releases that it supports is trivial:

```

    $ comm <(rpmdistro-repoquery fedora rawhide \
      --provides libkdumpfile >/dev/null) \
      <(rpmdistro-repoquery centos-stream 9 \
      --provides libkdumpfile >/dev/null)
        libaddrxlat.so.2()(64bit)
        libaddrxlat.so.2(LIBADDRXLAT_0)(64bit)
    libaddrxlat.so.3
    libaddrxlat.so.3()(64bit)
    libaddrxlat.so.3(LIBADDRXLAT_0)
    libaddrxlat.so.3(LIBADDRXLAT_0)(64bit)
        libkdumpfile = 0.4.1-5.el9
    libkdumpfile = 0.5.0-3.fc38
    libkdumpfile(x86-32) = 0.5.0-3.fc38
        libkdumpfile(x86-64) = 0.4.1-5.el9
    libkdumpfile(x86-64) = 0.5.0-3.fc38
    libkdumpfile.so.10
    libkdumpfile.so.10()(64bit)
    libkdumpfile.so.10(LIBKDUMPFILE_0)
    libkdumpfile.so.10(LIBKDUMPFILE_0)(64bit)
        libkdumpfile.so.9()(64bit)
        libkdumpfile.so.9(LIBKDUMPFILE_0)(64bit)

```

And likewise, finding the blast radius of said update:

```

    $ rpmdistro-repoquery centos-stream 9 \
      --whatrequires "libaddrxlat.so.2()(64bit)"
    libkdumpfile-devel-0:0.4.1-5.el9.x86_64
    libkdumpfile-util-0:0.4.1-5.el9.x86_64
    python3-libkdumpfile-0:0.4.1-5.el9.x86_64

    $ rpmdistro-repoquery centos-stream 9 \
      --whatrequires "libkdumpfile.so.9()(64bit)"
    drgn-0:0.0.22-1.el9.x86_64
    libkdumpfile-devel-0:0.4.1-5.el9.x86_64
    libkdumpfile-util-0:0.4.1-5.el9.x86_64
    python3-libkdumpfile-0:0.4.1-5.el9.x86_64

    $ rpmdistro-repoquery centos-stream-legacy 8 \
      --whatrequires "libaddrxlat.so.2()(64bit)"
    libkdumpfile-devel-0:0.4.1-5.el8.x86_64
    libkdumpfile-util-0:0.4.1-5.el8.x86_64
    python3-libkdumpfile-0:0.4.1-5.el8.x86_64

    $ rpmdistro-repoquery centos-stream-legacy 8 \
      --whatrequires "libkdumpfile.so.9()(64bit)"
    drgn-0:0.0.22-1.el8.x86_64
    libkdumpfile-devel-0:0.4.1-5.el8.x86_64
    libkdumpfile-util-0:0.4.1-5.el8.x86_64
    python3-libkdumpfile-0:0.4.1-5.el8.x86_64

```

#### Building OS images

[mkosi][15] is a tool for generating OS images; currently it contains the logic for different distributions (e.g. [Fedora][16], [CentOS][17]), but this makes it hard to, for example, build an image for CentOS SIGs such as [Hyperscale][18].

With [Daan De Meyer’s refactor][19] rpmdistro-repoquery’s repo files can now be reused by mkosi so in the future, tailoring what repositories are used to build an OS image should be much easier.

### Conclusion

The contributors for this tool have found it very useful in our Linux distribution work, and we hope this article can help introduce it to others who likewise find it useful.

Please try it yourself — on Fedora Linux, and on any CentOS Stream or derivatives with [EPEL][20] enabled, simply do:

```

    $ sudo dnf install rpmdistro-repoquery

```

If the distro you want to work with is not supported, [pull][21] [requests][21] are welcome! Likewise with [suggestions][22] [or][22] [requests][22]. If you want to package rpmdistro-repoquery in a different distribution, feel free to use [the Fedora packaging][23] as reference.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/rpmdistro-repoquery-a-cross-distribution-repoquery-tool/

作者：[Michel Alexandre Salim][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/salimma/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/02/rpmdistro-repoquery-816x345.jpg
[2]: https://unsplash.com/@pgreen1983?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/mln2ExJIkfc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://pagure.io/rpmdistro-repoquery
[5]: https://fedoraproject.org/wiki/User:Ngompa
[6]: https://bodhi.fedoraproject.org
[7]: https://gitlab.com/redhat/centos-stream/rpms/clang/-/commit/9bfb2774ee5b40164ef1f148e0b88385931f2a93
[8]: https://kojihub.stream.centos.org/koji/buildinfo?buildID=29815
[9]: https://src.fedoraproject.org/rpms/myrepos
[10]: https://pagure.io/epel/ebranch
[11]: https://bodhi.fedoraproject.org/updates/FEDORA-EPEL-2022-103282f5c3
[12]: https://docs.fedoraproject.org/en-US/fesco/Updates_Policy/#stable-releases
[13]: https://docs.fedoraproject.org/en-US/epel/epel-policy-incompatible-upgrades/
[14]: https://lists.fedoraproject.org/archives/list/epel-devel@lists.fedoraproject.org/thread/5DCGRHG5COBSCZXMECIFWEBDYAEMMRNZ/
[15]: https://github.com/systemd/mkosi
[16]: https://github.com/systemd/mkosi/blob/main/mkosi/distributions/fedora.py
[17]: https://github.com/systemd/mkosi/blob/main/mkosi/distributions/centos.py
[18]: https://sigs.centos.org/hyperscale/
[19]: https://pagure.io/rpmdistro-repoquery/pull-request/9
[20]: https://docs.fedoraproject.org/en-US/epel/#_quickstart
[21]: https://pagure.io/rpmdistro-repoquery/pull-requests
[22]: https://pagure.io/rpmdistro-repoquery/issues
[23]: https://src.fedoraproject.org/rpms/rpmdistro-repoquery
