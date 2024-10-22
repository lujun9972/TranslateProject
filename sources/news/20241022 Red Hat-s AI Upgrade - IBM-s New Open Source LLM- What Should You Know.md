[#]: subject: "Red Hat's AI Upgrade + IBM's New Open Source LLM: What Should You Know?"
[#]: via: "https://news.itsfoss.com/red-hats-ai-ibm-granite/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Red Hat's AI Upgrade + IBM's New Open Source LLM: What Should You Know?
======
It's time for some AI-focused releases for IBM.
[![][1]][2]

Not a day goes by without me reading about some new developments in the rapidly evolving field of Artificial Intelligence (AI). Be it big multinationals like Meta getting [called out][3] for being misleading, or an AI startup [receiving funding][4] by copying another's work.

So far, this space has been full of surprises and controversies, with such happenings showing no signs of stopping anytime soon. Now, we have two rather interesting pieces of news to report from the house of IBM.

Let's see what they have been up to.

### Upgraded Red Hat Enterprise Linux AI (RHEL AI)

![Image Credits: Red Hat][5]

We kick things off in this two-part article with the RHEL AI 1.2 release, which has arrived just over a month after the [initial release][6] with loads of new improvements that focus on making things easier for AI developers and researchers.

With this release, there is now support for AMD's [Instinct Accelerators][7], including full integration with the [ROCm][8] software stack, and newly added availability on [Azure][9] and [GCP][10].

Similarly, the developers have worked on adding support for Lenovo [ThinkSystem SR675 V3][11] servers, bringing automatic detection of hardware accelerators, and introducing [PyTorch FSDP][12] for enhancing training tasks.

There's also **a new training checkpoint and resume feature** that lets users save their long training runs so that they can return to working on them later, saving time and resources.

**Suggested Read** 📖

![][13]

#### Get RHEL AI 1.2

You can grab the latest RHEL AI release from the [official website][14], with the [announcement blog][15] consisting of all the relevant information on it.

Another thing to note is that **support for RHEL AI 1.1 will be deprecated by the second week of November** , and users are advised to upgrade to the 1.2 release to continue receiving support.

[RHEL AI 1.2][14]

### Introduction Of Granite 3.0

![Image: IBM][16]

Next up on the agenda is IBM's newly released family of open source LLMs, [Granite 3.0][17].

Acting as the third iteration for the popular AI model family, Granite 3.0 is touted by IBM to be better than LLMs provided by other organizations on both academic and industrial grounds.

Released under the [Apache 2.0][18] license, **there are a total of ten models under the Granite 3.0 family** , which cover many use cases.

For **general purpose or language tasks** , there are models like the Granite 3.0 8B Instruct, Granite 3.0 2B Instruct, Granite 3.0 8B Base, and Granite 3.0 2B Base.

For **running models on CPU-based systems or for low latency applications** , there are _Mixture Of Experts_ ([MoE][19]) models such as the Granite 3.0 3B-A800M Instruct, Granite 3.0 1B-A400M Instruct, Granite 3.0 3B-A800M Base, and Granite 3.0 1B-A400M Base.

And, finally, there are **two guardrail/safety-focused models** , the Granite Guardian 3.0 8B and Granite Guardian 3.0 2B. These are used to detect and prevent harmful content/inputs, and can be deployed alongside any open or proprietary AI models.

All of these join an ever-expanding list of [open source LLMs][20] that can be used freely for both research and commercial use cases.

If you are searching for the numbers behind IBM's claims, here are some benchmarks for the _Base_ and _Instruct_ models shared by them. 👇

![Source: IBM][21]

According to IBM, **the data used to train these models has been gathered from various curated sources** that include things like unstructured natural language text, code data, a collection of synthetic datasets, and many publicly available datasets with permissive licenses.

#### Get Granite 3.0

If you are interested in deploying any one of the Granite 3.0 models, then you can get started by visiting the [Hugging Face][22] collections page for this family of models.

Alternatively, you can source the models from the project's [GitHub][23] repo. If you just want a quick hands-on, then IBM has also provided a live demo of the Granite 3.0 8B Instruct model on the [Granite playground][24].

[Granite 3.0 (Hugging Face)][22]

If you are keen on learning more about the Granite 3.0 family of models, then you can go through the extensive [technical paper][25] and [announcement blog][26].

_💬 Looking forward to these new releases? Let me know your thoughts in the comments below!_

**Suggested Read** 📖

![][27]

* * *

[Get It's FOSS Plus Membership][28]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/red-hats-ai-ibm-granite/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/osi-meta-ai/
[4]: https://news.itsfoss.com/pearai-controversy/
[5]: https://news.itsfoss.com/content/images/2024/10/RHEL_AI_Illustration.png
[6]: https://news.itsfoss.com/red-hat-gen-ai/
[7]: https://www.amd.com/en/products/accelerators/instinct.html
[8]: https://www.amd.com/en/products/software/rocm.html
[9]: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux_ai/1.2/html/installing/installing_azure#installing_azure
[10]: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux_ai/1.2/html/installing/installing_gcp
[11]: https://lenovopress.lenovo.com/lp1611.pdf
[12]: https://pytorch.org/tutorials/intermediate/FSDP_tutorial.html
[13]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[14]: https://developers.redhat.com/products/rhel-ai/overview
[15]: https://www.redhat.com/en/blog/whats-new-red-hat-enterprise-linux-ai-12
[16]: https://news.itsfoss.com/content/images/2024/10/Granite_Banner.jpg
[17]: https://www.ibm.com/new/ibm-granite-3-0-open-state-of-the-art-enterprise-models
[18]: https://www.apache.org/licenses/LICENSE-2.0
[19]: https://huggingface.co/blog/moe
[20]: https://itsfoss.com/open-source-llms/
[21]: https://news.itsfoss.com/content/images/2024/10/Granite_3.0_Base_Model_Bench.jpg
[22]: https://huggingface.co/collections/ibm-granite/granite-30-models-66fdb59bbb54785c3512114f
[23]: https://github.com/ibm-granite/granite-3.0-language-models/
[24]: https://www.ibm.com/granite/playground/
[25]: https://github.com/ibm-granite/granite-3.0-language-models/blob/main/paper.pdf
[26]: https://newsroom.ibm.com/2024-10-21-ibm-introduces-granite-3-0-high-performing-ai-models-built-for-business
[27]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[28]: https://itsfoss.com/#/portal/signup
