[#]: subject: "Microsoft's Unexpected Move to Hand Over an Open-Source Project to the Wine Team: A Generous Shift?"
[#]: via: "https://news.itsfoss.com/microsoft-donates-mono-project/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft's Unexpected Move to Hand Over an Open-Source Project to the Wine Team: A Generous Shift?
======
Wow! This is surprising. But, is it what it sounds like, or is it
something else?
[![][1]][2]

Usually, when one hears the words [Microsoft][3] and open-source being used in the same sentence, they usually expect something bad to have happened. But, you see, Microsoft supports a [long list][4] of open-source projects that are used for various things.

One of those projects used to be [Mono][5], the long-running [.NET][6]-compatible framework for creating cross-platform software, whose ownership has changed hands over the years, with Microsoft being the latest in the line of owners.

However, now that has changed, possibly for the final time. 😲

### Microsoft Being Generous: What Is Happening?

![The Mono project's homepage.][7]

[Announced][8] a few days ago, **Microsoft has decided to hand over the Mono project to the folks over at** [**WineHQ**][9]. They are the ones behind the popular [Wine][10] compatibility layer, which is used for running Windows apps on Linux and other [POSIX][11]-compliant OSes.

Due to this change, Microsoft is now recommending users and maintainers of Mono-based apps make use of their actively maintained [fork][12] of Mono, which is a part of the .NET code.

As for **what happens to Mono's repository** over on [GitHub][13], it will remain available, with the repos most likely being archived, and binaries being accessible up to four years from now.

Of course, Mono now has a new home at WineHQ's [GitLab][14] instance, so no need to worry.

Concluding the announcement, Microsoft developer [Jeff Schwartz][15] added that:

> We want to recognize that the Mono Project was the first .NET implementation on Android, iOS, Linux, and other operating systems. The Mono Project was a trailblazer for the .NET platform across many operating systems.

> It helped make cross-platform .NET a reality and enabled .NET in many new places and we appreciate the work of those who came before us.
>
> Thank you to all the Mono developers!

While at first glance, this sounds generous, but it may not be in another angle.

#### Some Different Thoughts

When you take a look at Mono's [release history][16], the last major release ( _6.0_ ) was way back in 2019, and following that were minor patch releases ( _6.x.x)_ that came to an end earlier this year in February.

It's good to see that Mono has found a new home and won't be facing the same fate as many other open-source projects when [they aren't actively developed][17] or maintained anymore.

But, there's **another viewpoint that I am slowly warming up to** : that Microsoft just did this to avoid letting people know that they intended to discontinue the project. An r/linux member [puts it][18] well:

> Looks more like they want to discontinue the project, but that sounds bad so they just declared that wine is the new upstream now.

Whatever their motivation behind handing over Mono to the Wine project maybe, I am just glad to see that an open-source project has found a new home, where it is hopefully valued more.

_💬 What do you think about Microsoft's move? Are there any ulterior motives behind this shift?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/microsoft-donates-mono-project/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.microsoft.com/
[4]: https://opensource.microsoft.com/projects/
[5]: https://www.mono-project.com/
[6]: https://dotnet.microsoft.com/en-us/
[7]: https://news.itsfoss.com/content/images/2024/08/Mono_Homepage.png
[8]: https://github.com/mono/mono/issues/21796
[9]: https://www.winehq.org/
[10]: https://itsfoss.com/use-windows-applications-linux/
[11]: https://en.wikipedia.org/wiki/POSIX
[12]: https://github.com/dotnet/runtime/tree/main/src/mono
[13]: https://github.com/mono/mono
[14]: https://gitlab.winehq.org/wine-mono/mono
[15]: https://www.linkedin.com/in/jeff-schwartz-4ba91023/
[16]: https://github.com/mono/mono/tags
[17]: https://news.itsfoss.com/neofetch-rip/
[18]: https://www.reddit.com/r/linux/comments/1f2qbi1/comment/lk8kir4/
