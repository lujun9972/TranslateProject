[#]: subject: "Microsoft’s AI Coding Agent Testing Tool Has Been Open-Sourced"
[#]: via: "https://itsfoss.com/news/microsoft-scope-self-hosted-agent-testing/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microsoft’s AI Coding Agent Testing Tool Has Been Open-Sourced
======

[![Warp Terminal][1]][2]

Coding agents now decide which SDK to use and which tools to call, though something that works smoothly for a human developer can still leave an agent stumbling.

Microsoft built [Scope][3] to find those failures. It runs the same task through different agents and scores what each one produces. The code for it is provided under **the MIT license**.

They are calling it the field Developer Agent Experience, or _DevAx_ , though its 'scope' is to evaluate existing coding agents.

### How does it work?

![][4]

You give Scope a task, a starting codebase if needed, and an agent setup. It then drives existing agents such as _GitHub Copilot_ and _Claude Code_ through that task.

Success is defined through criteria that form a dependency graph. One check can gate another. A simple case is asking an agent for a Node.js server and checking for a `GET` /health route that returns JSON.

An LLM-based _Judge_ service scores each run against those criteria. Keep in mind that it can make mistakes, and Microsoft says **important conclusions still warrant human review**.

Each run keeps live logs, generated files, workspace snapshots, and tool calls. A failed criterion can be traced back through those steps. Versioned profiles save the agent, model, skills, MCP servers, and extensions.

You can also swap one, rerun the same task, and compare. Results vary from attempt to attempt, and repeating a task helps separate a recurring problem from a one-off issue.

Then there are the configurable personas that let you set the viewpoint and tone of the simulated user. You can review results in the web portal or use the _CLI_ and _REST API_ to feed them into scripts and pipelines.

### Where would you use it?

Docs teams can watch for an instruction that agents miss run after run. Fix the page, then run the scenario again.

SDK maintainers can check whether an agent picks their SDK in the first place. They can also test whether new sample code or a skill changes that.

For CLIs and MCP servers, the traces show where an agent stalled. That can point to a vague tool description or an error message that leaves the agent guessing.

### What's the catch?

You can't just sign up and start testing. Scope has no hosted version, so you run it yourself.

A local setup requires these components: Docker with Compose v2, Node 22, pnpm, mkcert, and the GitHub CLI. Microsoft has a [local development guide][5] for guiding you through that.

The default worker also calls for an active GitHub Copilot entitlement, and the Judge needs credentials for a model provider. Teams that want a shared deployment can [deploy it on Kubernetes][6] with the Helm chart.

Scope's code is on [GitHub][7]. Though if you were looking to contribute, you will most likely need to agree to the Microsoft Contributor License Agreement.

* * *

**Suggested Read 📖:** You can [use AI to get rid of ads][8] on your smart TV.

![][9]

Enjoyed this update? Support independent Linux news coverage

It's FOSS has been helping people use Linux for the past 14 years. Help us stay independent from big tech. Become a Plus member, enjoy ad-free reading and get 5 eBooks.

Plus yearly

Ad-free, FREE ebooks

[Join yearly][10]

Best value

Plus lifetime

Pay once, Enjoy forever

[Go lifetime][11]

Buy us a coffee

Any amount, no commitment

[Support on Ko-fi][12]

Skip the AI slop and SEO spam in your Google results

Tell Google you prefer It's FOSS, and it will show our Linux news and tutorials, created by experienced Linux users, more often when you search. It takes just a click.

[Set as preferred source][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/microsoft-scope-self-hosted-agent-testing/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://microsoft.github.io/scope/
[4]: https://itsfoss.com/content/images/2026/10/scope-demo.png
[5]: https://microsoft.github.io/scope/getting-started/local-development/
[6]: https://microsoft.github.io/scope/self-hosting/overview/
[7]: https://github.com/microsoft/scope
[8]: https://itsfoss.com/news/debloat-smart-tv/
[9]: https://itsfoss.com/content/images/icon/android-chrome-512x512-eaef5626-ecd3-4689-a7ac-22469190e52c.png
[10]: https://itsfoss.com/#/portal/signup
[11]: https://itsfoss.com/lifetime-membership/
[12]: https://ko-fi.com/itsfoss
[13]: https://www.google.com/preferences/source?q=itsfoss.com
