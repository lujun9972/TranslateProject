[#]: subject: "Using LM Studio to Run LLMs Easily, Locally and Privately"
[#]: via: "https://itsfoss.com/lm-studio-linux/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Using LM Studio to Run LLMs Easily, Locally and Privately
======

[![Warp Terminal][1]][2]

Break free from limited cloud-based AI models that are too pricey and do not respect your privacy by installing LLMs directly on your computer. This empowers you with greater control over your data, all without relying on big tech companies.

My previous articles explored building your own [Private GPT][3] or running [Ollama][4], empowering you with [advanced open source LLMs][5]. However, these solutions often require running lengthy commands in the terminal.

[LM Studio][6] streamlines the process entirely. Imagine a user-friendly application akin to the familiar interface of ChatGPT, where you can effortlessly download and utilize various Large Language Models.

### Installing LM Studio on Linux

✋

LM Studio Linux app is currently in the beta stage.

LM Studio provides an AppImage for Linux users. If it's your first time installing an AppImage program, you can read our [AppImage guide][7].

You can download the AppImage from the [LM Studio website's homepage][6].

![LM Studio's official website][8]

### Exploring LM Studio

Now let's explore the LM Studio and try running some AI models for fun:

![LM Studio first look][9]

As you can see, on the top we have a search bar to look for any AI models, you can even paste the direct URLs of repositories from [Hugging Face][10].

💡

Hugging Face is an AI company renowned for its open-source libraries, like Transformers, that facilitate easy access and development of advanced machine learning models for natural language processing and other tasks.

#### Downloading the first AI Model

It is quite easy to download AI models in LM Studio. Just search for the model, look for the relevant specs and requirements, and download it.

For example, I am running this on my laptop with 16GB RAM on a Ryzen 5 5500U with no dedicated GPU; thus, I would look for some small models with 2B to 7B instruct parameters.

![Searching for Llama 2][11]

Okay all this information might intimidate you; let me explain what is happening here:

  * I searched for the [Llama 2 model][12] in the search bar at the top
  * The left pane shows you the different models relevant to your search
  * Once a model is selected, you can see its specs and download options on the right pane



If you look closely, you will notice that there are four options that says **"FULL GPU OFFLOAD POSSIBLE".** I will choose a model from those options only because LM Studio already analyzed my system resources and suggested the most suitable options.

![LLaMA 2 downloading pane][13]

#### Running LLaMA 2 model

Once an AI model has been downloaded, let's start chatting with the LLM.

Load the model first and then all you have to do is go to the **"Chat"** section (chat bubble emoji in left), at the top, press the drop down menu that says **"Select a model to load"** and from below you can select any model you have downloaded.

![Loading LLaMA 2 model to chat][14]

Now that you have selected your model, it's time to chat with your personal, totally private, offline AI assistant.

![Chatting with AI Model \(Click to Expand\)][15]

I have changed the default system prompt to a personalized one i.e. "You are a French language assistant AI" and I must say, the response was quite accurate.

I know that was a prompt you weren't expecting, but I'm learning French, so bear with me.

Let's ask our model to write a `docker-compose` file for WordPress with MySQL database:

![Writing docker-compose file in action][16]

It's already been a minute and it's still going:

![Same docker-compose file after 2 minute][17]

Okay, I don't want you guys to feel the pain of waiting for it to finish. It took 4 minutes and 56 seconds. No wonder AI computing is expensive. You need good hardware (read GPU).

This was the response if you are wondering:

![Finally a response after 4 minutes of struggle][18]

### Final Thoughts

If you have a powerful system with plenty of RAM and dedicated GPU(s), I highly recommend installing LM Studio.

You have full control over your data since it runs locally on your machine. LM Studio also features a user-friendly interface and allows you to experiment with the latest AI models beyond what companies typically offer. This is truly a win-win situation.

And yes I am well aware the system I use for testing was quite slow but I was targeting the average Joe and yes I will try to run this on a Raspberry Pi because why not, that is the fun of tinkering with technology.

If you have suggestions for more AI tools, feel free to comment.

--------------------------------------------------------------------------------

via: https://itsfoss.com/lm-studio-linux/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/privategpt-setup/
[4]: https://itsfoss.com/raspberry-pi-ollama-ai-setup/
[5]: https://itsfoss.com/open-source-llms/
[6]: https://lmstudio.ai/
[7]: https://itsfoss.com/use-appimage-linux/
[8]: https://itsfoss.com/content/images/2024/06/lm-studio-official-wwebsite.png
[9]: https://itsfoss.com/content/images/2024/06/lm-studio-firstlook.png
[10]: https://huggingface.co/
[11]: https://itsfoss.com/content/images/2024/06/searching-llama2-in-lm-studio.png
[12]: https://www.ibm.com/topics/llama-2
[13]: https://itsfoss.com/content/images/2024/06/llama2-download-pane-lm-studio.png
[14]: https://itsfoss.com/content/images/2024/06/loading-ai-model-in-lm-studio.png
[15]: https://itsfoss.com/content/images/2024/06/chatting-with-llama2-in-lm-studio.png
[16]: https://itsfoss.com/content/images/2024/06/docker-compose-query-llama2-lm-studio.gif
[17]: https://itsfoss.com/content/images/2024/06/ongoing-docker-compose-query-llama2-lm-studio.gif
[18]: https://itsfoss.com/content/images/2024/06/final-docker-compose-response-lm-studio.png
