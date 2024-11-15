[#]: subject: "Running Opencoder LLM in VS Code: A Local, Copilot Alternative"
[#]: via: "https://itsfoss.com/opencoder-vscode/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Running Opencoder LLM in VS Code: A Local, Copilot Alternative
======

[![Warp Terminal][1]][2]

Programming is the one area where AI is being used extensively. Most editors allow you to add AI agents like chatGPT, Microsoft's Copilot etc.

There are also several open source large language models specifically centered around coding like [CodeGemma][3].

And then we have a new player entering the scene and everyone talking about it.

This new player is [OpenCoder][4], an open-source Code LLM available in 1.5B and 8B models.

Since OpenCoder is getting popular, I decided to quickly test it out as a local AI assistent to help me code in VS Code.

With my experience here, you’ll also be able to integrate OpenCoder (or any other LLM) into [VS Code][5] with the help of [CodeGPT][6] extension and enjoy the perks of a local AI assistant.

📋

This tutorial is performed on Ubuntu 24.04 in a VM. Steps mentioned are mostly applicable on Ubuntu. But, feel free to replicate the same on other Linux distributions and operating systems.

### Step 1: Install VS Code (if you don't have it already)

First, ensure that Visual Studio Code is installed on your system. If not, follow these steps to get it set up:

  * Download VS Code for Ubuntu [here][7].
  * Once downloaded, open your terminal and install it by running:



```

    sudo dpkg -i ./<downloaded-file>.deb

```

After installation, launch VS Code from your applications menu or by typing `code` in the terminal.

### Step 2: Install the CodeGPT Extension

✋

While you can integrate some major platforms like [Ollama][8] and [LM Studio][9] for free, CodeGPT isn’t entirely free. Basic usage comes at no cost, but if you're looking for a one-click solution with advanced features, [CodeGPT offers paid plans][10] that require creating an account.

[CodeGPT][6] is a powerful tool that I've found invaluable for boosting productivity and simplifying coding workflows.

As an extension for VS Code, it integrates seamlessly, providing instant code suggestions, completions, and debugging insights right where I need them.

Here’s how to set it up:

  1. Open VS Code.
  2. Click on the Extensions icon in the sidebar.
  3. Search for “CodeGPT” in the Extensions Marketplace.
  4. Select the extension and click “Install.”



![][11]

After installation, the extension should appear in the sidebar for easy access.

![][12]

This extension serves as the interface between your VS Code environment and OpenCoder, allowing you to request code suggestions, completions, and more.

### Step 3: Install Ollama

Ollama is an essential tool for managing and deploying language models locally. It simplifies the process of downloading and running models locally, making it a crucial component for this setup.

Ollama provides an official installation script. Run the command below to install Ollama:

```

    curl -fsSL https://ollama.com/install.sh | sh

```

Once the installation process completes, open a web browser and enter:

```

    localhost:11434

```

It should show the message, "Ollama is running".

![][13]

We have also covered [Ollama installation steps][14] in detail, in case you need that.

![][15]

### Step 4: Download Opencoder model with Ollama

With CodeGPT and Ollama installed, you’re ready to download the Opencoder model:

In the terminal window, type:

```

    ollama run opencoder

```

This may take a few minutes, depending on your internet speed and hardware specifications.

![][16]

Once complete, the model is now ready for use within CodeGPT.

### Step 5: Run your Copilot AI with opencoder

Open a code file or project in VS Code (I'm using an empty `docker-compose.yml` file).

In the CodeGPT panel, ensure Ollama is selected as your active provider.

![][17]

Next, it'll ask you to select the model. I've downloaded both version of Opencoder with 1.5B & 8B parameters but I'll be using the former:

![][18]

Start engaging with the model by typing your queries or use it for code completions, suggestions, or any coding help you need:

![][19]

Here’s a quick video of me interacting with the OpenCoder model inside VS Code using the CodeGPT extension.

### Conclusion

After testing OpenCoder with Ollama on my Ubuntu VM setup, I found that while the performance wasn't as snappy as cloud-based AI services like ChatGPT, it was certainly functional for most coding tasks.

The responsiveness can vary, especially on modest hardware, so performance is a bit subjective depending on your setup and expectations.

However, if data privacy and local processing are priorities, this approach still offers a solid alternative.

For developers handling sensitive code who want an AI copilot without relying on cloud services, Ollama and CodeGPT in VS Code is a worthwhile setup, balancing privacy and accessibility right on your desktop.

--------------------------------------------------------------------------------

via: https://itsfoss.com/opencoder-vscode/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://ollama.com/library/codegemma
[4]: https://opencoder-llm.github.io/
[5]: https://code.visualstudio.com
[6]: https://codegpt.co
[7]: https://code.visualstudio.com/
[8]: https://ollama.com/
[9]: https://lmstudio.ai/
[10]: https://codegpt.co/pricing
[11]: https://itsfoss.com/content/images/2024/11/extension-codegpt-1.png
[12]: https://itsfoss.com/content/images/2024/11/codegpt-icon.png
[13]: https://itsfoss.com/content/images/2024/05/check-ollama-running.png
[14]: https://itsfoss.com/ollama-setup-linux/
[15]: https://itsfoss.com/content/images/icon/android-chrome-192x192-108.png
[16]: https://itsfoss.com/content/images/2024/11/downloading-opencoder.png
[17]: https://itsfoss.com/content/images/2024/11/selecting-ollama-inside-codegpt-2.png
[18]: https://itsfoss.com/content/images/2024/11/selecting-opencoder-model-inside-codegpt-1.png
[19]: https://itsfoss.com/content/images/2024/11/typing-prompt-in-opencoder.png
