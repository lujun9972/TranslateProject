[#]: subject: "Winamp's Brief Experiment on Opening Their Source Ends in Disaster"
[#]: via: "https://news.itsfoss.com/winamp-disaster/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Winamp's Brief Experiment on Opening Their Source Ends in Disaster
======
It was a short-lived dream for Winamp in the open source world, even if
it was imperfect.
[![][1]][2]

Earlier this year, when [we reported][3] that Winamp was opening their source, many of you were suspicious of the move, with [the wording][4] used in their announcement blog raising many concerns, and rightly so.

Months later, in September, when the [Llama Group][5], the company that owns the Winamp [IP][6], provided the source code, many were left utterly disappointed and surprised with the number of blunders that they had made throughout the process.

However, it now appears that their missteps have finally caught up with them, as they have done something quite radical.

### Winamp, Can You Make Up Your Mind?

![The Winamp Collaborative License \(WCL\) was an absolute mess.][7]

In an abrupt and unannounced manner, the [source code][8] for Winamp has been taken offline, with no trace of any related data from the GitHub repo being accessible. This **comes as no surprise** , as there have been signs.

You see, **when the source code first appeared on GitHub, there were numerous issues with it**. Take, for instance, the fact that forking was not allowed, distribution of modified versions was not allowed, and only official maintainers were allowed to distribute the source code for Winamp.

There were even many bits of proprietary code from the likes of Intel and Microsoft in the source code release, and many believed that this violated the [TOS][9] of GitHub. If I had to make an educated guess, these last two points might've been the key reasons behind the removal.

A person [reported][10] to be a former employee of the Llama Group stated that they wanted to fully open source all the code that belonged to Winamp, removing any intellectual property work from the likes of Dolby, Intel, etc.

They wanted it to be something similar to the [GPL release][11] of DOOM, but management failed to see it like that and were busy guarding their IP because they paid for that. They also mention that the 100 employees [claim][12] by the Llama Group was a sham and that many of the staff were fired following an asset sale.

📋

We cannot verify if the events happened as per the person claiming all this.

#### Closing Thoughts

In the end, **I think Winamp and the company behind it have done something of a** [**PR**][13] **move here** , taking the original repository away from the public eye. In doing so, they have also managed to discard the many issues that people had complained about on the repo.

Luckily, the source code and the WCL have been preserved thanks to the many forks made by the open source community. One such fork can be found on [GitHub][14] for those interested in digging deeper.

[Winamp Source (3rd Party Fork)][14]

_💬 What are your thoughts on the blunders by Winamp? Do you think they will re-release the source code for Winamp?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/winamp-disaster/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/winamp-open-source/
[4]: https://about.winamp.com/press/article/winamp-open-source-code
[5]: https://www.llama-group.com/
[6]: https://en.wikipedia.org/wiki/Intellectual_property
[7]: https://news.itsfoss.com/content/images/2024/10/Scummy_Winamp.png
[8]: https://github.com/WinampDesktop
[9]: https://docs.github.com/en/site-policy/github-terms/github-terms-of-service
[10]: https://arstechnica.com/gadgets/2024/10/winamp-really-whips-open-source-coders-into-frenzy-with-its-source-release/
[11]: https://github.com/id-Software/DOOM
[12]: https://www.businesswire.com/news/home/20240923775631/en/Llama-Group-SA-Winamp-Opens-the-Legacy-Player-Code-and-Delivers-the-Latest-Features-of-Winamp-for-Creators./#:~:text=Employees%3A-,100,-Organization%3A%20PRI
[13]: https://en.wikipedia.org/wiki/Public_relations
[14]: https://github.com/alexfreud/winamp
