[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (VR hits a new milestone, Mozilla's growing open source voice library, change in Redis maintainers, and more open source news)
[#]: via: (https://opensource.com/article/20/7/news-july-7)
[#]: author: (Lauren Maffeo https://opensource.com/users/lmaffeo)

VR hits a new milestone, Mozilla's growing open source voice library, change in Redis maintainers, and more open source news
======
Catch up on the biggest open source headlines from the past two weeks.
![][1]

In this week’s edition of our open source news roundup, Mozilla updates its open source voice stack, a tool to tame VR cybersickness, and more open source news.

### A new open source toolkit to prevent VR cybersickness

Researchers at The University of Texas at San Antonio (UTSA) announced the release of [GingerVR][2] last month. A UTSA blog post announcing the news called GingerVR the first open-source Unity software toolkit using proven techniques to help virtual reality (VR) users fight cybersickness. 

John Quarles, an associate professor in UTSA's Department of Computer Science, [said in the blog post][3] that GingerVR can be applied to any Unity application, from personal games to enterprise tools. That's relevant given Unity's increased focus on B2B solutions, alongside its lead in AR/VR game development.

Quarles and Ph.D. student Samuel Ang named GingerVR after the plant commonly used to treat nausea, a key sign of cybersickness. Side effects ranging from headaches and nausea to confusion and sensory processing problems have plagued AR and VR tools [for decades][4]. 

GingerVR's release arrives three years after AR/VR leaders launched [OpenXR][5], a royalty-free platform offering open source access to AR/VR platforms and devices. Quarles says that OpenXR doesn't address cybersickness, which led him to co-create GingerVR. (Note that GingerVR is still [in the process of choosing an open source license][6] but intends to do so.)

### Mozilla updates its open source voice data library

Mozilla's [Common Voice project][7] released a large voice dataset last week. Common Voice is an open source collection of transcribed recordings and metadata for voice app and voice-enabled device designers to use. 

The Common Voice project boasts 5.5 million clips in 54 languages over 7,226 hours. Mozilla wants Common Voice users to integrate the data with its [DeepSpeech toolkit][8] of voice and text models.

Volunteers upload recorded clips of themselves speaking to the Common Voice project. Then, the transcribed sentences are collected in a voice database under the CC0 license. This allows developers to use the clips sans costs and copyright restrictions. 

Common Voice aims to fill gaps left by common voice tech apps, which are often critiqued for [not being trained][9] on diverse datasets representing a range of accents, inflections, and languages. Along with its recent update to Common Voice, Mozilla also improved DeepSpeech's speed of recognition recently. 

### Redis co-creator steps back as maintainer

11 years after co-founding [Redis][10], Salvatore Sanfilippo announced plans to step down as project maintainer of the NoSQL database. He also shared plans to stay with the project on the Redis Labs advisory board.

In a note [announcing his move][11], Sanfilippo shares that he never aspired to be a software maintainer. His colleagues, Yossi Gottlieb and Oran Agra, will maintain the Redis project moving forward.

Under their leadership, Redis will use a new governance model. Rather than the BDFL-style project of the past, they're proposing [a light governance model][12].

This will involve selecting a small group of longtime Redis developers to act as core contributors and uphold the project's Code of Conduct. That search is ongoing, with [Itamar Haber][13] announced as the first member.

### In other news

  * [Meet CutiePi: A 100% Open Source And Ultra-Portable Raspberry Pi Tablet][14]
  * [How DevOps teams can get more from open source tools][15]
  * [IBM Has Open Sourced Its Edge Device Platform and Wishes AWS and Microsoft Got On Board][16]
  * [How Facebook's open source factory gave rise to Presto][17]
  * [Making open source code more inclusive by eradicating ‘problematic language’][18]



Thanks, as always, to Opensource.com staff members and [Correspondents][19] for their help this week.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/news-july-7

作者：[Lauren Maffeo][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/lmaffeo
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/weekly_news_roundup_tv.png?itok=tibLvjBd
[2]: https://github.com/angsamuel/GingerVR
[3]: https://www.utsa.edu/today/2020/06/story/software-aims-reduce-cybersickness.html
[4]: https://www.insidescience.org/news/cybersickness-why-people-experience-motion-sickness-during-virtual-reality
[5]: https://www.khronos.org/openxr/
[6]: https://github.com/angsamuel/GingerVR/issues/1
[7]: https://labs.mozilla.org/projects/common-voice/
[8]: https://github.com/mozilla/DeepSpeech
[9]: https://www.theguardian.com/technology/2020/jan/11/why-do-we-gender-ai-voice-tech-firms-move-to-be-more-inclusive
[10]: https://redis.io/
[11]: http://antirez.com/news/133
[12]: https://redis.io/topics/governance
[13]: https://github.com/itamarhaber
[14]: https://fossbytes.com/cutiepi-a-100-open-source-and-ultra-portable-raspberry-pi-tablet/
[15]: https://enterprisersproject.com/article/2020/7/devops-open-source-tools
[16]: https://www.datacenterknowledge.com/open-source/ibm-has-open-sourced-its-edge-device-platform-and-wishes-aws-and-microsoft-got-board
[17]: https://www.techrepublic.com/article/how-facebooks-open-source-factory-gave-rise-to-presto/
[18]: https://www.wraltechwire.com/2020/06/30/red-hat-making-open-source-code-more-inclusive-by-eradicating-problematic-language/
[19]: https://opensource.com/correspondent-program
