[#]: subject: "I Found a New Open Source Grammar Checker Tool And I Like it... Well... Kind of"
[#]: via: "https://itsfoss.com/harper-grammar-checker/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Found a New Open Source Grammar Checker Tool And I Like it... Well... Kind of
======

[![Warp Terminal][1]][2]

When it comes to grammar checking, Grammarly is the premium tool for it. It's a proprietary tool and it was among the first one to make a mark as a web-based Grammar checking tool.

Then there is [LanguageTool][3] (partner link). This is the tool that we use here in our team. It is/was open source, made in Germany and offers hosted service for free or for a price (you get additional features). LanguageTool was acquired a couple of years back and since then it's privacy policy has changed as it processes data on US servers, instead of European ones.

Recently, I came across a new grammar checker tool, Harper, and I am sharing my experience and my views on this new open source tool.

### Meet Harper, a local first open source grammar checker

Harper is a new project coming from Automattic developer, Elijah Potter. Automattic is the company behind WordPress, world's most [popular Content Management System][4] (CMS).

The idea is to have a local first tool that doesn't depend on the cloud for any processing or stores away the data. That's a W right there.

Harper is currently available as browser extension and plugin for Obsidian and VS Code. It is a new project and I hope they release more extensions, specially for LibreOffice, in the future.

[Try Harper][5]

I tried the Firefox add-on and tested it while writing this review itself.

### Features that I like

Now, Firefox already has a built-in spell checker and I believe Chrome and other browsers may also have it. So, do we need a third-party browser extension for this purpose? The short answer is yes.

The built-in spell checker in Firefox is limited. It will underline even when you use a brand name. It is essentially a spell checker and hence it just checks for spelling mistakes. It won't warn you if you use "the the" two times in row. It won't warn you even if you write 'an pineapple'.

![Harper is definitely msarter than the default spellchecker of your web browser][6]

Harper does these things and it does that without interacting with a central server. Everything is processed locally.

Here's what Harper is capable of:

  * Spell checking (obvious)
  * Spotting repetition (example, double the the)
  * Spotting multiple simultaneous spaces in a sentence
  * Save words to dictionary (excellent)
  * Correcting the use of a/an
  * Common misused words like "despite of" which should be "in spite of" or "despite" or "its/it's"
  * Styling issue with comma usage



Another interesting feature is that Harper uses different colors for different type of mistakes. This way it is easier to visualize the mistakes and their types.

![][7]

The option to add strangely spelled words into the local dictionary is an excellent feature.

![Save special words in your local dictionary][8]

You can access this local dictionary by accessing the extension settings.

![][9]

And this is where you'll see various settings that you can change. You can even bring your custom dictionary as long as the words are in their own line.

You can also choose between American, British, Canadian, and Australian English dialect.

![Harper extension settings][10]

📋

As you can see, it seems Harper only supports English language at the time of writing this article.

There are also a huge list of rules that detects errors like "along time" and suggest "a long time" as the alternative. The list is huge and that's why there is the option to search for a rule.

There is no option to add your own rules though.

![][11]

### Fast but how fast, really?

Harper claims to be faster than both Grammarly and LanguageTool. I don't have data to prove it. But I can show you this video in which I show how quickly Harper gets into action as I type.

0:00

/0:28

1×

Since the processing is local, the suggestions are pretty fast actually.

### Harper is not perfect, of course

For example, here I deliberately mistyped "video in" as "videoin" and Harper didn't suggest it as one of the possible correct options.

And I think it limits itself to suggest maximum three suggestions or the most it can fit in a line.

![Harper offers limited suggestions][12]

Another thing is that Harper is not as intelligent as I would want it to be. I am an excellent tester for grammar tools. I make so many mistakes and on so many levels that even the best grammar checkers throw in the towel.

That's why I tested Harper against LanguageTool with a sentence with multiple grammatical issues.

Harper was primarily so focused on the spelling of Wikimedia and Cloudflare that it forgot to point out other grammatical mistakes.

![][13]

The weird thing is that both Cloudflare and Wikimedia were correctly spelled. Usually, Harper is good at recognizing brand names, except in this case where it made two false positives in a single sentence.

On the other hand, LanguageTool did indicate that there are some grammatical mistakes worth looking for.

![][14]

Neither could correct the sentence entirely, as the correct sentence I was aiming for was:

> Grammarly, LanguageTool, and Cloudflare went to a bar run by Wikimedia but it was closed, so they went to Wikipedia.

Yeah! I know. No AI can guess what goes in my mind when I make these typos. It takes real intelligence to deal with such stupidity 😜

At least in Ghost, the CMS I use to publish content on It's FOSS, sometime the suggestions tooltip wouldn't close until I start typing something. It's minor but annoying.

### Conclusion

Both Grammarly and LanguageTool have evolved to writing assistant with AI features.

But here's the thing. Sometime simplicity is the best feature you look for. Not everyone is a professional writer looking for additional features to improve their work.

For a casual user, a no-fluff, simple grammar checker is more than sufficient to save them from embarrassing typos and grammatical mistakes in their emails.

And Harper is an excellent choice at that. It is definitely better than your browser's built-in spell checker, it is an [open source software][15] and it processes your data locally.

If you are not dependent on a more professional tool like LanguageTool or Grammarly, you should definitely 'upgrade' to Harper.

It's FOSS turns 13! 13 years of helping people use Linux ❤️

And we need your help to go on for 13 more years. Support us with a Plus membership and enjoy an ad-free reading experience and [get a Linux eBook for free][16].

To celebrate 13 years of It's FOSS, we have a [lifetime membership][17] option with reduced pricing of just $76. This is valid until 25th June only.

If you ever wanted to appreciate our work with Plus membership but didn't like the recurring subscription, this is your chance 😃

[Get Lifetime Membership of It's FOSS][17]

--------------------------------------------------------------------------------

via: https://itsfoss.com/harper-grammar-checker/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://tidd.ly/3UtGpd2
[4]: https://itsfoss.com/open-source-cms/
[5]: https://writewithharper.com/
[6]: https://itsfoss.com/content/images/2025/07/harper-spell-check-features-1.png
[7]: https://itsfoss.com/content/images/2025/07/harper-different-colors.png
[8]: https://itsfoss.com/content/images/2025/07/harper-add-to-dictionary-1.png
[9]: https://itsfoss.com/content/images/2025/07/access-harper-extension-settings-1-1.png
[10]: https://itsfoss.com/content/images/2025/07/harper-settings.png
[11]: https://itsfoss.com/content/images/2025/07/Harper-rules.png
[12]: https://itsfoss.com/content/images/2025/07/harper-limited-suggestions-1.png
[13]: https://itsfoss.com/content/images/2025/07/harper-focus-spelling-1.png
[14]: https://itsfoss.com/content/images/2025/07/languagetool-focu-grammar-1.png
[15]: https://github.com/automattic/harper
[16]: https://itsfoss.com/plus-member-resources/
[17]: https://itsfoss.com/lifetime-membership/
