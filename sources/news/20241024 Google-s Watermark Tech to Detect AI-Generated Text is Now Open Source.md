[#]: subject: "Google's Watermark Tech to Detect AI-Generated Text is Now Open Source"
[#]: via: "https://news.itsfoss.com/google-synthid-text-open-source/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Google's Watermark Tech to Detect AI-Generated Text is Now Open Source
======
It's time we all get to detect AI-generated text easily, at least, most
of it.
[![][1]][2]

Just as AI has risen to great heights, so has the occurrence of misinformation and plagiarism of people's work. Some of the biggest names in the space have been taken to court over this, and things are only getting worse.

To remedy such problems with AI models, Google introduced a tool called [SynthID][3] back in 2023, which can be used to embed digital watermarks directly into AI-generated images, videos, text, and videos.

Now, it turns out they have open sourced the text watermarking component of it.

### SynthID Text Goes Open: What To Expect?

![An excerpt from the announcement blog.][4]

Meant as a solution for identifying AI-generated text, SynthID Text can run alongside a LLM without affecting its performance, accuracy, or generation quality. It makes use of a [pseudorandom function][5] called the _g-function_ that runs in the background, adding a watermark that can't be recognized by a human.

Currently, it is being used by [Gemini][6] and Google's various other enterprise-focused online chatbots, and now, it can be implemented on other AI models and large language models (LLMs) too.

In [a conversation][7] with MIT Technology Review, [Pushmeet Kohli][8], VP of Research at Google DeepMind, added that:

> Now, other [generative] AI developers will be able to use this technology to help them detect whether text outputs have come from their own [large language models], making it easier for more developers to build AI responsibly.

Before you go on to implement SynthID Text in your AI model, keep in mind that **it has a few limitations**.

For starters, even though it can safeguard against cropped text and modified words, the watermarking is less effective with factual responses. Similarly, it is ineffective when the AI-generated text is completely rewritten or translated into a different language.

#### Want To Check It Out?

If you want to dive into the technical details of SynthID Text, the [technical paper][9] is worth a read. On the other hand, if you just want an overview, then the [official documentation][10] and the announcement blog on [Hugging Face][11] are what you are looking for.

Google has also made a [reference implementation][12] and [a demo][13] of SynthID Text available.

[SynthID Text][10]

**Suggested Read** 📖

![][14]

* * *

[Get It's FOSS Plus Membership][15]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-synthid-text-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://deepmind.google/technologies/synthid/
[4]: https://news.itsfoss.com/content/images/2024/10/SynthID_Text_Blog.png
[5]: https://en.wikipedia.org/wiki/Pseudorandom_function_family
[6]: https://gemini.google.com/
[7]: https://www.technologyreview.com/2024/10/23/1106105/google-deepmind-is-making-its-ai-text-watermark-open-source/
[8]: https://www.linkedin.com/in/pushmeet-kohli-4838994/
[9]: https://www.nature.com/articles/s41586-024-08025-4
[10]: https://ai.google.dev/responsible/docs/safeguards/synthid
[11]: https://huggingface.co/blog/synthid-text
[12]: https://github.com/google-deepmind/synthid-text
[13]: https://huggingface.co/spaces/google/synthid-text
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://itsfoss.com/#/portal/signup
