[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Why I switched from Vim to Emacs)
[#]: via: (https://opensource.com/article/20/8/vim-to-emacs)
[#]: author: (Jimmy Sjölund https://opensource.com/users/jimmysjolund)

Why I switched from Vim to Emacs
======
A long-time, loyal Vim user moves to the other side in the age-old
debate between text editors.
![Emoji keyboard][1]

I have been a loyal [Vim][2] user since, well, I don't even remember any longer. Over the years, I tried other editors, but Vim commands and keyboard shortcuts are second nature to me, so much so that I ended up doing `:w` every time I wanted to save in another application. So, for a long time, I stuck with Vim for all my note-taking and writing. By combining Vim with [Markdown][3] syntax, I could easily export my notes to any format for other uses or sharing with my colleagues.

I've always enjoyed working in a terminal, but I usually needed other applications for my email, calendar, and tracking the time I spend on various tasks, which I like to do for numerous reasons. I tried different cloud solutions, [kanban boards][4], and email clients, but I kept looking for a way to do it all in a terminal. I tried some great projects for time tracking and kanban on the command line—but there was always something missing in my workflow. That is until I read an article about using [Org mode][5] in Emacs.

I had tried Emacs before and found out there are even more commands and keyboard combinations to keep track of in Emacs than Vim! However, every time I read an article explaining different ways to use Org mode, it seemed like [Emacs][6] was the solution I was looking for. So I made another venture into the world of Emacs.

### My steps toward Emacs

At first, I struggled to try to remember all the new commands and endless combinations of **CTRL +** keys. I learned I could tweak Emacs to use my well-known Vim commands and keyboard shortcuts, but I decided I should try to learn Emacs' basics first.

I messed up a lot. I had to keep a [cheat sheet][7] handy to check myself. Undo was the command I looked up most often. In time, the commands and keystrokes grew on me, and, as I moved along, adding more features into my Emacs configuration and getting used to the environment, it turned out to be, if not everything I needed, at least the best solution I have found so far.

#### Time and task tracking

I started out by using Emacs and Org mode just for my tasks and planning, replacing how I had been using online kanban boards. I set up my tasks with **TODO**, **IN-PROGRESS**, and **DONE** labels, mirroring the workflow and setup I was used to using on my kanban board. It's easy to sort or filter on different statuses or keywords, which makes it easy to find the most important task to focus on. Later, I added **WAIT** and **HOLD** options for tasks that were waiting for someone else or were on hold for different reasons. Emacs has great options to customize it for my unique needs; for example, I quickly set up color-coding to make it easy to see the different statuses.

![Color-coded statuses in Emacs][8]

(Jimmy Sjölund, [CC BY-SA 4.0][9])

By using Emacs' [agenda][10], I could see all my scheduled meetings and deadlines, so I had less need to switch to my company's calendar application.

Emacs' main advantage for me was the ability to track my time for each task I work on or every meeting I attend. At the end of each week and month, I can pull statistics for time reporting or just for my own information and follow-up. I mainly use [this method][11] to clock my time.

#### Note-taking

Since I was using Emacs for time tracking and planning, it became kind of strange to switch over to Vim for note-taking and writing. So I started to create and open my notes files directly in Emacs; no surprise, it was quite handy because it was easier to switch between my notes and my to-do file.

Also, just like in Vim, you can set up Emacs to colorize Markdown. But soon, I started using Org mode's syntax for my notes instead because it provides other nice features, such as the ability to close and expand different headings.

With Pandoc installed, I can export my notes to HTML, PDF, and other document formats with only a few keystrokes.

The one thing I have not yet moved to Emacs is email. At work, we use Microsoft 365 and, while it's possible to read and send email in Emacs, there are too many obstacles, like booking meetings and conference rooms, to seem worth the trouble to bring them into my terminal. Maybe my personal email, though…

### What's the real debate?

After all these years of using Vim and observing the old "Vim vs. Emacs" debates, I feel like a traitor moving over to Emacs. I have seen and tried similar features or add-ons in Vim, but they never seemed to work as fluently as they do in Emacs. I still use Vim for quick notes or when I want to copy and paste something within or between files (as I can't remember the way to do it right in Emacs—but someday I will).

Maybe the debate isn't really about Vim vs. Emacs, and it's about using the technology that works best for the task at hand. Explore both, appreciate both. Until then `:wq!`

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/vim-to-emacs

作者：[Jimmy Sjölund][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/jimmysjolund
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/emoji-keyboard.jpg?itok=JplrSZ9c (Emoji keyboard)
[2]: https://opensource.com/resources/what-vim
[3]: https://daringfireball.net/projects/markdown/
[4]: https://en.wikipedia.org/wiki/Kanban_(development)
[5]: https://orgmode.org/
[6]: https://opensource.com/resources/what-emacs
[7]: https://opensource.com/downloads/emacs-cheat-sheet
[8]: https://opensource.com/sites/default/files/uploads/emacs-example.png (Color-coded statuses in Emacs)
[9]: https://creativecommons.org/licenses/by-sa/4.0/
[10]: http://cachestocaches.com/2016/9/my-workflow-org-agenda/
[11]: https://sachachua.com/blog/2007/12/clocking-time-with-emacs-org/
