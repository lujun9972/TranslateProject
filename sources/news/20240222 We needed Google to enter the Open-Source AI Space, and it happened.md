[#]: subject: "We needed Google to enter the Open-Source AI Space, and it happened!"
[#]: via: "https://news.itsfoss.com/google-gemma/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

We needed Google to enter the Open-Source AI Space, and it happened!
======
Google's AI model can help you build chatbots, and many other useful
tools. A good addition to the open-source AI industry.
Google is on a roll! After recently [open-sourcing Magika][1], their AI-powered tool for file identification; they have now introduced **Gemma** , a state-of-the-art open-source AI model that shares similar foundations used to create [Gemini][2] family of models.

Let's take a look at it without any further ado.

**Suggested Read** 📖

![][3]

### Gemma: What to Expect?

![][4]

Developed by [Google DeepMind][5] and other teams at Google, the name “Gemma” takes cues from Gemini, and means “ _precious stone_ ” in Latin.

With the launch, Google aims to provide model weights and development tools to further boost progress while also helping with collaboration, and guiding the responsible use of Gemma models.

They have released Gemma in two sizes, **Gemma 2B** with two billion parameters and **Gemma 7B** with seven billion parameters. Both feature pre-trained and instruction-tuned variants, with **the license for using Gemma** said to permit commercial usage and allowing distribution to all organizations.

You can take a look at the [terms][6] for your judgement.🤓

Moving on, Google says that **Gemma is cross-device compatible** and can run on devices such as mobiles, laptops, desktops, IoT, and cloud. To ensure that, they have **made optimizations across many AI hardware platforms** that include [Google Cloud TPU][7]s and NVIDIA GPUs.

For the latter, they have [partnered with NVIDIA][8] for **optimizing Gemma for NVIDIA GPUs** , starting from your run-of-the-mill RTX-equipped AI PCs all the way to the bleeding-edge hardware found in data centers.

That doesn't stop here. NVIDIA will soon add support for GNOME to help you personalize your chatbot as well:

Google also shared some benchmarks comparing it with Meta's [Llama-2][9] model, where it **was able to outpace Llama-2** by some considerable margin in various tasks such as Math, Reasoning, Code, etc.

They also shared a [detailed report][10] on how Gemma sizes up to other AI models.

![Source: Google][11]

One more thing that Google claims for Gemma is that it follows their [AI Principles][12]. By making use of automated techniques to remove any personal information or other kinds of sensitive data, they can provide pre-trained models that are quite safe and reliable in nature.

Google also mentions that they have employed “ _extensive fine-tuning and reinforcement learning from human feedback (RLHF)_ ” to keep Gemma's instruction-tuned models in line with “responsible behaviors”.

To complement Gemma, they also offer a [Responsive Generative AI Toolkit][13] that aims to help developers and researchers focus on building safe and [responsible AI][14] (RAI) applications.

For more details on how Google pulled off Gemma, you can refer to the [announcement blog][15] and the blog on [how they are building][16] open models responsibly.

### Should OpenAI be worried?

Well, I would say yes. We needed a big player like Google to enter the open-source AI space, not because we want Google to dominate, but a big player entering the open-source AI market is most likely to shake things up.

More importantly, the model has close ties with its Gemini AI, making things very intriguing:

And, competition never hurts, right? Companies like OpenAI who pride themselves with their closed source solutions need to understand the importance of the situation we are in right now.

Closing access to things as important as AI is not the way to go, it only serves to alienate a large part of the global AI community who could have taken advantage of its capabilities.

I know AI can be misused, but that can be curtailed if you have the right safeguards in place to deter misuse.

After reading the above; **Do you want to try out Gemma?**

Well, Google is offering free access to Gemma on [Kaggle][17], a free tier on [Colab notebooks][18], and a $300 credit for first-time [Google Cloud][19] users. There is also a way to potentially **get $500,000 in credits** for researchers, who can apply for it using this [Google Form][20].

For other ways to implement Gemma, you can refer to the [official website][21] for more information.

[Gemma][21]

Furthermore, Google has hosted a [PyTorch implementation][22] and a [standalone C++ inference engine][23] for Gemma on their official GitHub page.

_The possibilities with Google opening up a model like this are endless! What do you have in mind with Google's Gemma? Share your thoughts in the comments!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-gemma/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/google-magika-ai/
[2]: https://deepmind.google/technologies/gemini/
[3]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[4]: https://news.itsfoss.com/content/images/2024/02/Gemma_Banner.png
[5]: https://deepmind.google/
[6]: https://ai.google.dev/gemma/terms
[7]: https://cloud.google.com/tpu
[8]: https://blogs.nvidia.com/blog/google-gemma-llm-rtx-ai-pc/
[9]: https://llama.meta.com/
[10]: https://storage.googleapis.com/deepmind-media/gemma/gemma-report.pdf
[11]: https://news.itsfoss.com/content/images/2024/02/Gemma_Benchmark.jpg
[12]: https://ai.google/responsibility/principles/
[13]: https://ai.google.dev/responsible
[14]: https://ai.google/responsibility/responsible-ai-practices/
[15]: https://blog.google/technology/developers/gemma-open-models/
[16]: https://opensource.googleblog.com/2024/02/building-open-models-responsibly-gemini-era.html
[17]: https://www.kaggle.com/models/google/gemma
[18]: https://colab.research.google.com/
[19]: https://cloud.google.com/
[20]: https://docs.google.com/forms/d/e/1FAIpQLSe0grG6mRFW6dNF3Rb1h_YvKqUp2GaXiglZBgA2Os5iTLWlcg/viewform
[21]: https://ai.google.dev/gemma
[22]: https://github.com/google/gemma_pytorch
[23]: https://github.com/google/gemma.cpp
