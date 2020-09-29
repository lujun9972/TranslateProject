[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Should you be concerned about the Windows XP leak?)
[#]: via: (https://www.networkworld.com/article/3583732/should-you-be-concerned-about-the-windows-xp-leak.html)
[#]: author: (Andy Patrizio https://www.networkworld.com/author/Andy-Patrizio/)

Should you be concerned about the Windows XP leak?
======
Windows XP code is almost 20 years old, but it could still live on in newer operating systems.
WildPixel / DNY59 / Getty Images / Dept. of Justice

Reports hit the Web last week that the Windows XP source code has been leaked and posted to 4chan, one of the seediest boards not on the dark web.

A link to a 42.9GB file was posted but quickly scrolled off. 4chan does not archive its posts so once the message scrolled off it was gone, but the link is getting around in other ways. The code is being hosted by Mega, a file-sharing service with its own dubious past.

Reports from other sites say the code is legitimate. Microsoft has only said “We are investigating the matter."

[[Get regularly scheduled insights by signing up for Network World newsletters.]][1]

What is still unclear is whether the code is the whole codebase or just a portion. Those who have examined the code have said it covers Windows XP Service Pack 1, Windows 2000, and Windows Server 2003. The code has been circulating privately for years, according to the leaker. One theory is that the source of the code is an academic institution.

So, is this cause for alarm? To a degree, yes. Six years after Microsoft ended all support for the XP codebase, XP has [just 1% of the user base][2], according to NetMarketshare. Windows Server 2003, which was based on the XP codebase, also went out of support in 2014. So direct impact of a new exploit should be minimal.

But Microsoft reuses code with each new version of its operating system. If you go through the Patch Tuesday fixes, you’ll see that fixes cover Windows 10, Windows Server 2019/2016/2012. Windows 7 reached end of life this past January and is no longer being patched, but the server operating systems have much longer lifespans.

You saw this most recently in “ZeroLogon,” the serious Active Directory vulnerability that was so severe the Department of Homeland Security issued a directive to all government agencies to [apply the patch immediately][3] and strongly implored private industry to do the same. That vulnerability covered Windows Server 2012 through 2019. But we don’t know if Server 2008 and 2003 are affected because Microsoft stopped supporting them.

And right on time, because there's an exploit in use out there. (That’s what happens when you tell the bad guys where to look.) Kevin Beaumont, senior threat intelligence analyst with Microsoft’s Threat Intelligence Global Engagement &amp; Response team, [issued a warning][4] that he has found an exploit in the wild.

So it is theoretically possible that the bad guys can comb through the XP code and find an exploit that impacts Server 2016 and 2019.

For now, the toothpaste is out of the tube, there’s nothing that can be done, except keep your eyes on [Microsoft Security Response Center][5] and Patch Tuesday alerts.

### An Opportunity for Microsoft?

Part of me wonders if there is a positive outcome for Microsoft. For years, game developer id Software had a tradition of releasing the source code of game engines that were a few revisions old. At the time, id was led by John Carmack, one of the most gifted game developers in the world.

When a game was out of date, and he had developed a whole new gaming engine, he would remove licensed third-party code and toss the source out for all to play with under a GPL license, and see what they came up with. All kinds of mods would be made, but more important, it gave coders a chance to show off their chops.

At the time I was heavily into the first-person shooter genre that id had single-handedly created, and I followed the community closely. It seemed like hardly a week went by when I didn’t see a report that a modder had impressed a game company with their work and been hired.

Quite a few gamers got jobs at game companies thanks to Carmack, and I wonder if the same will happen here. Will people come up with Windows modifications and will Microsoft bring them on board?

(Irony of ironies, Microsoft is in the middle of a $7.5 billion acquisition of gaming giant Bethesda Softworks, which bought out id Software in 2009. Carmack went to work for Oculus VR and is now doing Artificial General Intelligence (AGI) research, which is defined as AI that can pick up intellectual tasks like a human being does rather than standard AI that does only what it’s told. And if anyone can create Project 2501, it’s Carmack.)

Join the Network World communities on [Facebook][6] and [LinkedIn][7] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3583732/should-you-be-concerned-about-the-windows-xp-leak.html

作者：[Andy Patrizio][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Andy-Patrizio/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/newsletters/signup.html
[2]: https://www.netmarketshare.com/operating-system-market-share.aspx?options=%7B%22filter%22%3A%7B%22%24and%22%3A%5B%7B%22deviceType%22%3A%7B%22%24in%22%3A%5B%22Desktop%2Flaptop%22%5D%7D%7D%5D%7D%2C%22dateLabel%22%3A%22Trend%22%2C%22attributes%22%3A%22share%22%2C%22group%22%3A%22platformVersion%22%2C%22sort%22%3A%7B%22share%22%3A-1%7D%2C%22id%22%3A%22platformsDesktopVersions%22%2C%22dateInterval%22%3A%22Monthly%22%2C%22dateStart%22%3A%222019-09%22%2C%22dateEnd%22%3A%222020-08%22%2C%22segments%22%3A%22-1000%22%7D
[3]: https://www.networkworld.com/article/3583770/government-cybersecurity-agency-warns-of-windows-server-exploit.html
[4]: https://twitter.com/GossiTheDog/status/1309901911869587463
[5]: https://www.microsoft.com/en-us/msrc
[6]: https://www.facebook.com/NetworkWorld/
[7]: https://www.linkedin.com/company/network-world
