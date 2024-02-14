[#]: subject: "This Open-Source AI Tech Generates Personalised Digital Avatars"
[#]: via: "https://news.itsfoss.com/instantid/"
[#]: author: "Rishabh Moharir https://news.itsfoss.com/author/rishabh/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Open-Source AI Tech Generates Personalised Digital Avatars
======
A pretty cool open-source AI project.
The rapid emergence of new AI tools, particularly in the consumer-focused market, has brought Gen AI (or generative artificial intelligence) to the forefront.

If you've noticed, most of these tools are open-source. This enables anyone to experiment with models, improve them via contributions, and even develop newer models based on existing published works.

Of course, openness drives healthy collaboration and innovation in the field of AI.

One such example is [Stable Diffusion][1] which is primarily a text-to-image AI model that allows users to create stunning images with a prompt. Since its public release back in 2022, several open-source projects and models have been created based on Stable Diffusion for various use cases.

Here, let me highlight one such interesting open-source project: **InstantID**.

### InstantID: A Cool AI Tool for Digital Avatars

InstantID lets users generate customized images in different styles using a person's face as a reference.

In other words, it lets you create a digital avatar of yourself.

It tries to preserve the facial identity of the reference face when generating the image, while keeping the style of the image in mind.

![InstantID Examples, source: https://github.com/InstantID/InstantID][2]

📋

Typically, an AI model needs to be trained on a dataset of a person's face to achieve high likeability. However, this approach takes up extra computational resources and time and is not feasible for everyone.

InstantID intends to do away with this approach and produce quality images using a single person's face and a prompt for customizability as inputs. If you're not happy with the results, InstantID also allows users to upload additional reference images to enhance facial identity.

For a more controlled generation like assigning a particular human pose, InstantID also supports [ControlNet][3] which is another cool open-source model that tweaks generation by adding extra conditions in Stable Diffusion.

Sure, there could have been other similar attempts like InstantID. But, I found this particularly intriguing.

![Comparison with previous works, source: https://github.com/InstantID/InstantID][4]

For technically inclined readers, you can refer to the [official research paper][5] for in-depth information on how the model works.

[InstantID Project Page][6]

### How to Try It Out?

You can check out the official Huggingface demo to experiment with the model.

[Demo on HuggingFace][7]

If you're familiar with Python and Stable Diffusion, the project's [GitHub repository][8] includes documentation to guide you to implement and test the project yourself.

💬 _Open-source AI tools like InstantID open up exciting possibilities for various use cases. But at the same time, such tools can be misused for malicious purposes, as seen in recent news. What's your take?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/instantid/

作者：[Rishabh Moharir][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/rishabh/
[b]: https://github.com/lujun9972
[1]: https://en.wikipedia.org/wiki/Stable_Diffusion
[2]: https://github.com/InstantID/InstantID/raw/main/assets/0.png
[3]: https://github.com/lllyasviel/ControlNet
[4]: https://instantid.github.io/static/documents/compare-a.png
[5]: https://arxiv.org/abs/2401.07519
[6]: https://instantid.github.io/
[7]: https://huggingface.co/spaces/InstantX/InstantID
[8]: https://github.com/InstantID/InstantID
