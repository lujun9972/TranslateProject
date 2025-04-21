[#]: subject: "The Fedora Project history and family tree"
[#]: via: "https://fedoramagazine.org/the-fedora-project/"
[#]: author: "Abdel El Aoami https://fedoramagazine.org/author/tophat/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The Fedora Project history and family tree
======

![][1]

NASA / WMAP Science Team <https://map.gsfc.nasa.gov/media/060915/index.html>

This article provides a short overview and history of [the Fedora Project][2].

### Introduction

The Fedora Project has become known for Linux innovation. Since its inception in 2003, Fedora has been a proving ground where new ideas in Linux are tested and refined by a global community of contributors. Its creation sprang from Red Hat Linux’s transformation into Red Hat Enterprise Linux. This move required a separate open-source distribution to remain on the leading edge. Over the years, this approach has nurtured developments like Wayland, rpm-ostree, and many more spin-off editions, each having its own use case. As a result, Fedora has become a cornerstone for the broader open-source world, inspiring many other models.

### Prior to Fedora Linux

The beginning of Fedora starts the same as many other systems, with the development of Unix and the GNU/Linux. Unix was conceived in the late 1960s at Bell Labs. The technicalities it offered, like emphasizing modularity and portability, proved influential to future systems. The GNU Project, which contributed a key ideological foundation, urged programs to be published under the GNU General Public License. This license gave end users the freedom to modify and redistribute given software, as long as they extended the same rights downstream. In the early 1990s, Linus Torvalds released the Linux kernel. The GNU Project’s userland software and Torvalds’s kernel gave birth to “GNU/Linux” (usually abbreviated simply to Linux). Gradually distributions such as Debian, Slackware, and Red Hat Linux emerged to package these elements conveniently.

### Red Hat and the transition

Red Hat Linux rose to prominence in the mid-1990s by combining RPM (Red Hat Package Manager) with a systematic method for creating, distributing, and updating packages. Its user and corporate friendliness made it stand out among other distributions. Yet as the 2000s approached, Red Hat faced opportunities with bigger commercial and governmental institutions. These organizations were attracted by Linux’s stability and cost-effectiveness, and sought multi-year support guarantees and formalized maintenance models. Red Hat began to pivot to a subscription-based enterprise solution known, thereafter, as Red Hat Enterprise Linux (RHEL). This business strategy aligned with demands for predictable release cadences and dedicated security patches. However, it also introduced a new question: what would happen to the fast-paced development tradition that had existed under Red Hat Linux?

To answer this, Red Hat attempted to continue open development under the banner of the “Red Hat Linux Project”. But that model created a lot of confusion for customers. The result was a decisive move, in 2003, to discontinue the classic Red Hat Linux brand and unveil two new branches. These were RHEL and an openly developed community distribution. The community-based operating system took the name Fedora. This was in collaboration with Warren Togami’s Fedora Project, an external repository of add-on software for Red Hat Linux. Fedora quickly coalesced as the new “upstream” community layer. Now emerging technologies could be introduced, refined, and tested by a global volunteer network before eventually being integrated into Red Hat’s enterprise offerings.

### Naming the Project

In its initial phase, Fedora was referred to as “Fedora Core” with “Core” denoting the central packages curated by Red Hat employees. A separate repository, known as Fedora Extras, captured community-maintained software. Over time however, the artificial boundary between Red Hat–maintained packages and community-contributed packages became increasingly frustrating to everyone working on the project. Red Hat engineers and volunteers alike recognized that the distribution would benefit from a single, unified development process. By the mid-2000s, community leaders pressed for the elimination of Fedora Core and Fedora Extras as separate entities. This became reality with the release of Fedora 7. In this release “Core” and “Extras” became unified ensuring that all packages would be maintained under shared infrastructure and open governance. This shift definitively set Fedora on a path toward greater inclusivity, allowing volunteers and Red Hat employees to collaborate as equals.

### The Fedora Project Editions, Spins, Labs, CentOS, ….

Since [Fedora Linux 21][3], the distribution has maintained a set of “editions”, each targeting a particular environment.

  * Fedora Workstation is designed for desktops and laptops, shipping with GNOME as the default interface. With Fedora Linux 42, KDE was added as another desktop and laptop option.


  * Fedora Server focuses on server environments, offering packaging for critical server applications.


  * Fedora Cloud is Fedora Server optimized to run on cloud platforms like AWS, Azure, etc.
  * Fedora CoreOS is “atomic” and uses rpm-ostree to provide an atomic means of upgrading the operating system.
  * Fedora IoT addresses Internet of Things deployments. It ensures that Fedora’s security and update mechanisms can be extended to small-scale or embedded hardware.



Over time, the distributions have been joined by specialized “Labs”. These are curated sets of packages aimed at gaming, design, robotics, and scientific computing.

Concurrent with these developments, Red Hat began rethinking the role of CentOS. This distribution had historically been a rebuild of RHEL’s source packages. Instead of simply mirroring RHEL, Red Hat inaugurated “CentOS Stream” as a midpoint between Fedora and RHEL. Under this arrangement, Fedora remains the upstream integration point, incorporating the newest features, libraries, and subsystems, under a community governance model. In CentOS Stream, Red Hat engineers refine the result into a near-final pipeline for the next RHEL release. Thus, in effect, Fedora not only drives RHEL but also aids in CentOS Stream’s progression. This intricate relationship shows Fedora’s status as a proving ground of enterprise-ready Linux technology, albeit governed by a global collective of paid and volunteer contributors.

### Future goals of the Fedora Project

The Fedora Project sees continued expansion in contributor counts and new technical vistas. The project aims to remain at the forefront of container orchestration, edge computing, Internet of Things deployments, and imaginative spins such as Sway Atomic or Budgie Atomic, which repackage the immutable model for other user interfaces.

One can regard Fedora’s twenty-year saga as a success in technological progress and community organization. Tracing its lineage through Unix, GNU, Linux, Red Hat Linux, and into RHEL, Fedora endures its legacy of shared knowledge. By preserving its guiding principles of transparency, inclusive governance, and rapid iteration, with its dedication to open source, Fedora remains poised to continue as a locus of innovation, shaping the paths of CentOS Stream, Red Hat Enterprise Linux, and many other distributions. In so doing, it carries forward the spirit of Unix and GNU, that advanced operating systems share their combined efforts, all striving toward accessible and empowering computing for everyone.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/the-fedora-project/

作者：[Abdel El Aoami][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/tophat/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/01/history_n_familiy_tree-816x345.jpg
[2]: https://fedoraproject.org/
[3]: https://fedoramagazine.org/announcing-fedora-21/
