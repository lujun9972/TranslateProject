[#]: subject: "Running AI Locally Using Ollama on Ubuntu Linux"
[#]: via: "https://itsfoss.com/ollama-setup-linux/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Running AI Locally Using Ollama on Ubuntu Linux
======

[![Warp Terminal][1]][2]

Here's the thing. AI is the f̶u̶t̶u̶r̶e̶ present. You are already seeing it everywhere without even realizing it. From [LanguageTool][3] to [Warp terminal][4] to Nextcloud, AI is now integrated into your favorite tools.

But I believe that the future of AI should be private, local, and open source. I want it to be a tool I use, both the other way around.

Thankfully, I am not the only one to have these thoughts. There are numerous open source LLMs out there, and new tools are coming up that make it easy to install and run AI locally on your system.

I am experimenting with AI as an end user and will share my experience with you.

For this tutorial, I will show:

  * how you can install Ollama and set it up to run various open source LLMs
  * how you can set up Open WebUI to use a web-based interface to interact with AI



💡

AI is a broad term that describes the entire artificial intelligence field. What you, as an end user, would be doing is interacting with [LLMs][5] (Large Language Models). LLMs are basically tools that have already been trained on vast amounts of data to learn patterns and relationships between words and phrases, and more. Different LLMs are often designed for specific tasks such as coding, language interpretation, visuals, etc. A very simplistic description, to be honest.

### What is Ollama?

[Ollama][6] is a command line based tools for downloading and running open source LLMs such as Llama3, Phi-3, Mistral, CodeGamma and more. It streamlines model weights, configurations, and datasets into a single package controlled by a Modelfile. All you have to do is to run some commands to install the supported open source LLMs on your system and use them.

I like to think of it as a Docker-like tool (wrong analogy, I know). Like Docker fetches various images on your system and then uses them, Ollama fetches various open source LLMs, installs them on your system, and allows you to run those LLMs on your system locally.

You can find the full list of LLMs supported by Ollama [here][7].

### Prerequisite

Here are a few things you need to run AI locally on Linux with Ollama.

  * GPU: While you may run AI on CPU, it will not be a pretty experience. If you have TPU/NPU, it would be even better.
  * curl: You need to download a script file from the internet in the Linux terminal
  * **Optionally, you should have Docker installed on your system** if you want to use Open WebUI. Ollama gives you a command line interface for interacting with the AI. Open WebUI provides you a web interface with ChatGPT like experience.



### Step 1: Installing Ollama on Linux

new tools are coming provides an [official script][8] that can be used on any Linux distribution.

Open a terminal and use the following command:

```

    curl -fsSL https://ollama.com/install.sh | sh

```

As you can see in the screenshot below, it took approximately 25 seconds to install Ollama on Ubuntu for me.

![Ollama installed on Ubuntu Linux][9]

Also note the warning it shows at the end. My Dell XPS has integrated Intel GPU but clearly, Ollama wants NVIDIA/AMD GPU.

In other words, I'll be running AI on CPU only 🤖🔥💻

This is the easy way out. You may [go for the manual installation option][10] if you are feeling adventurous.

#### Check that Ollama is running

Once you have installed Ollama, you should check whether it is running. By default it runs on port number of localhost.

So, open a web browser and enter:

```

    localhost:11434

```

It should show the message, "Ollama is running".

![][11]

Great! So, you have the tool that could fetch LLMs in your system. Let's see how to do that.

### Step 2: Installing LLMs with Ollama

You can "install" your desired LLM in the following manner.

```

    ollama pull <LLM_NAME>

```

As of now, you cannot search for available LLMs from the terminal. You'll have to [go to its website][7]. From there, you can get the exact name of the LLM you want to use.

For example, I am going to use `llama2`, an [open source offering from Meta][12] (Facebook).

```

    ollama pull llama2

```

This will take time as it downloads GBs of data. As you can see in the screenshot, it took 2 minutes and 24 seconds to complete for me.

![Installing Llama2 with Ollama][13]

Ollama keeps the LLMs in /usr/share/ollama/.ollama/models directory on Linux. I wanted you to know it.

Great! You have a large language model available now. You have a tool to interact with it. Let's use the AI!

### Step 3: Running the AI with Ollama (in terminal)

Run the LLM with this command:

```

    ollama run <LLM_NAME>

```

Since I have installed `llama2`, I use this command:

```

    ollama run llama2

```

💡

You can list all the installed LLMs on your system with `ollama list` command.

There are no instant greetings that tell you that AI is ready to serve you. You just have to start asking questions to it.

I asked it 'what is itsfoss' but it was not the answer I was expecting.

![Well, AI doesn't know everything 😕][14]

**You can use Ctrl+D or type /bye to exit interacting with the AI.**

When you start asking a question, you should hear a whirring sound. That's the sound of your system going crazy as it consumes all the available resources to run the AI locally. That's why running AI is expensive and not good for the environment.

For me, the response was really slow. It was like using text-based chatting in the early 90s. Words appeared in a stop-motion way. But hey, I am running my own AI without a dedicated GPU or NPU 💪

![My Dell XPS has never been \(ab\)used in this way before][15]

📋

I am looking forward to trying this on my [Sige7 board by ArmSoM][16]. It comes with RK3588 SoC that has a 6 TOPS NPU and see how the local AI performs on this device.

### Optional Step 4: Use AI in ChatGPT like browser interface with Open WebUI

[Open WebUI][17] is an open source project that lets you use and interact with local AI in a web browser. If you ever used ChatGPT, Perplexity or any other commercial AI tool, you probably are familiar with this interface.

It's more user-friendly. Your conversations are stored, and you can easily revisit them or even search for them.

🚧

This setup runs Open WebUI in a Docker container. Even if you do not know Docker, you should be able to run it without much trouble as long as you follow the commands properly.

#### Get Docker installed

First, ensure that you have Docker installed on your system.

![][18]

#### Install Open WebUI in Docker

Once Docker is installed on your system, all you have to is run this command as mentioned in the [Open WebUI documentation][19]:

```

    sudo docker run -d --network=host -e OLLAMA_BASE_URL=http://127.0.0.1:11434 -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main

```

This, too, will take time to download the required docker images and then run the container:

![][20]

Once the process is completed, make sure that your open-webui container is running by using the `docker ps` command:

```

    docker ps
    CONTAINER ID   IMAGE                                COMMAND           CREATED      STATUS      PORTS     NAMES
    8541f122b75d   ghcr.io/open-webui/open-webui:main   "bash start.sh"   2 days ago   Up 2 days             open-webui

```

#### Run Open WebUI

Open a browser and access the localhost at port number 8080:

```

    127.0.0.1:8080

```

You'll see a web interface that asks you to create an account.

🚧

Make sure that you use a password that is easy to remember or save it in a password manager like ProtonPass. Because if you forgot the password, there is no easy way to reset it. You can remove the container and the attached Docker Volume with `sudo docker volume rm open-webui` but you'll lose all the chat history and existing accounts.

![][21]

The account you create on the first run is also the admin account. It lets you create more accounts and manage on the same server. This is helpful if you plan to deploy a local AI server which is accessible from other computers on your network.

Once you have logged into the interface, you should click on 'Select a model' and choose the LLMs of your choice. At this point, I had only `llama2` installed. If there were more, the choices will be shown here. In fact, you can interact with more than one LLM at a time in Open WebUI.

![][22]

With that, you are ready to interact with it:

![Using Llama2 LLM running with Ollama in Open WebUI \(click to expand\)][23]

You can edit a response, copy it, give it feedback, read it aloud or regenerate it.

#### Stop running the AI

When you close the browser tab, your system no longer runs the LLMs and thus your system resource usage comes back to normal.

Keep in mind that Open WebUI container always runs on your system. But it doesn't consume resources unless you start using the interface.

### Removal steps

Alright! So you experimented with open source AI and do not feel a real use for it at the moment. Understandably, you would want to remove it from your system and reclaim the disk space.

That's only logical. Let me help you with that.

#### Removing Open WebUI

If you used Open WebUI, follow these steps.

Stop the running container and then remove it:

```

    docker container stop open-webui
    docker container remove open-webui

```

Next, remove the Docker image as well. List the images with this command:

```

    docker images

```

And note down the `IMAGE ID` of the open-webui image and use it in the following fashion:

```

    docker image rm IMAGE_ID

```

You may also remove the content of `/var/lib/docker/volumes/open-webui` directory.

I don't see the need to uninstall Docker altogether.

#### Removing Ollama

Now, let's talk about uninstalling Ollama.

First, list all the LLMs you have installed through Ollama:

```

    ollama list

```

And then use its name to uninstall:

```

    ollama rm LLM_NAME

```

![][24]

If you missed this step, you can get your disk space back by removing files in the `/usr/share/ollama/.ollama/models` directory on Linux

With that aside, let's remove Ollama itself.

Remove Ollama service:

```

    sudo systemctl stop ollama
    sudo systemctl disable ollama
    sudo rm /etc/systemd/system/ollama.service

```

![][25]

Remove the ollama binary from your bin directory. It could be in `/usr/local/bin`, `/usr/bin`, or `/bin`. So use the command substitution with:

```

    sudo rm $(which ollama)

```

Next, remove the Ollama user and other remaining bits and pieces:

```

    sudo rm -r /usr/share/ollama
    sudo userdel ollama
    sudo groupdel ollama

```

You may see a message with userdel 'group ollama not removed because it has other members'. Just ignore it.

### Conclusion

As you can see, tools like Ollama make it so easy to install different open source LLMs locally. You can use them for a variety of purpose while keeping it private. From summarizing documents to coding, the use-cases are numerous, and it will only increase in the future.

Of course, your system should be capable enough to run AI like this, as it consumes tremendous CPU and GPU. Eventually, NPU (Neural Processing Units) will be available on all modern laptops like GPU these days.

🗨️ Let me know your thoughts about running local AI. And if you face any issues while following this tutorial, do let me know in the comments and I'll try to help you out.

--------------------------------------------------------------------------------

via: https://itsfoss.com/ollama-setup-linux/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://news.itsfoss.com/languagetool-grammarly-experience/
[4]: https://news.itsfoss.com/warp/
[5]: https://www.cloudflare.com/en-gb/learning/ai/what-is-large-language-model/
[6]: https://ollama.com/
[7]: https://ollama.com/library
[8]: https://github.com/ollama/ollama/blob/main/scripts/install.sh
[9]: https://itsfoss.com/content/images/2024/05/installing-openllama-ubuntu.webp
[10]: https://github.com/ollama/ollama/blob/main/docs/linux.md
[11]: https://itsfoss.com/content/images/2024/05/check-ollama-running.png
[12]: https://llama.meta.com/llama2/
[13]: https://itsfoss.com/content/images/2024/05/ollama-installing-llama2.webp
[14]: https://itsfoss.com/content/images/2024/05/running-llama2.webp
[15]: https://itsfoss.com/content/images/2024/05/running-ai-locally-consumes-too-much-cpu.webp
[16]: https://www.armsom.org/sige7
[17]: https://openwebui.com/
[18]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[19]: https://docs.openwebui.com/
[20]: https://itsfoss.com/content/images/2024/05/installing-openwebui-docker.webp
[21]: https://itsfoss.com/content/images/2024/05/openwebui-first-run.webp
[22]: https://itsfoss.com/content/images/2024/05/select-model-openwebui.png
[23]: https://itsfoss.com/content/images/2024/05/using-ai-with-open-webui.png
[24]: https://itsfoss.com/content/images/2024/05/ollama-remove-llm.png
[25]: https://itsfoss.com/content/images/2024/05/remove-ollama-systemd-services.png
