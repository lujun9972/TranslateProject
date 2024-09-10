[#]: subject: "Roblox Teases an Open-Source AI 3D World Creator"
[#]: via: "https://news.itsfoss.com/roblox-open-source-ai/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Roblox Teases an Open-Source AI 3D World Creator
======
AI models for creating 3D game environments. Sounds exciting!
[![][1]][2]

Artificial intelligence has spread to many aspects of our daily lives; you have most likely interacted with an AI-powered product or service by now.

Similarly, **video games are no strangers to having AI in them**. Cyberpunk 2077, the popular game set in a dystopian future ( _one of my_ [_favorites_][3]), uses an AI-powered software called “[JALI][4]” to automate facial animation and lip-syncing of dialogues to provide [realistic interactions][5] with the game's [NPC][6]s.

There is another game, [Roblox][7], which has been [experimenting][8] with AI-powered tools to improve productivity and output for some time now. But, as part of this year's Roblox Developers Conference (RDC), they have [announced][9] something really cool.

### Roblox Launches A 3D Foundational Model

Yes, that is what Roblox calls their upcoming open-source generative AI platform. It **can take in text prompts to quickly create 3D environments**. As demonstrated by the video above, you can see that the 3D foundation model created a racetrack with different environments, such as a desert and a forest.

As for how the tech works, it “[tokenizes][10]” the 3D blocks from the wide range of in-game worlds created by users in Roblox and interprets the blocks as things that can be assigned a numerical value. This enables the AI model to anticipate the subsequent blocks and generate 3D environments.

If you were wondering, **what if the output is all messed up?**

Well, to mitigate that, there's a second AI model that has been trained on 2D data from both open-source and licensed data sets to moderate the first one's output.

When in [conversation][11] with MIT Technology Review, [Anupam Singh][12], VP of Engineering, Growth & AI Platform at Roblox, said that:

> We’re doing it in open source, which means anybody, including our competitors, can use this model. Getting it into as many hands as possible also opens creative possibilities for developers who are not as skilled at creating Roblox environments.

#### Want To Check It Out?

At first glance, this foundational model seems like **it could be a great thing for those who want to create game worlds quickly** without having to dabble too much with code while focusing more on the creative side of things.

Being open-source means that it will be very accessible. But, **the code is yet to show up** , and we are not sure which license it would be provided under. My best guess would be one of the OSI-approved [licenses][13].

Meanwhile, you can keep an eye on Roblox's [GitHub][14] project page, where it is bound to show up eventually.

[Roblox (GitHub)][14]

**Suggested Read** 📖

![][15]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/roblox-open-source-ai/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/windows-game-on-linux-experience/
[4]: https://jaliresearch.com/
[5]: https://www.youtube.com/watch?v=fa3_Mfqu8KA
[6]: https://en.wikipedia.org/wiki/Non-player_character
[7]: https://www.roblox.com/
[8]: https://devforum.roblox.com/t/code-assist-full-release-ai-powered-code-completion/2848978
[9]: https://corp.roblox.com/newsroom/2024/09/rdc-2024-robloxs-next-frontier
[10]: https://en.wikipedia.org/wiki/Lexical_analysis
[11]: https://www.technologyreview.com/2024/09/06/1103707/roblox-is-launching-a-generative-ai-that-builds-3d-environments-in-a-snap/
[12]: https://www.linkedin.com/in/anupamvsingh/
[13]: https://opensource.org/licenses
[14]: https://github.com/Roblox
[15]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
