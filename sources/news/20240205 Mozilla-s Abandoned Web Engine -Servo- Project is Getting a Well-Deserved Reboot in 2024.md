[#]: subject: "Mozilla's Abandoned Web Engine 'Servo' Project is Getting a Well-Deserved Reboot in 2024"
[#]: via: "https://news.itsfoss.com/servo-rust-web-engine/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Mozilla's Abandoned Web Engine 'Servo' Project is Getting a Well-Deserved Reboot in 2024
======
What if I tell you that the 'Servo' web engine performs faster on
Raspberry Pi compared to Chromium? Get more details here!
The developers of Servo are starting 2024 by going all in.

Spotted by [Bernie Innocenti][1] when he was visiting [FOSDEM 2024][2], the Servo Project team were there showing off the work done so far.

![Pic Credits: Bernie Innocenti][3]

That got me wondering; **What's the progress with Servo nowadays?** 🤔

If you were not familiar, [Servo][4] is **an experimental browser engine** that leverages the power of Rust to provide a memory-safe and modular experience that is highly adaptable.

After Mozilla created Servo back in 2012 as a research project, it saw its share of ups and downs over the years, with it [making a comeback][5] in 2023; thanks to a fresh approach by the developers on how Servo should move forward.

Even though there are plenty of [open source Chrome alternatives][6]; With this, there's a chance that we will get some really cool options based on Servo that just might give Blink and Gecko a run for the money! 😃

Let's see how The Servo Project has fared so far, and what's in store for it in 2024.

📋

[Blink][7] is used by Chromium, and other browsers based on it, whereas [Gecko][8] is used by Firefox and a few others.

### Servo: What to Expect?

Just a few months back, in September 2023, after The Servo Project [officially joined][9] Linux Foundation Europe, the existing contributors from [Igalia][10] stepped up their game by taking over the project maintenance.

To complement that, at Open Source Summit Europe last year, [Manuel Rego][11] from Igalia shared some really [useful insights][12] when he presented.

He showcased stuff like the **WebGL support** , **cross-platform support** including **mobile support** for Android and Linux, among other things.

They have experimented with Servo for embedded applications use-cases (like running it on Raspberry Pi), and have plans to make advances on it. As far as I can see, it looks like, Servo is faster for Raspberry Pi compared to Chromium 🤩

You can explore more such demos on [Servo's demo webpage][13].

Not to forget, a new layout engine is also in the works, where new features and compatibility arrangements are being made within its development.

**Did you know that even though Mozilla dropped the experimental project, Firefox still utilizes some servo components in the browser?** 😉

Naturally, that makes us wonder if the newer Servo layout engine (or any other component) might make it into the Firefox ( _never say never!_ ).

Back then, Servo was still considered experimental, and in 2024, I hope that progresses a bit further.

Seeing this is an independent project, **the progress so far looks very promising** , the official website [now lists][14] an updated roadmap for 2024 that pretty much has the same things for all of 2024.

![][15]

There's **project maintenance and outreach** that will include the usual project maintenance tasks alongside community management, then there's the **implementation of CSS support** which will see work being done on providing basic CSS features for the Servo layout engine.

With **embedding API definition** , the Servo team will finish work on defining the Servo webview API in collaboration with [Tauri][16] while also implementing new features and requirements for the API.

And, finally, we have **Initial Android support** , that will see Servo being made to build on modern Android versions, with the developers publishing nightly APKs on the official website some time in the future.

For staying in sync with the Servo roadmap, you can follow the [official roadmap][17], and for more details regarding this project, you may head over to its [GitHub repo][18] or its official [Zulip chat][19].

_💬 What do you think of Servo? Will it rise to become a strong contender to the likes of Blink and Gecko?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/servo-rust-web-engine/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://mstdn.io/@codewiz/111868362077005163
[2]: https://fosdem.org/2024/
[3]: https://news.itsfoss.com/content/images/2024/02/Servo_a-1.jpg
[4]: https://servo.org/
[5]: https://news.itsfoss.com/mozilla-servo-web-engine/
[6]: https://itsfoss.com/open-source-browsers-linux/
[7]: https://en.wikipedia.org/wiki/Blink_(browser_engine)
[8]: https://en.wikipedia.org/wiki/Gecko_(software)
[9]: https://www.igalia.com/2023/09/07/The-Servo-project-is-joining-Linux-Foundation-Europe.html
[10]: https://www.igalia.com/
[11]: https://twitter.com/regocas
[12]: https://www.youtube.com/watch?v=9lkIX5ryZZ4
[13]: https://demo.servo.org/
[14]: https://servo.org/about/
[15]: https://news.itsfoss.com/content/images/2024/02/Servo_b.png
[16]: https://tauri.app/
[17]: https://github.com/servo/servo/wiki/Roadmap
[18]: https://github.com/servo/servo
[19]: https://servo.zulipchat.com/
