[#]: subject: "Stability AI Launches Open-Source Model to Generate Audio"
[#]: via: "https://news.itsfoss.com/stability-ai-open-audio/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Stability AI Launches Open-Source Model to Generate Audio
======
A new open-source AI model for audio and sound design. Intriguing!
[![][1]][2]

In recent times, AI-powered tools have managed to break into the audio production space, with many options offering something that sets it apart from its competition.

[Stability AI][3] is one such popular generative AI company that offers a range of AI tools for creating images, audio, and videos with ease. They have recently announced an open-source AI text-to-audio model under the “ **Stable Audio Open** ” moniker, which is geared towards creators.

Let's find out what it can do.

### Stable Audio Open: What to Expect?

![][4]

When implemented, users can generate up to **47 seconds of high-quality audio data from a text prompt**. **** It specializes in creating instrument riffs, ambient sounds, drum beats, Foley recordings and more.

It has been made open-source under the Stability AI Non-Commercial Research Community [License][5] that **prohibits any form of commercial usage** , and users are required to accept Stability AI's [privacy policy][6] too.

Users also have the freedom to fine-tune the model by using their custom audio data, Stability AI gave an interesting example:

> A drummer could fine-tune on samples of their own drum recordings to generate new beats.

As for the model's inner workings, it features **1.21 billion parameters** with three key components, an autoencoder, a T5-based text embedding, and a transformer-based diffusion model (DiT).

For the datasets, it uses **a total of 486492 audio recordings** , of which 472,618 are from [Freesound][7] and 13,874 from the [Free Music Archive][8] (FMA). All of these are licensed under _CC0_ , _CC BY_ , or _CC Sampling+_.

To ensure there was **no copyrighted audio in the datasets** , they sent identified music samples from Freesound to [Audible Magic][9] for checking the presence of copyrighted music.

They did find some, but those were removed before training began. In the case of the FMA subset, they used a different method to check for copyrighted content by performing a metadata search against a [large database][10] of copyrighted music.

Stability AI also pointed out that **Stable Audio Open is different from their commercial product,** [**Stable Audio**][11], which allows subscribers to generate 3 minutes of high-quality tracks with a coherent music structure, and some other advanced capabilities.

So, to wrap things up, I will say this: Stable Audio Open is **a great option for individual users** who are into audio production, or just want to mess around and see what kind of interesting output they can generate.

You can learn more about it by going through the [announcement blog][12].

### Get Stable Audio Open

Stability AI has uploaded the Stable Audio Open model weights on [Hugging Face][13], and are encouraging professionals to explore it as well as provide feedback.

[Stable Audio Open (Hugging Face)][13]

_💬 In a sea of AI models, this one tries to offer something distinctive I think. Have you come across such interesting ones? Let me know!_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/stability-ai-open-audio/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://stability.ai/
[4]: https://news.itsfoss.com/content/images/2024/06/Stable_Audio.jpg
[5]: https://huggingface.co/stabilityai/stable-audio-open-1.0/blob/main/LICENSE
[6]: https://stability.ai/privacy-policy
[7]: https://freesound.org/
[8]: https://freemusicarchive.org/
[9]: https://www.audiblemagic.com/
[10]: https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset
[11]: https://www.stableaudio.com/
[12]: https://stability.ai/news/introducing-stable-audio-open
[13]: https://huggingface.co/stabilityai/stable-audio-open-1.0
