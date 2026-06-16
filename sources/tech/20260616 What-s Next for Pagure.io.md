[#]: subject: "What’s Next for Pagure.io?!"
[#]: via: "https://fedoramagazine.org/whats-next-for-pagure-io/"
[#]: author: "Tomáš Hrčka https://fedoramagazine.org/author/humaton/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What’s Next for Pagure.io?!
======

![][1]

At the Flock 2026 Birds of a Feather session, poetically named **FFFwF** (or, for us lazy people, _Forging Fedora’s Future with Forgejo_ ), we discussed the current state of our migration effort to the new forge. I asked the obligatory question: _Who still has things on pagure.io?!_

A few brave contributors raised their hands, some with an uneasy look in their eyes. Miro swiftly pointed out that everybody is affected by one particular repository; looking at you, `fedora-scm-requests`. Luckily, the RelEng folks have it in their sights. Sure, there are a few other repos lying around the old faithful, but it is time for the Fedora Project to move on and embrace the Forge.

Our new home is currently running on the LTS branch in v15.0.2. We are going to stick with it in production, and our next LTS upgrade will be to v19.

### What is going to happen next?

Pagure itself as a project is hosted on pagure.io, and that service is going to be decommissioned at the end of July 2026. What does that mean for you? Well, that depends on when you are reading this.

If you just came back from Flock 2026 and you still have active repositories on pagure.io, here is what you need to do:

  * Check out the existing organizations in the Forge. If your project fits into any of the existing ones, ask its owners for a migration.


  * If it doesn’t fit, open a ticket with the forge team, and we will help you decide the best path forward.



Some of us have commits in projects that point back to pagure.io. Don’t worry, we are not going to break your links, for foreseeable future. We will explore options for implementing redirects so your historical links successfully point to their current locations.

The best way to handle the transition after your move, right now, is to inform your users about your new home. Add a **BIG BOLD ANNOUNCEMENT** to your README, close all open issues, and create a single pinned issue with your migration announcement.

**Note: Do not expect to be able to log in to pagure.io after July 2026.**

### Wait… and what about `dist-git`?

Well, that is the next target in the scopes of the Forge team. As I showed you in the room, we have 11 Features that define the transition. The biggest task at hand is a bit more sneaky. We are missing multiple enhancements to the upstream project that will require a lot of coordination and Go code. So, if you find yourself in possession of spare cycles and a particular need to help us make it better and faster, Forgejo is waiting for you!

A road-map with all the tasks for the move will land in the Forge soon. (See resource list below.)

### Important Links & Resources

  * **Check out the new home:** Browse existing [organizations][2] on the new Fedora Forge
  * **Want to write some Go?** Contribute to the [upstream Forgejo][3] project.
  * **Track our progress:** Migration roadmap will be posted [here][4] soon



**AI Disclaimer:** Grammar and formatting were done with the help of robots; all the original brain-farts are my own.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/whats-next-for-pagure-io/

作者：[Tomáš Hrčka][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/humaton/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/06/forge_new_header-816x345.jpeg
[2]: https://forge.fedoraproject.org/explore/organizations
[3]: https://codeberg.org/forgejo/forgejo/issues?q=&type=all&sort=relevance&labels=201023%2c222666&state=open&milestone=0&project=0&assignee=0&poster=0
[4]: https://forge.fedoraproject.org/forge/forge/issues
