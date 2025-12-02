[#]: subject: "Google's New AI Tool Solves a Problem for Every Lazy Developer"
[#]: via: "https://itsfoss.com/news/google-code-wiki/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Google's New AI Tool Solves a Problem for Every Lazy Developer
======

[![Warp Terminal][1]][2]

Back on November 13, Google launched [Code Wiki][3] in public preview. The platform automatically generates and maintains documentation for code repositories using [Gemini][4].

The tool addresses what Google calls **software development's biggest, most expensive bottleneck** , " _reading existing code_ ". In simple terms, Code Wiki keeps documentation constantly updated as the codebase develops.

Instead of static content that becomes outdated, it serves as a living wiki that evolves with every code change. Here's what it brings to the table. 👇

### Code Wiki: Ciao Manual Documentation?

![][5]

Code Wiki **creates interactive documentation** that links high-level explanations directly to specific code files, classes, and functions. Every wiki section is hyperlinked to relevant code files and definitions, merging reading and exploring into a relatively simple workflow.

The platform scans the full codebase and creates fresh documentation after each change. It can automatically generate architecture diagrams, class diagrams, and sequence diagrams that change with the code.

**A Gemini-powered chat agent is also built in** that uses content from the up-to-date wiki as context to answer specific questions about the code repository.

#### An Early Preview

![Code Wiki does a surprisingly good job!][6]

I tested Code Wiki by searching for the [Kubernetes repository][7]. It displayed a detailed page with video, diagrams, and text explanations of the project structure.

After that, I asked the integrated Gemini chat a basic question about what the repository contains. It listed everything cleanly and organized the information in a way that made sense ( _using bullet points and so on_ ).

If you want to check it out yourself, then the [Code Wiki website][8] is already live as a public preview. It should work well for searches of public repositories.

[Code Wiki (public preview)][8]

**Google is also developing a Gemini CLI extension** for private repositories, where developers and teams will be able to run Code Wiki locally on their internal codebases. It is **not live yet** , but you can [join the waitlist][9] to get access when it launches.

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/google-code-wiki/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://developers.googleblog.com/en/introducing-code-wiki-accelerating-your-code-understanding/
[4]: https://gemini.google.com/
[5]: https://itsfoss.com/content/images/2025/12/google-code-wiki-website.png
[6]: https://itsfoss.com/content/images/2025/12/google-code-wiki-website-search.png
[7]: https://codewiki.google/github.com/kubernetes/kubernetes
[8]: https://codewiki.google/
[9]: https://developers.google.com/profile/badges/community/sdlcagents/gca-agents
