[#]: subject: "Finally! Brave Brings Local AI to the Browser"
[#]: via: "https://news.itsfoss.com/brave-browser-local-ai/"
[#]: author: "Ankush Das https://news.itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Finally! Brave Brings Local AI to the Browser
======
A step in the right direction to protect users' privacy.
[![][1]][2]

Brave browser is one among the best free and open-source web browser based on Chromium.

Sure, it has its quirks and a bit of a controversial history of crypto tech being integrated to it. But, it is still arguably one of the fastest and privacy-focused browsers out there.

To make things right, it has tried to approach the AI integration to its browser in an interesting manner.

Earlier this year, Brave started experimenting with a " _Bring Your Own Model (BYOM)_ " for Brave Leo's AI functionality on its nightly (or development) releases. This idea aimed to give users the ability to run custom AI models or local AI models to use Brave Leo safely.

With this feature, you do not have to trust Brave's integrated AI model or any remote connections. You can just slide in your favorite local model using [Ollama][3], and keep the conversations on your device 🔒

And, now, **this functionality is finally available on Brave 1.69 or higher**. My colleague spotted this on 1.70, and I believe it is worth pointing it out 🤯

### Use Your Custom Local or Remote AI Models

![][4]

I tested Brave's BYOM feature using a local AI model, i.e., **llama3**. You can utilize [Ollama to download the model][5] on Linux or other platforms.

![][6]

Once done, head to **Brave's Leo settings** to add the model using the following information:

  * **Label:** Any custom display name that you see fit
  * **Model request name** : Put the model name here
  * **Server endpoint** : The endpoint URL provided for the AI model. In our case, it is _<http://localhost:11434/v1/chat/completions>_ (for local models via Ollama).
  * **API key** : If you are using a remote AI model, like OpenAI's ChatGPT or something else. For local AI models, you do not need it.



As soon as you add it, you can see it listed as:

![][7]

Next, you need to set it as the " **Default model for new conversations** " in the same settings and restart the browser for Brave Leo to use it. The screenshot below should guide you how to do that:

![][8]

Or, you can just select the custom AI model when using Brave Leo, as shown below:

0:00

/0:12

1×

### Wrapping Up

The most exciting thing about Brave's BYOM feature is that you no longer require a separate [Web UI to run LLMs][9]. Of course, **Page Assist** is one of my favorites if you want to try using local AI models on other browsers. But, if you are using Brave, you no longer require that.

I think with this functionality, Brave gives you a good control of what AI model you would like to use (how you would like to use) and when you do not. It is better than a forced integration by any web browser for you to use AI assistance.

_💬 What do you think about Brave's new approach to AI integration? Share your thoughts in the comments below!_

**Suggested Read** 📖

![][6]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/brave-browser-local-ai/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://itsfoss.com/ollama/
[4]: https://news.itsfoss.com/content/images/2024/09/brave-leo-llama3.png
[5]: https://itsfoss.com/ollama-setup-linux/
[6]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[7]: https://news.itsfoss.com/content/images/2024/09/brave-llama3-model.png
[8]: https://news.itsfoss.com/content/images/2024/09/changing-leo-default-ai-model.png
[9]: https://itsfoss.com/ollama-web-ui-tools/
