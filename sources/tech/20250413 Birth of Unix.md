[#]: subject: "Birth of Unix"
[#]: via: "https://itsfoss.com/birth-of-unix/"
[#]: author: "John Paul Wohlscheid https://itsfoss.com/author/john/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Birth of Unix
======

[![Warp Terminal][1]][2]

Sometimes it feels like Unix has been around forever, at least to users who have used Linux, or BSD in any form for a decade or more now.

Its ideals laid the groundwork for Linux, and it underpins macOS. A modern version (FreeBSD) is used on thousands of servers while Linux rules the server space along with the super computer industry.

Even though the original form of it is a history, it remains a significant development to help start Linux and more.

But initially, it had a rocky start and had to be developed in secret.

### Punch Cards and Multics

![][3]

Back in the days when computers took up whole rooms, the main method of using computers was the punch card interface. Computers didn't come with an operating system, they had a programming language built into them. If you wanted to run a program, you had to use a device to enter your program and the data on a series of punch cards.

According to an [interview][4] with [Brian Kernighan][5], one of the Unix creators, "So if you had a 1,000-line program, you would have 1,000 cards. There were no screens, no interactive output. You gave your cards to the computer operator and waited for your printout that was the result of your program."

![][6]

At the time, all text output from these computers was capitalized. Kernighan wrote an application to handle the formatting of his thesis. "And so thesis was basically three boxes of cards, 6,000 cards in each box, probably weighed 10, 12 pounds, five kilograms. And so you’d take these three boxes, 1,000 cards of which the first half of the first box was the program and then the remaining 5,000 cards was the thesis. And you would take those three boxes and you’d hand them to the operator. And an hour or two or three later back would come a printed version of thesis again."

Needless to say, this makes modern thesis writing seem effortless, right?

In the late 1950s, AT&T, Massachusetts Institute of Technology, and General Electric created a project to revolutionize computing and push it beyond the punch card.

The project was named [Multics][7] or “Multiplexed Information and Computing Service”. According to the [paper][8] that laid out the plans for the project, there were nine major goals:

  * Convenient remote terminal use.
  * Continuous operation analogous to power & telephone services.
  * A wide range of system configurations, changeable without system or user program reorganization.
  * A high reliability internal file system.
  * Support for selective information sharing.
  * Hierarchical structures of information for system administration and decentralization of user activities.
  * Support for a wide range of applications.
  * Support for multiple programming environments & human interfaces.
  * The ability to evolve the system with changes in technology and in user aspirations.



![][9]

Multics would be a time-sharing computer, instead of relying on punch cards. This means that users could log into the system via a terminal and use it for an allotted period of time. This would turn the computer from a system administered by a high priest class (Steven Levy mentioned this concept in his book [_Hackers_][10].) to something that could be accessed by anyone with the necessary knowledge.

The project was very ambitious. Unfortunately, turning ideas into reality takes time. Bell Labs withdrew from the project in 1969. They had joined the project to get a time-sharing operating system for their employees, but there had been little progress.

The lessons learned from Multics eventually helped in the creation of Unix, more on that below.

### To Space Beyond

![Image Credits: Multicians / A team installing GE 645 mainframe in Paris][11]

The Bell engineers who had worked on Multics (including Ken Thompson and Dennis Ritchie) were left without an operating system, but tons of ideas. In the last days of their involvement in the Multics, they had started writing an operating system on a [GE-645 mainframe][12]. But then the project ended, and they no longer needed the mainframe.

They lobbied their bosses to buy a mini-computer to start their own operating system project but were denied. They continued to work on the project in secret. Often they would get together and discuss what they would want in an operating system and sketch out ideas for the architecture.

During this time, Thompson started working on a little side project. He wrote a game for the GE-645 named Space Travel. The [game][13] "simulated all the major bodies in the solar system along with a spaceship that could fly around them".

Unfortunately, it was expensive to run on the mainframe. Each game cost $75 to play. So, Thompson went looking for a different, cheaper computer to use. He discovered a [PDP-7 mini-computer][14] left over from a previous project. He rewrote the game to run on the PDP-7.

![PDP-7, Image Credits: Wikipedia][15]

In the summer of 1969, Thompson's wife took their newborn son to visit her parents. Thompson took advantage of this time and newly learned programming skills to start writing an operating system for the PDP-7. Since he saw this new project as a cut-down version of Multics, he named it “Un-multiplexed Information and Computing Service," or Unics. It was eventually changed to Unix.

Other Bell Labs employees joined the project. The team quickly ran into limitations with the hardware itself. The PDP-7 was in its early stages, so they had to figure out how to get their hands on a newer computer. They knew that their bosses would never buy a new system [because][13] "lab's management wasn't about to allow any more research on operating systems."

At the time, Bell Labs produced lots of patents. According to Kernighan, "typically one or two a day at that point." It was time-consuming to create applications for those patents because the formatting required by the government was very specific.

At the time, there were no commercial word processing programs capable of handling the formatting. The Unix group offered to write a program for the patent department that would run on a shiny new [PDP-11][16]. They also promised to have it done before any commercial software would be available to do the same. Of course, they failed to mention that they would need to write an operating system for the software to run on.

Their bosses agreed to the proposal and placed an order for a PDP-11 in May 1970. The computer arrived quickly, but it took six months for the drives to arrive.

![PD-11/70, Image Credits: Wikipedia][17]

In the meantime, the team continued to write Unix on the PDP-7, making it the first platform where the first version of Unix developed. Once the PDP-11 was up and running, the team ported what they had to the new system. In short order, the new patent application software was unveiled to the patent department. It was a hit. The management was so pleased with the results, they bought the Unix team their own PDP-11.

### Growing and Legal Problems

![Image Credits: Amazon][18]

With a more powerful computer at their command, work on Unix continued. In 1971, the team released its first official manual: [The UNIX Programmer's Manual][19]. The operating system was officially debuted to the world via a paper presented at the 1973 symposium of the Association for Computing Machinery. This was followed by a flood of requests for copies.

This brought up new issues. AT&T, the company that financed Bell Labs, couldn't sell an operating system. In 1956, AT&T was forced by the US government to agree to a consent decree.

This consent decree prohibited AT&T [from][13] "selling products not directly related to telephones and telecommunications, in return for its legal monopoly status in running the country's long-distance phone service." The solution was to release "the Unix source code under license to anyone who asked, charging only a nominal fee".

The consent decree also prohibited AT&T from providing tech support. So, the code was essentially available as-is. This led to the creation of the first user groups as Unix adopters banded together to provide mutual assistance.

### C Programming, The Necessary Catalyst

The creation of the C programming language by Dennis Ritchie at Bell Labs helped Unix make progress with its future versions, and indirectly influenced the ability to create BSD and Linux.

And, now, we have many programming languages, operating systems, including several variants of Linux, BSD, and Unix-like operating systems as well.

--------------------------------------------------------------------------------

via: https://itsfoss.com/birth-of-unix/

作者：[John Paul Wohlscheid][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/john/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/04/1024px-This_is_a_card_puncher-_an_integral_part_of_the_tabulation_system_used_by_the_United_States_Census_Bureau_to_compile..._-_NARA_-_513295.jpg
[4]: https://corecursive.com/brian-kernighan-unix-bell-labs1/
[5]: https://en.wikipedia.org/wiki/Brian_Kernighan
[6]: https://itsfoss.com/content/images/2025/04/1024px-Keypunch_operator_1950_census_IBM_016.jpg
[7]: https://en.wikipedia.org/wiki/Multics
[8]: https://www.multicians.org/history.html
[9]: https://itsfoss.com/content/images/2025/04/Multics-Login.png
[10]: https://www.amazon.in/Hackers-Steven-Levy/dp/1449388396
[11]: https://itsfoss.com/content/images/2025/04/ge645-paris.jpg
[12]: https://en.wikipedia.org/wiki/GE_645
[13]: https://spectrum.ieee.org/the-strange-birth-and-long-life-of-unix
[14]: https://en.wikipedia.org/wiki/PDP-7
[15]: https://itsfoss.com/content/images/2025/04/pd7.jpeg
[16]: https://en.wikipedia.org/wiki/PDP-11
[17]: https://itsfoss.com/content/images/2025/04/PDP-11-70.JPG
[18]: https://itsfoss.com/content/images/2025/04/unix-manual.jpg
[19]: https://man.cat-v.org/unix-1st/
