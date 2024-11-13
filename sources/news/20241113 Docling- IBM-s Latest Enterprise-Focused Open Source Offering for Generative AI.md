[#]: subject: "Docling: IBM's Latest Enterprise-Focused Open Source Offering for Generative AI"
[#]: via: "https://news.itsfoss.com/docling-ibm-open-source-gen-ai/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Docling: IBM's Latest Enterprise-Focused Open Source Offering for Generative AI
======
It's good to see open source toolkits for making generative AI.
[![][1]][2]

[IBM][3] has a rich history in the tech space, with the company constantly evolving according to global trends and pushing for the next big thing in the industry. Unsurprisingly, the AI craze has not gone unnoticed by them.

They [recently introduced][4] the Granite 3.0 family of open source LLMs, along with updates to [RHEL AI][5], their enterprise-grade AI platform. But, it appears they are not done, as they have officially launched **Docling** , a long-running project of theirs ( _initially released back in July 2024_ ).

### Docling: What To Expect?

![The Docling process flow. \(Source: GitHub\)][6]

Developed as an open source toolkit under the [MIT License][7], **Docling is a tool for extracting documents and exporting them into Markdown and JSON** for easy reading by large language models (LLMs) and foundation models.

It is **powered by two models** that were designed by IBM researchers. The first is the vision model, which employs object-detection techniques to figure out the layout of a page in a document, then subsequently identifying and classifying blocks of text, images, tables, etc.

The other is [TableFormer][8], which is meant to convert image-based tables into machine-readable formats with rows and columns of cells.

To showcase its ability to perform, **IBM has stated that they have tested it extensively** , with the researchers behind [InstructLab][9] using Docling to extract information from PDFs to train InstructLab's underlying AI models.

They used it for **analyzing 2.1 million PDFs** from [Common Crawl][10], converting the raw data into usable AI training data. Moreover, there are **plans to go through a whopping 1.8 billion PDF files** and feeding the extracted data into a future version of [Granite][11].

Docling is **targeted for enterprise use** , where crunching a large amount of data and organizing it properly is crucial. It can be used to process things like technical manuals, user guides, specifications, legal documents, and really any other structured document.

A **typical use case for it would be to train internal AI models on company data** to aid in knowledge sharing and optimizing workflows. The IBM researchers are, in fact, planning to introduce support for more complex data types such as math equations, charts, etc.

#### Want To Check It Out?

Docling is equipped with a command-line interface and a Python API, and it has been **optimized to run on conventional laptops**. IBM claims that it only takes five lines of code to configure/integrate it with open source LLM frameworks like [LlamaIndex][12] and [LangChain][13].

You can get started with Docling by going through its [documentation][14] and the [GitHub][15] repository. If you would like to learn more about it, the [announcement blog][16] is definitely worth a read.

[Docling][15]

**Suggested Read** 📖

![][17]

* * *

[Get It's FOSS Plus Membership][18]

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/docling-ibm-open-source-gen-ai/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://www.ibm.com/
[4]: https://news.itsfoss.com/red-hats-ai-ibm-granite/
[5]: https://news.itsfoss.com/red-hat-gen-ai/
[6]: https://news.itsfoss.com/content/images/2024/11/Docling_Process_Flow_Banner-1.png
[7]: https://opensource.org/license/mit
[8]: https://research.ibm.com/publications/tableformer-table-structure-understanding-with-transformers
[9]: https://instructlab.ai/
[10]: https://commoncrawl.org/
[11]: https://www.ibm.com/granite
[12]: https://www.llamaindex.ai/
[13]: https://www.langchain.com/
[14]: https://ds4sd.github.io/docling/
[15]: https://github.com/DS4SD/docling
[16]: https://research.ibm.com/blog/docling-generative-AI
[17]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
[18]: https://itsfoss.com/#/portal/signup
