[#]: subject: "Changes to the ELN kernel RPM NVR"
[#]: via: "https://fedoramagazine.org/changes-eln-kernel-rpm-nvr/"
[#]: author: "prarit https://fedoramagazine.org/author/prarit/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Changes to the ELN kernel RPM NVR
======

![][1]

Photo by [Łukasz Rawa][2] on [Unsplash][3]

Red Hat is excited to announce significant changes to ELN kernel RPM NVR in the kernel-ark project. This change will be to limited to the kernel-ark ELN RPMs and **does not impact Fedora**. If you don’t use Fedora ELN builds you can likely stop reading as this change won’t affect you.

### What is the kernel-ark project?

The [kernel-ark project][4] is an upstream kernel-based repository from which the Fedora kernel RPMs are built ([contributions welcomed!][5]). This project is also used by the Centos Stream and Red Hat Enterprise Linux (RHEL) maintainers to implement, test, and verify code that is destined to be used in Centos Stream and RHEL. In other words, the kernel-ark repository contains code that is enabled to build several different kernels which may contain unique code for different use cases. The kernel RPMs used for CentOS Stream and RHEL are commonly referred to as the ‘ELN’ (Enterprise Linux Next) RPMs.

### Why are there ELN RPMs? Why can’t Centos Stream and Red Hat use Fedora RPMs?

While Fedora Linux is the source of a lot of code that lands in CentOS Stream and later RHEL, the kernel configuration used in each operating system is unique. Fedora Linux is configured to achieve its specific goals and targets. CentOS Stream and RHEL do the same but for a slightly different set of goals and targets.

The differences are significant enough that the Fedora Linux, Centos Stream, and RHEL kernel maintainers recognized the need for separate RPMs targeted for Fedora and those targeted for Centos Stream and RHEL. Examples of these differences are [BTRFS is enabled in Fedora Linux but not in ELN][6] and there are some [specific devices][7] that are disabled in ELN but are enabled in Fedora Linux.

Red Hat uses kernel-ark’s ELN RPMs to continuously test upstream changes with a Red Hat specific configuration. This enables Red Hat to monitor performance and resolve issues before they make it into a Red Hat Enterprise Linux (RHEL) release. In accordance with Red Hat’s long established ‘upstream first’ policy, all fixes and suggestions for improvements are sent back to the upstream kernel community. This benefits the entire Linux community with improvements due to issues resolved in ELN.

This structure also allows Red Hat to test and make changes without affecting the Fedora Linux kernel except in a positive or desired way, such as through bug fixes. Fedora Linux, CentOS Stream, and RHEL have the opportunity to accept or reject changes easily.

### What ELN NVR changes are being made?

Before explaining the changes to the ELN kernel rpm NVR, it is important to understand what an NVR is. All RPMs have [**N** ame, **V** ersion, and **R** elease (NVR) directives][8] that describe the RPM package. In the case of the Fedora Linux kernel RPMs the Name is ‘kernel’ and the Version is the kernel’s uname (aka UTSNAME or the kernel version). The last field, the Release, contains additional upstream tagging information (release candidate tags), a monotonically increasing build number, and a distribution tag. The NVR is separate from the kernel’s uname and the uname is not generated from it. Instead, we have traditionally generated the NVR from the uname.

For example, for a recent Fedora Linux kernel build,

```

    $ rpm -qi kernel-6.3.0-0.rc5.42.fc39.src.rpm

```

Name: kernel
Version: 6.3.0
Release: 0.rc5.42.fc39

In the next few weeks, the Centos Stream and RHEL maintainers will introduce **ELN RPMs that have new kernel Name, Version, and Release (NVR) directives that are unique to the ELN builds.** **This change has no impact on the kernel uname.** The net result of the change is that the version number will have more meaning to CentOS Stream and RHEL builds, instead of being solely based on the kernel uname. For example, an ELN kernel may have NVR kernel-redhat-1.0.39.eln which packages a kernel with a kernel uname of 6.3.0-39.eln.

**We have already decided that the new ‘Name’ directive for the ELN kernel NVR will be changed from ‘kernel’ to ‘kernel-redhat’**. More information on the Version and Release directive changes will be released in the following months as they are finalized by the Centos Stream and RHEL kernel maintainers. You can follow these discussions on the [Fedora Kernel Mailing List][9].

### Why is the ELN NVR being changed?

The new ELN NVR will allow for better coordination of feature introduction, bug fixes, and CVE resolutions in future versions of Centos Stream and RHEL. More information on these improvements to the Centos Stream and RHEL ecosystems will be released in the upcoming months.

### How is Fedora Linux impacted?

**Fedora Linux is not impacted by these changes.**

Since the inception of the kernel-ark project, the Fedora Linux, Centos Stream, and RHEL maintainers have been extraordinarily careful to ensure that Fedora Linux kernel builds are not impacted by ELN kernel builds (and vice-versa) in the kernel-ark project. The commitment to prevent cross-OS issues is strictly enforced by the maintainers. Due to the maintainers continued diligence, there is no impact to Fedora Linux.

### How can I obtain Fedora Linux or ELN kernels?

Fedora Linux and ELN kernels can be downloaded from [Fedora Project’s koji instance][10].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/changes-eln-kernel-rpm-nvr/

作者：[prarit][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/prarit/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/04/ELN-Kernel-RPM-NVR-816x345.jpg
[2]: https://unsplash.com/ja/@lukasz_rawa?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/popcorn-kernels?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://gitlab.com/cki-project/kernel-ark
[5]: https://cki-project.gitlab.io/kernel-ark/
[6]: https://cki-project.gitlab.io/kernel-ark/faq.html#i-am-booting-an-eln-rhel-kernel-on-fedora-or-vice-versa-and-the-kernel-won-t-boot-what-do-i-do-now
[7]: https://gitlab.com/cki-project/kernel-ark/-/blob/os-build/drivers/message/fusion/mptsas.c#L5391
[8]: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/packaging_and_distributing_software/packaging-software_packaging-and-distributing-software#ref_spec-file-preamble-items_assembly_what-a-spec-file-is
[9]: https://lists.fedoraproject.org/archives/list/kernel@lists.fedoraproject.org/
[10]: https://koji.fedoraproject.org/koji/packageinfo?packageID=8
