[#]: subject: "Even Linux Creator Linus Torvalds is Using AI to Code in 2026"
[#]: via: "https://itsfoss.com/news/linus-torvalds-vibe-coding/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Even Linux Creator Linus Torvalds is Using AI to Code in 2026
======

[![Warp Terminal][1]][2]

While the holiday season is often seen as a time to slow down, relax and just lie down idle, some people choose to use this period to quietly work on side projects they never get time for during the year. With relaxed schedules and a mental break from routine pressures, the holiday period creates space for experimentation and creativity. A good time to tinker with ideas that have been postponed all year long or build something just for the joy of it.

It seems that Linux creator Linus Torvalds also utilized the holidays to work on a side project.

Last holiday, he had [created his own guitar pedals][3]. This year, he worked on a new project called [AudioNoise][4] that generates random digital audio effects. It is open source software, of course, licensed under GPL 2.0.

For sure, it's "just a hobby, won't be big and professional" in the real sense. It's a small side project that Torvalds created to learn about digital audio processing.

> These are – like the analog circuits that started my journey – toy effects that you shouldn't take seriously. The main design goal has been to learn about digital audio processing basics. Exactly like the guitar pedal was about learning about the hardware side.

### Part of this new project is 'vibe coded'

The interesting part comes at the bottom of the README of [AudioNoise GitHub repo][4].

![][5]

While Torvalds coded the C language part on his own, he took the help of [AI coding assistant][6] for the visualizer written in Python.

> Also note that the python visualizer tool has been basically written by vibe-coding. I know more about analog filters – and that's not saying much – than I do about python. It started out as my typical "google and do the monkey-see-monkey-do" kind of programming, but then I cut out the middle-man – me – and just used Google Antigravity to do the audio sample visualizer.

Linus used [Google's Antigravity][7], an AI powered IDE which is a fork of Windsurf which itself is a fork of Microsoft's VS Code. While it is not clear which AI agent Torvalds used, I can safely guess that he would have used the default Google Gemini here.

Well, at least Torvalds explored vibe coding. It gives me motivation to stop resisting and experiment with AI for some coding-related side projects, too. How about you?

_Source:_ [_Phoronix_][8].

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/linus-torvalds-vibe-coding/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/torvalds/GuitarPedal
[4]: https://github.com/torvalds/AudioNoise
[5]: https://itsfoss.com/content/images/icon/pinned-octocat-093da3e6fa40-29.svg
[6]: https://itsfoss.com/coding-llms-copilot-alternatives/
[7]: https://antigravity.google/
[8]: https://www.phoronix.com/news/Linus-Torvalds-Vide-Coding
