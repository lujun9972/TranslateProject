[#]: subject: "AI Can Now Easily Unmask Your Secret Online Life (Even If You Use a Fake Name)"
[#]: via: "https://itsfoss.com/news/ai-online-deanonymization/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

AI Can Now Easily Unmask Your Secret Online Life (Even If You Use a Fake Name)
======

[![Warp Terminal][1]][2]

Imagine this: You're on Reddit, Hacker News, or some forum, posting with a silly username like GamerCat2025 or SecretCoderX. You think you are anonymous, and no one knows you and so you can freely express your thoughts.

Well, a [brand-new research paper][3] just blew that idea apart. It's called "Large-scale online deanonymization with LLMs" which is a fancy way of saying "figuring out the real person behind a secret online name".

![][4]

The researchers include people ETH Zurich and, [Anthropic][5] (parent company of Claude), and a research group called [MATS][6] and they proved that today's super-powerful AI chatbots can play detective and unmask people way better than ever before.

### How does it work?

Think of the AI as a detective like Hercule Poirot or Sherlock Holmes. Only this detective is super fast and super smart. It has read every single post ever written online. Here's how their system works in simple steps:

  1. **Read and spot clues** : The AI looks at your posts and pulls out little hints about you. Things you that are part of your personality. Like it can see that this person talks a lot about coding games in Python, loves Marvel movies, complains about school in Seattle, and types with a certain style.
  2. **Search the whole internet** : It quietly checks LinkedIn, Google, other Reddit accounts, etc., to find possible real people who match those clues.
  3. **Think hard and double-check** : The AI reasons like "Is this a match? The writing style is the same, the hobbies line up, the timing fits... yep, 90% sure!"



The researchers called their method ESRC which stands for Extract clues, Search, Reason, Calibrate how sure they are. No human needed; it's all automatic.

### Pretty (scary) impressive results

If you think it's all theory, you are going to be disappointed.

On real [Hacker News][7] users, the AI correctly linked the secret username to the real person 67% of the time, and when it made a guess, it was right 90%. The paper also states that matching the same person's Reddit posts from different years or groups met with 68% success.

That's not the scary part. The thing is that it costs only upto $4 to check a person. Anyone with a good chatbot (think future ChatGPT or Claude) could do it.

One of the main researchers, Simon Lermen, said it straight:

> Could a team of smart investigators figure out who you are from your posts? If yes, these AI agents can likely do the same – and the cost is only going down.

### Private life becomes less private

Until now, staying hidden online was pretty easy because it took human experts hours or days. Now? One person (or a bad guy, a bully, a stalker, a company, or even government) can run this on thousands of accounts super fast.

This means that someone could find your real name, school, city, or job from just a few comments. Stalkers or bullies could dox you. Companies could secretly link all your accounts and track everything you do.

The old idea that "if I use a fake name, I'm safe" doesn't work anymore. It's the end of practical obscurity. Meaning you used to be kind of hidden in practice, but not anymore. Welcome to a new kind of 1984!

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/ai-online-deanonymization/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://arxiv.org/abs/2602.16800
[4]: https://itsfoss.com/content/images/2026/02/paper.webp
[5]: https://www.anthropic.com/
[6]: https://www.matsprogram.org/
[7]: https://news.ycombinator.com/
