[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (8 ways not to do open source)
[#]: via: (https://opensource.com/article/20/10/how-not-do-open-source)
[#]: author: (Mike Bursell https://opensource.com/users/mikecamel)

8 ways not to do open source
======
Avoid these mistakes when creating an open source project.
![x sign ][1]

A while ago, I published my wildly popular[1][2] article [_How not to make a cup of tea_][3]. Casting around for something to write here, it occurred to me that I might write about something that I believe is _almost_ as important as world peace, the forward march of progress, and brotherly/sisterly love: open source projects. There are so many guides out there around how to create an open source project that it's become almost too easy to start a new, successful, community-supported one. I think it's time to redress the balance and give you some clues about how _not_ to do it.

### Throw it over the wall

You know how it is: you're a large corporation, you've had a team of developers working on a project for several years now, and you're very happy with it. It's quite expensive to maintain and improve the code, but luckily, it's occurred to you that other people might want to use it—or bits of it. And recently, some of your customers have complained that it's difficult to get improvements and new features, and partners complain that your APIs are obscure, ill-defined, and subject to undocumented change.

Then you hit on a brilliant idea: why not open source it and tell them their worries are over? All you need to do is take the existing code, create a GitHub or GitLab[2][4] project (preferably under a Game of Thrones-themed username that happens to belong to one of your developers), make a public repository, upload all of the code, and put out a press release announcing: a) the availability of your project; and b) what a great open source citizen you are.

People will be falling over themselves to contribute to your project, and you'll suddenly have hundreds of developers basically working for you for free, providing new features and bug fixes!

### Keep a tight grip on the project

There's a danger, however, when you make your project open source, that other people will think that they have a right to make changes to it. The way it's _supposed_ to work is that your product manager comes up with a bunch of new features that need implementing and posts them as issues on the repository. Your lucky new contributors then get to write code to satisfy the new features, you get to test them, and then, if they're OK, you can accept them into the project! Free development! Sometimes, if you're lucky, customers or partners (the only two parties of any importance in this process, apart from you) will raise issues on the project repository, which, when appropriately subjected to your standard waterfall development process and vetted by the appropriate product managers, can be accepted as "approved" issues and earmarked for inclusion into the project.

There's a danger that, as you've made the project code open source, some people might see this as an excuse to write irrelevant features and fixes for bugs that none of your customers have noticed (and therefore, you can safely assume, don't care about). Clearly, in this case, you should reject and close any issues related to such features or fixes, and reject (or just ignore) any related patches.

Worse yet, you'll sometimes find developers[3][5] complaining about how you run the project. They may "fork" the project, making their own version. If they do this, beware of setting your legal department on them. There's a possibility that, as your project is open source, they might be able to argue that they have a _right_ to create a new version. Much better is to set your public relations department on them, rubbishing the new project, launching _ad hominem_[4][6] attacks on them, and showing everybody that you hold the moral high ground.

### Embrace diversity (in licensing)

There may be some in your organisation who say that an open source project doesn't need a licence.[5][7] Do not listen to their siren song: they are wrong. What your open source project needs is _lots_ of licences! Let your developers choose their favourite for each file they touch, or, even better, let the project manager choose. The [Open Source Initiative][8] maintains a useful list, but consider this just a starting point: why not liberally sprinkle different licences through your project? Diversity, we keep hearing, is good, so why not apply it to your open source project code?

### Avoid documentation

Some people suggest that documentation can be useful for open source projects, and they are right. What few of them seem to understand is that their expectations for the type of documentation are likely to be skewed by their previous experience. You, on the other hand, have a wealth of internal project documentation and external product marketing material that you accrued before deciding to make your project open source: this is great news. All you need to do is to create a docs folder and copy all of the PDF files there. Don't forget to update them whenever you do a new product version!

### Avoid tooling

All you need is code (and docs—see above). Your internal developers have carefully constructed and maintained build environments, and they should, therefore, have no problems building and testing any parts of the project. Much of this tooling, being internal, could be considered proprietary, and the details must therefore be kept confidential. Any truly useful contributors will be able to work out everything they need for themselves and shouldn't need any help, so providing any information about how actually to build the code in the repository is basically redundant: don't bother.

An alternative for more "expert" organisations is to provide build environments that allow contributors to batch builds to see if they compile or not (whilst avoiding giving them access to the tooling themselves, obviously). While this can work, beware providing too much in the way of output for the developer/tester, as this might expose confidential information. Generally, a "build successful" or "build failed" message should be sufficient.

### Avoid diagrams

Despite what some people [think][9], diagrams are dangerous. They can give away too much information about your underlying assumptions for the project (and, therefore, the product you're selling that is based on it), and _serious_ developers should be able to divine all they need from the 1,500 source files that you've deposited in the repository anyway.

A few "marketiture" diagrams from earlier iterations of the project may be acceptable, but only if they are somewhat outdated and don't provide any real insight into the existing structure of the code.

### Keep quiet

Sometimes, contributors—or those hoping to become contributors, should you smile upon their requests—will ask questions. In the old days, these questions tended to be sent to email lists[6][10] where they could be safely ignored (unless they were from an important customer). More recently, there are other channels that developers expect to use to contact members of the project team, such as issues or chat.

It's important that you remember that you have no responsibility or duty to these external contributors: they are supposed to be helping _you_. What's more, your internal developers will be too busy writing code to answer the sort of uninformed queries that are likely to be raised (and as for so-called "[vulnerability disclosures][11]," you can just fix those in your internal version of the product, or at least reassure your customers that you have). Given that most open source projects will come with an issue database and possibly even a chat channel, what should you do?

The answer is simple: fall back to email. Insist that the only channel that is guaranteed attention[7][12] is email. Don't make the mistake of failing to create an email address to which people can send queries; contributors are much more likely to forget that they're expecting an answer to an email if they get a generic auto-response ("Thanks for your email; a member of the team should get back to you shortly") than if they receive a bounce message. Oh, and close any issues that people create without your permission for "failing to follow project process."[8][13]

### Post huge commits

Nobody[9][14] wants to have to keep track of lots of tiny changes to code (or, worse, documentation—see above), or have contributors picking holes in it. There's a useful way to avoid much of this, however, which is to train your developers to post only large commits to the open source project. You need to ensure that your internal developers understand that code should only be posted to the external repository when the project team (or, more specifically, the product team) deems it ready. Don't be tempted to use the open source repository as your version-control system: You should have perfectly good processes internally, and, with a bit of automation, you can set them up to copy batches of updates to the external repository on a regular basis.[10][15]

* * *

  1. Well, lots of you read it, so I'm assuming you like it.
  2. Other public repositories may be available, but you won't have heard of them, so why should you care?
  3. The canonical term for such people is "whingers": they are invariably "experts." According to them (and their 20 years of security experience, etc., etc.).
  4. Or _ad mulierem_—please don't be sexist in your attacks.
  5. Or license, depending on your spelling choice.
  6. Where they existed—a wise organisation could carefully avoid creating them.
  7. "Attention" can include a "delete all" filter.
  8. You don't actually need to define what the process is anywhere, obviously.
  9. In your product organisation, at least.
  10. Note that "regular" does not equate to "frequent." Aim for a cadence of once every month or two.



_This article was originally published on [Alice, Eve, and Bob][16] and is reprinted with the author's permission._

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/how-not-do-open-source

作者：[Mike Bursell][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/mikecamel
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/x_stop_terminate_program_kill.jpg?itok=9rM8i9x8 (x sign )
[2]: tmp.VFy944zzyQ#1
[3]: https://aliceevebob.com/2019/09/17/how-not-to-make-a-cup-of-tea/
[4]: tmp.VFy944zzyQ#2
[5]: tmp.VFy944zzyQ#3
[6]: tmp.VFy944zzyQ#4
[7]: tmp.VFy944zzyQ#5
[8]: https://opensource.org/licenses
[9]: https://opensource.com/article/20/5/diagrams-documentation
[10]: tmp.VFy944zzyQ#6
[11]: https://aliceevebob.com/2020/05/26/security-disclosure-or-vulnerability-management/
[12]: tmp.VFy944zzyQ#7
[13]: tmp.VFy944zzyQ#8
[14]: tmp.VFy944zzyQ#9
[15]: tmp.VFy944zzyQ#10
[16]: https://aliceevebob.com/2020/06/23/8-tips-on-how-do-open-source-badly/
