[#]: subject: "We Ditched Clickup for Fizzy: An (Open Source) Kanban Board App"
[#]: via: "https://itsfoss.com/fizzy-self-hostable-kanban-solution/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

We Ditched Clickup for Fizzy: An (Open Source) Kanban Board App
======

[![Warp Terminal][1]][2]

Being able to maintain 100% productivity is fiction that's best reserved for comic books. But there are certain tools and resources that genuinely help. If you asked me, listening to music ( _without disturbing others_ ), using [a Pomodoro timer][3], and having [solid window tiling][4] are some of the essentials.

Then there are [Kanban boards][5], which act as visual tools to help you track tasks as they progress through various states, the most elementary of them being from " _to-do_ " to being " _done_."

### We tried a number of project management applications in the past

Over the past several years, we tried a number of project management tools. There was [Trello][6] in the play ten years ago. I consider Trello the OG of simple but effective Kanban board service. Then we had a self-hosted Nextcloud instance for everything. Mainstream tools like Asna were tried for a few months as well.

And then we switched to [ClickUp][7] as it provided plenty for free and was suitable for our needs. It has everything that we needed for our collaboration with internal and external contributors. Last years, we made a brief switch to [Huly][8], a new open source project management tool, but it was more geared towards software development, so we moved back to ClickUp.

Things were comfortable until Abhishek was bit by the 'we got to try new things' bug again. And hence we are trying some new services that help us manage the work around It's FOSS and Linux Handbook.

This is where [Fizzy][9] comes in. The new tool we are using for task managements these days.

🚧

Fizzy is not fully open source, only source available. No matter how much they claim to be 'open source'.

### Fizzy: Kanban for Everyone

It is a Rails-based Kanban tracker built by [37signals][10], the folks behind [Basecamp][11] and [HEY][12]. Designed to be fast, colorful, and devoid of the bloat found on most [mainstream project management tools][13], Fizzy just clicked with us.

With this, you get boards, cards, columns, a few handy options, and that's about it. There are **no complicated features** , **no AI bloat** , or analytics dashboards that you will never look at. Though it does feature **a custom license that will rub many the wrong way**.

Called the [O'Saasy License Agreement][14], it lets you download, modify, and **self-host Fizzy for free**. You can use it for your personal projects, your company, or even tweak the code to fit your needs.

What you can't do is **turn around and sell Fizzy as a hosted service to other people**. That right stays with 37signals.

### And we switched to it from ClickUp

While I still check [ClickUp][7] occasionally, as many of my earlier pending tasks are still over there, we at It's FOSS have switched to Fizzy since the beginning of this month. Abhishek was trying it personally for most of January.

#### What Works?

![This is how the tasks page looks in Fizzy.][15]

For starters, **creating new tasks and boards is easy** ; you just have to click a few well-placed buttons, and you will be set. Access control to these is simple, with an auto-close timer moving any unattended tasks to the " _Not Now_ " status when the set time frame is reached.

The top menu bar, which is accessible by clicking on the Fizzy logo, **does a good job in presenting all the commonly accessed options** like boards, tasks, and people on the team.

![The board and user profile settings on Fizzy.][16]

Browser notifications work well too, at least on the Linux version of [Vivaldi][17], where I use it. The **search functionality is a good one too** ; it is quick, doesn't mess about, and provides relevant results.

#### What doesn't work?

![You could fit two Boeing 747s in the wasted space. /s][18]

The _Home_ page and the overall interface **have plenty of wasted space** that could've been used better. Maybe a quick-access sidebar that could house notes, a pomodoro timer, and other productivity-focused niceties.

Toward the bottom, the three options to access pinned tasks, the search, and notifications feel tacky at best. While these work, the way they are laid out feels very limited/closed off.

Another quirk is whenever I go into the " _Assigned to Me_ " page, open a task, and then close it, I am taken back into the board the task was on. **Why is this an issue, you ask?**

We usually have many tasks up on the board, and having to retrace my steps to return to the tasks assigned to me is just plain annoying. Then there's **the absence of the ability to set deadlines for tasks**. This is something any Kanban board worth its salt should have.

That said, **Fizzy is still evolving**. The good news is that 37signals tends to listen to feedback, so there's room for improvement as the project matures.

### Explore Fizzy

You can either [self-host Fizzy on your own server][19] or opt for [their managed service][20], which offers 1,000 cards for free. **$20/month** gives you access to unlimited cards and users.

[Fizzy][20]

We have not reached the 1,000 cards limit yet and still contemplating if we should self-host it or add it to our list of the few open source services we pay for. I know it's not 100% open source but still.

Sadly, **there's no importing feature** , so you will have to manually move over data from other services. I intend to do this for my existing tasks over on ClickUp. This is also one of the factors you should weigh in if you want to make the switch for your team and project.

* * *

**Suggested Read 📖:** [_This Local, Offline Tool is Good for Personal Project Management_][21]

![][22]

--------------------------------------------------------------------------------

via: https://itsfoss.com/fizzy-self-hostable-kanban-solution/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/koncentro-app/
[4]: https://itsfoss.com/rise-of-window-tiling/
[5]: https://en.wikipedia.org/wiki/Kanban_board
[6]: https://trello.com/
[7]: https://clickup.com/
[8]: https://huly.io/
[9]: https://www.fizzy.do/
[10]: https://37signals.com/
[11]: https://basecamp.com/
[12]: https://www.hey.com/
[13]: https://zapier.com/blog/free-project-management-software/
[14]: https://osaasy.dev/
[15]: https://itsfoss.com/content/images/2026/02/fizzy-task-dialog-1.png
[16]: https://itsfoss.com/content/images/2026/02/fizzy-board-settings.png
[17]: https://vivaldi.com/
[18]: https://itsfoss.com/content/images/2026/02/fizzy-board-view.png
[19]: https://github.com/basecamp/fizzy
[20]: https://www.fizzy.do/#pricing
[21]: https://itsfoss.com/schedule-kanban-board/
[22]: https://itsfoss.com/content/images/icon/android-chrome-512x512-270.png
