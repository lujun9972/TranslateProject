[#]: subject: "This Open-Source AI Image Generator Plans to Take on Stable Diffusion 3"
[#]: via: "https://news.itsfoss.com/open-source-image-generator-auraflow/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Open-Source AI Image Generator Plans to Take on Stable Diffusion 3
======
Finally, a truly open-source Stable Diffusion contender!
[![][1]][2]

The ability of [generative AI][3] ( _GenAI_ ) to create images has been evolving at a rapid pace thanks to the many innovations in the field, ushering in a new era of creative spontaneity.

Unfortunately, **that has come at the cost of many people's hard work being plagiarized without their knowledge** , OpenAI knows [what][4] I am talking about.

In any case, the use and development of such tech has not slowed down, with one of the most talked-about GenAI models in recent times being [Stable Diffusion 3][5].

However, its licensing terms didn't sit well with many, and [rightly so][6], highlight the need for a capable, more permissive model.

That is where a U.S.-based AI outfit, [fal.ai][7]'s challenger, “ **AuraFlow** ” has stepped in.

🚧

This is an under-development piece of software that's not recommended for production use, but is still good enough for casual use.

### AuraFlow: A New Contender Enters The Ring

![Various images generated using AuraFlow][8]

Born out of a need for a _state-of-the-art_ open-source model, fal collaborated with developers and researchers to introduce an initial AuraFlow 0.1 release, which has been made available under the [Apache 2.0 License][9].

When implemented, users can perform text-to-image generation tasks with AuraFlow, provided they have the necessary hardware to do so, as it's **quite resource intensive**.

fal shared that during four weeks of intensive compute time, **AuraFlow was taken through exhaustive training** , with pretraining of images in various sizes such as _256×256_ , _512×512_ , and _1024×1024_ , followed up by aspect ratio fine-tuning, and a few other tweaks.

All that resulted in a [GenEval][10] score of 0.63~0.67 during pretraining for the final model, with the score going up to 0.703 after the use of a prompt-enhancement pipeline.

Moving on from the numbers, fal has provided an [online demo][11] for users to check out AuraFlow in action.

![][12]

**When I ran a prompt for generating an image** with a happy Tux looking into the horizon, I was presented with the above result, which was creepy as heck.

Like, why does it have only one limb? Where are its flippers, its face? Mind you, I didn't touch any of the advanced settings, this was the result with the default settings, running on fal's NVIDIA [A100 GPU][13]-equipped machine.

I do have a hunch that its face is actually pointing towards the horizon, but it's one limb facing in the wrong direction is enough to terrify people.

Anyhow, it's in a very early phase of development, so I can let it slide.

There are also **plans to introduce a less resource intensive model** for running on GPUs with lower VRAM and compute power, fal says to expect this very soon.

Wrapping up, if you are eager to learn how they were able to pull off AuraFlow, I highly suggest you give the [announcement blog][14] a read.

Moreover, with [Decrypt][15]'s original coverage, they have gone in deep, with very comprehensive benchmarks pitching it against [Stable Diffusion 3 Medium][16], if you are curious to know.

### Get AuraFlow

As is the standard for most open AI models, the model weights for AuraFlow are available on [Hugging Face][17], where you will find all the relevant details and files.

_It has seen over 30,000 downloads already._ 😯

[AuraFlow (Hugging Face)][17]

Those looking to build Comfy workflows with this model can get started with the latest version of [ComfyUI][18].

If you are interested in being part of its community, then you can join fal's official [Discord server][19].

💬 _If you have played around with AuraFlow, do let me know how your experience was!_

**Suggested Read** 📖

![][20]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/open-source-image-generator-auraflow/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/Generative_artificial_intelligence
[4]: https://www.theguardian.com/technology/2024/apr/30/us-newspaper-openai-lawsuit
[5]: https://stability.ai/news/stable-diffusion-3
[6]: https://decrypt.co/235866/sd3-license-stability-ai-civit-ai-ban
[7]: https://fal.ai/
[8]: https://news.itsfoss.com/content/images/2024/07/AuraFlow_a.jpg
[9]: https://www.apache.org/licenses/LICENSE-2.0
[10]: https://github.com/djghosh13/geneval
[11]: https://fal.ai/models/fal-ai/aura-flow/playground
[12]: https://news.itsfoss.com/content/images/2024/07/AuraFlow_b.jpg
[13]: https://www.nvidia.com/en-us/data-center/a100/
[14]: https://blog.fal.ai/auraflow/
[15]: https://decrypt.co/240883/auraflow-comparison-sd3-fal-ai-new-model
[16]: https://stability.ai/news/stable-diffusion-3-medium
[17]: https://huggingface.co/fal/AuraFlow
[18]: https://github.com/comfyanonymous/ComfyUI
[19]: https://discord.gg/fal-ai
[20]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
