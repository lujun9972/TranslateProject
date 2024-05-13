[#]: subject: "UK's AI Safety Regulation Tool is Now Open-Source"
[#]: via: "https://news.itsfoss.com/uk-ai-safety-regulation-open-source/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

UK's AI Safety Regulation Tool is Now Open-Source
======
An open-source tool to evaluate AI models. We needed this.
AI has been growing at an astonishing pace; some might revere it, some might not. However, one thing is [now clear][1]: There is a need to keep AI in check.

Which is why we require tools and services built for the job, particularly ones that are open-source, as doing so helps promote transparency.

In recent times, many governments around the world have been [warming up][2] to the concept of open-sourcing important tools and services to benefit the general population.

One such move from the UK Government has caught our attention. With a recent [press release][3], they have open-sourced an AI safety tool, “ **Inspect** ”, for the global community to adopt and utilize it.

### Inspect: What to Expect?

![][4]

Spearheaded by the [AI Safety Institute][5], Inspect is a safety evaluation tool that has been **open-sourced under the** [**MIT License**][6], allowing anyone to copy, modify, merge, publish, distribute, sublicense, and/or sell copies of it.

This tool allows anyone to test specific elements of AI models, such as their ability to reason, their autonomous capabilities, and their core knowledge, to generate a score based on the results that best fit the AI model in question.

If you were wondering how Inspect facilitates that, **the evaluations have three key aspects** : The first are the **Datasets** , which consist of a set of standardized samples for evaluation.

Then, there are the **Solvers** , which carry out the actual evaluation, and finally, the **Scorers** , which take the output from the Solvers and give out the final result.

Moments after the announcement, CEO of [Hugging Face][7], Clément Delangue chimed in on a [Twitter thread][8] by Ian Hogarth, Chair of the AI Safety Institute, saying that:

> This is very cool, thanks for sharing openly! Wonder if there’s a way to integrate with [https://t.co/XZn1kgwGFM][9] to evaluate the million models there or to create a public leaderboard with results of the evals (ex: [https://t.co/ZkSmieEPbs][10]) cc [@IreneSolaiman][11] [@clefourrier][12]
>
> — clem 🤗 (@ClementDelangue) [May 10, 2024][13]

An idea to create a public leaderboard of AI safety evaluation results? That would be pretty useful!

If this were to become a reality, people around the globe could easily look into how different AI models perform in terms of safety evaluations on one of the most popular open AI communities out there.

As things stand now, Inspect also has the opportunity to be an influential tool in how governments handle AI.

### Want to check it out?

You can do that by visiting the [official website][14], where you will find instructions on how you can configure Inspect on the platform of your choice.

[Inspect][14]

If you are interested in the source code, head to its [GitHub][15] repo.

_💬 Would this encourage other countries and organizations to come up with safety evaluation systems for AI models, and probably introduce some kind of certifications for it? Let me know your thoughts on this._

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/uk-ai-safety-regulation-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.technologyreview.com/2023/10/04/1080801/generative-ai-boosting-disinformation-and-propaganda-freedom-house/
[2]: https://news.itsfoss.com/german-state-ditches-microsoft/
[3]: https://www.gov.uk/government/news/ai-safety-institute-releases-new-ai-safety-evaluations-platform
[4]: https://news.itsfoss.com/content/images/2024/05/Inspect_AI_Tool.jpg
[5]: https://www.gov.uk/government/organisations/ai-safety-institute
[6]: https://github.com/UKGovernmentBEIS/inspect_ai/blob/main/LICENSE
[7]: https://huggingface.co/
[8]: https://twitter.com/ClementDelangue/status/1788942198542909542
[9]: https://t.co/XZn1kgwGFM
[10]: https://t.co/ZkSmieEPbs
[11]: https://twitter.com/IreneSolaiman?ref_src=twsrc%5Etfw
[12]: https://twitter.com/clefourrier?ref_src=twsrc%5Etfw
[13]: https://twitter.com/ClementDelangue/status/1788942198542909542?ref_src=twsrc%5Etfw
[14]: https://ukgovernmentbeis.github.io/inspect_ai/
[15]: https://github.com/UKGovernmentBEIS/inspect_ai
