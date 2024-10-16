[#]: subject: "Turn Your Android Phone into a Ham Radio with this Open-Source Project"
[#]: via: "https://news.itsfoss.com/android-open-source-ham-radio/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Turn Your Android Phone into a Ham Radio with this Open-Source Project
======
A clever hack to make your phone more useful!
[![][1]][2]

A [ham radio][3], or amateur radio, as it is known more formally, is a type of radio communication device that is used by many people to communicate over large distances for a multitude of things.

The most popular use case for such devices is for relaying emergency communication during natural/man-made disasters, facilitating information sharing between first responders and people trapped in a remote disaster-struck area.

Of course, there are more casual uses for ham radios too. Many people connect with other ham radio operators from around the world to have a conversation, learn about the person/people on the other end, enter contests, and more.

However, **traditional ham radio setups are bulky** , sitting on top of a desk with antennas, a mic, and the radio itself.

What if I told you that there is **an open source project** that allows you to convert your [Android][4] smartphone into a portable ham radio?

Join me as I take you through an interesting DIY project. 😃

### kv4p HT: What To Expect?

[Vance Vagell][5], an experienced UX professional at Google, is the brains behind the kv4p HT project. He has been working on this for a long time and recently shared [a video][6] demonstrating how it works.

Distributed under the permissive [GPL 3.0][7], the kv4p HT is a homebrew [VHF][8] ham radio that can be attached to an Android smartphone via a USB-C port for turning it into a portable radio [transceiver][9].

The radio is made up of many parts that include the [DRA818V][10] radio module, an [ESP-WROOM-32 Development Board][11], a SMA male antenna, a SMA female 90-deg connector, a USB-C coupler, a custom PCB, a 3D-printed case, and some sticky gel pads ( _for attaching the radio to a phone_ ).

As for the **key features** of the kv4p HT, they include functions like:

  * Scanning for frequencies.
  * Freedom to switch antennas.
  * Saving frequencies to memory for later use.
  * Communicating with others via real-time messaging.



The companion app is what brings all of these things together. It also offers several other useful features, such as enabling sticky push-to-talk, audio filters for tweaking audio quality, and support for Android's [Live Caption][12] function to show captions when conversing with another person.

But, **the app has to be built from source and sideloaded** onto an Android device, as there is no APK available via F-Droid or the Play Store. Needless to say, if you want to build this, you will need to have some decent soldering and software handling skills.

#### Want To Build Your Own?

If you are up for the task, then the official [quick-start guide][13] will set you on the path to building your own kv4p HT VHF radio. If you are looking for the project files, then you can head to [GitHub][14].

[kv4p HT][13]

Furthermore, a newer version of the PCB ([ _v1.6_][15]) is already out, if anyone wants to be on the bleeding edge, and there are plans to further improve the Android app in the near future.

If you get lost along the way, the kv4p [Discord server][16] has a friendly community that can answer any questions you might have.

#### Closing Thoughts

I find such projects very cool; When implemented, they can help people stay connected with others in extremely remote areas or areas where traditional forms of communication have been disrupted due to a calamity.

Seeing where the world is headed currently, such seemingly ordinary forms of communication might just be the thing that helps people survive catastrophes.

**Via:** [Hackaday][17]

**Suggested Read** 📖

![][18]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/android-open-source-ham-radio/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Amateur_radio
[4]: https://www.android.com/
[5]: https://www.linkedin.com/in/vancevagell/
[6]: https://www.youtube.com/watch?v=9eXHgktFD-U
[7]: https://www.gnu.org/licenses/gpl-3.0.en.html
[8]: https://en.wikipedia.org/wiki/Very_high_frequency
[9]: https://en.wikipedia.org/wiki/Transceiver
[10]: https://www.dorji.com/docs/data/DRA818V.pdf
[11]: https://www.amazon.com/gp/product/B0CDRLLTHD
[12]: https://support.google.com/accessibility/android/answer/9350862?hl=en
[13]: https://www.kv4p.com/quick_start.html
[14]: https://github.com/VanceVagell/kv4p-ht
[15]: https://github.com/VanceVagell/kv4p-ht/tree/main/pcb/v1.6%20(better%20filter)
[16]: https://discord.gg/Ev9R9uFeCq
[17]: https://hackaday.com/2024/10/15/a-phone-a-ham-radio-relax-its-both/
[18]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
