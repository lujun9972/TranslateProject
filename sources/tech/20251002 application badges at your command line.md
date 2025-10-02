[#]: subject: "application badges at your command line"
[#]: via: "https://jao.io/blog/application-badges-at-your-command-line.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

application badges at your command line
======

I've been playing with macOS lately, and _needed_ a quick way of grabbing the number of unread articles in [NetNewsWire][1]. So I wondered if I could somehow access its application badge label.

### The tip

Turns out one can:

```

    lsappinfo info -app NetNewsWire -only StatusLabel

```

which produces something like:

```

    "StatusLabel"={ "label"="6" }

```

One day I'll learn `awk` and feel ashamed of what I'm about to write below, but here's how to use grep to get just that count, if you must:

```

    lsappinfo info -app NetNewsWire -only StatusLabel | grep -E '[0-9]+' -o

```

and we get only the digits in the output:

```

    6

```

Hat tip to [Alexander's answer to this question][2], which put me on the right track despite his reservations. Reading the convoluted code in the other answers, I have none at all.

### The context

You won't be surprised to know that the actual place where I wanted to read that badge wasn't the CLI but Emacs, to display it in [my little notification centre hosted in the minibuffer][3]. I've been putting together some utilities to run applescript and such, and at first I thought of using NetNewsWire's dictionary with something like:

```

    tell application "NetNewsWire"
      set result to 0
      repeat with acc in accounts
         set theFeeds to allWebFeeds of acc
         repeat with f in theFeeds
           set theArticles to articles of f
           repeat with a in theArticles
             if (not (read of a)) then set result to (result + 1)
           end repeat
         end repeat
      end repeat
      return result
    end tell

```

which works… if you're willing to wait the couple of minutes it takes to run! Reminded me of the old adage in systems programming stating that a result that comes in late is an incorrect result.

[Tags][4]: [macos][5]

--------------------------------------------------------------------------------

via: https://jao.io/blog/application-badges-at-your-command-line.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: https://en.wikipedia.org/wiki/NetNewsWire
[2]: https://stackoverflow.com/questions/75163201/how-can-i-get-the-dock-badge-text-of-other-applications
[3]: https://codeberg.org/jao/elibs/src/commit/d03b2109650003ff98d89ebe9db22d62df1374e1/lib/eos/jao-minibuffer.el
[4]: https://jao.io/blog/tags.html
[5]: https://jao.io/blog/tag-macos.html
