[#]: subject: "VibeOps Folks Rejoice! Warp Launches Oz for Managing AI Coding Agents in the Cloud"
[#]: via: "https://itsfoss.com/news/warp-launches-oz/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

VibeOps Folks Rejoice! Warp Launches Oz for Managing AI Coding Agents in the Cloud
======

[![Warp Terminal][1]][2]

[Warp][3] has established itself as a known name in modern developer tooling.

The company's terminal application combines traditional command-line functionality with AI-powered features, letting developers write code, debug issues, and manage projects with ease.

Yesterday, [they announced Oz][4], a new service for managing AI coding agents in cloud environments.

🚧

****Warp is not open source software. It's covered here because it is a software available for Linux.****

### Oz by Warp: What to Expect?

At its core, **Oz handles the infrastructure side of running AI coding agents**. Instead of setting up your own systems for sandboxing, monitoring, and coordinating these agents, you get a ready-made platform that does it for you.

It is focused on team collaboration. When you configure an environment ( _essentially a Docker container linked to your Git repositories_ ), that setup becomes available to everyone on your team. Each running agent gets [a URL][5] you can share, letting teammates track progress or take over if needed.

**What can these agents do you ask?** They can write code spanning multiple repositories, push commits, open pull requests, run tests, and make fixes without requiring constant human supervision.

Warp has shared a few examples where they built an automated fraud detector that scans for suspicious Warp account activity three times a day.

In another case, a Warp developer used Oz to port the [mermaid.js][6] JavaScript visualization library to Rust by running multiple agents, each handling a different diagram type, and in another, they created an issue triage app that lets engineers review GitHub issues and dispatch agents to tackle them.

You can control it through various interfaces. There's a command-line tool, a REST API with SDK libraries, a web dashboard, and integration with [Warp's terminal app][7] ( _partner link_ ).

You can start agents manually or schedule them to run at specific times. The platform also works with [Skills][8], which are reusable instruction sets compatible with various coding agent systems.

### Get Started with Oz

[Oz][9] works with any Warp account, **free** or **paid**. Pricing depends on how much AI inference and cloud computing you consume, measured in credits.

This month, both new and existing [subscribers][10] on the _Build_ , _Business_ , and _Max_ tiers receive 1,000 complimentary credits for cloud-hosted agents.

[Oz][9]

Companies wanting to run Oz on their own servers **can opt for self-hosting** , and the web interface at [oz.warp.dev][11] serves as a management console where you can oversee active agents.

* * *

**Suggested Read 📖:** [_I Ditched Claude Code_][12]

![][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/warp-launches-oz/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.warp.dev/
[4]: https://www.warp.dev/blog/oz-orchestration-platform-cloud-agents
[5]: https://docs.warp.dev/agent-platform/cloud-agents/agent-session-sharing
[6]: https://mermaid.js.org/
[7]: https://app.warp.dev/referral/6N3LPK
[8]: https://docs.warp.dev/agent-platform/cloud-agents/skills-as-agents
[9]: https://www.warp.dev/oz
[10]: https://www.warp.dev/pricing
[11]: https://oz.warp.dev/
[12]: https://itsfoss.com/qwen-code-sysadmin-tasks/
[13]: https://itsfoss.com/content/images/icon/android-chrome-512x512-275.png
