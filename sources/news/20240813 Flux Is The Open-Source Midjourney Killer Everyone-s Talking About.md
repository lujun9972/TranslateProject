[#]: subject: "Flux Is The Open-Source Midjourney Killer Everyone's Talking About!"
[#]: via: "https://news.itsfoss.com/flux-image-generator/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Flux Is The Open-Source Midjourney Killer Everyone's Talking About!
======
Flux is an interesting open-source image generator model that you need
to take a look at!
[![][1]][2]

[Generative artificial intelligence][3] (GenAI) models are increasingly becoming better at producing creative works, with 2024 being a year where we are seeing an increase in new GenAI models being shipped out, particularly open-source ones.

Earlier this year, we had Stability AI launching [Stable Audio Open][4], a model for generating high-quality audio data, then we had [AuraFlow][5], a text-to-image generation model that's quite resource intensive.

Now, we have yet another AI-focused outfit, [Black Forest Labs][6], entering the space, equipped with **$31 million in series seed funding**. They have introduced a family of GenAI models, “ **Flux.1** ”, which consist of both closed-source, and open-source options.

### Flux.1: Should Midjourney Be Worried?

![Source: Black Forest Labs][7]

Comprised of a team that has an extensive track record in developing GenAI models like the original [Stable Diffusion][8], Black Forest Labs believes that:

> Widely accessible models not only foster innovation and collaboration within the research community and academia, but also increase transparency, which is essential for trust and broad adoption.

In that line of thought, they have introduced three variants of Flux.1, the first is the **closed-source FLUX.1 [pro]** , which is the most cutting-edge model that Black Forest Labs has to offer currently, it is locked behind a login wall.

The second one is the **open-weight FLUX.1 [dev]** , which is a slightly watered-down version of the _pro_ that can achieve similar levels of performance and prompt adherence capabilities, but in a more efficient avatar.

And, finally, the third one is the **Apache 2.0 Licensed, FLUX.1 [schnell]** , which is the fastest model in the Flux.1 family, that has been fine-tuned for local development and personal use.

Both the _dev_ and _schnell_ models are compatible with [ComfyUI][9], and **make use of a hybrid architecture of multimodal and parallel diffusion transformer blocks** , scaled to 12B parameters.

They have also implemented rotary positional embeddings and parallel attention layers to improve model performance and hardware efficiency.

To back their claim, Black Forest Labs shared **some benchmarking numbers** pitching Flux against popular GenAI models. The first is an ELO score rating of the Flux.1 family:

![Source: Black Forest Labs \(higher is better\)][10]

As you can see, the _pro_ and _dev_ variants are quite close to each other, and the _schnell_ variant is not too far away. They also shared another more detailed radar chart, which features many judging factors such as prompt following, size/aspect variability, typography, etc. Take a look. 👇

![Source: Black Forest Labs][11]

You can quickly try it on HuggingFace using its "Inference API" to get an idea:

![][12]

For a detailed test trial, you need to set it up yourself to compare, considering you have access to Midjourney. I don't have access to it, so I can't compare, but I noticed Decrypt shared some pretty [detailed insights][13] comparing it to Midjourney.

In their testing, comparing Flux.1 with AuraFlow, [Stable Diffusion 3 Medium][14] (SD3 Medium), and Midjourney, they found that on average, Flux.1 was able to deliver good-quality results while adhering to the prompts very well.

![Credit: Decrypt][15]

Even though it required more detailed prompting, they found that results were accurate and realistic. For an alternative to Midjourney, they suggest people to go for the _pro_ variant, and for an alternative to SD3 Medium, the _dev_ and _schnell_ variants.

If the above benchmarks shared by Black Forest Labs and Decrypt are taken into account, then Flux looks like a real performer that can give Midjourney a run for its money.

Plus, it's good to see open-source GenAI models ( _dev_ & _schnell_ ) that perform well. 😃

### 📥 Get Flux.1

You can get any of the three Flux variants from the [official website][6], which has options to try it via [Replicate][16], [fal.ai][17], and [Hugging Face][18].

[Flux.1][6]

You can access the official inference repository on [GitHub][19].

_💬 Are you going to try out Flux.1? If you do, let me know how it went!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/flux-image-generator/

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
[4]: https://news.itsfoss.com/stability-ai-open-audio/
[5]: https://news.itsfoss.com/open-source-image-generator-auraflow/
[6]: https://blackforestlabs.ai/
[7]: https://news.itsfoss.com/content/images/2024/08/Flux_a.jpg
[8]: https://github.com/CompVis/stable-diffusion
[9]: https://github.com/comfyanonymous/ComfyUI
[10]: https://news.itsfoss.com/content/images/2024/08/Flux_b.jpg
[11]: https://news.itsfoss.com/content/images/2024/08/Flux_c.jpg
[12]: https://news.itsfoss.com/content/images/2024/08/flux-demo.png
[13]: https://decrypt.co/242822/flux-ai-image-generator-review-midjourney-sd3-auraflow
[14]: https://stability.ai/news/stable-diffusion-3-medium
[15]: https://news.itsfoss.com/content/images/2024/08/Flux_d.jpg
[16]: https://replicate.com/collections/flux
[17]: https://fal.ai/models/fal-ai/flux
[18]: https://huggingface.co/black-forest-labs
[19]: https://github.com/black-forest-labs/flux
