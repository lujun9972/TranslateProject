[#]: subject: "Anaconda Installer Partitioning and Storage Survey Results"
[#]: via: "https://fedoramagazine.org/anaconda-installer-partitioning-and-storage-survey-results/"
[#]: author: "Flo Forno https://fedoramagazine.org/author/fforno/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Anaconda Installer Partitioning and Storage Survey Results
======

![][1]

Background photo taken by [David Cantrell][2] (cropped)

Back in late January, we distributed a survey focusing on partitioning preferences for Anaconda Installer (OS Installer for RHEL, CentOS, and Fedora). We were able to get 1269 responses! Thank you to all who participated. The data we collected will help the Anaconda team continue to provide an installer that best suits the majority’s needs.

Given the high participation rate, we’re excited to share the main results and findings with you!

### Who are our users?

First, we wanted to understand who the users are. The most common answers to demographic-style questions gave us the following results:

  * 96% (of 1138 responses) are _desktop/workstation Linux users_
  * Have _11+ years of experience_ using Linux (50% of 1138 responses)
  * 90% _use Fedora_ (sometimes in combination with RHEL, CentOS, Ubuntu, or Debian)



450 users identify as having an _Intermediate level of expertise_ with Linux storage partitioning

![][3]

_n=1138_

![][4]

_n=1109_

These data points mean that most of you have been using Linux with Fedora (not exclusively) on a desktop/workstation for over a decade! That’s impressive! But when it comes to Linux storage partitioning there is still quite a bit to learn – and we are here to make that easier.

### What storage and partitioning is used?

#### Storage

Once we got a better picture of who our participants were, we asked questions regarding your current storage and partitioning set up. For example, we uncovered that when it comes to identifying the disks you will use for your installation, most of you are mainly interested in the disk name, size, and the sizes of partitions. This helps the team decide which data is more helpful to present on the disk selection screen.

![][5]

_n=969_

#### Partitioning

Then, we asked questions about your preferences and expectations regarding partitioning. From studies in the past, we kept seeing an almost even preference for auto-partitioning and custom partitioning because of the different needs they each fulfill. However, this survey clarified that there is a slightly stronger preference for auto-partitioning, but many of you made it clear that you need the Installer to allow _some_ customizations to partitioning. The team is certainly keeping this in mind. In fact, we asked you “How do you prefer to create partitions (storage layout) during the installation process?” and most of the multiple-choice responses were split between “Installer creates the partitions for me”, “Installer creates partitions based on my set preferences”, or “I modify the partitions proposed by the installer”. These three options indicate some form of auto-partition, leading to the combined 70% of 964 responses preferring auto-partitioning.

![][6]

### Next steps for Anaconda

Finally, we wanted your input on what the next steps for Anaconda should be. The team has been considering a few different approaches, and most of you ranked the “Ability to select pre-defined partitioning configuration options with streamlined steps” as your #1 choice, closely followed by “Ability to customize details of partitioning”. This tells us that you are expecting a more guided experience for partitioning, especially given that most of you also feel there is a lot left to learn about Linux storage partitioning. Be on the lookout for what’s next with Anaconda!

### Thanks to all who participated

Again, thank you to all who took the time to fill out the survey. You have provided the team with plenty of data to consider for the future of Anaconda Installer.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/anaconda-installer-partitioning-and-storage-survey-results/

作者：[Flo Forno][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/fforno/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/04/anaconda-survey-results-816x345.jpg
[2]: https://fedoraproject.org/wiki/User:Dcantrell
[3]: https://lh4.googleusercontent.com/Ll0JKMqRRkk27QDAkiVWSOKCtTw5WxEK_YcanAg4y4GQVSb1gy3mLzrFH1_3qz0pg9RfzZDQClWirxs_VktGYNJVmokeTCcnyVo5w1tl7ogQvppMVtzkA7va3E3viVjrTCVxRntmketBJIZYfEgbN-k
[4]: https://lh6.googleusercontent.com/Kh84MgBt1ruL7EPpOvlMKjGXCr95src1RNIfIF0wUc8Mn0ToU1CK9AXlRlr9Z-DJQa0IYyLbtA7ccNr2Zm4B9PLEzjSKjloxRAOweYGZjPv7mDlNkAlZrP85iqEIzekLASZAeZLm2nzdqnHVW1oDCvs
[5]: https://lh3.googleusercontent.com/gK84djPSEqq1uUdpyOd6u_EsvyRtmFXoK142g8WtM9EJa-TGEFUGxKmNuo1Lq82Xcs-yivZWaen8jaBoDGBL7q2Bf16eL4Bo3Plk3mYnPhXC9-gvYfrIajZ7TcZE0_qZTuQYtd0C16cCYP5jt94lf0Q
[6]: https://lh6.googleusercontent.com/JBiUci5JMpnxIwmqTzUBt465-REV36IjuzcIRciJRpunKLMlbHdiWigTDiQQpFxBY2Gkby0pA9HZE4OT3oKtpaYytndbgu2ZsiRjzJNZpaJ_a8YkA526btuLhtaDgfp56-uNuzlwSkb4WbjgsVXF37I
