[#]: subject: "A New Open-Source AI Model 'Molmo' Joins The Race to Tackle The Big Tech"
[#]: via: "https://news.itsfoss.com/molmo-open-source-ai-model/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

A New Open-Source AI Model 'Molmo' Joins The Race to Tackle The Big Tech
======
The list of open-source AI models is growing, and that's a good sign!
[![][1]][2]

Recently, the field of AI has been making some significant strides when it comes to following an open-source approach to development. The proprietary crowd wished they had that kind of close-knit community of developers working towards achieving great things.

In the space, [multimodal models][3] have been a major point of interest due to their powerful capabilities, which enable them to process many types of input data, such as text, images, and videos, resulting in richer, more context-aware outputs.

There is always someone or some organization trying to offer a model that is more powerful and tractable than the ones that came before. In this instance, we have a Seattle-based non-profit AI research institute called [Ai2][4] introducing a new family of open-source multimodal models called **Molmo**.

Let's check it out. 😃

### Molmo: Better Than Proprietary Models?

Introduced as **a family of state-of-the-art ( _SOTA_ ) multimodal AI models**, Molmo can be used to develop things like a chatbot, interactive educational platforms, content moderation systems, or even AI agents.

As demonstrated by the video above, you could ask a Molmo-powered agent to tell you a joke, help you navigate a new area, convert ideas from a whiteboard into a digital document, and carry out many such everyday tasks.

Molmo has been trained on a dataset called **PixMo** , which **consists of almost 1 million carefully chosen image text pairs** with two main categories of data. One is the dense captioning data used in multimodal pre-training, and the other is supervised fine-tuning data, used for enabling a wide range of user interactions.

Molmo consists of **four different models** with varying capabilities:

  * **MolmoE-1B**
  * **Molmo-7B-O**
  * **Molmo-7B-D**
  * **Molmo-72B**



In this lineup, the 72B is the flagship model, the 7B-O is the most open one, and the 7B-D is the demo model, with the E-1B being the most efficient one. Here, the B's represent the billion parameter metric.

📋

The Molmo 72B and 7B-D's LLM backbone consists of some closed-source data and code.

To demonstrate the performance of Molmo, **the developers showcased two benchmarks** where the four Molmo models were pitched against other, more popular/proprietary models.

![Molmo evaluated against other options.][5]

On both benchmarks, the Molmo family of models was able to either perform better, or be close in performance to the likes of GPT-4O, Gemini 1.6 Pro, Claude 3.5 Sonnet, Qwen VL2 72B, and Pixtral 12B.

To see how it works, **I tested out the demo Ai2 has provided**. It was running the Molmo-7B-D model, which was only available for [vision][6]-related tasks, and required me to upload an image before it would accept a prompt.

![Pic Source: Pexels][7]

First, I asked it to identify what kind of cat the photo I uploaded had on it. It was able to correctly point out that it was a domestic shorthair cat with tabby markings. It seemed to pull in information from [Wikipedia][8] and some other sources.

![Pic Source: Pexels][9]

Then, I asked Molmo what was happening in a photo filled with people. It gave me a very relevant answer that it was a large-scale event ( _unsure about the church service part_ ) with a stage and many people gathered; it even described what the woman in the focus of the photo was wearing and what she was doing.

But, these were some basic questions I asked Molmo to answer. You can ask it for more advanced things like explaining a graphic, fact-checking a photo to ascertain whether it is fake or not, and more such requests.

#### Want To Try It Out?

There is no requirement to get an API or sign up for a subscription to try Molmo. The developers intend to provide all of their model weights, captioning/fine-tuning data, and source code in the near future for everyone to use.

But, for now, you can check out [the demo][10] for Molmo ( _vision-related tasks only_ ). There is also a [Hugging Face][11] page for those who want to get started with any one of those models on their hardware.

[Molmo (demo)][10]

For more details on Molmo, you can go through the official [blog][12] and [paper][13] to get an overall view of things.

_💬 In these AI-crazed times, which open-source AI model has caught your attention?_

**Suggested Read** 📖

![][14]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/molmo-open-source-ai-model/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Multimodal_learning
[4]: https://allenai.org/
[5]: https://news.itsfoss.com/content/images/2024/09/Molmo_bench.png
[6]: https://en.wikipedia.org/wiki/Computer_vision
[7]: https://news.itsfoss.com/content/images/2024/09/Molmo_test_a.png
[8]: https://en.wikipedia.org/wiki/Tabby_cat
[9]: https://news.itsfoss.com/content/images/2024/09/Molmo_test_b.png
[10]: https://molmo.allenai.org/
[11]: https://huggingface.co/allenai
[12]: https://molmo.allenai.org/blog
[13]: https://molmo.allenai.org/paper.pdf
[14]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
