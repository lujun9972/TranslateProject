[#]: subject: "12 Tools to Provide a Web UI for Ollama"
[#]: via: "https://itsfoss.com/ollama-web-ui-tools/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

12 Tools to Provide a Web UI for Ollama
======

[![Warp Terminal][1]][2]

Ollama is a free and open-source tool that lets users run Large Language Models (LLMs) locally. It makes the AI experience simpler by letting you interact with the LLMs in a hassle-free manner on your machine.

You can run some of the most popular LLMs and a couple of [open-source LLMs][3] available.

Unfortunately, it offers a CLI, which may not be everyone's cup of tea ☕ So, you can choose to enhance your experience (and make it easier) by running LLMs locally **using a web user interface**. To accomplish that, you have a few open-source tools that provide a web UI.

Let me highlight some options here.

📋

Make sure you have Ollama installed before you try working with the front-end UI. If you do not have Ollama installed, refer to our [Ollama installation guide][4].

![][5]

### 1\. Page Assist

![][6]

[Page Assist][7] is an interesting **open-source browser extension** that lets you run local AI models. It supports Ollama, and gives you a good amount of control to tweak your experience. You can install it on Chromium-based browsers or Firefox.

From letting you easily manage the installed models, adding files to analyze or research to be able to enable internet search, it is a convenient way to access LLMs right on your browser.

You can also decide to share your output with the world using a self-hosted URL (not sure who would want that, but yes).

[Page Assist][7]

### 2\. Open WebUI

![][8]

[Open WebUI][9] is the most **popular and feature-rich solution to get a web UI** for Ollama. The project initially aimed at helping you work with Ollama. But, as it evolved, it wants to be a web UI provider for all kinds of LLM solutions.

It supports OpenAI-compatible APIs and works entirely offline. You can install it quickly using Docker or Kubernetes. Furthermore, it features a Progressive Web App for mobile, and image generation integrations.

If you want a web UI for Ollama, I think this is an easy recommendation. However, if you are looking for something different, there are plenty of other options too.

[Open WebUI][9]

### 3\. Lobe Chat

![][10]

[Lobe Chat][11] is a local and privacy-focused ChatGPT-like UI framework.

You can deploy your private Ollama chat application using Lobe Chat, and it should look pretty sleek. **It is also available as a one-click script** if you use Pinokio, the AI browser.

Lobe Chat also supports voice conversations and text-to-image generation. Furthermore, you can enhance its capabilities using plugins. It features support for Progressive Web App as well.

[Lobe Chat][11]

**Suggested Read 📖**

![][5]

### 4\. Text Generation Web UI

![][12]

A web UI that focuses entirely on text generation capabilities, built using **Gradio** library, an open-source Python package to help build web UIs for machine learning models.

[Text Generation Web UI][13] features three different interface styles, a traditional chat like mode, a two-column mode, and a notebook-style model. You get OpenAI compatible model support and transformers library integration.

[Text Generation Web UI][13]

### 5\. Ollama UI

![][14]

If you do not need anything fancy, or special integration support, but more of a bare-bones experience with an accessible web UI, [Ollama UI][15] is the one.

It is **a simple HTML-based UI** that lets you use Ollama on your browser. **You also get a Chrome extension** to use it. As you can see in the screenshot, you get a simple dropdown option to select the model you want to use, and that's it.

[Ollama UI][15]

### 6\. Ollama GUI

![][16]

While all the others let you access Ollama and other LLMs irrespective of the platform (on your browser), [Ollama GUI][17] is an app for macOS users.

The app is free and open-source, **built using SwiftUI framework,** it looks pretty, which is why I didn't hesitate to add to the list.

Yes, it may not be a web UI tool that lets you access the model from your phone or any browser, but it is a feasible option for macOS users.

[Ollama GUI][17]

### 7\. Lord of LLMs Web UI

A pretty descriptive name, a.k.a., [LoLLMs Web UI][18] is a decently popular solution for LLMs that includes support for Ollama.

It supports a range of **abilities that include text generation, image generation, music generation, and more**. You can integrate it with the GitHub repository for quick access and choose from the different personalities offered.

You can set it up on Linux using the automatic installation script, and that'sprovide-a- an easy to way to get started with it.

### 8\. LibreChat

[LibreChat][19] is an [open-source ChatGPT alternative][20] that you can deploy locally or in the cloud.

It is compatible with Ollama. You can use [open-source LLMs][3] and popular proprietary models like Google Vertex AI, ChatGPT, and more. It is tailored to be a ChatGPT clone, so you will not find anything unique about the UI offered. But, for some, the familiarity of the UI can help you navigate things better.

[LibreChat][19]

**Suggested Read 📖**

![][5]

### 9\. Minimal LLM UI

Want something basic but capable?

[Minimal LLM UI][21] is an unusual option that provides **a web UI for Ollama using** [**React**][22], aiming to provide you with a clean and modern design.

You can switch between LLMs, and save your conversation locally using a database.

[Minimal LLM UI][21]

### 10\. Enchanted

[Enchanted][23] is an open-source app that lets you connect to your private models, compatible with Ollama to get a **seamless experience across the Apple ecosystem** (iOS, macOS, Vision Pro).

This is a useful tool for users who want the Apple platform support. If you wanted to have a GUI and still have the option to configure a web UI to access on macOS.

[Enchanted][23]

### 11\. Msty.app (Non-FOSS)

![][24]

[Msty][25] is a fascinating non-foss app available across multiple platforms, providing you a local-first UI to run AI models or LLMs.

The highlights of this tool include **conversational branches** , and the ability to add knowledge stacks using Obsidian vaults (and other services).

[Msty.app][25]

### 12\. Hollama

![][26]

[Hollama][27] is yet another minimal web UI option that offers a publicly hosted version that does not need you signing up and still be able to use it (data stored locally).

You can run Hollama locally by using a docker image. Unlike most others, it lacks plenty of features. But, if you only wanted a quick web UI for Ollama, you can try this out.

[Hollama][27]

### Wrapping Up

Considering, we are just getting started with the local and private AI. I am certain that there will be several more tools available that allow us to use Ollama for interesting use-cases.

For me, **the Page Assist extension seems like a time-saver** (with no setup) which lets me run AI models locally while having the ability to search from the internet.

_💬 What is your favorite tool to get a web UI for Ollama? Would you mind sharing how you use Ollama + web UI in your day-to-day life? Use the comments section below and let's talk!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/ollama-web-ui-tools/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/open-source-llms/
[4]: https://itsfoss.com/ollama-setup-linux/
[5]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[6]: https://itsfoss.com/content/images/2024/06/page-assist-extension.png
[7]: https://github.com/n4ze3m/page-assist
[8]: https://itsfoss.com/content/images/2024/06/open_webui_settings-1.png
[9]: https://github.com/open-webui/open-webui
[10]: https://itsfoss.com/content/images/2024/06/lobechat-ollama.jpg
[11]: https://github.com/lobehub/lobe-chat/
[12]: https://itsfoss.com/content/images/2024/06/text-generation-ui.png
[13]: https://github.com/oobabooga/text-generation-webui
[14]: https://itsfoss.com/content/images/2024/06/ollama-ui.jpg
[15]: https://github.com/ollama-ui/ollama-ui
[16]: https://itsfoss.com/content/images/2024/06/ollama-gui-1.png
[17]: https://github.com/enoch1118/ollamaGUI
[18]: https://github.com/ParisNeo/lollms-webui
[19]: https://github.com/danny-avila/LibreChat
[20]: https://itsfoss.com/open-source-chatgpt-alternatives/
[21]: https://github.com/richawo/minimal-llm-ui
[22]: https://react.dev/
[23]: https://github.com/AugustDev/enchanted
[24]: https://itsfoss.com/content/images/2024/06/msty-feature-refinements-dark.png
[25]: https://msty.app/
[26]: https://itsfoss.com/content/images/2024/06/hollama.png
[27]: https://github.com/fmaclen/hollama
