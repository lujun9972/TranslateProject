[#]: subject: "New zine: The Pocket Guide to Debugging"
[#]: via: "https://jvns.ca/blog/2022/12/21/new-zine--the-pocket-guide-to-debugging/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

New zine: The Pocket Guide to Debugging
======

Hello! On Monday, we released a new zine: **The Pocket Guide to Debugging**! It has 47 of my favourite strategies for solving your sneakiest bugs.

You can get it for $12 here: <https://wizardzines.com/zines/debugging-guide>, or get an [12-pack of all my zines here][1].

Here’s the cover:

[![][2]][3]

### the table of contents

Here’s the table of contents!

<https://jvns.ca/images/debugging-guide-toc.png>

A few people mentioned that they were printing it out, so I made a PDF poster version if you want to print it:

  * [Printable table of contents (letter paper)][4]
  * [Printable table of contents (A4 paper)][5]



I love that the table of contents is already kind of useful as a collection of strategies on its own.

### why debugging?

I wrote this zine because debugging is a huge part of how we spend our time as programmers, but nobody teaches us how to do it! If you’re lucky, you get to pair program with someone who’s good at debugging and explaining their thought processes, and they can show you. But not all of us have that person, so we end up just struggling through it ourselves and learning strategies the hard way.

So I wanted to write a zine where beginners can learn some of these strategies the easy way, and which more experienced programmers can use as a reference to get ideas when you’re in the middle of a tricky bug.

### it comes with some debugging mysteries!

This zine comes with a few choose-your-own-adventure debugging mysteries (like “The Case of the Connection Timeout”), at <https://mysteries.wizardzines.com>.

These mysteries show you how to apply some of the tricks in the zine to a specific kind of bug: computer networking issues! It also demos some of my favourite networking spy tools – it’ll show you some tips for interpreting their output.

You can read some notes on designing those puzzes here: [Notes on building debugging puzzles][6]. (You might notice that post is from a year and half – that’s because I’ve been trying to write this zine on and off for 3 and a half years and a lot of things happened along the way :))

### it’s actually been helping me debug!

I’ve actually been shocked by how useful this zine has been for helping _me_ debug – after all, I know all these strategies! I like to think I’m pretty good at debugging!

But when I’m in the middle of a tricky bug and I’m frustrated, I’ve actually been finding it incredibly helpful to reach for the table of contents and get an idea for something to try.

It’s also been fun to reflect on what strategies I’m using when debugging. For example, yesterday I had a CSS bug, and I was super frustrated. But it turned that I just needed to:

  1. come up with **one small question**
  2. write a **tiny program**
  3. start **writing a message asking for help**
  4. quickly **read the docs**
  5. delete the message I started writing without sending it, since I’d figured it out :)



### some blog posts I wrote along the way

Here are a few blog posts I wrote while thinking about how to write this zine:

  * [a debugging manifesto][7]
  * [some ways to get better at debugging][8]
  * [reasons why bugs might feel “impossible”][9]
  * [when debugging, your attitude matters][10]
  * [what does debugging a program look like?][11]



### you can get a print copy shipped to you!

There’s always been the option to print the zines yourself on your home printer.

But this time there’s a new option too: you can get a print copy shipped to you! (just click on the “print version” link on [this page][12])

The only caveat is print orders will ship around **the end of January** – I need to wait for orders to come in to get an idea of how many I should print before sending it to the printer.

# the home printing directions are a little bit different!

This zine is twice the length of other zines, but half the height! This makes it extremely pocket sized, and it means you have to cut the print version in half. But don’t worry – there’s a dotted line and a video :)

The video with the print directions is at <https://wizardzines.com/print/>

### the hardest part of writing this zine: making it specific

It’s relatively easy to give high-level debugging advice. Reproduce the bug! Be rigorous! Try to divide the problem space in half! Print stuff out! And this zine started out as pretty general high-level advice. (you can read a [old table of contents here from an earlier draft][13])

Turning those high-level guidelines into **specific things that you can actually do** was a lot harder. I sat down with my amazing friend [Marie Claire LeBlanc Flanagan][14] every weekday at 10am for 6 months, and every day we made the zine a little more specific and concrete and useful.

I’m really proud of how it turned out.

### beta readers are amazing

Also, I want to thank the beta readers – 40 of you read the zine and left comments about what was confusing, what was working, and ideas for how to make it better. It made the end product so much better.

### thank you

As always: if you’ve bought zines in the past, thank you for all your support over the years. I couldn’t do this without you. Happy holidays.

--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2022/12/21/new-zine--the-pocket-guide-to-debugging/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://wizardzines.com/zines/all-the-zines/
[2]: https://jvns.ca/images/debugging-guide-cover.jpg
[3]: https://wizardzines.com/zines/debugging-guide
[4]: https://wizardzines.com/images/debugging/toc-letter.pdf
[5]: https://wizardzines.com/images/debugging/toc-a4.pdf
[6]: https://jvns.ca/blog/2021/04/16/notes-on-debugging-puzzles/
[7]: https://jvns.ca/blog/2022/12/08/a-debugging-manifesto/
[8]: https://jvns.ca/blog/2022/08/30/a-way-to-categorize-debugging-skills/
[9]: https://jvns.ca/blog/2021/06/08/reasons-why-bugs-might-feel-impossible/
[10]: https://jvns.ca/blog/debugging-attitude-matters/
[11]: https://jvns.ca/blog/2019/06/23/a-few-debugging-resources/
[12]: https://wizardzines.com/zines/debugging-guide/
[13]: https://jvns.ca/images/debugging-old-toc.png
[14]: https://marieflanagan.com/
