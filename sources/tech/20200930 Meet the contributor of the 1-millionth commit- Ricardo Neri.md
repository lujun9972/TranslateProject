[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Meet the contributor of the 1-millionth commit: Ricardo Neri)
[#]: via: (https://www.linux.com/interviews/meet-the-one-millionth-committer-to-linux-ricardo-neri/)
[#]: author: (Swapnil Bhartiya https://www.linux.com/author/swapnil/)

Meet the contributor of the 1-millionth commit: Ricardo Neri
======

_August was a historic month for Linux. The largest open source project on the planet enjoyed its one-millionth code commit. The honor goes to Ricardo Neri, the Linux kernel engineer at Intel. Swapnil Bhartiya, founder, and host at TFiR sat down with Neri on behalf of the Linux Foundation to discuss Neri’s journey and involvement with the Linux kernel community._

A lightly edited transcript of the interview:

**Swapnil Bhartiya**: _Hi, this is Bhartiya, on behalf of the Linux Foundation, and today we have with us Ricardo Neri, Linux Software Engineer at Intel, whose code contribution has become 1 millionth contribution to the Linux kernel._

**Ricardo Neri:** Hi, thank you. Thank you very much.

**Swapnil Bhartiya:** _Ricardo, tell us a little bit about yourself, your journey. When was the first time you came in contact with open source or Linux in general?_

**Ricardo Neri:** That was, I think in 2008. It was a time when the iPhone came out and at the time I used to work in Symbian, but then because the iPhone came out, Symbian died. So I was transferred to a new team, which was working on audio drivers for Linux and the VS. So, maybe by chance I landed on that team and that’s how I started 12 years ago.

**Swapnil Bhartiya:** _You started contributing to the kernel as part of your organization, but you had personal interactions with the kernel community. How was that interaction?_

**Ricardo Neri:** It was very daunting because I had heard that it was really hard to convince maintainers to take your code. And also, I don’t know, maybe intimidating because the people in the community were very smart and also, they had strong opinions for various things. So yeah, maybe I’d say it was intimidating but exciting at the same time.

**Swapnil Bhartiya:** _How have you seen the community itself evolve over time?_

**Ricardo Neri:** Just building on my previous comment I saw at the time that maintainers, they care deeply about the quality of the code that may be drove them to make harsh comments on code from people. And maybe that was a barrier for new people to start contributing. But I have seen a change in the last years like a new code of conduct and rules are agreed upon for people, maybe if they are hesitant or they are not so sure about the quality of their code, just to take it out there and they will not have such a harsh reply as it used to be in the early years when I joined the open source community. I think that is a change that I have observed. Another change that I have observed is more companies are now embracing Open Source. In the early days, the industry was still dominated by closed source software but now I have seen companies building more and more business models around open source software, where the value of the product is not software, but the things that you do with it.

**Swapnil Bhartiya:** _What is interesting is that the contributions to the kernel are coming from all around the globe. You don’t have to be in a specific place to become part of the project. So, what role do you think Linux has played in democratizing software development where you don’t have to prove yourself before you get involved. You send a patch. If the patch is good, they will take your patch. If it’s not good, they will not take it. They don’t have to look at your resume or CV that, hey, have you done any work before or not? So how much role has Linux played in democratizing software development itself?_

**Ricardo Neri:** Yeah, I think it has played a big role because as you said, you don’t have to have a college degree or a computer science degree to start contributing to it because the currency, as you say, is a quality of code. So I have seen, myself, I am not a computer scientist or a software engineer. My background is electrical engineering. So probably I can be a good example of that. I didn’t need to go to college for five years and study computer science to start contributing. Anyone, with the interest to learn and to do something, can start contributing. I am not the only example. There are other people who have a biology degree and they now have become key contributors to Linux.

You can just go to the Linux kernel mailing list, read all the patches, maybe contribute your own reviews. And maybe you start sending your patch. All you need is essentially a workstation with the compiler and the source code. And you can find a bug or an improvement, and you can just do it. You don’t need anything more on that.

**Swapnil Bhartiya:** _Yeah. I fully agree with you. Have you attended any of these Linux Plumbing or any other conferences and events?_

**Ricardo Neri:** Yes, actually I was just attending the Linux Plumbers Conference a few hours ago. I was in the power management micro-conference. Yes, and in previous years I have also been attending Open Source Summit, which used to be LinuxCon.

**Swapnil Bhartiya:** _When you interact with the kernel community over email, it is a bit daunting and you feel intimidated because you don’t know how they will respond to the patch. But when you go and meet these developers in-person, when you sit down for either breakfast or for beer in the evening, you suddenly find that they are as human as we are. So, when you meet them in person, how does the chemistry, the trust, the relationship changes?_

**Ricardo Neri:** Yeah, that is very true. Because, as you said, if you interact with these people only through the mailing list, you can only see words without any context of it. And as you said, this is prone to misinterpretation on both sides. But as equally as you said, when you meet with them, maybe in a virtual event or in person, you see that they are actually friendly. They do care about the quality of the code, but they are approachable and friendly in my experience. And that is also the experience that I have heard from all of my coworkers, who are also new to this community. They have similar feedback as I do.

**Swapnil Bhartiya**: _Do you have any interesting anecdotes to share from any of these events, which are like, “Hey, I met that person or this person or we just sat down. We were debating for months over the patch. We sat down and suddenly we saw the solution.” Any interesting news story that you have to share?_

**Ricardo Neri:** I noticed just in this Plumbers Conference this year, that discussing things over the mailing list can take time because you need to put your comments in written form and then wait for the answer and so forth. And have several iterations of that process. But if you sit down in a room or in a virtual room, the conversation is more fluid and faster. You can arrive at conclusions or to designs or to agreements that would otherwise take maybe weeks for a month to do in the mailing list. So, yeah, I think I have noticed that.

**Swapnil Bhartiya:** _Let’s talk about your contribution. What was this code contribution that historically became a 1 millionth contribution?_

**Ricardo Neri:** That is related to the work that I do with Intel, in which I am part of the CPU enabling team. Whenever Intel comes up with a new feature in the processor, our team is responsible for taking that new feature and making it consumable by the Linux kernel. In this particular case, this is for a new instruction called SERIALIZE, which essentially serialized execution of the code. It puts a landmark in which all the execution before that instruction gets done, before starting to execute the code after that instruction. And that was solving problems that we had in the past. Because for instance, you can achieve the same goal using an instruction called CPUID or return from interrupt. But those instructions have certain side effects and can also have a performance penalty. So this serialize instruction allows you to divide the execution of code, but without having those side effects that you will need to fix up in the software. So it helps to make the software simpler and you have a performance bonus side of it as well.

**Swapnil Bhartiya:** _Do you contribute code in your capacity as an Intel engineer, or do you also contribute some code in your free time as well?_

**Ricardo Neri:** Right now, I am only contributing coding in the capacity as an Intel engineer.

**Swapnil Bhartiya:** _So, this is the reason I ask this question is that in the early days of open source most of the contribution was coming through people working in their spare time, but today a majority of contributors are getting paid by companies to do that work. Working on Open Source is no longer a part-time hobby. How have you seen this change itself, where you get paid to work on open source?_

**Ricardo Neri:** That’s very true. As I was mentioning earlier that now companies have found ways to build business models around open source software. A good example is Red Hat where the software is free, but they build their business around the software and not regard the software as the product; it’s a vehicle to deliver value to their customers. And the same is true for semiconductors companies such as Intel, which are in the business of selling computer chips. But today, you cannot just only sell the chip. You also need to provide a full solution to the customer. And that, of course, includes the software. And that is also true for other companies that were able to build business models around open source software.

In my early days when I was new to Linux, I had many, many colleagues that were in Linux because they believed in it. They believed in the value of open source software. Then they happen to stumble on a job that they were paid to do the things in which they believed. I remember them giving talks in my university about how to build a Linux scanner, how to configure it for your own needs. And they did it for free. During my university days, I remember having installfests in which you could just take your laptop and people would help you to install Linux. People that had a true belief in open source software and were willing to help you for free.

**Swapnil Bhartiya:** _What role has open source played in, as we were talking earlier, that you don’t have to prove yourself, you don’t have to be in a specific region to get involved? So, talk about what role open source has played in creating a level playing field in giving access to underrepresented minorities and give them not only tools but also a voice._

**Ricardo Neri:** I think that, yeah, probably it’s similar to what I was saying at the beginning that in the traditional model in which you have to go to college and then spend four years there and not work and have good grades. You need to have certain opportunities in life to be able to do that, to have the luxury of attending college for five years, and gain a degree. But in software, for instance, you don’t need that. All you need is willingness. Just the willingness of learning and contributing to it. So I think that for underrepresented minority groups, statistically, they have a lesser chance of attending college and getting a degree.

I have also seen companies realizing the fact that you don’t actually need to be a computer scientist to start writing software. That has opened doors for people of different backgrounds and very diverse backgrounds in which you don’t have to be part of a certain career path or school path that can land you a job in this industry. You can just start wherever you want.

There are many efforts in the community. The GNOME Foundation has scholarships to help recruit people from underrepresented groups to start contributing and they get mentoring. Because that is an important point. The software is free and anyone can contribute to it. But if you have a mentor, if you have someone that can help you navigate an open source software community that will help you a lot and it will go a long way to get you established in that community. You can start contributing very simple patches. But over time you have that guidance, you can optimize your time and your effort to make the things that will have an impact, and will maybe someday make you a key contributor to the community.

**Swapnil Bhartiya:** _Thank you._

**Ricardo Neri:** Thank you very much.
--------------------------------------------------------------------------------

via: https://www.linux.com/interviews/meet-the-one-millionth-committer-to-linux-ricardo-neri/

作者：[Swapnil Bhartiya][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.linux.com/author/swapnil/
[b]: https://github.com/lujun9972
