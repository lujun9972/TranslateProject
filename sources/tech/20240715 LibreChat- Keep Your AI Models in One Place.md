[#]: subject: "LibreChat: Keep Your AI Models in One Place"
[#]: via: "https://itsfoss.com/librechat-linux/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

LibreChat: Keep Your AI Models in One Place
======

[![Warp Terminal][1]][2]

One problem AI users often face is the constant need to switch the chat interface.

ChatGPT might be good at many things but Perplexity is better at searching the web and answering your questions.

In fact, you may feel like asking the same question to another AI model if you are not satisfied with the current AI's answer.

But logging into another AI and then copy pasting the same questions is cumbersome task.

This is why there are tools that allow you to use more than one AI model from a single interface. However, most of such services are paid.

And this is where [LibreChat][3] comes into the picture.

Let's dive in and discover how this game-changing platform can enhance your digital experience.

### What is LibreChat AI?

**LibreChat AI** is an open-source platform that allows users to chat and interact with various AI models through a unified interface. You can use OpenAI, Gemini, Anthropic and other AI models using their API. You may also use [Ollama][4] as an endpoint and use LibreChat to interact with local LLMs. It can be installed locally or deployed on a server.

LibreChat is designed to be highly customizable and supports a wide range of AI providers and services. Let me summarize its main features:

  * **Free and Open Source:** Accessible to everyone without any costs.
  * **Customization:** Offers extensive options to tailor the platform to individual preferences.
  * **Multi-AI Support:** Integrates with numerous AI models and services.
  * **Unified Interface:** Provides a consistent experience for interacting with different AI models.



![LibreChat Official website homepage][5]

### Installing LibreChat

Getting LibreChat AI up and running is a straightforward process, with two primary methods: **NPM** and **Docker** installation.

While both options offer advantages, **Docker is my preferred choice for its simplicity and efficiency**. However, we'll explore both in this article.

You can also refer to the [official documentation][6] for detailed installation instructions on LibreChat. I must say that they have done a great job by providing a comprehensive guide covering every step of the process.

![LibreChat documentation page][7]

#### Method 1: Install LibreChat with NPM

Before you begin with the installation, make sure that you have all the prerequisites for our project:

**Prerequisites:**

  * Node.js 18+: [https://nodejs.org/en/download][8]
  * Git: [https://git-scm.com/download/][9]
  * MongoDB (Atlas or Community Server)
    * [MongoDB Atlas][10]
    * [MongoDB Community Server][11]



Once they are installed, you can move forward setting-up your openAI clone interface.

**Preparing installation environment**

First, you need to clone the official LibreChat repository as it contains all the files you need to build LibreChat:

```

    git clone https://github.com/danny-avila/LibreChat.git

```

Navigate to the cloned directory:

```

    cd LibreChat

```

Now you create a `.env` file from the `.env.example`

```

    cp .env.example .env

```

🚧

Edit the newly created `.env` file to update the `MONGO_URI` with your own

![][12]

**Building LibreChat**

Once the preparation steps have finished, we can build the project from the source in a few simple steps.

To install the dependencies:

```

    npm ci

```

![Downloading all the dependencies][13]

This command will build the frontend of LibreChat:

```

    npm run frontend

```

![Building the frontend of LibreChat][14]

💡

In the documentation, they directly build the backend, but during testing, I learned that you first need to run the MongoDB server. Otherwise, it'll throw errors and won't work at all.

MongoDB requires a data directory to store its data files. Thus, create a directory on your system where you want to store the MongoDB data files (e.g., `/path/to/data/directory`).

After that, you need to be in the same directory where the MongoDB has been installed i.e. `/usr/bin` then just type this command:

```

    ./mongod --dbpath=/path/to/data/directory

```

Now you can build the backend (ignore the errors):

```

    npm run backend

```

![][15]

You have successfully installed LibreChat. You can access it by visitng [http://localhost:3080/][16]

#### Method 2: Install LibreChat using Docker

Okay hear me out! This explains my frustration. So, it took me just a one liner command to run LibreChat in Docker. After battling with all the pop-ups & dependency errors, this was like a walk in the park.

**Please ensure that you have Git and Docker installed on your system.**

The first few steps will remain the same like cloning the repository:

```

    git clone https://github.com/danny-avila/LibreChat.git

```

and creating `.env` file from `.env.example` :

```

    cp .env.example .env

```

The docker compose file is already provided in the repository that we cloned, thus all we need to do is run our docker:

```

    sudo docker compose up -d

```

![Running LibreChat on Docker][17]

To access the LibreChat, visit [http://localhost:3080/][16].

### First run of LibreChat

Getting started with LibreChat involves a straightforward login process.

![][18]

You do have to signup first to login.

![][19]

Once you've navigated that initial step, you're greeted by a minimalist interface that's almost reminiscent of ChatGPT's clean design. It's a no-frills approach that puts the focus squarely on the conversation.

![LibreChat first look][20]

There is an option to create custom prompts as well:

![Creating prompt pane for LibreChat \(click to expand\)][21]

You can customize LibreChat to your liking by going to the settings pane:

![][22]

While to some people, it might not be as visually striking as some other platforms, the simplicity is refreshing and allows you to dive right into interacting with the AI without distractions.

### Accessing AI models using their API

LibreChat operates as a gateway to various AI models. It provides a platform to access and utilize the capabilities of models from other providers like OpenAI's ChatGPT, Google's Gemini, and others.

This means that to fully experience LibreChat's potential, you'll need to have API access to these external AI services.

For this tutorial, I have used Google's Gemini (free) API to have a conversation with our AI assistant. Unfortunately, I couldn't test with OpenAI's API since during testing they flagged my account and banned me.

#### Getting Google's API key:

For Google, you can either use the **Generative Language API** (for Gemini models), or the **Vertex AI API** (for Gemini, PaLM2 & Codey models).

To use Gemini models through Google AI Studio, you’ll need an API key. If you don’t already have one, create a key in [Google AI Studio][23].

Once you have your key, provide the key in your .`env` file, which allows all users of your instance to use it:

```

    GOOGLE_KEY=mY_SeCreT_w9347w8_kEY

```

Or you can enter it via GUI by selecting your prefered AI provider i.e. Google in our case:

![][24]

After that, it'll prompt you to enter your API key:

![][25]

Now we are ready to chat with our Chat BOT.

### Results

Since LibreChat is essentially a wrapper for powerful AI models housed in massive data centers, you can expect lightning-fast response times and minimal latency.

Here are a few results:

![LibreChat's reply to the question about difference between ARM & X86 architecture][26]

Another one:

![LibreChat's reply to create a docker-compose file for Nextcloud][27]

As per [documentation][28], LibreChat can also integrate with Ollama. This means that if [you have Ollama installed on your system][29], you can run local LLMs in LibreChat.

Perhaps we'll have a dedicated tutorial on integrating LibreChat and Ollama in the future.

### Final Thoughts

LibreChat presents an intriguing proposition for users seeking AI interaction. Its open-source nature and ability to leverage multiple AI models offer a degree of flexibility and potential customization that proprietary platforms might lack.

In terms of alternatives, LibreChat could be a compelling option for Linux users who might find Copilot for Windows to be exclusive.

Unfortunately, due to account restrictions, I couldn't personally test the OpenAI API, a limitation that prevented a more comprehensive evaluation, specially the "Chat with documents" feature.

Nevertheless, LibreChat's potential is undeniable, and its evolution will be interesting to watch.

If you have more open source AI projects in mind, feel free to share with us!

--------------------------------------------------------------------------------

via: https://itsfoss.com/librechat-linux/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.librechat.ai/
[4]: https://itsfoss.com/ollama/
[5]: https://itsfoss.com/content/images/2024/07/librechat-homepage.png
[6]: https://www.librechat.ai/docs
[7]: https://itsfoss.com/content/images/2024/07/librechat-documentation.png
[8]: https://nodejs.org/en/download
[9]: https://git-scm.com/download/
[10]: https://www.librechat.ai/docs/configuration/mongodb/mongodb_atlas
[11]: https://www.librechat.ai/docs/configuration/mongodb/mongodb_community
[12]: https://itsfoss.com/content/images/2024/07/librechat-mongodb-uri.png
[13]: https://itsfoss.com/content/images/2024/07/librechat-installing-dependencies-1.png
[14]: https://itsfoss.com/content/images/2024/07/librechat-building-frontend.png
[15]: https://itsfoss.com/content/images/2024/07/librechat-server-started-at-localhost.png
[16]: http://localhost:3080/
[17]: https://itsfoss.com/content/images/2024/07/librechat-docker-compose.png
[18]: https://itsfoss.com/content/images/2024/07/librechat-login.png
[19]: https://itsfoss.com/content/images/2024/07/librechat-signup.png
[20]: https://itsfoss.com/content/images/2024/07/librechat-homepanel.png
[21]: https://itsfoss.com/content/images/2024/07/librechat-system-prompt.png
[22]: https://itsfoss.com/content/images/2024/07/librechat-settings.png
[23]: https://aistudio.google.com/app/apikey
[24]: https://itsfoss.com/content/images/2024/07/librechat-selecting-google-gemini.png
[25]: https://itsfoss.com/content/images/2024/07/librechat-gemini-api-gui.png
[26]: https://itsfoss.com/content/images/2024/07/librechat-response-difference-between-arm-x86.png
[27]: https://itsfoss.com/content/images/2024/07/librechat-response-nextcloud-docker.gif
[28]: https://www.librechat.ai/blog/2024-03-02_ollama
[29]: https://itsfoss.com/ollama-setup-linux/
