[#]: subject: "We Got an Open Source AI Video Model Before GTA 6"
[#]: via: "https://news.itsfoss.com/open-source-ai-video-lightricks/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

We Got an Open Source AI Video Model Before GTA 6
======
More AI is boring, but open source? We are curious!
[![][1]][2]

2024 is just weeks from ending, and a surge in new open source generative AI launches highlights the state of the rapidly advancing field, and growing interest among the general populace.

Be it the increasingly advanced large language models, image generators, or video generators. Organizations across the world are pushing each other to redefine the boundaries of what's possible.

We recently saw IBM introduce an AI-powered document extraction tool called [Docling][3]. Not long after that, a group of researchers from Beijing announced a novel open source model called [OmniGen][4] that makes image editing via prompts effortless.

Now, we have yet another organization pushing the frontier of open source AI who have launched a new model for videos called LTX Video (LTXV).

### LTXV: What To Expect?

0:00

/0:16

1×

Credit: [Lightricks][5]/[VentureBeat][6]

Introduced by [Lightricks][5], a tech company out of Israel, LTXV is an open source [DiT-based][7] ( _diffusion transformer_ ) AI model that **can be used to generate high-grade videos quickly** , depending on the hardware used.

LTXV is distributed under [Apache License 2.0][8] and **has been trained on large-scale datasets of videos**. There are many things to like about it:

  * Can be used for long-form video production.
  * Is optimized for GPU and TPU-equipped systems.
  * Ensures coherence between frames, preventing issues like flickering.



The **video shown above is a prime example of what LXTV can do**. The text prompt was to create a [high-fashion][9] scene. LXTV generated a video with a businesswoman in the financial district of a city going about her business while soothing audio was being played in the background.

That video was generated in just four seconds on [NVIDIA H100][10] GPUs. The developers have ensured that this runs well on consumer-grade hardware too, offering up swift video generations.

Of course, your mileage may vary depending on the hardware configuration of your system. But you can still give it a shot.

#### Want To Check It Out?

For more details on LTXV, you can head to the [official website][11], where you will find relevant information on the model. If you are looking to deploy it on your system, then the [documentation][12] and [Hugging Face][13] pages for Lightricks should be your next stops.

The [GitHub][14] repo is also handy for those looking to dive in deeper, and there are live demos of the model on [Hugging Face Playground][15] and [fal.ai][16].

[LTX Video (Hugging Face)][13]

At the time of writing, **the technical documentation for LTXV was still not out** , but you can keep an eye out on the documentation page linked above.

**Via:** [VentureBeat][6]

**Suggested Read** 📖

![][17]

* * *

[Get It's FOSS Plus Membership][18]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/open-source-ai-video-lightricks/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/docling-ibm-open-source-gen-ai/
[4]: https://news.itsfoss.com/omnigen-open-source/
[5]: https://www.lightricks.com/
[6]: https://venturebeat.com/ai/exclusive-lightricks-bets-on-open-source-ai-video-to-challenge-big-tech/
[7]: https://arxiv.org/abs/2212.09748
[8]: https://www.apache.org/licenses/LICENSE-2.0
[9]: https://en.wikipedia.org/wiki/Haute_couture
[10]: https://www.nvidia.com/en-us/data-center/h100/
[11]: https://www.lightricks.com/ltxv
[12]: https://www.lightricks.com/ltxv-documentation
[13]: https://huggingface.co/Lightricks/LTX-Video
[14]: https://github.com/Lightricks/LTX-Video
[15]: https://huggingface.co/spaces/Lightricks/LTX-Video-Playground
[16]: https://fal.ai/models/fal-ai/ltx-video
[17]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[18]: https://itsfoss.com/#/portal/signup
