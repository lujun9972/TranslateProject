[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (5 lessons I learned from Open Jam 2020)
[#]: via: (https://opensource.com/article/20/10/open-jam-2020)
[#]: author: (Klaatu https://opensource.com/users/klaatu)

5 lessons I learned from Open Jam 2020
======
Game jams are a really fun way to create something interesting quickly,
provided you don't succumb to the pitfalls.
![Astropi gaming console][1]

For many people, programming is fun because it's a little like solving a puzzle. You know that, in theory, if you can just arrange logic statements and conditions in the right order, using just the right syntax, then you'll end up with an application that does something useful. The problem, strangely, is that sometimes you don't know why you'd need the application you end up with. It's like stepping outside for a walk with nowhere to go. Just as marathons provide a framework and a goal for aimless foot traffic, there are events without a cause for coders. Called sprints, hackathons, dares, or jams, these programming events are great excuses to sit down, possibly with a team of your coding comrades, and develop something interesting.

![Open Jam logo][2]

(Open Jam, [CC BY-SA 4.0][3])

[Open Jam][4] is an annual, weekend-long, virtual game jam that results in as many open source games as the participants manage to complete within the 80 hours the event is open. I first encountered Open Jam at the [All Things Open][5] 2018 conference, where the jam's organizers had an arcade cabinet running the previous year's work.

![Open Jam game console][6]

(Opensource.com, [CC BY-SA 4.0][3])

I'd played small games from other jams before and always thought it could be fun to join one someday. However, I had no interest in contributing to projects that were not open source, nor to projects developed on non-open stacks. So the idea of an _open source_ jam was persuasive enough for me to commit.

This year, I completed a game for Open Jam, and the experience was great—and nothing at all like I expected. If you're tempted by the prospect of fame and fortune through a game jam, avoid some of the pitfalls by reading through five lessons I learned from taking part in Open Jam.

### 1\. Keep it simple

In 2019, I signed up for Open Jam with the intent of programming a simple game in [Lua][7]. I had some good ideas for a game, and I thought participating seemed like a simple idea, so I blocked out the weekend for coding. This game was never completed.

As it turns out, there are simple ideas, and then there are _actually_ simple ideas. For a weekend game jam, you must allow simplicity to pervade every aspect of your game.

You want a story in your game? It must be a two-beat story. Skip the second act and move straight from the first act (a problem is presented) to the third (problem solved, game over).

You need graphics for your game. Keep them simple. Even if you find a wandering artist (they do exist, and they converge on Open Jam's chat server in search of projects to join), their time is as limited as yours. Graphics in games multiply quickly—and exponentially when you use animation.

If you want sound effects and music, keep it simple. You might find composers, but a weekend doesn't allow much time for composition, performance, and delivery. You'll likely have to choose existing music that may not fit your game perfectly, or use simple tunes that are quick to deliver. Loops are probably ideal, and letting your composer handle sound effects ensures that the music and effects are well integrated.

For my game this year, I did away with simplicity and adopted _extreme minimalism_. I was a one-person team (which, it occurred to me later, isn't necessarily in the spirit of a collaborative game jam), so I opted for no graphics beyond colored blocks and used mostly single-note musical pieces (composed on [LMMS][8])—and much of the music is composed by the user as an effect of what they do during the game.

### 2\. Start from the beginning

When I started writing my game, I began with my game board and worked out the mechanics largely in an attempt to discover whether I actually had a game. For several hours, I wasn't entirely convinced I wasn't merely writing a digital Etch-A-Sketch with no game element in sight. I eventually found a game in the code I was writing, but when I finished my first draft, I discovered that I had a game that needed to be relaunched each time you want to play again. I had no start screen, no end screen, no leaderboard, and no way to choose to play again.

Fixing these issues required some refactoring, and even in its present state, the code isn't as optimized as it could be. In my utilitarian code, I usually don't mind code that's more verbose than necessary in order to document the logic for myself and others who want to understand it. However, this is just a relaxing game, so I think it would be nice to have optimized code that's well organized rather than after-thought functions mixed in with important classes and hastily added global variables.

Some of this can be excused by my code being written during a frantic game jam, but in the future, I'd prefer to start from the beginning, even if it's just boilerplate templates. I'll begin with a start screen where the player can set difficulty levels, I'll ensure there's an end screen with the option to quit or play again, and so on.

### 3\. Focus on one game mechanic

I'm not a game designer, but that doesn't stop me from trying to be. In the best big video games with lots of levels, part of the experience is discovering new game mechanics. Imagine a game where you start out by discovering, through subtle prompts, that you can stop time. Next, you gain the power to not just stop time, but to rewind it by some number of seconds. Later, you gain the ability to fast-forward time. And so on.

Sounds fun and like something you should never try to make in a game jam.

In the original version of my game, I started writing automated actions for the computer to take against the player in an attempt to disrupt the game board. This led me down a path of complex calculations, state detection, turn anticipation, and probability. I spent several hours trying to find a good balance between offering good aggravation and being just plain annoying and also struggling to emulate intelligent decisions.

Ultimately, I learned a lesson or two from my experience as a Dungeon Master™: the player's most menacing opponent is the player. I discarded the idea of disrupting the game state and instead allowed the player room to overthink things.

This was the correct choice from both a design perspective and a code perspective. After all, the more mechanics you have in your game, the more code you have to write. The more code you have to write, the more code you have to debug.

### 4\. Choose your language carefully

I didn't so much choose [Python][9] and [Pygame][10] for my project this year as Python and Pygame chose me. I'd just been demonstrating to someone how to create a grid (a simple two-dimensional array) using nested loops, and it happens that the language they were using was Python. I used Pygame instead of something more modern like [Arcade][11] because I am familiar with Pygame. After I'd demonstrated the task, I realized it was Open Jam weekend and that, with "just a few" extra lines of code, I could create a game out of the array I'd created. Unsurprisingly, those few extra lines turned out to be 200 or so.

Python is great because it's cross-platform, but delivering a Python app to all of its possible platforms can be another jam in itself if you haven't planned ahead (and I hadn't planned ahead). You absolutely _can_ deliver Python to desktop operating systems, Android, iOS, and more, but for best results, you must develop with that in mind by using [Kivy][12] or [BeeWare][13] or a similar framework. These aren't processors that you run your code through to magically and instantly end up with packages for all platforms; these are frameworks you must work with from start to finish. Because I hadn't planned with my targets in mind, I finished Open Jam with a game that runs well on Linux, Windows, and macOS but still requires packaging and does not run at all on mobile platforms.

Were I to repeat the game jam with improved foresight, I'd have used Java or [Processing][14], both of which feature simple packaging solutions for desktops and mobile.

Ultimately, keep your target in mind and work toward your desired result. Don't program all weekend only to find that final delivery requires another weekend.

### 5\. Use what you know

Removing barriers to completion is one of the best ways to ensure you finish your game. While Pygame may not have been the best choice by some measures, it was the best choice given the results. As I demonstrated to myself last year, it's easy _not_ to finish a game jam, so ensuring I had every opportunity to finish by using a framework I've taught to kids and adults for the past several years was a good strategy.

This extends to other aspects, too. A game jam probably isn't the best occasion to experiment with anything unfamiliar. Don't try to compose music on an application you've barely ever touched. Don't design your graphics with a cool new application you read about on the internet but have only opened once. It's hard enough to finish a game in two days, so you want everything you use during development to facilitate the end goal.

### Planning for next time

I was a one-person team, so I didn't take advantage of (or contribute to) the social aspect of Open Jam, and yet it was still a satisfying and fun experience. There's a lot of momentum when lots of people gather together for a unified goal, and Open Jam's promotion of open source gaming is something that's easy to get excited about from both the open source and gamer angle. If you've ever thought of joining a game jam, I highly recommend signing up for [Open Jam][4] next year!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/open-jam-2020

作者：[Klaatu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/klaatu
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/astropi_lead.png?itok=mCMSx9my (Astropi gaming console)
[2]: https://opensource.com/sites/default/files/uploads/open-jam-logo.png (Open Jam logo)
[3]: https://creativecommons.org/licenses/by-sa/4.0/
[4]: http://openjam.io
[5]: http://allthingsopen.com
[6]: https://opensource.com/sites/default/files/uploads/arcadeconsoles2_0.jpg (Open Jam game console)
[7]: https://opensource.com/article/17/4/how-program-games-raspberry-pi
[8]: https://opensource.com/life/16/2/linux-multimedia-studio
[9]: https://www.python.org/
[10]: https://www.pygame.org/news
[11]: https://opensource.com/article/18/4/easy-2d-game-creation-python-and-arcade
[12]: https://kivy.org/#home
[13]: http://beeware.org
[14]: http://processing.org
