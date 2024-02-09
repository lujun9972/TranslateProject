[#]: subject: "Introducing Fedora Atomic Desktops"
[#]: via: "https://fedoramagazine.org/introducing-fedora-atomic-desktops/"
[#]: author: "Joseph Gayoso https://fedoramagazine.org/author/joseph/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introducing Fedora Atomic Desktops
======

![][1]

Original image by Daimar Stein

We are happy to announce the creation of a new family of Fedora Linux spins: Fedora Atomic Desktops! As Silverblue has grown in popularity, we’ve seen more of our mainline Fedora Linux spins make the jump to offer a version that implements rpm-ostree. It’s reached the point where it can be hard to talk about all of them at the same time. Therefore we’ve introduced a new brand that will serve to simplify how we discuss rpm-ostree and how we name future atomic spins.

Some may note that this is more of a reintroduction. [Project Atomic][2] was started 10 years ago with the development of Atomic Host. As the team stated back then, “the Atomic Host comprises a set of packages from an operating system (…) , pulled together with rpm-ostree to create a filesystem tree that can be deployed, and updated, as an atomic unit.” In 2018 we saw the start of [Fedora Atomic Workstation][3], a desktop client implementation using GNOME, which became [Silverblue a year later][4].

2021 saw the introduction of [Kinoite in Fedora 35][5]. Things seemed quiet for a while until last year, when we saw the release of two more rpm-ostree spins – [Sericea in Fedora 38][6] and [Onyx in Fedora 39][7].

## [][8] Why a New Brand?

That leads to the first reason for needing to adjust our branding: more spins may come. We have four traditional Fedora Linux spins that do not yet have atomic variants. Some of these desktop environments are being experimented with, like Vauxite (Xfce) from within the [Universal Blue custom images][9] project. There are other desktop environments, like Pantheon or the upcoming COSMIC, that we would love to welcome to the community if contributors would like to make that happen. As this group of spins grows, we need to organize them under one umbrella.

Secondly, not having a unified way to talk about our atomic spins makes it harder to talk about them. Have you ever tripped over yourself trying to mention all four atomic spins, or using a shorthand for referring to them (ie Silverblue and friends)? It’s a byproduct of how unwieldy it is to have one spin, Silverblue, represent three others while also meaning something specific, an rpm-ostree implementation of Fedora Linux Workstation. There is also confusion about what aspects of these spins are shared. For example, some folks may be looking for documentation on Kinoite not realizing that an article about Silverblue also applies to their problem. Using so many keywords when you’re looking for information on the one aspect they all share is inefficient.

Thirdly, this nice branding term is also a more accurate way of talking about how rpm-ostree works. Fedora Atomic spins are not actually immutable. There are ways to get around the read-only aspects of the implementation even though it is much harder. The nature of the OS, where updates are only implemented when they successfully build and you can rollback or rebase between core host systems, is better described by atomicity than immutability. Atomic is also how many of the contributors who work on rpm-ostree prefer to talk about it! Rebranding provides an opportunity to change the language surrounding this technology.

## [][10] The Good Part

Fedora Atomic Desktops is made up of four atomic spins:

  * [Fedora Silverblue][11]
  * [Fedora Kinoite][12]
  * [Fedora Sway Atomic][13] (was Fedora Sericea)
  * [Fedora Budgie Atomic][14] (was Fedora Onyx)



Silverblue and Kinoite retained their names because of brand recognition and being around for much longer. There are many articles and videos made with the Silverblue or Kinoite brands, and we don’t want to waste those resources by making them harder to find with a rebrand. Sericea and Onyx are much newer and both SIGs wanted to switch to the new naming convention.

Going forward, new atomic spins will use the ‘Fedora (DE name) Atomic’ format to keep things simple and clear. No more questions about which name refers to what desktop environment. No more mispronunciations. Much more clarity on why these Fedora spins are different from the regular spins.

The new umbrella brand also gives us a new name to put alongside their rpm-ostree cousins! Fedora Atomic Desktops live alongside Fedora CoreOS and Fedora IoT as they all use rpm-ostree in serving different needs.

The [Fedora Atomic Desktops SIG][15], and many in the community, are very excited about this change. We hope it makes talking and learning about this kind of operating system easier.

Click [here][16] to learn more about Fedora Atomic. Let’s start using #FedoraAtomic to streamline our conversations on social media too!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/introducing-fedora-atomic-desktops/

作者：[Joseph Gayoso][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/joseph/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/02/Fedora-Atomic-Desktops-816x345.jpg
[2]: https://projectatomic.io/blog/2014/04/announcing-project-atomic/
[3]: https://projectatomic.io/blog/2018/02/fedora-atomic-workstation/
[4]: https://fedoramagazine.org/what-is-silverblue/
[5]: https://fedoramagazine.org/announcing-fedora-35/
[6]: https://fedoramagazine.org/announcing-fedora-38/
[7]: https://fedoramagazine.org/announcing-fedora-linux-39/
[8]: https://discussion.fedoraproject.org/t/article-proposal-announcing-the-fedora-atomic-rebrand/104502#why-a-new-brand-2
[9]: https://universal-blue.org/
[10]: https://discussion.fedoraproject.org/t/article-proposal-announcing-the-fedora-atomic-rebrand/104502#the-good-part-3
[11]: https://fedoraproject.org/atomic-desktops/silverblue/
[12]: https://fedoraproject.org/atomic-desktops/kinoite/
[13]: https://fedoraproject.org/atomic-desktops/sway/
[14]: https://fedoraproject.org/atomic-desktops/budgie/
[15]: https://fedoraproject.org/wiki/SIGs/AtomicDesktops
[16]: https://fedoraproject.org/atomic-desktops/
