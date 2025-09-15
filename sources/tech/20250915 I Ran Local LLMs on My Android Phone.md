[#]: subject: "I Ran Local LLMs on My Android Phone"
[#]: via: "https://itsfoss.com/android-on-device-ai/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Ran Local LLMs on My Android Phone
======

[![Warp Terminal][1]][2]

Like it or not, AI is here to stay. For those who are concerned about data privacy, there are several [local AI options][3] available. Tools like Ollama and LM Studio makes things easier.

Now those options are for the desktop user and require significant computing power.

What if you want to use the local AI on your smartphone? Sure, one way would be to [deploy Ollama with a web GUI][4] on your server and access it from your phone.

But there is another way and that is to use an application that lets you install and use [LLMs][5] (or should I say SLMs, Small Language Models) on your phone directly instead of relying on your local AI server on another computer.

Allow me to share my experience with experimenting with LLMs on a phone.

📋

Smartphones these days have powerful processors and some even have dedicated AI processors on board. Snapdragon 8 Gen 3, Apple’s A17 Pro, and Google Tensor G4 are some of them. Yet, the models that can be run on a phone are often vastly different than the ones you use on a proper desktop or server.

Here's what you'll need:

  * An app that allows you to download the language models and interact with them.
  * Suitable LLMs that have been specifically created for running on mobile devices.



### Apps for running LLMs locally on a smartphone

After researching, I decided to explore following applications for this purpose. Let me share their features and details.

#### 1\. MLC Chat

[**MLC Chat**][6] supports top models like Llama 3.2, Gemma 2, phi 3.5 and Qwen 2.5 offering offline chat, translation, and multimodal tasks through a sleek interface. Its plug-and-play setup with pre-configured models, NPU optimization (e.g., Snapdragon 8 Gen 2+), and beginner-friendly features make it a good choice for on-device AI.

You can download the MLC Chat APK from [their GitHub release page][7].

[Android is looking to forbid sideloading of APK files][8]. I don't know what would happen then, but you can use APK files for now.

Put the APK file on your Android device, go into Files and tap the APK file to begin installation. Enable “Install from Unknown Sources” in your device settings if prompted. Follow on-screen instructions to complete the installation.

![Enable APK installation][9]

Once installed, open the MLC Chat app, select a model from the list, like Phi-2, [Gemma 2B][10], Llama-3 8B, [Mistral][11] 7B. Tap the download icon to install the model. I recommend opting for smaller models like Phi-2. Models are downloaded on first use and cached locally for offline use.

![Click on the download button to download a model][12]

Tap the Chat icon next to the downloaded model. Start typing prompts to interact with the LLM offline. Use the reset icon to start a new conversation if needed.

![][13]

#### 2\. SmolChat (Android)

[**SmolChat**][14] is an open-source Android app that runs any [GGUF-format model][15] (like Llama 3.2, Gemma 3n, or TinyLlama) directly on your device, offering a clean, ChatGPT-like interface for fully offline chatting, summarization, rewriting, and more.

Install SmolChat from [Google's Play Store][16]. Open the app, choose a GGUF model from the app’s model list or manually download one from Hugging Face. If manually downloading, place the model file in the app’s designated storage directory (check app settings for the path).

![][17]

#### 3\. Google AI Edge Gallery

[Google AI Edge Gallery][18] is an experimental open-source Android app (iOS soon) that brings Google's on-device AI power to your phone, letting you run powerful models like Gemma 3n and other Hugging Face models fully offline after download. This application makes use of Google’s LiteRT framework.

You can [download it from Google Play Store][19]. Open the app and browse the list of provided models or manually download a compatible model from Hugging Face.

Select the downloaded model and start a chat session. Enter text prompts or upload images (if supported by the model) to interact locally. Explore features like prompt discovery or vision-based queries if available.

![][20]

### Top Mobile LLMs to try out

Here are the best ones I’ve used:

Model | My Experience | Best For
---|---|---
**Google’s Gemma 3n (2B)** | Blazing-fast for multimodal tasks including image captions, translations, even solving math problems from photos. | Quick, visual-based AI assistance
**Meta’s Llama 3.2 (1B/3B)** | Strikes the perfect balance between size and smarts. It’s great for coding help and private chats.The 1B version runs smoothly even on mid-range phones. | Developers & privacy-conscious users
**Microsoft’s Phi-3 Mini (3.8B)** | Shockingly good at summarizing long documents despite its small size. | Students, researchers, or anyone drowning in PDFs
**Alibaba’s Qwen-2.5 (1.8B)** | Surprisingly strong at visual question answering—ask it about an image, and it actually understands! | Multimodal experiments
**TinyLlama-1.1B** | The lightweight champ runs on almost any device without breaking a sweat. | Older phones or users who just need a simple chatbot

All these models use aggressive quantization (GGUF/safetensors formats), so they’re tiny but still powerful. You can grab them from [Hugging Face][21]—just download, load into an app, and you’re set.

### Challenges I faced while running LLMs Locally on Android smartphone

Getting large language models (LLMs) to run smoothly on my phone has been equally exhilarating and frustrating.

On my Snapdragon 8 Gen 2 phone, models like Llama 3-4B run at a decent 8-10 [tokens][22] per second, which is usable for quick queries. But when I tried the same on my backup Galaxy A54 (6 GB RAM), it choked. Loading even a 2B model pushed the device to its limits. I quickly learned that **Phi-3-mini (3.8B) or Gemma 2B are far more practical** for mid-range hardware.

The first time I ran a local AI session, I was shocked to see 50% battery gone in under 90 minutes. MLC Chat offers power-saving mode for this purpose. Turning off background apps to free up RAM also helps.

I also experimented with 4-bit quantized models (like Qwen-1.5-2B-Q4) to save storage but noticed they struggle with complex reasoning. For medical or legal queries, I had to switch back to 8-bit versions. It was slower but far more reliable.

### Conclusion

I love the idea of having an AI assistant that works exclusively for me, no monthly fees, no data leaks. Need a translator in a remote village? A virtual assistant on a long flight? A private brainstorming partner for sensitive ideas? Your phone becomes all of these staying offline and untraceable.

I won’t lie, it’s not perfect. Your phone isn’t a data center, so you’ll face challenges like battery drain and occasional overheating. But it also provides tradeoffs like total privacy, zero costs, and offline access.

The future of AI isn’t just in the cloud, it’s also on your device.

#### Author Info

![][23]

Bhuwan Mishra is a Fullstack developer, with Python and Go as his tools of choice. He takes pride in building and securing web applications, APIs, and CI/CD pipelines, as well as tuning servers for optimal performance. He also has passion for working with Kubernetes.

--------------------------------------------------------------------------------

via: https://itsfoss.com/android-on-device-ai/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/open-source-chatgpt-alternatives/
[4]: https://itsfoss.com/ollama-setup-linux/
[5]: https://itsfoss.com/llm-vs-generative-ai/
[6]: https://llm.mlc.ai/
[7]: https://github.com/mlc-ai/binary-mlc-llm-libs/releases
[8]: https://news.itsfoss.com/new-android-sideloading-rules/
[9]: https://itsfoss.com/content/images/2025/09/allow-apk-file-installation-1.webp
[10]: https://huggingface.co/google/gemma-2b
[11]: https://mistral.ai/
[12]: https://itsfoss.com/content/images/2025/09/mlc-chat-available-llm-models-1.webp
[13]: https://itsfoss.com/content/images/2025/09/mlc-chat-local-LLM-example.webp
[14]: https://github.com/shubham0204/SmolChat-Android
[15]: https://huggingface.co/docs/hub/en/gguf
[16]: https://play.google.com/store/apps/details?id=io.shubham0204.smollmandroid&pli=1
[17]: https://itsfoss.com/content/images/2025/09/smolchat-download-model-1.webp
[18]: https://github.com/google-ai-edge/gallery
[19]: https://play.google.com/store/apps/details?id=com.google.ai.edge.gallery
[20]: https://itsfoss.com/content/images/2025/09/google-ai-edge-gallery-1-2.webp
[21]: https://itsfoss.com/hugging-face/
[22]: https://itsfoss.com/llm-token/
[23]: https://itsfoss.com/content/images/2025/03/bhuwan.png
