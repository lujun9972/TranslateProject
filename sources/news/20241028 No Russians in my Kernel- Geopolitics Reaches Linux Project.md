[#]: subject: "No Russians in my Kernel! Geopolitics Reaches Linux Project"
[#]: via: "https://news.itsfoss.com/russian-linux-maintainers-geopolitics/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

No Russians in my Kernel! Geopolitics Reaches Linux Project
======
So, geopolitics into the mix, and it is a US-thing, or not?
[![][1]][2]

The Linux kernel is one of the biggest open source projects in the entire world. The majority of people consider it as the most influential collaboration with several thousand developers from across the globe.

However, a recent development has raised eyebrows towards the project and its lead maintainer, Linus Torvalds.

### So, What Just Happened?

In a [patch][3], Greg Kroah-Hartman ( _stable kernel maintainer_ ) announced that **more than 10 Russian developers have been removed** from their roles as a maintainer due to ' **various compliance requirements** '.

Here's what the patch mentioned:

> Remove some entries due to various compliance requirements. They can come back in the future if sufficient documentation is provided.

![A screenshot of the patch in the mailing list that removes Russian Linux developers][4]

Considering how short (or vague) the description of the patch is — everyone in the community was caught up in surprise and confusion, and started speculating things.

Until Linus Torvalds commented on the reasoning in the [mailing list][5]. He said:

> Ok, lots of Russian trolls out and about.
>
> It's entirely clear why the change was done, it's not getting
>  reverted, and using multiple random anonymous accounts to try to
>  "grass root" it by Russian troll factories isn't going to change
>  anything.
>
> And FYI for the actual innocent bystanders who aren't troll farm
>  accounts - the "various compliance requirements" are not just a US
>  thing.
>
> If you haven't heard of Russian sanctions yet, you should try to read
>  the news some day. And by "news", I don't mean Russian
>  state-sponsored spam.
>
> As to sending me a revert patch - please use whatever mush you call
>  brains. I'm Finnish. Did you think I'd be *supporting* Russian
>  aggression? Apparently it's not just lack of real news, it's lack of
>  history knowledge too.

### The Linux Foundation Complies to US Sanctions

After a day passed with the comment by Linus Torvalds, **James Bottomley** , another Linux kernel maintainer, clarified:

> We finally got clearance to publish the actual advice:
>
> If your company is on the U.S. OFAC SDN lists, subject to an OFAC
>  sanctions program, or owned/controlled by a company on the list, our
>  ability to collaborate with you will be subject to restrictions, and
>  you cannot be in the MAINTAINERS file.

So, as per their suggestions from the lawyers and other officials in The Linux Foundation, they removed the Russian maintainers until they can submit documentation that they do not work for a Russian state-sponsored organization (and are just innocent volunteers).

For context, there have been recent [US sanctions][6] that affect interactions with Russian companies and technology. Even one of the biggest cybersecurity firms, like Kaspersky, was impacted by it, leading for them to exit the country.

But, let's be real: _if you are from Russia, it is impossible to convince the US that you are not a part of a state-sponsored entity_. If that had been the case, Russian companies could still operate in the US.

Something similar happened with companies like Huawei in the past too.

### Linus Torvald's Response Was Not Entirely OK

Linus Torvalds have made [interesting comments before][7], and it could be taken as something similar.

However, the response to clarifying the situation did not make it any better, as the community still has mixed responses to the whole ordeal as of now.

📋

I am not supporting or taking any sides here. So, I am taking an unbiased view of about what could have been done better, and what could be wrong/right.

To start with, Linus Torvalds mentions that the _compliance requirements are not just a US thing_. And, I would have strongly agreed to that, if he explained that further instead of other thoughts in the same message.

The problematic part, I believe, is that he went on mentioning " **history knowledge** ", " **Russian aggression** ", and things like " **I'm Finnish** ". 🥲

Well, what does he want to say here?

_Does he mean that the compliance requirements are based on historical knowledge? Does this mean that they decided to remove volunteers from which the project benefited for years just because he is Finnish?_

Of course, I am not assuming anything here at all. But, seriously, the message could have been put way better.

### Linux kernel is a US Thing After All?

Now, the community has several questions in mind, some of them are pointed to Linus Torvalds, and some to the Linux kernel project in general.

  * Can someone's political stand make them ineligible to be a Linux maintainer?
  * Are we taking historical knowledge of all the countries in the globe to form a compliance requirement?
  * If the Linux kernel project is not a US-thing, then why is it about U.S. OFAC SDN lists?
  * Does this set a precedent that one of the most impactful open source project could not avoid getting into complex geopolitics bias?



Of course, all these questions are going around the Linux community, with numerous takes to them. Not to forget, you can find plenty of insights on the good-old [Hacker News][8] as well.

_What would be your answer to them? Let me know your thoughts in the comments below!_

* * *

[Get It's FOSS Plus Membership][9]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/russian-linux-maintainers-geopolitics/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://lore.kernel.org/all/2024101835-tiptop-blip-09ed@gregkh/
[4]: https://news.itsfoss.com/content/images/2024/10/russian-linux-devs-delisted.jpg
[5]: https://lore.kernel.org/all/CAHk-=whNGNVnYHHSXUAsWds_MoZ-iEgRMQMxZZ0z-jY4uHT+Gg@mail.gmail.com/#t
[6]: https://ofac.treasury.gov/faqs/added/2024-06-12
[7]: https://news.itsfoss.com/linus-torvalds-woke-communists/
[8]: https://news.ycombinator.com/item?id=41927838
[9]: https://itsfoss.com/#/portal/signup
