[#]: subject: "Meet Open NotebookLM: An Open Source Alternative to Google's NotebookLM"
[#]: via: "https://itsfoss.com/open-notebooklm/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Meet Open NotebookLM: An Open Source Alternative to Google's NotebookLM
======

[![Warp Terminal][1]][2]

Google's latest AI offering, NotebookLM took the tech world by storm.

Whether you are a university student or a working professional, getting time to sit and read is not an option for many, and often, the text-heavy PDFs get pushed to the bottom of the to-read pile.

Feed your documents to Google's NotebookLM and it creates a podcast styled conversation between two people discussing the core of the document.

Benefit? Instead of reading, you can just listen to the 'important' parts in podcast style while commuting, exercising, or doing chores.

However, not everyone trusts Google with their data, and it is likely to be a paid feature in the future.

Luckily, I came across an open source alternative.

### What is Open NotebookLM?

Open [NotebookLM][3] turns PDFs into dynamic podcast-style audio files using [**Llama 3.1**][4] for natural language generation and [**MeloTTS**][5] for text-to-speech.

Unlike traditional text readers, it structures the content into a natural conversation between speakers.

While the language model processes up to 100,000 characters, MeloTTS handles speech synthesis, delivering a range of tones from "fun" to "formal."

Open NotebookLM allows users to test the tool via its Hugging Face page or install it locally from its [GitHub repository][6].

#### Key Features

  * **PDF to Podcast** : Upload any PDF, and it’s automatically transformed into an audio file.
  * **Interactive Dialogue** : The generated dialogue simulates a podcast conversation, enhancing listener engagement.
  * **User-Friendly Interface** : Thanks to Gradio, users can interact with the tool through a simple web interface, even without deep technical knowledge.



### Access and Usage

If you’re just starting out and want to see how Open NotebookLM works, you can check out the official project hosted on [Hugging Face][3].

This lets you upload a PDF and quickly see it converted into a podcast without any installation. If you prefer to install it locally, follow these steps:

  1. Clone the [GitHub repository][6].



```

    git clone https://github.com/gabrielchua/open-notebooklm.git
    cd open-notebooklm

```

![][7]

  2. Set up a Python virtual environment.



```

    python -m venv .venv
    source .venv/bin/activate

```

![][8]

  * `python -m venv .venv`: Creates a virtual environment in the `.venv` directory, isolating project dependencies from the global Python setup.
  * `source .venv/bin/activate`: Activates the virtual environment, so all Python commands and packages used will be from the `.venv` environment.


  3. Install dependencies from `requirements.txt` , this may take a bit of time to install them all so sit back & relax.



```

    pip install -r requirements.txt

```

![][9]

  4. Run the application:



💡

Ensure you set your API key as the `FIREWORKS_API_KEY` environment variable before running the application.

```

    python app.py

```

![I didn't have the API key for this article thus it popped me errors, but if you set the API key as environment variables then you are good to go.][10]

### Performance

If you're like me and trying the [Hugging Face web app][11], be prepared for a long wait. I waited over 30 minutes in a queue just to test Open NotebookLM, and initially faced a few errors, but managed to access it.

You can check out my video of the interaction with a PDF I downloaded from Wikipedia about Linux:

As you can see in the video I opted for the "fun" tone & the AI amusingly presented the history as if **Linus Torvalds** himself were speaking in a _female voice_ , which gave me quite a chuckle 😆

The tool not only generated engaging audio but also created a readable dialogue alongside it. I was impressed by how easy it was to download the podcast as an MP3 file.

### Comparing Google NotebookLM and Open NotebookLM

While Open NotebookLM offers a solid, open-source alternative for converting PDFs into podcasts, [**Google’s NotebookLM**][12] provides a more comprehensive, free tool that generates summaries and allows interactive queries about uploaded documents.

However, Google’s track record raises concerns about future monetization and data privacy, as they often leverage user data to train AI models.

Though NotebookLM is free for now, it could easily shift behind a paywall or impose usage restrictions.

Open NotebookLM, on the other hand, while not as feature-rich as Google's version, it offers an important alternative for users who value data privacy and the flexibility of an open-source approach.

### My Thoughts

After testing Open NotebookLM, it’s clear the project has potential. While the Hugging web app provides an accessible way to try it out, long queues and initial errors were frustrating.

That said, the idea of converting documents into podcasts is valuable, especially for busy individuals who need to consume content on the go.

In conclusion, Open NotebookLM delivers a fresh and practical approach to document consumption, especially with its open-source foundation.

Conversely, Google’s tool, though polished, feels like a double-edged sword with potential hidden costs in terms of data privacy and future accessibility.

Both have their strengths, but as with most AI-driven tools, the trade-offs depend on user priorities, whether it’s data control or convenience.

If it interests you, check out the project on GitHub, give it a star maybe.

[Open NotebookLM on GitHub][6]

--------------------------------------------------------------------------------

via: https://itsfoss.com/open-notebooklm/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://huggingface.co/spaces/gabrielchua/open-notebooklm
[4]: https://huggingface.co/meta-llama/Llama-3.1-405B
[5]: https://huggingface.co/myshell-ai/MeloTTS-English
[6]: https://github.com/gabrielchua/open-notebooklm/tree/main
[7]: https://itsfoss.com/content/images/2024/10/open-notebooklm-git-repo-1.png
[8]: https://itsfoss.com/content/images/2024/10/open-notebooklm-python-venv.png
[9]: https://itsfoss.com/content/images/2024/10/open-notebooklm-requirements.png
[10]: https://itsfoss.com/content/images/2024/10/open-notebooklm-api-error-1.png
[11]: https://huggingface.co/webapp
[12]: https://blog.google/technology/ai/notebooklm-google-ai/
