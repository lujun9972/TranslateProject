[#]: subject: "This is AI Magic! OmniGen Open Source Model Can Edit Images With Prompts"
[#]: via: "https://news.itsfoss.com/omnigen-open-source/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This is AI Magic! OmniGen Open Source Model Can Edit Images With Prompts
======
AI image editing is getting better. What do you think?
[![][1]][2]

AI-powered image generation is very useful for creating visual content from text prompts, where it usually combines computer vision and natural language processing to produce outputs based on a user's description of the image.

Even though it takes center stage when we mention AI-generated content, there is another aspect that has been consistently growing alongside, and that's AI-powered image editing.

Many popular editors have already integrated such functionality, with others contemplating adding it. Now, a new open source AI model called **OmniGen** has been put forward that focuses on image editing via prompt ( _among other things_ ).

Let's take a peek. 😃

### OmniGen: Quick AI-Powered Image Edits

![OmniGen in action on Replicate.][3]

Developed by a group of nine researchers at the [Beijing Academy of Artificial Intelligence][4], OmniGen is an [MIT][5]-licensed **unified image generation model** that can be used to create images by taking in multi-modal prompts.

I gave it a quick try, and here's how it went:

OmniGen was able to take in an existing image, and comfortably follow what the prompt said about removing the woman's earrings, and replacing the mug near her with a clear glass filled with sparkling iced cola.

Moreover, it is capable of performing conventional image generation tasks, subject-driven generation, image-conditioned generation, identity-preserving generation, and various other tasks.

The **key highlight of this model** is that it doesn't require the implementation of additional techniques like [ControlNet][6], [IP-Adapter][7], and Reference-Net, while also doing away with the need to perform preprocessing steps like face detection, pose estimation, cropping, etc.

Its creators believe that:

> The future image generation paradigm should be more simple and flexible, that is, generating various images directly through arbitrarily multi-modal instructions without the need for additional plugins and operations, similar to how GPT works in language generation.

What you have seen so far is the first stable version of OmniGen. The developers have stated that **they are continually improving it** , and hope that it can act as an inspiration for other universal image-generation models.

#### Want To Check It Out?

You can dive deeper into OmniGen's technical aspects by going through its [technical paper][8], with the source code being hosted over at [GitHub][9].

The developers have provided a limited-use [live demo][10] via Hugging Face, where you will also find the [model card][11] for OmniGen. You can also use [ComfyUI][12] to run it too.

[OmniGen][9]

**Via:** [Decrypt][13]

**Suggested Read** 📖

![][14]

* * *

[Get It's FOSS Plus Membership][15]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/omnigen-open-source/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/content/images/2024/11/OmniGen_Output_Replicate.jpg
[4]: https://www.baai.ac.cn/english.html
[5]: https://opensource.org/license/mit
[6]: https://huggingface.co/docs/diffusers/en/using-diffusers/controlnet
[7]: https://github.com/tencent-ailab/IP-Adapter
[8]: https://arxiv.org/pdf/2409.11340
[9]: https://github.com/VectorSpaceLab/OmniGen
[10]: https://huggingface.co/spaces/Shitao/OmniGen
[11]: https://huggingface.co/Shitao/OmniGen-v1
[12]: https://www.comfy.org/
[13]: https://decrypt.co/290075/omnigen-open-source-ai-model-images-art
[14]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[15]: https://itsfoss.com/#/portal/signup
