[#]: subject: "Is The AI Open Source? OSI Gives a New Definition to Help Us Know That!"
[#]: via: "https://news.itsfoss.com/osi-ai-open-source-definition/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Is The AI Open Source? OSI Gives a New Definition to Help Us Know That!
======
The OSI finally makes a new definition for open source AI systems,
encouraging organizations to do more instead of slapping the term "open
source."
[![][1]][2]

AI models have taken the tech world by storm, with the underlying systems behind the most popular ones being an enigma because of the various companies' reluctance to completely disclose their source.

Usually, they seem to imply that a competitor might gain an advantage by using their tech. However, there is a more clear-cut issue at hand here.

The training methods and data used to train such proprietary and open weight models are never really shared openly, and we already know that there are plenty of copyrighted/IP-protected pieces of data in the outputs of such models.

The Open Source Initiative (OSI) had [called out Meta][3] on this recently, as they market the [Llama][4] family of models as open source, which, in reality, is open weight at best.

Now, the [OSI][5] has introduced the first version of the long-awaited **Open Source AI Definition** (OSAID), which aims to tackle such issues by defining the concept explicitly.

### Open Source AI Definition: What To Expect?

![Just a stand in image of the OSAID webpage.][6]

Worked on by a diverse mix of organizations and individuals, **the first version of the OSAID has been drafted jointly.**

Organizations involved include the Open Knowledge Foundation, Wikimedia Foundation, Mozilla Foundation, Hugging Face, Amazon, Microsoft, Meta, and many others. ( _OpenAI doesn't seem to have collaborated_ )

Without going too much into the technical aspects of the OSAID, here are some **key points** of the definition that you should be aware of:

  * Anyone can use an open source AI system for any use case, study how it works, modify it according to one's needs, and should be able to share it freely with/without modifications for any purpose.
  * There is a precondition for the above, which is to have access to a “ _preferred form_ ” to make modifications to the AI system.
  * The “ _preferred form_ ” must include things like having access to the complete description of the data used for training, disclosure of the [provenance][7] of the data, listing of all publicly available data, and the source code used to train the AI system. Even the model parameter or configuration settings used are to be provided.



To summarize, the definition covers all “ _fully functional structure and its discrete structural elements_ ” under its purview. This includes things like **the model, the weights, the parameters** , etc.

This means that to meet the OSAID standards, an AI model's entire architecture, along with the smaller components that make it function, must be accessible and modifiable by anyone.

Additionally, the term “AI system” broadly covers any machine-based system that can take in inputs and generate outputs that affect physical or virtual environments for both [explicit and implicit][8] objectives.

You can learn more about OSAID by going through [the definition][9] itself.

#### Closing Thoughts

There is an inescapable pain point here, which is that there is **no clause that stipulates the training data itself be open sourced**. This has led to many people questioning whether this definition truly encompasses the fundamental principles of open source when such a major part is left out.

The OSI is said to be working on updates and defining rules for the maintenance of the OSAID, but they have not clarified how they intend to handle the matter of open sourcing the training data.

But, of course, having this definition is better than not having a standard.

In any case, you can learn more about the OSAID by going through the [deepdive][10] published by the OSI, which shows an overview of the processes and governance-related aspects of the initiative.

_💬 What are your views on OSAID? Do you think they could have done a better job?_

* * *

[Get It's FOSS Plus Membership][11]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/osi-ai-open-source-definition/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://news.itsfoss.com/osi-meta-ai/
[4]: https://www.llama.com/
[5]: https://opensource.org/
[6]: https://news.itsfoss.com/content/images/2024/10/OSAID_Banner.jpg
[7]: https://en.wikipedia.org/wiki/Provenance
[8]: https://www.dictionary.com/e/explicit-vs-implicit/
[9]: https://opensource.org/ai/open-source-ai-definition
[10]: https://opensource.org/deepdive
[11]: https://itsfoss.com/#/portal/signup
