[#]: subject: "ChromeOS + Android Linux Kernel: Google's Plan to Add AI Features to Chromebook"
[#]: via: "https://news.itsfoss.com/chrome-os-android-linux-kernel/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ChromeOS + Android Linux Kernel: Google's Plan to Add AI Features to Chromebook
======
Google is all set to utilize the Android Linux kernel for ChromeOS.
[![][1]][2]

It's common knowledge that Google got bamboozled by the likes of [NVIDIA][3] and [OpenAI][4], who got the drop on them when it comes to Artificial Intelligence (AI).

And, software is not the only side they got caught out on, they have also been behind in terms of implementing AI on their hardware, particularly on their [Chromebook][5] series of laptops.

The laptop space has been receiving its fair share of AI-powered gimmicks, more so on Windows-equipped laptops than Apple's macOS-equipped MacBook, but, they are getting there.

Sure, **many of you don't like the idea of AI in your computers** , and there's [solid evidence][6] backing your claims. But, Big Tech thinks different, they always focus on outmatching their competitors by using any means possible, right now, it's means jumping on the AI bandwagon.

Let's see what search engine giant is planning to do.

### Combining Android & ChromeOS: What Gives?

![][7]

[Prajakta Gudadhe][8], Senior Director, Engineering at Google ChromeOS and [Alexander Kuscher][9] from Google ChromeOS recently [announced][10] something very noteworthy.

To deliver new Google AI features to their users, they will start incorporating parts of the Android stack, such as the [Android Linux kernel][11] and [Android Frameworks][12] **into the foundation of ChromeOS**.

During the announcement, they added that:

> Bringing the Android-based tech stack into ChromeOS will allow us to accelerate the pace of AI innovation at the core of ChromeOS, simplify engineering efforts, and help different devices like phones and accessories work better together with Chromebooks.

They have already [begun the switch][13] ( _Project Floss_ ) by changing the Bluetooth stack on ChromeOS 122 from [BlueZ][14] to [Fluoride][15], which is used on Android. All of that was done in a bid to take advantage of its larger user base, straightforward architecture, and better security.

It's interesting to see Google pushing to make ChromeOS and Android closer to each other, I agree there are many benefits for both users and developers alike.

However, the announcement does mention that **these improvements to their tech stack are just the beginning** , and it will take a long time to actually ship complete products to the end-users.

Once that is done, **they are promising a seamless transition to the updated experience** , that will not cause any major downtimes.

Until then, we must wait.

**Suggested Read** 📖

![][16]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/chrome-os-android-linux-kernel/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.nvidia.com/
[4]: https://openai.com/
[5]: https://www.google.com/chromebook/
[6]: https://news.itsfoss.com/microsofts-recall-ai-insecure/
[7]: https://news.itsfoss.com/content/images/2024/06/ChromeOS-AndroidLinux.png
[8]: https://www.linkedin.com/in/pgudadhe
[9]: https://www.linkedin.com/in/alexander-kuscher
[10]: https://chromeos.dev/en/posts/building-a-faster-smarter-chromebook-experience-with-the-best-of-google
[11]: https://source.android.com/docs/core/architecture/kernel
[12]: https://developer.android.com/guide/platform
[13]: https://chromeos.dev/en/posts/androids-bluetooth-stack-fluoride-comes-to-chromeos
[14]: https://www.bluez.org/
[15]: https://android.googlesource.com/platform/system/bt/+/289a49814aef7f0f0bb98aac8246080abdfeac01/README.md
[16]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
