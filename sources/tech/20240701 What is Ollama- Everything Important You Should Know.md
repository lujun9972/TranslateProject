[#]: subject: "What is Ollama? Everything Important You Should Know"
[#]: via: "https://itsfoss.com/ollama/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What is Ollama? Everything Important You Should Know
======

[![Warp Terminal][1]][2]

Ollama is a free and open-source project that lets you run [various open source LLMs locally][3].

Whether you want to utilize an open-source LLM like Codestral for code generation or LLaMa 3 for a [ChatGPT alternative][4], it is possible with Ollama.

But those are the end goals that you can achieve locally with Ollama on your system. What do you need to know to make that happen? How do you do all that?

In this article, I'll provide all the essential information about Ollama.

### What is Ollama?

[Ollama][5] is a free and open-source tool that lets anyone run open LLMs locally on your system. It supports Linux (Systemd-powered distros), Windows, and macOS (Apple Silicon).

It is a command-line interface (CLI) tool that lets you conveniently download LLMs and run it locally and privately. With a couple of commands you can download models like Llama 3, Mixtral, and more.

Think of it like Docker. With Docker, you download various images from a central repository and run them in a container. Similarly, using Ollama, you download various open source LLMs and then run them in your terminal.

### What are the system requirements?

To be able to utilize Ollama, you need a system that is capable of running the AI models.

For starters, you require a GPU to run things. With a CPU (or integrated GPU), it will be a painfully slow experience. So, it is not recommended.

Next, you need to ensure that you have a GPU from Nvidia/AMD with compute capability of 5 at the very least. Some popular supported GPUs include:

  * NVIDIA RTX 40x0 series, NVIDIA RTX 30x0 series, GTX 1650 Ti, GTX 750 Ti, GTX 750
  * AMD Vega 64, AMD Radeon RX 6000 series, AMD Radeon RX 7000 series



You can find the complete list of supported GPUs in [Ollama's official documentation][6].

### Does Ollama work With TPU or NPU?

Unfortunately, **Ollama does not officially support TPUs or NPUs currently.**

If you are curious, TPU (Tensor Processing Unit) is Google's custom-made integrated circuit (IC) tailored for machine learning workflows. It may not be the most powerful solution to run machine learning models, but it makes things convenient/flexible and affordable in some cases with Google Cloud.

NPU is the Neural Processing Unit, which is specifically used for AI-related tasks. Think of them as GPU but for AI.

There are projects like [ezrknpu][7] that try to provide some LLM models that run on NPU. [Abhishek tested it on ArmSoM Sige7][8] but for now, Ollama doesn't utilize NPU, it needs GPU.

### Can Ollama run on CPU only?

Yes, it can but it should be avoided. Ollama is designed to use the Nvidia or AMD GPUs. It does not recognize the integrated Intel GPU. While you may go ahead and run Ollama on CPU only, the performance will be way below par even when your 16 core processor is maxed out.

### How to install Ollama?

If you want to get started with [Ollama on Linux][9], we have a fantastic tutorial that you can follow:

![][10]

### Ollama models

Ollama focuses on providing you access to open models, some of which allow for commercial usage and some may not.

The models are hosted by Ollama, which you need to download using the pull command like this:

```

    ollama pull codestral

```

![][11]

Your data is not trained for the LLMs as it works locally on your device. However, if you like, you can deploy it as a service to interact with your software application. You can refer to its [GitHub repo][12] to find out more about it.

Some of the useful models available with Ollama include:

  * **llama 3:** A family of open models developed by Meta Inc with instruction-tuned and pre-trained variants
  * **gemma** : Lightweight open models developed by Google DeepMind and inspired by Google Gemini.
  * **Mistral** : A powerful open-source model available under Apache 2.0 license
  * **Codestral** : Mistral's AI model under a non-production license, trained with 80+ programming languages



You can find all the LLMs available listed in the [Ollama library][13] portal. You can check the details and pull it to use it on your device.

If you do not need a model, you can simply remove it using the command on Linux:

```

    ollama rm codestral

```

![][14]

### Where are the models stored?

Sometimes users report that even after using the remove command, the storage space is not freed up, meaning the deletion was not successful.

So, in those cases, or maybe if you want to delete multiple models using the graphical user interface (GUI) or the file manager, you need to know the storage location. Here is the default storage path for the models downloaded:

  * Linux: `/usr/share/ollama/.ollama/models`
  * Windows: `C:\Users\%username%\.ollama\models`
  * macOS: `~/.ollama/models`



### How to stop Ollama?

For Windows/macOS, you can head to the system tray icon in the bottom-right or top-right (depending on your position of the taskbar) and click on "Exit Ollama".

With Linux, you need to enter the following command to stop Ollama process from running in the background:

```

    sudo systemctl stop ollama

```

### How to get a GUI for Ollama?

Ollama is a CLI-based tool. So, you do not get a graphical user interface to interact with or manage models by default. However, you can install web UI tools or GUI front-ends to interact with AI models without needing the CLI. You can refer to our list here to explore options:

![][10]

### Conclusion

Though there are plenty of similar tools, Ollama has become the most popular tool to run LLMs locally. The ease of use in installing different LLMs quickly make it ideal for beginners who want to use local AI.

I have tried to answer one of the most frequently asked questions you may have about Ollama. If you still have some questions, please feel free to ask in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ollama/

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
[4]: https://itsfoss.com/open-source-chatgpt-alternatives/
[5]: https://ollama.com/
[6]: https://github.com/ollama/ollama/blob/main/docs/gpu.md
[7]: https://github.com/Pelochus/ezrknpu
[8]: https://itsfoss.com/arosom-sige7-review/
[9]: https://itsfoss.com/ollama-setup-linux/
[10]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[11]: https://itsfoss.com/content/images/2024/06/ubuntu-ollama-model-pull.png
[12]: https://github.com/ollama/ollama
[13]: https://ollama.com/library
[14]: https://itsfoss.com/content/images/2024/06/ollama-remove-model.png
