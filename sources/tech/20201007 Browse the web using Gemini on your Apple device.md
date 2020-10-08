[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Browse the web using Gemini on your Apple device)
[#]: via: (https://opensource.com/article/20/10/gemini-ios)
[#]: author: (Lee Tusman https://opensource.com/users/leeto)

Browse the web using Gemini on your Apple device
======
The new Gemini internet protocol may not have an iOS app, but you can
still access its clients from your iPad or iPhone.
![A person looking at a phone][1]

Lately, I've been checking out pages on the nascent [Gemini protocol][2], a new application-level protocol for hypertext documents. It [falls somewhere][3] between the minimalism of Gopher and the complexity and weight of the World Wide Web.

The Gemini protocol requires using a [Gemini client][4], and there are multiple command-line and GUI applications available. I've wanted to read Gemini from the comfort and convenience of my iPad, but there isn't an app for iOS.

I found [AV-98][5], a Python-based command-line client created by Gemini's originator, Solderpunk. I decided this would work for me, as in a previous article, I demonstrated [how to set up and use iSH to run Linux or develop applications on iOS][6].

### Install AV-98 on iOS

AV-98 only requires Python 3 and is a quick, easy install:


```
`git clone https://tildegit.org/solderpunk/AV-98`
```

Running AV-98 is easy enough:


```
`python3 av98.py`
```

I decided to make an alias to make this easy to run anytime, anywhere. I'm using [fish shell][7]. So I made a _function_:


```
`function av98`
```

Then entered:


```
`python3 ~/AV-98/av98.py`
```

And saved it permanently:


```
`funcsave av98`
```

Now I can run it anywhere by just typing `av98`.

### AV-98 basics

  * List commands: `help`
  * Go somewhere directly: `go gemini.circumlunar.space`
  * Follow a link: Type its number (e.g., `3`) and hit Enter
  * If a page is too long to read: `less`.
  * Exit a page by pressing `q` on your keyboard
  * Go back one page: **b** (or back)
  * Exit: **q** (or exit)



I recommend making `gemini://gemini.circumlunar.space/capcom`, an aggregator for Atom feeds containing Gemini content, your homepage. It's an easy and convenient way to discover great new Gemini activity.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/gemini-ios

作者：[Lee Tusman][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/leeto
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/idea_innovation_mobile_phone.png?itok=RqVtvxkd (A person looking at a phone)
[2]: https://gemini.circumlunar.space/
[3]: https://opensource.com/article/20/9/introduction-gemini
[4]: https://gemini.circumlunar.space/clients.html
[5]: https://tildegit.org/solderpunk/AV-98
[6]: https://opensource.com/article/20/9/run-linux-ios
[7]: https://opensource.com/article/20/3/fish-shell
