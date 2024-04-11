[#]: subject: "Google Releases New Open-Source Tools to Push AI Development"
[#]: via: "https://news.itsfoss.com/google-open-source-tools-ai/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Google Releases New Open-Source Tools to Push AI Development
======
A good initiative by Google for the advancements of open-source AI.
Recently, Google [unveiled][1] the wide range of advancements they have made in their AI offerings during the [Cloud Next '24][2] event, with the [AI Hypercomputer][3] architecture taking the center stage.

They also showcased a few performance optimized hardware enhancements such as Cloud TPU v5p, NVIDIA H100 Tensor Core GPU-powered A3 Mega VMs, a new block storage service optimized for AI inference, and the introduction of NVIDIA's [Blackwell GPU][4]s in Google Cloud.

But, something else caught my eye in the flurry of announcements that focused on Google's advancements in open software.

### A Rekindled Push by Google towards Open-Source AI?

Just a few months back, we saw Google [open sourcing][5] Magika, their AI-powered tool focused on cybersecurity, and I thought what will they do next?

Well, as it turns out, they have introduced some interesting open-source AI tools that aim to achieve a variety of goals.

We start off with [MaxDiffusion][6], a collection of reference implementation of various diffusion models that was written in [Python][7]/[Jax][8], which is meant to run on Cloud [TPU][9]s and [GPU][10]s. It supports Stable Diffusion 2 base, 2.1, and XL.

While working to achieve that, they also added support for new models in [MaxText][11], their scalable Jax LLM. It now has support for [Gemma][12], [GPT3][13], [Llama2][14], and [Mistral][15].

Then there's a new LLM inference engine, [Jetstream][16], which has been introduced as a throughput, memory optimized engine for LLM inference on XLA devices ( _such as TPUs and GPUs_ ).

And finally, we have [Optimum-TPU][17], that Google has worked to develop in collaboration with [Hugging Face][18], which is a performance optimized package for PyTorch users intended to help with hassle-free training of Hugging Face models on TPUs.

Overall, Google seems to be going in the right direction, and many in the industry could take some pointers from them ( _read OpenAI_ ).

But, it remains to be seen how the development of the above-mentioned tools progresses, and the impact they have on open-source AI.

_💬 What do you think of Google's move? Will it promote a more open-source focused approach in the field of AI?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-open-source-tools-ai/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://www.youtube.com/watch?v=V6DJYGn2SFk
[2]: https://cloud.withgoogle.com/next
[3]: https://cloud.google.com/solutions/ai-hypercomputer
[4]: https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/
[5]: https://news.itsfoss.com/google-magika-ai/
[6]: https://github.com/google/maxdiffusion
[7]: https://www.python.org/
[8]: https://github.com/google/jax
[9]: https://cloud.google.com/tpu
[10]: https://en.wikipedia.org/wiki/Graphics_processing_unit
[11]: https://github.com/google/maxtext
[12]: https://ai.google.dev/gemma
[13]: https://openai.com/blog/gpt-3-apps
[14]: https://llama.meta.com/
[15]: https://mistral.ai/
[16]: https://github.com/google/JetStream
[17]: https://github.com/huggingface/optimum-tpu
[18]: https://huggingface.co/
