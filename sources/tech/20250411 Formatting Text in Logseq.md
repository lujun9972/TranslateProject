[#]: subject: "Formatting Text in Logseq"
[#]: via: "https://itsfoss.com/logseq-format-text/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Formatting Text in Logseq
======

[![Warp Terminal][1]][2]

Logseq is a highly efficient note-taking and knowledge management app with decent Markdown support.

While using Logseq, one thing to keep in mind is that the text formatting isn't pure Markdown. This is because Logseq uses bullet blocks as the basic unit of content and also supports [Org-mode][3].

Whenever you start a new document or press Enter after a sentence, a new block is created — and this block can be referenced from anywhere within Logseq. That’s part of what makes Logseq so powerful.

Still, formatting your notes clearly is just as important. In this article, we’ll take a closer look at how text formatting works in Logseq.

### Basic Markdown syntax

As I said above, since Logseq supports Markdown, all the [basic Markdown syntax][4] will work here.

You remember the Markdown syntax, right?

Description | Markdown Syntax
---|---
Six Levels of Heading | # Level One
### Level Two
#### Level Three
##### Level Four
###### Level Five
####### Level Six
Hyprlink | [Link Text](Link Address/URL)
Image | ![Image Caption](Image path)
Bold Text | **Bold Text**
Italics Text | *Italics*
Striked-out Text | ~~Striked-out Text~~
In-line code | `inline code`
Code block | ```
code block
```
Table | |Column Header|Column Header|
| ---------------- | ---------------|
| Items | Items |


![Logseq Markdown Rendering][5]

💡

You can press the `/` key to get all the available format options.

### Adding quotes

Quotes can be added in Logseq using two methods.

First, using the [traditional Markdown method of adding a quote][6] by using `>` in front of the text.

```

    > This should appear as a quote

```

Second, since Logseq has Org-mode support, you can create a quote block using the syntax:

```

    #+BEGIN_QUOTE
    Your Quote text here
    #+END_QUOTE

```

You can access this by pressing `<` key and then typing Quote and enter.

🚧

If you are using the quotes with a preceding `>` syntax, then every markdown renderer will render the document properly. The org-mode syntax won't work in all environments.

0:00

/0:15

1×

Adding Quotes in Logseq

### Add an admonition block

Admonition blocks or callouts come in handy for highlighting particular piece of information in your notes, like a tip or a warning.

The warning below is the best example here.

🚧

These admonition blocks are a feature of Logseq app. You cannot expect this to work properly in other apps. So, plain text markdown users should take care in this scenario.

The usual Org-mode syntax for these blocks is:

```

    #+BEGIN_<BLOCK NAME>
    Your Block Text
    #+END_<BLOCK NAME>

```

For example, a simple tip block syntax looks like:

```

    #+BEGIN_TIP
    This is a tip block
    #+END_TIP

```

Let's take a look at some other interesting syntax names:

BLOCK NAME
---
NOTE
TIP
IMPORTANT
CAUTION
PINNED

![Admonition Blocks in Logseq.][7]

You can access this by typing the `<` key and then searching for the required block.

0:00

/0:27

1×

Admonition blocks in Logseq.

### Conclusion

The ability to add a call out box makes your notes more useful, in my opinion. At least it does for me as I can highlight important information in my notes. I am a fan of them and you can see plenty of them in my articles on It's FOSS as well.

Stay tuned with me in this series as I'll share about adding references in Logseq in the next part.

--------------------------------------------------------------------------------

via: https://itsfoss.com/logseq-format-text/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://orgmode.org/worg/org-syntax.html
[4]: https://itsfoss.com/markdown-guide/
[5]: https://itsfoss.com/content/images/2025/01/basic-markdown-samples.png
[6]: https://itsfoss.com/markdown-quotes/
[7]: https://itsfoss.com/content/images/2025/01/admoniton-blocks-in-logseq-image.png
