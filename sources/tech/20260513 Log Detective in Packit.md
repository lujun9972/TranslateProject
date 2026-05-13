[#]: subject: "Log Detective in Packit"
[#]: via: "https://fedoramagazine.org/log-detective-in-packit/"
[#]: author: "Jiri Podivin https://fedoramagazine.org/author/jpodivin/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Log Detective in Packit
======

![][1]

[Log Detective][2] analysis is coming to Packit.

Starting this month, Log Detective will provide an analysis of failed Packit-triggered scratch Koji builds on dist-git pull-requests.

Packit will keep on doing what it’s good at, integrating upstream projects with downstream distributions.
Only now, it will have Log Detective to explain package build failures.

In [Copr][3], the user can already request a Log Detective analysis by clicking on the “Ask AI” button.

![][4]

In Packit, a build failure triggers a request for analysis automatically and presents the result in the [dashboard][5], when it is ready.

The analysis does not require any additional setup. It is not necessary to choose which logs to send or to tune a prompt. Our service handles everything for you.

### Log parsing and analysis derivation

Starting with version [4.0][6], the Log Detective works as an agent written in the [BeeAI Framew][7][ork][7].

The agent receives all logs and other build artifacts, as a part of the analysis request. Log Detective then uses a variety of tools, mostly based around the Drain template mining algorithm, to extract potentially useful snippets from the files. These snippets represent only a small fraction of the original log file size.

By extracting and using snippets, instead of entire original logs, we save tokens and limit the time needed for the analysis to finish. We also limit the amount of useless information in the model context.

This approach allows us to use even relatively small models and still get good results.

### Communication architecture

Packit service handles failed Koji builds in the same way as before.
However, Packit now also requests an analysis of a failed build by sending a request to the Log Detective
interface server. The interface server, designed as a lightweight containerized service, handles all communication between the Log Detective and Packit services.

Packit sends a request for analysis to the Log Detective server. When the results are ready, the interface server posts them on the [Fedora Messaging bus][8] where Packit collects them.

### Result presentation

An analysis from Log Detective consists of a statement of what, if anything, went wrong during the package build, and optionally, a suggestion of a solution. In the current configuration, Log Detective does not use sources other than build logs for the analysis.

Packit dashboard links Log Detective results to the PR that has triggered them.

![][9]

### Purpose and limitations

Since Log Detective uses a general purpose model, and lacks access to other information sources, it is obviously limited. Therefore it is not, and cannot be a substitute for years of experience in package maintenance in the Fedora ecosystem. If you have been building packages for a while, it probably has little to offer you.

It is intended to help those who don’t have such experience, and hopefully make their job a little easier.

### Future development

Log Detective is under active development and we are looking into ways to improve it.
We are continually revising the Log Detective system prompt to improve response quality, while periodically comparing the overall performance against a selection of annotated build logs, which we are collecting on our [website][10].

We also plan to reuse a select part of this dataset to create an additional information source for Log Detective, to further improve the quality of the analysis we provide.

In the future, we also plan to provide an analysis for Copr builds handled by Packit.

We are also considering ways of improving the presentation of an analysis, such as expanding the Packit dashboard results to include not only the final analysis, but also extracted log snippets that were used to derive it.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/log-detective-in-packit/

作者：[Jiri Podivin][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/jpodivin/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/05/Log_detective-816x345.jpg
[2]: https://github.com/fedora-copr/logdetective
[3]: https://fedora-copr.github.io/posts/logdetective-explain
[4]: https://fedoramagazine.org/wp-content/uploads/2026/05/image-2.png
[5]: https://dashboard.packit.dev/
[6]: https://github.com/fedora-copr/logdetective/releases/tag/v4.0.0
[7]: https://github.com/i-am-bee/beeai-framework
[8]: https://apps.fedoraproject.org/datagrepper/v2/search?topic=org.fedoraproject.prod.logdetective.analysis
[9]: https://fedoramagazine.org/wp-content/uploads/2026/05/image-3-1024x185.png
[10]: https://www.logdetective.com/
