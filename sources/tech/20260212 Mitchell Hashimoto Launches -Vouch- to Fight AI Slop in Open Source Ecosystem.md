[#]: subject: "Mitchell Hashimoto Launches 'Vouch' to Fight AI Slop in Open Source Ecosystem"
[#]: via: "https://itsfoss.com/news/mitchell-hashimoto-vouch/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Mitchell Hashimoto Launches 'Vouch' to Fight AI Slop in Open Source Ecosystem
======

[![Warp Terminal][1]][2]

[Mitchell Hashimoto][3] from Vagrant, Terraform, HashiCorp, and [Ghostty][4] fame has introduced [Vouch][5], new trust management system for open source projects.

With this in place, maintainers **can implement a trust-based system** where contributors must be vouched before submitting code to designated areas.

The system also allows blocking bad actors entirely through a denouncement feature and maintains a simple list of approved and blocked contributors for easy management ( _stored as a_ [_.td_][6] _file_ ).

Thanks to this, **vouch lists of other projects can be aggregated to create a network** where open source projects can check if someone is already trusted elsewhere. This means contributors don't need to get vouched separately for every project they want to contribute to.

Vouch also has a [GitHub][7] integration that can check pull requests and auto-close ones from unvouched users and lets maintainers vouch or denounce people by commenting on issues, and a CLI that can be used to check user status, add people to the vouch list, or denounce them.

The [FAQ][8] for Vouch also clarifies how the vouching itself would work:

> There's no reason for getting vouched to be difficult. The primary thing Vouch prevents is low-effort drive-by contributions. For my projects (even this one), you can get vouched by simply introducing yourself in an issue and describing how you'd like to contribute.

> Basically: introduce yourself like any normal human social environment, and you're vouched. If you abuse your privilege in the group, then you'll be denounced.
>
> Ultimately, Vouch does not impose any policy. Policy is up to downstream projects that integrate Vouch.

It also clarifies that someone adept in the skills of manipulation and gaslighting ( _the technical term is social engineering_ ) won't be able to trick their way into being able to merge a pull request into a repo, as reviewers would have to do that.

Only people with write access to the project can vouch for or denounce contributors. This also means that **vouched users can't vouch for others** , maintaining a clear hierarchy where maintainers keep full control over who gets access.

### AI Slop Begone?

By now, you must already know that the plague of [AI slop][9] has reached the shores of open source and maintainers are drowning in it. These AI-generated contributions look okay at first glance, but reviewing and rejecting them takes more time than just writing proper code would have.

Mitchell says this is a recent problem. Before AI tools took off, **you actually had to understand code to submit a pull request**. That barrier kept out most of the garbage.

Let me give you an example, [cURL recently killed its bug bounty program][10] because they got flooded with AI slop. In one week, they got 7 HackerOne reports in just 16 hours.

The maintainers had enough and decided that removing cash rewards was the only way to stop the flood.

Vouch tackles the same issue. Instead of reviewing endless junk submissions, maintainers can just build a list of trusted people and only deal with contributions from them.

Altogether, this is an excellent project.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/mitchell-hashimoto-vouch/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://mitchellh.com/
[4]: https://itsfoss.com/ghostty-terminal-features/
[5]: https://github.com/mitchellh/vouch
[6]: https://github.com/mitchellh/vouch/blob/main/VOUCHED.example.td
[7]: https://github.com/mitchellh/vouch/tree/main/action
[8]: https://github.com/mitchellh/vouch/blob/main/FAQ.md
[9]: https://en.wikipedia.org/wiki/AI_slop
[10]: https://itsfoss.com/news/curl-closes-bug-bounty-program/
