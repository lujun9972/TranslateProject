[#]: subject: "Open Source Project LLVM Says Yes to AI-Generated Code, But Not Without Conditions"
[#]: via: "https://itsfoss.com/news/llvm-ai-policy/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Open Source Project LLVM Says Yes to AI-Generated Code, But Not Without Conditions
======

[![Warp Terminal][1]][2]

Following the lead of other open source projects, [LLVM][3] has now implemented their new " _human in the loop_ " AI policy that [governs the use of AI tools][4] in contributions to the project.

With this in place, **contributors can use whatever AI tools they like** to help with their contributions, but they are fully accountable for what they submit. They also have to mention which tool they used, either in the pull request description, commit message, or wherever authorship is listed.

Additionally, contributors must be able to answer questions about their work during review, and should be confident that what they are submitting is worth a maintainer's time to go over.

LLVM's new AI policy also clarifies that:

> Contributors are expected to be transparent and label contributions that contain substantial amounts of tool-generated content. Our policy on labelling is intended to facilitate reviews, and not to track which parts of LLVM are generated.

For the uninitiated, LLVM is **a collection of compiler and toolchain components** that serves as the foundation for many programming languages and development tools. It is used by major projects like **Clang** ( _the C/C++ compiler_ ), **Rust** , **Swift** , and even in [Linux kernel][5] development.

### The Community Was Involved

Just like any open source project worth its salt, the new policy was drafted taking community feedback into account.

One of the earlier calls for this came from a LLVM community member [who pointed out][6] that there was a mismatch in LLVM's AI-generated code handling policy, their code of conduct, and what was happening in reality.

This person cited a specific pull request that had attracted [a lot of attention on Hacker News][7], where a contributor had openly admitted to using AI but not disclosing it in the actual pull request itself.

[Reid Kleckner][8], an LLVM maintainer, took the lead in addressing these concerns. First, he posted [a draft policy][9] to gather community feedback. His initial proposal borrowed heavily from [Fedora's AI policy][10] and included specific limits, like **restricting newcomers to 150 lines of non-test code**.

A few months later, [he was back][11] after gathering extensive feedback from community meetings and forum discussions. Reid mentioned that **he had moved away from the Fedora-based draft** , with the new version focusing on making the requirements more explicit and actionable.

Instead of vague clauses like " _owning the contribution_ ," the updated policy spelled out clearly that contributors must review their work and be prepared to answer questions about it.

The updated AI Tool Use Policy is now live on LLVM's [documentation website][12], complete with guidelines for handling violations and examples of acceptable AI-assisted contributions.

Via: [Phoronix][13]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/llvm-ai-policy/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://llvm.org/
[4]: https://github.com/llvm/llvm-project/commit/18695b27d565
[5]: https://www.kernel.org/
[6]: https://discourse.llvm.org/t/our-ai-policy-vs-code-of-conduct-and-vs-reality/88300
[7]: https://news.ycombinator.com/item?id=45244295#:~:text=%7C%20next%20%5B%E2%80%93%5D-,I%27ve%20been%20using%20AI%20to%20contribute%20to%20LLVM%2C%20which%20has%20a%20liberal%20policy.,-The%20code%20is
[8]: https://discourse.llvm.org/u/rnk/summary
[9]: https://discourse.llvm.org/t/rfc-llvm-ai-tool-policy-start-small-no-slop/88476
[10]: https://itsfoss.com/news/fedora-ai-guidelines/
[11]: https://discourse.llvm.org/t/rfc-llvm-ai-tool-policy-human-in-the-loop/89159
[12]: https://llvm.org/docs/AIToolPolicy.html
[13]: https://www.phoronix.com/news/LLVM-Human-In-The-Loop
