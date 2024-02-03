[#]: subject: "Run LLMs Locally on Raspberry Pi Using Ollama AI"
[#]: via: "https://itsfoss.com/raspberry-pi-ollama-ai-setup/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Run LLMs Locally on Raspberry Pi Using Ollama AI
======

Last week, I shared a tutorial on [using PrivateGPT][1]. It's an AI tool to interact with documents.

Now, that's fine for the limited use, but if you want something more than just interacting with a document, you need to explore other projects.

That's when I came across a fascinating project called [Ollama][2]. It's an open source project that lets you run various Large Language Models (LLM's) locally.

While browsing through Reddit communities, I came across discussions that talk about running LLMs on Raspberry Pi.

I was curious to verify this 'claim' so I decided to run LLMs locally with Ollama on my Raspberry Pi 4.

Let me share my experiments with you in this brief article.

📋

This article assumes that you have the basic understanding of AI, LLMs and other related tools and jargon.

### Installing Ollama on Raspberry Pi OS (and other Linux)

The installation process of Ollama is effortless. For installation on Linux, you have to fetch their official installation script and run it. That's the official method described on their website.

![][3]

You can download it manually and read what it does. Or, if you are lazy like me, combine them both in a single command like this:

```

    curl https://ollama.ai/install.sh | sh

```

![][4]

### Exploring different LLMs

Once the installation is done, you are now all ready to run LLMs on Pi and start chatting with AI in no time.

In my experiment, I used `tinyllama` , `phi` and `llava` LLMs. But you may try different large language models that are available in [Ollama's library][5].

📋

You should have at least 8 GB of RAM available to run the 7B models, 16 GB to run the 13B models, and 32 GB to run the 33B models.

#### TinyLlama

Let's start with [TinyLlama][6] which is based on 1.1 billion parameters and is a perfect candidate for the first try.

To download and run TinyLlama, you need to type this command:

```

    ollama run tinyllama

```

![][7]

It will take a few seconds to download the language model and once it is downloaded, you can start chatting with it.

The question I pose to the AI is: "What is the use case of div tag in html?"

![][8]

Here's the full answer with the time it took to finish it:

![][9]

Well, well, well! Who would have guessed that AI would have worked this fast on a Raspberry Pi?

#### phi

Moving on to some bigger models like [phi][10] which is a 2.7B parameters-based language model. I think our Raspberry Pi can handle this as well.

To install and run this model, type this command:

```

    ollama run phi

```

![][11]

Try asking it some questions, like I did: "What is the difference between a network switch and a hub?"

![][12]

and here's the complete answer from phi with other details:

![][13]

#### llava

This is the biggest LLM that I test as it comes with 7B parameters. I ask it to describe an image instead of asking simple questions.

I am using a 4 GB model of Raspberry Pi 4 and I don't think that it will work as well like the other language models did above.

But still, let's test it. To install `llava` use this command:

```

    ollama run llava

```

It will take some time to download this model, since it is quite big, somewhere close to 3.9 GB.

![][14]

I am going to ask this model to describe an image of a cat that is stored in `/media/hdd/shared/test.jpg` directory.

![][15]

**I had to terminate the process in the middle since it was taking too long to answer (more than 30 mins).**

But you can see, the response is pretty accurate and if you have the latest Raspberry Pi 5 with 8 GB of RAM, you can run 7B parameter language models easily.

### Conclusion

Combining the capabilities of the Raspberry Pi 5 with Ollama establishes a potent foundation for anyone keen on running open-source LLMs locally.

Whether you're a developer striving to push the boundaries of compact computing or an enthusiast eager to explore the realm of language processing, this setup presents a myriad of opportunities.

Do let me know your thoughts and experience with Ollama in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/raspberry-pi-ollama-ai-setup/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/privategpt-setup/
[2]: https://itsfoss.com/raspberry-pi-ollama-ai-setup/%5Bhttps://ollama.ai/%5D(https://ollama.ai/)
[3]: https://itsfoss.com/content/images/2024/01/ollama-downloads-page-for-linux.png
[4]: https://itsfoss.com/content/images/2024/01/ollama-script-installation-in-raspberrypi.png
[5]: https://ollama.ai/library
[6]: https://github.com/jzhang38/TinyLlama
[7]: https://itsfoss.com/content/images/2024/01/installing-tinyllama-llm-using-ollama-in-raspberrypi.png
[8]: https://itsfoss.com/content/images/2024/01/asking-question-from-tinyllama-in-ollama-in-raspberrypi.webp
[9]: https://itsfoss.com/content/images/2024/01/full-answer-of-tinyllama-llm-in-ollama-inside-a-raspberrypi.png
[10]: https://huggingface.co/microsoft/phi-1_5
[11]: https://itsfoss.com/content/images/2024/01/installing-phi-llm-using-ollama-in-raspberrypi.png
[12]: https://itsfoss.com/content/images/2024/01/switch-hub-question-from-phi-llm-in-ollama-inside-raspberrypi.webp
[13]: https://itsfoss.com/content/images/2024/01/full-answer-of-phi-llm-about-switches-in-ollama-inside-a-raspberrypi.png
[14]: https://itsfoss.com/content/images/2024/01/installing-llava-llm-using-ollama-in-raspberrypi.png
[15]: https://itsfoss.com/content/images/2024/01/combine-picture-of-a-cat-and-full-answer-of-llava-llm-describing-a-cat-in-ollama-inside-a-raspberrypi.png
