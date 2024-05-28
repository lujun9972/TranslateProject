[#]: subject: "I Installed AI Apps in a Single Click on My Linux System With Pinokio"
[#]: via: "https://itsfoss.com/install-ai-apps-pinokio-linux/"
[#]: author: "Ankush Das https://itsfoss.com/author/ankush/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Installed AI Apps in a Single Click on My Linux System With Pinokio
======

[![Warp Terminal][1]][2]

AI is everywhere. But, not all kinds of AI tools are accessible to the end-users.

Sure, you can try something like ChatGPT effortlessly or a couple of other AI tools through your web browser. But, what about running an AI app locally on your computer while protecting your privacy?

You do not have to pay anyone and still be able to safely use an AI app using your computer to generate text, generate images, videos, separate audio, and lots more.

Pinokio is an open-source tool that lets you do that with a single click. Here, let me tell you more about it and how to use it.

### Pinokio: Making AI Apps Easy to Run

![AI-generated image using Pinokio by It's FOSS][3]

Normally, to deploy an AI app locally, you need to go through a decent amount of mumbo jumbo instructions, and with that method, an end-result is not guaranteed either.

Pinokio comes to the rescue, describing itself as an "AI Browser". It is an app that utilizes 1-click scripts to install and configure various AI-powered apps or chatbots on your computer.

It stores them all in a single folder, and lets you customize some of it after you install it (if needed).

📋

Pinokio needs a good amount of system resources for all the AI apps to run smoothly, and enough storage (30-40 GB of free storage at least) to install all kinds of dependencies needed to run what you need.

**If you have a decent system with at least four–six cores, and a mid-range GPU with 6-12 GB of VRAM. You should be able to run some things smoothly.**

I have an **NVIDIA** **RTX** **3060 Ti graphics card with 8 GB of VRAM**. And, I did face some performance hiccups for tasks like text to video.

Don't be discouraged by not trying it — but if you think your system gets stuck and is unresponsive, you might have to try other tools that aren't as resource intensive. Some AI apps are more resource-intensive. Honestly, that's the only downside of trying to run an AI app locally.

### Features of Pinokio AI Browser

To give you an overview of what Pinokio is capable, let me highlight the key points:

  * It runs locally, without sharing any data to the cloud, making it a privacy-friendly option.
  * It is a free and open-source application.
  * You get cross-platform support
  * Easy to use



### How to Install an AI App Using Pinokio?

![][4]

First, **you need to install Pinokio AI browser on your Linux system**. They offer multiple packages on the [GitHub releases section][5] for you to get it installed including AppImage, .deb, and .rpm.

[Pinokio (GitHub)][5]

I tried it on **Ubuntu 24.04 LTS** , and I installed the deb package. I tried the AppImage file as well, but the 1-click installation process did not work as expected.

So, I encourage you to try the deb/rpm package instead as per your distribution.

For help, you can refer to our tutorials:

  * Ubuntu/Debian/APT: [3 Ways to install deb files][6]
  * Fedora/DNF: [Installing RPM files][7]



Once you have installed, just search for Pinokio and launch the browser. It first asks you to set the path to store things, and the theme for your user experience:

![][8]

Of course, I went with the dark theme ( _sorry to the dark mode fans looking at the bright white screenshot 😉_ )

Once you hit “Save”. It takes you to the welcome page with a button to visit the **Discover** page.

![][9]

You can explore a wide range of options when you click on to visit the Discover page.

![][10]

It does not show the scripts available in any specific order (popular to lesser-known) or best to worst. So, all you get is a grid list to explore options.

All you have to do is select the one you want to try, and then hit the download button as shown in the image below:

![][11]

For the first time, it will install several dependencies needed for all kinds of projects:

![][12]

Once done, it will prompt you to download the script for the AI tool you selected:

![][13]

When you hit download here, the script will start and the installation/configuration required will start making progress. Some AI apps might take a while, and others could be quick if the packages required already exist.

Some AI apps need a lot of download (upwards of 6 GB). So, make sure, you have a good internet connection and storage space to accommodate that. Here's how it looks when it starts downloading/installing:

![][14]

When the installation is complete, it will show up a "Start" option in the sidebar and then when you start it, you can click on the "Web UI" option to access the app that you want to use.

![][15]

🚧

I tried about 10 different models, and ended up downloading plenty of files. However, only a handful of them worked. So, it might need some troubleshooting with some apps, and some front-end apps might need you to set up the backend manually before you can use it.

The Pinokio AI browser hasn't seen any development activity for 9–10 months. Maybe, with articles like this, more contributors can help revive the project and fix existing issues.

Some of the AI applications that successfully work include:

  * **Foocus** — an image generation app
  * **FaceFusion** — face swapping/enhancement
  * **AudioSep** — separate anything from an audio clip that you describe



I also stumbled upon interesting chatbots like ChatGPT, but it didn't work. Maybe you can try exploring the [open-source ChatGPT alternatives][16] for this job:

![][17]

And, among the ones I was able to run, the Foocus image generator immediately became my favorite, and I plan to use it for a while, at least, for my social media.

![][18]

What do you think about it? I am sure this will be most of us! Cats, catnips, anime, and more stuff! Looks mind-blowing right? 🤯

The image generator gives you the ability to generate photorealistic images, anime style, and more. You can adjust the quality, add constraints, specify the number of images, aspect ratio of the final image, and more.

There was also a model that lets us generate comic pages using text prompts. I did not give it a try. You might want to explore that as well.

Curious about video generators? That's also there. But, I got " _out of memory_ " error when I ran the VideoCrafter app. Maybe it needs more than 8 GB VRAM.

This is how my storage folder looks like, with one app installed:

![][19]

So, yeah, it may not be the most convenient solution in every way. But, if you want to run AI apps locally without needing to know countless technical details, Pinokio browser seems like a fantastic option for the apps that work in it.

You can also refer to the [documentation][20] for greater details.

[Pinkio AI Browser][21]

### The AI Year is Exciting and Worrying

At the end of the day, I must mention that I'm excited to use all the AI tools at my disposal powered by generative models (or some [open-source LLMs][22]). And, if we can do all this now, what would we be able to do in the near future?

_💬 Just leaving you with food for thought, let me know what you think in the comments down below!_

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-ai-apps-pinokio-linux/

作者：[Ankush Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/ankush/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2024/05/ai-generated-itsfoss-feat.png
[4]: https://itsfoss.com/content/images/2024/05/ai-app-generating-photos.png
[5]: https://github.com/pinokiocomputer/pinokio/releases
[6]: https://itsfoss.com/install-deb-files-ubuntu/
[7]: https://itsfoss.com/install-rpm-files-fedora/
[8]: https://itsfoss.com/content/images/2024/05/pinokio-first-screen.png
[9]: https://itsfoss.com/content/images/2024/05/pinokio-welcome.png
[10]: https://itsfoss.com/content/images/2024/05/pinokio-discover-page-screen.png
[11]: https://itsfoss.com/content/images/2024/05/install-download-ai-model.png
[12]: https://itsfoss.com/content/images/2024/05/pinokio-dependencies.png
[13]: https://itsfoss.com/content/images/2024/05/ai-tool-download-script.png
[14]: https://itsfoss.com/content/images/2024/05/install-ai-app-pinokio.png
[15]: https://itsfoss.com/content/images/2024/05/pinokio-web-ui-button-1.png
[16]: https://itsfoss.com/open-source-chatgpt-alternatives/
[17]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[18]: https://itsfoss.com/content/images/2024/05/image-generator-realistic.png
[19]: https://itsfoss.com/content/images/2024/05/pinokio-storage.png
[20]: https://program.pinokio.computer/#/
[21]: https://pinokio.computer/
[22]: https://itsfoss.com/open-source-llms/
