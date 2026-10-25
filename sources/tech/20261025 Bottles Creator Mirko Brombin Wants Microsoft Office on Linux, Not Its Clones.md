[#]: subject: "Bottles Creator Mirko Brombin Wants Microsoft Office on Linux, Not Its Clones"
[#]: via: "https://itsfoss.com/interview/mirko-brombin-raven/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Bottles Creator Mirko Brombin Wants Microsoft Office on Linux, Not Its Clones
======

If you have used Linux for a while, chances are you have used something Mirko Brombin built. He created Bottles, the app that takes a lot of the pain out of running Windows software with Wine. He founded Vanilla OS. And these days, he is building [Singularity OS,][1] an operating system with its own desktop and its own approach to immutability.

We last [spoke with Mirko back in 2022][2]. A lot has happened since then. He now works full time at [fabricators][3], he is working on getting Microsoft Office running through [Bottles][4], and he has some strong views on AI and on the recent wave of apps cloning Adobe and Microsoft interfaces.

I sent him my questions over email. Here are his answers, exactly as he sent them.

### You have full time work at fabricators, Bottles, Sinty OS, and a long list of libraries and tools. How do you decide what gets your time?

I think anyone who's known me for a while knows that I'm not particularly good at sitting still, haha.

I've never really had a proper strategy for deciding what to dedicate my time to. Most of my projects are born from a problem I want to solve, an idea I want to experiment with, or simply the curiosity to find out whether something is possible.

Naturally, working full-time at fabricators and maintaining several open source projects, I've had to learn to set priorities. Not everything can receive the same attention, and not everything necessarily has to become a complete product.

### You've written about using AI agents for the mechanical work, so how much has that changed what you can realistically take on?

Artificial intelligence has certainly changed a lot about the way I work, but I think it's important to explain how, because it's a topic I've really spent a lot of time thinking about.

When I wrote my articles about using AI agents in software development, I spent quite a lot of time just trying to find the right words. In open source, it's a particularly delicate subject, especially when you're someone with a fairly public presence and free software isn't just a passion, but also part of your work and your life.

It's very easy to be misunderstood, both by those who consider artificial intelligence the solution to every problem and by those who reject it completely, and honestly... I don't see myself in either position, because I've always had a rather complicated relationship with LLMs. At first I was very skeptical and, frankly, the more I tried to understand how they worked, the harder I found it to fully trust them.

The problem isn't the quality of the code they can produce, but understanding why they produced that particular code, because when I design software, I start from the architecture, I decide how the components should interact, what responsibilities they should have, how to handle errors, which compromises to accept and, logically, which ones to avoid. I document all of this very carefully, because I want to be able to understand every decision even years later, and it's a process I particularly care about and have absolutely no intention of delegating.

I want to give an example. A large part of the applications and infrastructure I develop every day, including for work, is written in Go. Over the years I've built my own set of libraries, defined my own patterns, and developed a fairly precise way of writing software. When I use AI, I don't ask it to invent an architecture, I give it mine, along with the documentation, conventions, and constraints it has to respect. I'm the one who decides how a project is born, how it evolves, and, eventually, when it's time to abandon it.

I still write a great deal of code manually, often because I need to work on particularly delicate components, other times simply because it's faster for me to do it myself. In any case, I review every single line of code written by AI. If it does something badly, it's because I accepted it.

What still doesn't convince me, though, is the very nature of how they work, because a language model can produce a correct answer, it can even explain the steps that seem to have led it to that conclusion, but this is... Well, illogical, at least from my point of view. An LLM can produce reasoning, but it doesn't necessarily possess an explicit, persistent, and causally verifiable representation of the knowledge it uses to express that reasoning. And this bothers me quite a lot.

If an agent decides to use a particular data structure, I want to know whether it did so because my documentation specifies that it's the correct solution, or because that solution is statistically plausible given the context.

To me, these are two very different things, and it's precisely for this reason that, for quite some time now, I've been researching and experimenting with an alternative approach to current language models, a project called Amus, with which I'm exploring a different way of representing knowledge and constructing answers, trying to make the relationships that lead to a conclusion more explicit and verifiable.

I don't want to reveal too much because it's still a research project, but the first results have been really encouraging, and I hope to be able to talk about it publicly in more detail soon.

So, going back to the original question, yes, AI agents have allowed me to take on an amount of work that would have been unthinkable for a single person just a few years ago, but by using them, I've started questioning the very technology they're based on and, well, perhaps that's the best way to describe my relationship with artificial intelligence, haha.

### Your site now lists Vanilla OS as community-run. When we spoke in 2022, your goal was to make it sustainable enough to work full-time. What happened along the way, and how did it feel to step back from something you founded?

Not much has changed on this front. [Vanilla OS][5] continues to be maintained, it receives updates, especially when it comes to security and stability.

We recently released Vanilla OS 3 Reunion, which involved a huge amount of work to bring ARM support, along with writing the Vanilla OS SDK, which we used to rewrite many of the fundamental components of the operating system, so that everything could share a single common foundation.

Today, the project doesn't depend on my hands alone. There are several team members who make all of this possible, plus fabricators, which maintains its server infrastructure, and let's not forget all the contributors who report problems and provide solutions.

Over time, I've taken on a different role. I certainly still develop, in fact I developed Vanilla OS Continuity, the backup system included in Vanilla OS 3 Reunion, but... My role has started to become more political, both from the perspective of someone who finds ways to keep the project financially alive and from the perspective of making decisions about the architecture the project is built upon.

In short, I'm still holding the reins of everything :D

### When you started Bottles in 2017, Wine, PlayOnLinux, and Lutris already existed. What gap did you see that made you build another one?

Well, probably because I wasn't satisfied with any of the three, haha.

Jokes aside, when I started [Bottles][6], Wine was already an extraordinary technology, and PlayOnLinux and Lutris offered very useful tools to simplify its use. Actually, a special shout-out to [Mathieu][7]: "Hey look, I'm on It's FOSS, again!" D:

But none of them matched exactly my idea of "simplicity". My goal wasn't simply to create another launcher or a tool to install programs, but rather an environment where I could manage my applications without constantly having to touch the command line or place various DLLs here and there...

I've always found it curious how, in the Linux world, people so easily accepted the idea that technically complex tools necessarily had to be complicated to use as well. I think it's a stereotype, but also a fairly widespread one. The internal complexity of an application shouldn't automatically become the user's problem, and I'm saying this knowing that underneath Bottles there's literally a tangled mess making everything work.

And well, it's the same reason why I'm announcing [Raven][8] 😄

![][9]

![][10]

### Many FOSS folks would say the effort is better spent improving LibreOffice or ONLYOFFIC. Why is getting Microsoft's own suite running worth it to you, given that Microsoft could break it with any update?

Frankly, I don't understand why the two things should be mutually exclusive. LibreOffice, ONLYOFFICE, etc. are fantastic pieces of software that I recommend first and foremost to anyone wanting to move from Windows to Linux.

But I can't be blind either. I see it every day at work. In my office I have the privilege of using whatever I want (mainly Singularity OS with its office suite), but almost all of my clients and partners use Microsoft Office for one reason or another, for support, certification, and all those things that a user less immersed in this kind of working environment might not see.

I'm the first to say that users should have a choice, and I create those choices myself... But that's the ideal world. The real world is that sometimes we simply can't afford to make the choices we'd like to make.

![MS Office running on Linux with Soda project][11]

### Will this stay a Bottles thing, or do you expect the fixes to go upstream into Wine so that other projects benefit too?

My goal is to contribute as much as possible upstream. We'll have to see whether the Wine developers like my patches though, haha.

Jokes aside, I want this work not to remain something specific to Bottles. I'd like it to be adopted upstream.

First of all, I need to reach a point where Microsoft Office 365 works reliably, then I'll find a way to collaborate upstream. It would be pointless to do it now.

### There's also a wave of apps that clone Adobe and Microsoft tools almost one-to-one. Is copying familiar interfaces the right way to win people over, or does Linux need its own ideas? And how do you see their effort of bringing MS Office clone to Linux?

Honestly, this is the recent news I like the least, I have to be honest. I've made some tweets about it, I don't like how the identity of other people's products is being violated.

There's talk of [clean room][12]... But objectively, what's the point of talking about clean room if you then unleash a swarm of AI agents on the code, forcing them to keep Microsoft Word and Adobe Photoshop open so they can replicate them down to the very last millimeter?

It's not illegal... The practice itself isn't. But stealing, because that's what this is, the visual identity of that project is, it's called copyright infringement, and in some cases even unfair competition.

And what makes me even angrier is that I really don't see the point. Do we really need another Microsoft Office, identical down to the very last pixel?

If they had created a new suite with exactly the same functionality, using exactly the same approach, that would have been great. I would have been the first to promote it. And yet... This scares me a little, and it says a lot about what the future of open source will probably look like, especially if this is allowed and a precedent is set.

### You are also working on Sinty OS. Why build your own desktop environment and kernel platform from scratch instead of reusing GNOME or KDE pieces?

![][13]

Sinty OS is everything that Vanilla OS cannot be, because of its principles.

With [Sinty OS][1], I wanted the desktop environment to be a unique experience, tailored to my needs (and those of many others, apparently), while in Vanilla OS we use pure GNOME, vanilla, exactly as mother GNOME intended it, and it follows all its principles, its style, everything is libadwaita and consistent with that desktop environment.

On the technical side, the "behind the scenes", Sinty OS is a completely different challenge. I'm trying to build an operating system that stands on the shoulders of Atom Loops, a new immutable technology I'm working on, very different from ABRoot and anything else out there.

Atom Loops manages immutability from the very first second of boot. The bootloader, the initramfs, everything is managed by this component, which follows a strict chain of trust and update validation.

Sinty OS doesn't use partitions for the system root, it uses image files (EROFS for the rootfs and UKI for the kernelcache), which are mounted by Atom Loops during boot, which means that, well, all the disk space (formatted as F2FS) belongs to the user.

Unlike Vanilla OS, I don't use LUKS, but encrypt user files using their own unique key. It's, well, completely different. The init system isn't systemd, but an ultra-minimal solution compatible with systemd units.

Let's say the two operating systems are two very different ways of achieving very similar goals.

### When can people expect a stable release of SintyOS?

Haha, Sinty is the face of the project, as well as part of its identity.

Sinty is the shortened form I came up with for Singularity, which refers to the family of software related to Singularity Desktop and Singularity OS. Unfortunately, the term was too generic, so I decided to favor the name "Sinty". Little by little, I'm migrating everything to that name, which, in any case, will continue to mean Singularity.

There will be a lot more about Sinty, very soon. Many more applications and platforms are coming, all connected to Sinty OS.

### Anything you'd like It's FOSS readers to know?

I just want to reiterate that people need to experiment more, especially today, when we have the technologies to dream big.

It would be predictable to say that limits are made to be overcome. It's much more exciting to think about how to overcome them.

Thank you for having me in this interview, always a pleasure!

## Wrapping up

I would like to thank Mirko for taking the time to answer my questions in such detail.

I like how he refuses to pick a side in the AI debate. He uses agents heavily, yet he reviews every line they write and is researching an alternative to LLMs altogether. Amus and Raven are two things I'll be keeping an eye on, and so should you if you follow his work.

I'd also like to hear what you think about his take on the Adobe and Microsoft clones. Is copying a familiar interface fair game, or does it cross a line? Share your views in the comments.

--------------------------------------------------------------------------------

via: https://itsfoss.com/interview/mirko-brombin-raven/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://sinty.dev/
[2]: https://itsfoss.com/news/interview-mirko-brombin/
[3]: https://fabricators.ltd/en
[4]: https://itsfoss.com/news/bottles-arm64-support/
[5]: https://vanillaos.org/
[6]: https://usebottles.com/
[7]: https://itsfoss.com/news/lutris-creator-interview/
[8]: https://useraven.org/
[9]: https://itsfoss.com/content/images/2026/10/raven-project.webp
[10]: https://itsfoss.com/content/images/icon/logo-201-69b32cfb-c883-48ee-97a4-716514552196.png
[11]: https://itsfoss.com/content/images/2026/10/msoffice-linux-soda.jpeg
[12]: https://en.wikipedia.org/wiki/Clean-room_design
[13]: https://itsfoss.com/content/images/2026/10/sintyos-screenshot.webp
