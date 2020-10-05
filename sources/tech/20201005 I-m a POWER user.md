[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (I'm a POWER user)
[#]: via: (https://opensource.com/article/20/10/power-architecture)
[#]: author: (Peter Czanik https://opensource.com/users/czanik)

I'm a POWER user
======
Learn how the POWER architecture embraced open source.
![Person on top of a mountain, arm raise][1]

The [IBM POWER][2] processor architecture is now over 30 years old. Although it arrived in February 1990 with a closed source operating system and closed source applications on top, it gradually embraced open source. I became a POWER user soon after it launched and an open source user and contributor just two years later.

This article provides a subjective history of POWER and open source from the viewpoint of an open source developer, outlines a few trends and conclusions, and previews what the future will bring. It is based on [my talk][3] at the annual [OpenPOWER North America Summit][4], in which I aimed to show the importance of desktop/workstation-class hardware available to developers. In this article, I will cover a few additional topics, including cloud resources available to POWER developers, as well as a glimpse into the products and technologies under development.

### POWER's history

The following is a subjective history of POWER. While I try to stay objective, it is heavily based on how I have experienced POWER and open source over almost three decades.

#### The early years

My first encounter with POWER happened in 1992 at Dartmouth College. I had remote access to [RS/6000][5] systems, which I used to learn basic shell scripting and how to exit from the Vi text editor. These were the fastest machines I had access to—and also a bit mysterious for someone who had used only DOS and Mac OS previously. In the early nineties, I must admit, I was not yet aware if I was using closed or open source software.

I became aware of open source in 1994 when I started university back in Hungary. I first became a FreeBSD user and, within a few months, I was running the faculty's first Linux server and the university's first web server. In 1996, I became a SUSE Linux tester and contributor. Around this time, I helped one of my university friends boot Linux on the PowerPC (PPC) accelerator card in his Amiga. We cross-compiled the PPC kernel on my x86 Linux server.

#### Turn of the century

As the 2000s dawned, I became an intern at a major Hungarian systems integrator. Knowing of my Unix/open source background, they let me participate in RS/6000 installations. All of these systems ran AIX, a closed source Unix operating system, but clients who also used Linux/FreeBSD wanted their favorite applications to be able to run on top of AIX.

In those early years, open source applications were not available for AIX in a ready-to-use, packaged form. It was my task to compile open source applications from source and do the initial configuration. During my internship, I helped install the most powerful system in Hungary at that time: an RS/6000 system larger than a fridge with plenty of CPU power, RAM, and storage. It supported thousands of students and researchers at a university.

Near the end of my internship, I installed Linux on a spare POWER workstation. It worked, but compared to AIX, it was still very limited.

After my internship, I closely tracked POWER and Linux on POWER. Many open source developers were buying second-hand PowerMac and IBM POWER boxes as developer workstations. Most of them were just curious, using the computers more for hobbies than anything commercially viable. But some people were already running open source database servers on Linux on POWER in production in the early 2000s.

#### The Genesi years

In 2004, during my last year at the university, I was looking for a new desktop. As I had a degree in environmental engineering, I wanted this machine to be energy-efficient, not just fast. For a student, a new PowerMac was too expensive. This was when I learned about [Pegasos][6], the PowerPC workstation from Genesi. The company had a developer program that gave Pegasos machines for free to qualified open source developers, so I applied for one to continue SUSE testing on POWER (instead of x86).

A few weeks later, I was running openSUSE on Pegasos. And a few months later, when my PhD program abruptly ended, I started to work for Genesi on Linux support. While I tested everything related to Linux, my focus was openSUSE. You can still find [traces of my work][7] on openSUSE's wiki.

This is where I started my open source community career by participating in and moderating PowerDeveloper.org, a forum for open source users and developers on POWER. While this site mainly focused on the desktop side, a few years later, I ended up doing the same work on Power.org, focusing more on the high-end server side.

Of course, people were not buying Genesi workstations just to develop for POWER. Developers started buying the latest PowerMacs for Linux development. And more and more IBM POWER servers were running Linux right from the beginning using a fully open source stack. Altivec optimizations developed for Linux at Genesi didn't only help the desktop world but also servers and high-performance computing.

#### A disturbance in the force

In 2005, Apple decided to switch from POWER to Intel CPUs. Soon after, Freescale (the developer of G4 POWER CPUs used in Apple machines) stopped developing generic POWER CPUs and started focusing on networking-related products. There was hope in the form of PA Semi, which was working on a very promising new POWER CPU. Unfortunately, Apple bought the company and redirected the engineers to work on A-series ARM-based chips, which powered the iPhone and iPad and would soon power the Macintosh product line. Soon, Genesi also gave up on POWER.

Many developers kept using POWER on the desktop. But when even the latest PowerMac machines became old and were left behind by x86, most developers left the platform. Although the platform lost most of its open source developers, open source software gained even more users on the POWER server side. Instead of AIX, most of the POWER servers were sold with Linux. Even commercial applications, like SAP Hana, started to appear on Linux on POWER.

#### A new hope

When Raptor Computing Systems announced its plan to work on a POWER8 workstation, everyone in the POWER world became excited. For almost a decade, POWER was available only on high-end servers but not workstations. Finally, in 2017, Raptor announced its first product, the dual-socket Talos II board, based on POWER9. It was followed by the smaller, more affordable single-socket Blackbird board.

The Raptor workstations are not cheap but still a lot more affordable than IBM POWER-based servers. And they are completely open—not just the operating system and software running on top, but also the firmware and the instruction set. Ever since these workstations became available, many POWER developers have been returning to the platform.

#### Some other facts

Here are a few interesting facts that are not strictly related to open source:

  * POWER is the #1 CPU used in [Mars exploration][8].
  * POWER was #1 and #2 on the supercomputer [Top500][9] list until recently and still holds a number of prominent places. At least as important to me, these systems also take top places on the [Green500][10] list, based on energy efficiency.
  * Soon after POWER 9 appeared in 2017, I tested [syslog-ng][11] (the software I work with) on a number of different systems and platforms. At that time, syslog-ng ran 1.5x faster on a POWER 9 workstation than on any ARM and Intel servers I had access to.



### What this means

Looking back at this history, I see two major trends and conclusions.

#### POWER embraced open source

Originally, POWER launched with a closed source operating system with closed source applications on top. Later, open source applications appeared on top of AIX. Eventually, Linux and other open source operating systems were ported to POWER, providing a fully open source stack. Over time, Linux matured and replaced AIX on most POWER servers. Recently, the ability to run in little-[endian][12] mode (instead of big-endian) made it easier to port software to the platform. Commercial applications requiring high memory bandwidth and CPU performance, like SAP Hana, were ported soon after.

#### Developers need affordable workstations

In the beginning, developers used second-hand IBM POWER workstations and PowerMac machines. Later, they used Genesi workstations and PowerMac. When only high-end servers were available, many developers left POWER. With the Raptor POWER workstations, many developers returned to the platform. With even more affordable systems, the number of active users and developers could grow significantly.

### POWER cloud resources

While buying a Raptor POWER workstation is not an option for everybody (including me, due to Hungary's financial situation), there are other options for open source developers to work on POWER. This topic is worth a longer discussion, but here are a few highlights:

  * Both openSUSE's [Open Build Service][13] and Fedora's [Copr][14] build system can build software for POWER.
  * [Travis CI][15] can build and test software on POWER.
  * [MiniCloud][16] provides SSH access to POWER virtual machines for qualified open source developers.



### The future of POWER

IBM open sourced two POWER CPU cores, the A2I and the A2O. The LibreSoc project is working on an open CPU based on POWER. All of these belong to the embedded, edge, or desktop category. After my OpenPOWER North America talk, many people asked about Raspberry Pi-sized POWER devices, so I really hope someone creates an actual device from these designs.

POWER 10 was announced recently, but it won't become generally available for almost a year. Raptor Computing [announced][17] on Twitter that it will not have any new designs built around POWER 10 in 2021. Hopefully, this means early 2022.

A PowerPC laptop has been a long time in the making; this would be a huge step forward. However, it is designed around a big-endian CPU from NXP, and most Linux distributions have removed support for it.

So, for the foreseeable future, if you want POWER, you can source high-end servers from IBM or workstations from Raptor Computing.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/power-architecture

作者：[Peter Czanik][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/czanik
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/developer_mountain_cloud_top_strong_win.jpg?itok=axK3EX-q (Person on top of a mountain, arm raise)
[2]: https://en.wikipedia.org/wiki/IBM_POWER_microprocessors
[3]: https://www.youtube.com/watch?v=TtxZf2gp0l4
[4]: https://events.linuxfoundation.org/openpower-summit-north-america/
[5]: https://en.wikipedia.org/wiki/IBM_RISC_System/6000
[6]: https://en.wikipedia.org/wiki/Pegasos
[7]: https://en.opensuse.org/openSUSE:Genesi
[8]: https://en.wikipedia.org/wiki/Comparison_of_embedded_computer_systems_on_board_the_Mars_rovers
[9]: https://www.top500.org/
[10]: http://www.green500.org/
[11]: https://www.syslog-ng.com/
[12]: https://en.wikipedia.org/wiki/Endianness
[13]: https://openbuildservice.org/
[14]: https://copr.fedorainfracloud.org/
[15]: https://travis-ci.org/
[16]: https://openpower.ic.unicamp.br/minicloud/
[17]: https://twitter.com/RaptorCompSys/status/1295364416469377026
