[#]: subject: "Notes on git's error messages"
[#]: via: "https://jvns.ca/blog/2024/04/10/notes-on-git-error-messages/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Notes on git's error messages
======

While writing about Git, I’ve noticed that a lot of folks struggle with Git’s error messages. I’ve had many years to get used to these error messages so it took me a really long time to understand _why_ folks were confused, but having thought about it much more, I’ve realized that:

  1. sometimes I actually _am_ confused by the error messages, I’m just used to being confused
  2. I have a bunch of strategies for getting more information when the error message git gives me isn’t very informative



So in this post, I’m going to go through a bunch of Git’s error messages, list a few things that I think are confusing about them for each one, and talk about what I do when I’m confused by the message.

### improving error messages isn’t easy

Before we start, I want to say that trying to think about why these error messages are confusing has given me a lot of respect for how difficult maintaining Git is. I’ve been thinking about Git for months, and for some of these messages I really have no idea how to improve them.

Some things that seem hard to me about improving error messages:

  * if you come up with an idea for a new message, it’s hard to tell if it’s actually better!
  * work like improving error messages often [isn’t funded][1]
  * the error messages have to be translated (git’s error messages are translated into [19 languages][2]!)



That said, if you find these messages confusing, hopefully some of these notes will help clarify them a bit.

--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2024/04/10/notes-on-git-error-messages/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://lwn.net/Articles/959768/
[2]: https://github.com/git/git/tree/master/po
