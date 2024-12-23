[#]: subject: "Going Retro With AGC: Smart Computer That Powered Apollo Missions in the 60s"
[#]: via: "https://itsfoss.com/apollo-guidance-computer/"
[#]: author: "Bill Dyer https://itsfoss.com/author/bill/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Going Retro With AGC: Smart Computer That Powered Apollo Missions in the 60s
======

[![Warp Terminal][1]][2]

When we look at things retro, the [Apollo Guidance Computer][3] is about as retro as it gets!

This computer was cutting-edge in the 1960s, but what made the AGC so special? How did it manage to send astronauts to the moon and back with computing power less than today’s pocket calculators? It turns out that this gem of retro-computing was one of many firsts - and still influences computing today.

![][4]

The AGC laid the groundwork for concepts that still ring true today: [modular coding][5], [code reusability][6], and [optimization][7] for resource-constrained systems. The AGC was definite proof that a lean, well-designed system could handle major challenges, providing the way for both space exploration and other future technological achievements.

In a way, it’s like the ultimate minimal system - way ahead of its time in terms of principles that influenced later computing.

### What made the Apollo Spacecraft computer revolutionary?

The AGC was the principal onboard computer for NASA's Apollo missions, including all of the lunar landings. Both the [Command Module][8] (CM) and the [Lunar Module][9] (LM) had AGCs, so two AGCs were used on most of the Apollo missions, but with differing software, depending on the purpose of the AGC.

Developed by the MIT Instrumentation Laboratory (known as [Draper Labs][10] today), the AGC was one of the first to use integrated circuits, making it one of the most successful examples of miniaturization. It took up just about 1 cubic foot of space. It was also lightweight, weighing around 70 pounds (31.75 kilogram). This made the AGC was portable enough to fit aboard a small spacecraft.

This innovation wasn’t just about size. The AGC’s software, written in [assembler language][11], known as AGC4, allowed complex operations to be carried out within abnormally strict constraints of limited memory and processing power. The AGC had only 2K of [RAM][12] and 36K of [ROM][13]. That’s a fraction of what even the simplest of today's gadgets use, yet it was enough to guide humans to the moon. It is an excellent example of 'lean' programming - doing a lot with little - but the principles of modularity and code reuse, that we use today, come from the AGC.

The AGC also came equipped with a user interface - the [Display and Keyboard][14] (DSKY) interface. The term, “user-friendly” may not come to mind when you see one, but the DSKY did allow astronauts to effectively enter commands in real-time. In an era before touchscreens or even computer mice, the DSKY was certainly cutting-edge. In fact, it can even be considered one of the earliest forms of the [Command Line Interface][15] (CLI).

![][16]

### A smart computer

The AGC was also a smart computer, earning the nickname, "[the fourth astronaut][17]," from the vital role it played in the Apollo missions. The AGC performed calculations and managed tasks in real-time that were impossible for human astronauts to handle manually, especially under the constraints of time and stress.

The AGC calculated precise maneuvers, such as course corrections and lunar landings, where even slight errors could have been catastrophic. It also prioritized tasks autonomously. During the famous "[1202 program alarm][18]" incident, when the computer was overloaded, it managed to ignore non-essential tasks and continue critical operations, ensuring the mission's success.

The AGC was trusted as much as the astronauts themselves, forming a partnership where the machine’s reliability supported human judgment. The AGC, then, didn’t just assist - it actively contributed to the mission’s success. I think that the nickname is a poetic and fitting tribute to the machine’s significance.

### Lessons from the AGC for modern computing

#### Efficiency is key

The AGC’s developers didn’t have the luxury of abundant resources. They had to write hyper-efficient, reusable code and design hardware that maximized performance with little power. This mindset of doing more with less is still relevant today, especially in areas like [IoT][19] and [embedded systems][20].

The AGC's software was developed by a team at MIT, led by [Margaret Hamilton][21], and is a true master-class in software development. They implemented rigorous testing protocols and pioneered the concept of "software engineering."

#### Sophisticated real-time capabilities

The AGC was designed for [real-time processing][22], essential for navigation and control tasks in space. This was a significant achievement at a time when most computers were used for batch processing.

#### Collaboration pushes innovation

The AGC wasn’t the magic of a lone genius. It was the result of collaboration between NASA, MIT, and contractors. The best ideas often come from collective effort.

### Interested in more?

Recently, there has been a surge of interest in the AGC. Enthusiasts [restore vintage machines][23], program replicas, and even build [AGC emulators][24]. But why? For many, it’s a way to appreciate the ingenuity of early engineers and reconnect with the roots of modern tech.

![][25]

For instance, open-source projects like [VirtualAGC][26] allow anyone to explore the original Apollo software. Meanwhile, museums and exhibitions display AGC hardware, inspiring a new generation of engineers.

#### Can I build an AGC replica?

Yes! Projects like VirtualAGC provide [schematics][27] and code for building your own functional replica - a fantastic way to dive into retro-computing.

![][28]

#### Where can I see an original AGC?

Several museums, including the [Smithsonian’s National Air and Space Museum][29], display original AGC units. These exhibits often include interactive demos.

### Conclusion: a timeless tribute

The Apollo Spacecraft Computer isn’t just a relic of the past; it’s evidence to what human ingenuity and perseverance can accomplish. Constraints can propel creativity, and small, incremental innovations can bring about huge achievements. A look at tech history reminds us of how far we’ve come and how much we owe to the pioneers who got us here. The AGC is a perfect example of that.

--------------------------------------------------------------------------------

via: https://itsfoss.com/apollo-guidance-computer/

作者：[Bill Dyer][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/bill/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://en.wikipedia.org/wiki/Apollo_Guidance_Computer
[4]: https://upload.wikimedia.org/wikipedia/commons/7/79/Agc_view.jpg
[5]: https://en.wikipedia.org/wiki/Modular_programming
[6]: https://en.wikipedia.org/wiki/Code_reuse
[7]: https://en.wikipedia.org/wiki/Program_optimization
[8]: https://airandspace.si.edu/explore/stories/apollo-11-launch-vehicle-and-spacecraft#columbia
[9]: https://airandspace.si.edu/explore/stories/apollo-11-launch-vehicle-and-spacecraft#eagle
[10]: https://www.draper.com/
[11]: https://en.wikipedia.org/wiki/Assembly_language
[12]: https://en.wikipedia.org/wiki/Random-access_memory
[13]: https://en.wikipedia.org/wiki/Read-only_memory
[14]: https://airandspace.si.edu/collection-objects/keyboard-display-dsky-apollo-guidance-computer/nasm_A19760744000
[15]: https://en.wikipedia.org/wiki/Command-line_interface
[16]: https://appel.nasa.gov/wp-content/uploads/2009/09/dsky_lm.jpg
[17]: https://apollo11space.com/apollo-guidance-computer-and-its-significance-during-the-apollo-11-mission/
[18]: https://www.youtube.com/watch?v=z4cn93H6sM0
[19]: https://en.wikipedia.org/wiki/Internet_of_things
[20]: https://en.wikipedia.org/wiki/Embedded_system
[21]: https://apollo11space.com/5-women-who-contributed-to-the-moon-landing-mission/#mh
[22]: https://www.geeksforgeeks.org/difference-between-batch-processing-and-real-time-processing-system/
[23]: https://www.youtube.com/watch?v=2KSahAoOLdU&list=PL-_93BVApb59FWrLZfdlisi_x7-Ut_-w7
[24]: https://svtsim.com/moonjs/agc.html
[25]: https://itsfoss.com/content/images/icon/favicon-8.ico
[26]: https://www.ibiblio.org/apollo/download.html#Downloading_and_Building_Virtual_AGC&gsc.tab=0
[27]: https://github.com/virtualagc/agc_hardware
[28]: https://itsfoss.com/content/images/icon/pinned-octocat-093da3e6fa40-5.svg
[29]: https://airandspace.si.edu/
