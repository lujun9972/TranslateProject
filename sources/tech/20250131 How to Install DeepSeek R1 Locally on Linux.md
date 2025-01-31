[#]: subject: "How to Install DeepSeek R1 Locally on Linux"
[#]: via: "https://itsfoss.com/install-deepseek-r1-locally-linux/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Install DeepSeek R1 Locally on Linux
======

[![Warp Terminal][1]][2]

[DeepSeek][3] has taken the AI world by storm. While it's convenient to use DeepSeek on their hosted website, we know that there's no place like `127.0.0.1`. 😉

![Source: The Hacker News][4]

However, with recent events, such as [a cyberattack on DeepSeek AI that has halted new user registrations][5], or [DeepSeek AI database exposed][6], it makes me wonder why not more people choose to run LLMs locally.

Not only does running your AI locally give you full control and better privacy, but it also keeps your data out of someone else’s hands.

In this guide, we'll walk you through setting up DeepSeek R1 on your Linux machine using [**Ollama**][7] as the backend and [**Open WebUI**][8] as the frontend.

Let’s dive in!

📋

The DeepSeek version you will be running on the local system is a striped down version of actual DeepSeek that 'outperformed' ChatGPT. You'll need Nvidia/AMD graphics on your system to run it.

### Step 1: Install Ollama

Before we get to DeepSeek itself, we need a way to run Large Language Models (LLMs) efficiently. This is where **Ollama** comes in.

#### What is Ollama?

[Ollama][9] is a lightweight and powerful platform for [running LLMs locally][10]. It simplifies model management, allowing you to **download, run, and interact with models** with minimal hassle.

**The best part?** It abstracts away all the complexities, no need to manually configure dependencies or set up virtual environments.

##### Installing Ollama

The easiest way to [install Ollama][11] is by running the following command in your terminal:

```

    curl -fsSL https://ollama.com/install.sh | sh

```

![][12]

Once installed, verify the installation:

```

    ollama --version

```

Now, let's move on to getting DeepSeek running with [Ollama][13].

### Step 2: Install and run DeepSeek model

With Ollama installed, pulling and running the DeepSeek model is really simple as running this command:

```

    ollama run deepseek-r1:1.5b

```

This command downloads the **DeepSeek-R1 1.5B model** , which is a small yet powerful AI model for text generation, answering questions, and more.

The download may take some time depending on your internet speed, as these models can be quite large.

![][14]

Once the download is complete, you can interact with it immediately in the terminal:

![][15]

But let’s be honest, while the terminal is great for quick tests, it’s not the most polished experience. It would be better to [use a Web UI with Ollama][16]. While there are many such tools, I prefer [Open WebUI][17].

![][18]

### Step 3: Setting up Open WebUI

Open WebUI provides a beautiful and user-friendly interface for chatting with DeepSeek. There are **two ways** to install Open WebUI:

  * Direct Installation (for those who prefer a traditional setup)
  * Docker Installation (my personal go-to method)



Don't worry, we'll be covering both.

#### Method 1: Direct installation

If you prefer a traditional installation without Docker, follow these steps to set up **Open WebUI** manually.

##### Step 1: Install python & virtual environment

First, ensure you have Python installed along with the `venv` package for creating an isolated environment.

Run the following command:

```

    sudo apt install python3-venv -y

```

![][19]

This installs the required package for managing virtual environments.

##### Step 2: Create a virtual environment

Next, create a virtual environment inside your home directory:

```

    python3 -m venv ~/open-webui-venv

```

and then activate the virtual environment we just created:

```

    source ~/open-webui-venv/bin/activate

```

![][20]

You'll notice your terminal prompt changes, indicating that you’re inside the virtual environment.

##### Step 4: Install Open WebUI

With the virtual environment activated, install Open WebUI by running:

```

    pip install open-webui

```

![][21]

This downloads and installs Open WebUI along with its dependencies.

##### Step 5: Run Open WebUI

To start the Open WebUI server, use the following command:

```

    open-webui serve

```

![][22]

Once the server starts, you should see output confirming that Open WebUI is running.

##### Step 6: Access Open WebUI in your browser

Open your web browser and go to: <http://localhost:8080>

You'll now see the Open WebUI interface, where you can start chatting with DeepSeek AI!

#### Method 2: Docker installation (Personal favorite)

If you haven't installed Docker yet, no worries! Check out our step-by-step guide on how to [install Docker on Linux][23] before proceeding.

Once that's out of the way, let's get Open WebUI up and running with Docker.

##### Step 1: Pull the Open WebUI docker image

First, download the latest Open WebUI image from Docker Hub:

```

    docker pull ghcr.io/open-webui/open-webui:main

```

![][24]

This command ensures you have the most up-to-date version of Open WebUI.

##### Step 2: Run Open WebUI in a docker container

Now, spin up the Open WebUI container:

```

    docker run -d \
      -p 3000:8080 \
      --add-host=host.docker.internal:host-gateway \
      -v open-webui:/app/backend/data \
      --name open-webui \
      --restart always \
      ghcr.io/open-webui/open-webui:main

```

Don’t get scared looking at that big, scary command. Here’s what each part of the command actually does:

Command | Explanation
---|---
`docker run -d` | Runs the container in the background (detached mode).
`-p 3000:8080` | Maps port 8080 inside the container to port 3000 on the host. So, you’ll access Open WebUI at `http://localhost:3000`.
`--add-host=host.docker.internal:host-gateway` | Allows the container to talk to the host system, useful when running other services alongside Open WebUI.
`-v open-webui:/app/backend/data` | Creates a persistent storage volume named open-webui to save chat history and settings.
`--name open-webui` | Assigns a custom name to the container for easy reference.
`--restart always` | Ensures the container automatically restarts if your system reboots or if Open WebUI crashes.
`ghcr.io/open-webui/open-webui:main` | This is the Docker image for Open WebUI, pulled from GitHub’s Container Registry.

![][25]

##### Step 3: Access Open WebUI in your browser

Now, open your web browser and navigate to: <http://localhost:8080> .You should see Open WebUI's interface, ready to use with DeepSeek!

![][26]

Once you click on **"Create Admin Account,"** you'll be welcomed by the Open WebUI interface.

Since we haven't added any other models yet, the DeepSeek model we downloaded earlier is already loaded and ready to go.

![][27]

Just for fun, I decided to test DeepSeek AI with a little challenge. I asked it to: _"Write a rhyming poem under 20 words using the words: computer, AI, human, evolution, doom, boom."_

And let's just say… the response was **a bit scary.** 😅

Here's the full poem written by DeepSeek R1:

![][28]

### Conclusion

And there you have it! In just a few simple steps, you’ve got DeepSeek R1 running locally on your Linux machine with Ollama and Open WebUI.

Whether you’ve chosen the Docker route or the traditional installation, the setup process is straightforward, and should work on most Linux distributions.

So, go ahead, challenge DeepSeek to write another quirky poem, or maybe put it to work on something more practical. It’s yours to play with, and the possibilities are endless.

For instance, I recently ran [DeepSeek R1 on my Raspberry Pi 5][29], while it was a bit slow, it still got the job done.

Who knows, maybe your next challenge will be more creative than mine (though, I’ll admit, that poem about "doom" and "boom" was a bit eerie! 😅).

Enjoy your new local AI assistant, and happy experimenting! 🤖

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-deepseek-r1-locally-linux/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.deepseek.com
[4]: https://itsfoss.com/content/images/2025/01/the-hacker-news-deepseek-ai-1.png
[5]: https://thehackernews.com/2025/01/top-rated-chinese-ai-app-deepseek.html
[6]: https://thehackernews.com/2025/01/deepseek-ai-database-exposed-over-1.html
[7]: https://ollama.com
[8]: https://docs.openwebui.com
[9]: https://itsfoss.com/ollama/
[10]: https://itsfoss.com/open-source-chatgpt-alternatives/
[11]: https://itsfoss.com/ollama-setup-linux/
[12]: https://itsfoss.com/content/images/2025/01/installing-ollama.png
[13]: https://ollama.com/
[14]: https://itsfoss.com/content/images/2025/01/ollama-downloading-deepseek.png
[15]: https://itsfoss.com/content/images/2025/01/asking-deepseek-to-tell-a-joke.png
[16]: https://itsfoss.com/ollama-web-ui-tools/
[17]: https://openwebui.com/
[18]: https://itsfoss.com/content/images/icon/android-chrome-192x192-256.png
[19]: https://itsfoss.com/content/images/2025/01/checking-python-virt-env-install.png
[20]: https://itsfoss.com/content/images/2025/01/activating-virt-env-python.png
[21]: https://itsfoss.com/content/images/2025/01/pip-installing-open-webui.png
[22]: https://itsfoss.com/content/images/2025/01/direct-run-open-webui.png
[23]: tmp.8sD80RVvXl#
[24]: https://itsfoss.com/content/images/2025/01/docker-pull-open-webui.png
[25]: https://itsfoss.com/content/images/2025/01/docker-run-open-webui.png
[26]: https://itsfoss.com/content/images/2025/01/open-webui-login.png
[27]: https://itsfoss.com/content/images/2025/01/open-webui-deepseek-on-homepage.png
[28]: https://itsfoss.com/content/images/2025/01/poem-written-by-deepseek.png
[29]: https://itsfoss.com/deepseek-r1-raspberry-pi-5/
