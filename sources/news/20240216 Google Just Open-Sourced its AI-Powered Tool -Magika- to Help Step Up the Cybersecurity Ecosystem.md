[#]: subject: "Google Just Open-Sourced its AI-Powered Tool 'Magika' to Help Step Up the Cybersecurity Ecosystem"
[#]: via: "https://news.itsfoss.com/google-magika-ai/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Google Just Open-Sourced its AI-Powered Tool 'Magika' to Help Step Up the Cybersecurity Ecosystem
======
This AI tool is open-sourced by Google and available on GitHub.
Google is a name that most of us are familiar with. Even though they are known for [making the headlines][1], they do support an impressive lineup of [open-source projects][2] that have shaped how we experience the internet today.

Now, with the launch of their [AI Cyber Defense Initiative][3], **they have open-sourced Magika** ; their AI-powered file-type identification tool, in a bid to help others take advantage of its capabilities, and build upon it.

**Suggested Read** 📖

![][4]

### Magika: What Is It?

![][5]

Magika is a tool that can be used to detect the [most commonly used][6] file types such as _PNG_ , _JPG_ , _PDF_ , _APK_ , and quite a few others by using the power of artificial intelligence.

Google claims that it can easily outperform traditional tools and methods of file identification, with an **average precision level of over 99%**. The most obvious use case of this would be in the field of cybersecurity, but, more on that later.

Magika isn't something that just appeared out of thin air, **Google had been using it internally** with Gmail, Drive, and Safe Browsing for forwarding files to the relevant security and content policy scanners.

**All of that was possible,** thanks to the implementation of a custom, highly optimized deep-learning model that has been tailored and trained using [Keras][7] that weighs ~1 MB.

Inference times are also quite fast thanks to [Onnx][8], which ensures fast operations in just a matter of milliseconds; similar to non-AI tools, even when using a CPU.

![Source: Google][9]

They also **shared some helpful benchmarks** that compared Magika against other tools, and the average [F1 score][10] resulted in about a 20% uptick in performance when pitched against other tools on a 1M files benchmark with over 100 file types.

#### Helping the Cybersecurity Game

A tool like Magika can be a very potent thing to have by your side, as file scanning at such speeds was previously unheard of. Open sourcing this has opened the door for many security-focused services and products to use this as a reliable component in providing better security to their customers.

Google has themselves already begun work on **integrating Magika into** [**VirusTotal**][11]; the online service which they acquired in 2012. It helps analyze suspicious files and URLs.

And, with Magika AI integration, they plan to further bolster its existing Code Insight functionality.

The official [announcement blog][12] has more details if you are up for it, and stick around a bit longer to **learn how to try Magika**.

#### How Can You Try It?

![][13]

The most straightforward way for trying out Magika is the demo hosted on the [official website][14]. As you can see above, it can easily distinguish file types for multiple uploaded files.

[Magika][14]

📋

The screenshot only shows the first file's result, the rest were below it.

If you want to run it locally, or on a server, then you can install it as a Python package:

```

    pip install magika

```

Then, run it using the following command to start it:

```

    magika

```

For command examples, or official documentation, I highly suggest you give Magika's [GitHub repo][15] a visit. Though, at the time of writing, it had a weird disclaimer at the bottom that said 😐

> This project is not an official Google project. It is not supported by Google and Google specifically disclaims all warranties as to its quality, merchantability, or fitness for a particular purpose.

My best bet is that either this is a mistake, or I am missing something here. Anyway, only time will tell which one is the correct assumption.

[Magika (GitHub)][15]

Another interesting bit 💡

When asked during [a discussion][16] over at Hacker News — why they released a Node module for Magika, one of the co-authors, Elie Bursztein said that:

> We did release the npm package because indeed we create a web demo and thought people might want to also use it. We know it is not as fast as the python version or a C++ version – which why we did mark it as experimental.

> The release include the python package and the cli which are quite fast and is the main way we did expect people to use – sorry if that hasn't be clear in the post.

There also seems to be **plans for a .deb and similar packages** that I spotted on one of the [newly created][17] issues on the Magika repo. It is nice to see that they intend to support Linux in more ways than one.

_💬 What do you think of this move by Google? Was open-sourcing such a tool the right call?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/google-magika-ai/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/google-chrome-incognito-mode/
[2]: https://opensource.google/projects
[3]: https://blog.google/technology/safety-security/google-ai-cyber-defense-initiative/
[4]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[5]: https://news.itsfoss.com/content/images/2024/02/Magika_a.jpg
[6]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types
[7]: https://keras.io/
[8]: https://onnx.ai/
[9]: https://news.itsfoss.com/content/images/2024/02/Magika_b.jpg
[10]: https://en.wikipedia.org/wiki/F-score
[11]: https://www.virustotal.com/
[12]: https://opensource.googleblog.com/2024/02/magika-ai-powered-fast-and-efficient-file-type-identification.html
[13]: https://news.itsfoss.com/content/images/2024/02/Magika_d.jpg
[14]: https://google.github.io/magika/
[15]: https://github.com/google/magika
[16]: https://news.ycombinator.com/item?id=39391688
[17]: https://github.com/google/magika/issues/37
