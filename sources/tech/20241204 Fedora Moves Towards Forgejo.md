[#]: subject: "Fedora Moves Towards Forgejo"
[#]: via: "https://fedoramagazine.org/fedora-moves-towards-forgejo-a-unified-decision/"
[#]: author: "Matthew MillerAkashdeep Dhar https://fedoramagazine.org/author/mattdm/https://fedoramagazine.org/author/t0xic0der/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora Moves Towards Forgejo
======

![][1]

Photo by [Jonathan Kemper][2] on [Unsplash][3]

The decision to move to Forgejo as the new git forge has been made. There are numerous factors involved in this decision and this article will discuss them, present some background on the process, and invite one more chance for feedback before the formal Fedora Council vote.

### Gist of the situation

We’ve known for a long time that the Fedora Project needs a new [git forge][4] solution. The software we currently use, Pagure, has served us well. Sadly, it never took off in the wider world. So we had to maintain the Pagure git forge ourselves and use it to build the Fedora Linux releases at the same time. A few years ago, we considered GitLab, and had a lot of discussion… which ultimately didn’t go anywhere. Out of that we got a clear message. It’s important that this crucial part of our infrastructure be free and open source software.

At the Fedora Council’s annual face-to-face meeting in February we discussed a large list of options. By the end of the day, we crossed off all but two: [GitLab Community Edition][5] and [Forgejo][6]. We also determined that no hosting providers can meet our unique needs; we’ll have to self-host. We then asked the [Advanced Reconnaissance Crew][7] (ARC, a subteam of Fedora Infrastructure) to investigate these in more detail. They were particularly asked to look at 1) any show-stopper missing features and 2) maintenance effort and cost.

ARC has presented their initial results (about which Akashdeep goes into detail below). The quick summary: either option could work, and both have some gaps we’ll need to fill. Several things tilt the scales one direction. GitLab CE is “open core”, with some features only in the non-open-source “premium” version (including some we really want). This is both an immediate practical concern and a long-term one. Open core software tends, over time, to get less open (no matter how good the initial intentions). In addition, the Infrastructure team is more comfortable with the Forgejo codebase and the language it is written in.

So, what’s next? The Council, currently, has a clear preference for Forgejo. This is a big decision and we don’t want it to feel rushed. Therefore, we’re opening this up one last time to everyone’s comments. After two weeks, we’ll take our formal vote — and then get on with the work!

– Matthew

### How we got here

The earliest attempts to move over to an alternative git forge solution started as early as [January 2020][8]. At that time the development work on Pagure became increasingly inconsistent. This resulted in the maintenance costs soaring due to the unmaintained state of the development. Shortly after that, in [March 2020][9], the decision was made to move over to GitLab after evaluating [over 300 user stories][10] and a SaaS offering was planned for the Fedora Project. While the development of new features for Pagure slowed down, an exemplary group of contributors stepped up to ensure that the current state of Pagure was maintained well. After a detailed AMA session with folks from GitLab in [September 2020][11], a SaaS offering was announced for Fedora Project in [October 2021][12], and a bunch of sub-projects and SIGs started moving their workflows over to the [Fedora Project namespace][13] of GitLab.

While the case looked mostly positive for the sub-projects and SIGs like [Fedora Websites and Apps team][14], there were concerns regarding the scalability in terms of contributor counts and suitability in terms of the Dist Git purposes. This was specifically brought up in the [Fedora Council issue ticket][15] discussion and realized at a much later stage in function which led to the [initiative request of Dist Git to GitLab][16] from Fedora Infrastructure in February 2023. Fedora Infrastructure worked on an [application that helps migrate repositories][17] from Pagure to GitLab through November 2023. By December 2023, the [evaluation of Git Forges][18] had become a priority for Fedora Council and a concurrent investigation that explored [migrating Dist Git functionality][19] in a forge-agnostic way to another git forge was completed by March 2024.

### The Investigation, a.k.a The Prequel!

After the [Git Forge alternatives][20] were shortlisted during the Fedora Council F2F Hackfest in February 2024, the Community Linux Engineering (CLE) team (previously called the Community Platform Engineering (CPE) team) were tasked with the investigation. The [Advanced Reconnaissance Crew][7] (ARC) sub-team was to report the positives and negatives of each git forge option, while working with various stakeholders across the Fedora Project community to capture the projects requirements for our dist-git. The initiative was led by Tomas Hckra and Akashdeep Dhar, and Akashdeep also represented the Fedora Councils needs to the team. They began collecting these requirements in the form of [user stories][21] in March 2024 to use as the baseline of the investigation. The initiative was then joined by David Kirwan and Ryan Lerch who were able to deploy an instance of both Forgejo and GitLab CE in the CommuniShift app, and the team began validating that each user story worked in each git forge instance. These findings were reported in the [official documentation][22].

The availability of these instances really helped onboard more contributors into the user stories validation efforts. This meant that the focus was not only on the packagers and release engineering workflow but also covered those associated with subprojects/SIGs like Design, Documentation, Accessibility, Websites & Apps, Mindshare etc.

Throughout the investigation, conversations on [Fedora Discussion][23] and on the [Fedora Project mailing list][24] were happening, making sure Fedoras use cases were being addressed, and the ARC team had [presentations during the Fedora Linux 40 Release Party][25] as well as Tomas Hrcka’s [talk during the Flock To Fedora 2024][25] to give this huge change maximum exposure.

Once the investigation completed, Fedora Council was slated to make the final decision on which forge the project would choose to migrate to.

### And now the work _really_ begins

Like any other initiative, or large project or piece of work, the plan is never perfect, and this particular effort was quite literally years in the making. The next step for all the parties involved is to have some retrospectives to reflect on how this all went. There are plenty of learnings to be had for sure, and we hope to have a better understanding of how to drive such major decisions in a much better way.

With the investigation on the git forge solutions now wrapped up, we plan to work with Community Linux Engineering (CLE) to direct the [migration of Dist Git assets][19] and the [conversion of team workflows][26] to the deployed Forgejo Server instance once the decision is formally (and finally!) announced in the coming weeks by Fedora Council.

Pagure Dist Git is connected with a variety of ecosystem services. These include, among others:

  * [Bodhi][27]
  * [Fedora CI][28]
  * [COPR][29]
  * [Fedpkg][30]
  * [The New Hotness][31]
  * [Fedora Notifications][32]
  * [Pagure][33]
  * [Toddlers][34]
  * [Fedora Messaging][35]
  * [Monitor Gating][36]
  * [Release Engineering Scripts][37]
  * [Fedora Packagers][38]
  * [Packit][39]



Please do not hesitate to reach out to the Fedora Infrastructure team to provide your support.

Utmost attempts will be made to ensure that the git forge replacement has feature parity with the systems it is attempting to replace (i.e. Pagure Dist Git and Bugzilla). However, it is important to understand that this is a complex undertaking. Most workflows related to various subteams, subprojects and SIGs are likely to remain the same. In some cases we might have to re-imagine the workflows to fit the change (best case scenario). In other cases it may be necessary to deprecate workflows that are no longer reasonably supportable (worst case scenario).

Folks are requested to have an understanding of the [user stories][40] that were taken into consideration while comparing the git forge alternatives. Please collaborate with the Fedora Infrastructure team to integrate your specific workflows into the Dist Git Replacement platform.

We look forward to bringing this change to Fedora collaboratively with you in 2025!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-moves-towards-forgejo-a-unified-decision/

作者：[Matthew MillerAkashdeep Dhar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mattdm/https://fedoramagazine.org/author/t0xic0der/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/12/Forgejo-816x345.jpg
[2]: https://unsplash.com/@jupp?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/brown-wooden-wheel-on-brown-wooden-table-fsOKJe2eA0k?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://en.wikipedia.org/wiki/Forge_(software)
[5]: https://about.gitlab.com/install/?version=ce
[6]: https://forgejo.org/
[7]: https://fedora-arc.readthedocs.io/en/latest/
[8]: https://communityblog.fedoraproject.org/git-forge-requirements/
[9]: https://communityblog.fedoraproject.org/making-a-git-forge-decision/
[10]: https://hackmd.io/@My419-DISUGgo4gcmO1D6A/HJB74lcL8
[11]: https://communityblog.fedoraproject.org/gitlab-ama-follow-up/
[12]: https://communityblog.fedoraproject.org/gitlab-available-for-fedora/
[13]: https://gitlab.com/fedora
[14]: https://about.gitlab.com/blog/2023/07/11/building-new-fedora-project-website-with-gitlab/?ref=gridhead.net
[15]: https://pagure.io/Fedora-Council/tickets/issue/292
[16]: https://pagure.io/cpe/initiatives-proposal/issue/26
[17]: https://communityblog.fedoraproject.org/pagure-exporter-now-available/
[18]: https://pagure.io/Fedora-Council/tickets/issue/473
[19]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/index.html
[20]: https://communityblog.fedoraproject.org/2024-git-forge-evaluation/
[21]: https://pagure.io/fedora-infra/arc/issue/164
[22]: https://fedora-arc.readthedocs.io/en/latest/dist-git-comparison/index.html
[23]: https://discussion.fedoraproject.org/t/inviting-testers-for-git-forge-usecases/129016
[24]: https://lists.fedoraproject.org/archives/list/devel@lists.fedoraproject.org/message/7RT3PMMDEZTT6WHUUWUCQPMC5Q6C3YZQ/
[25]: https://youtu.be/KiG9H7t7EHk?si=AIZU9fdR4DxGFBf8
[26]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/solution.html
[27]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/bodhi.html
[28]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/ci.html
[29]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/copr.html
[30]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/fedpkg.html
[31]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/hotness.html
[32]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/notifications.html
[33]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/pagure.html
[34]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/toddlers.html
[35]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/messaging.html
[36]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/monitorgating.html
[37]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/releng.html
[38]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/packagers.html
[39]: https://fedora-arc.readthedocs.io/en/latest/dist-git-move/packit.html
[40]: https://fedora-arc.readthedocs.io/en/latest/dist-git-comparison/stories.html
