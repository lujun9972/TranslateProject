[#]: subject: "Entering text in the terminal is complicated"
[#]: via: "https://jvns.ca/blog/2024/07/08/readline/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Entering text in the terminal is complicated
======

The other day I asked what folks on Mastodon find confusing about working in the terminal, and one thing that stood out to me was “editing a command you already typed in”.

This really resonated with me: even though entering some text and editing it is a very “basic” task, it took me maybe 15 years of using the terminal every single day to get used to using `Ctrl+A` to go to the beginning of the line (or `Ctrl+E` for the end).

So let’s talk about why entering text might be hard! I’ll also share a few tips that I wish I’d learned earlier.

### it’s very inconsistent between programs

A big part of what makes entering text in the terminal hard is the inconsistency between how different programs handle entering text. For example:

  1. some programs (the `dash` shell, `cat`, `nc`, `git commit --interactive`, etc) don’t support using arrow keys at all: if you press arrow keys, you’ll just see `^[[D^[[D^[[C^[[C^`
  2. many programs (like `irb`, `python3` on a Linux machine and many many more) use the `readline` library, which gives you a lot of basic functionality (history, arrow keys, etc)
  3. some programs (like `/usr/bin/python3` on my Mac) do support very basic features like arrow keys, but not other features like `Ctrl+left` or reverse searching with `Ctrl+R`
  4. some programs (like the `fish` shell or `ipython3` or `micro` or `vim`) have their own fancy system for accepting input which is totally custom



So there’s a lot of variation! Let’s talk about each of those a little more.

### mode 1: the baseline

First, there’s “the baseline” – what happens if a program just accepts text by calling `fgets()` or whatever and doing absolutely nothing else to provide a nicer experience. Here’s what using these tools typically looks for me – If I start [dash][1] (a pretty minimal shell) press the left arrow keys, it just prints `^[[D` to the terminal.

```

    $ ls l-^[[D^[[D^[[D

```

At first it doesn’t seem like all of these “baseline” tools have much in common, but there are actually a few features that you get for free just from your terminal, without the program needing to do anything special at all.

The things you get for free are:

  1. typing in text, obviously
  2. backspace
  3. `Ctrl+W`, to delete the previous word
  4. `Ctrl+U`, to delete the whole line
  5. a few other things unrelated to text editing (like `Ctrl+C` to interrupt the process, `Ctrl+Z` to suspend, etc)



This is not _great_ , but it means that if you want to delete a word you generally can do it with `Ctrl+W` instead of pressing backspace 15 times, even if you’re in an environment which is offering you absolutely zero features.

You can get a list of all the ctrl codes that your terminal supports with `stty -a`.

### mode 2: tools that use `readline`

The next group is tools that use readline! Readline is a GNU library to make entering text more pleasant, and it’s very widely used.

My favourite readline keyboard shortcuts are:

  1. `Ctrl+E` to go to the end of the line
  2. `Ctrl+A` to go to the beginning of the line
  3. `Ctrl+left/right arrow` to go back/forward 1 word
  4. up arrow to go back to the previous command
  5. `Ctrl+R` to search your history



And you can use `Ctrl+W` / `Ctrl+U` from the “baseline” list, though `Ctrl+U` deletes from the cursor to the beginning of the line instead of deleting the whole line. I think `Ctrl+W` might also have a slightly different definition of what a “word” is.

There are a lot more ([here’s a full list][2]), but those are the only ones that I personally use.

The `bash` shell is probably the most famous readline user (when you use `Ctrl+R` to search your history in bash, that feature actually comes from readline), but there are TONS of programs that use it – for example `psql`, `irb`, `python3`, etc.

### tip: you can make ANYTHING use readline with `rlwrap`

One of my absolute favourite things is that if you have a program like `nc` without readline support, you can just run `rlwrap nc` to turn it into a program with readline support!

This is incredible and makes a lot of tools that are borderline unusable MUCH more pleasant to use. You can even apparently set up [rlwrap][3] to include your own custom autocompletions, though I’ve never tried that.

### some reasons tools might not use readline

I think reasons tools might not use readline might include:

  * the program is very simple (like `cat` or `nc`) and maybe the maintainers don’t want to bring in a relatively large dependency
  * license reasons, if the program’s license is not GPL-compatible – readline is GPL-licensed, not LGPL
  * only a very small part of the program is interactive, and maybe readline support isn’t seen as important. For example `git` has a few interactive features (like `git add -p`), but not very many, and usually you’re just typing a single character like `y` or `n` – most of the time you need to really type something significant in git, it’ll drop you into a text editor instead.



For example idris2 says [they don’t use readline][4] to keep dependencies minimal and suggest using `rlwrap` to get better interactive features.

### how to know if you’re using readline

The simplest test I can think of is to press `Ctrl+R`, and if you see:

```

    (reverse-i-search)`':

```

then you’re probably using readline. This obviously isn’t a guarantee (some other library could use the term `reverse-i-search` too!), but I don’t know of another system that uses that specific term to refer to searching history.

### the readline keybindings come from Emacs

Because I’m a vim user, It took me a very long time to understand where these keybindings come from (why `Ctrl+A` to go to the beginning of a line??? so weird!)

My understanding is these keybindings actually come from Emacs – `Ctrl+A` and `Ctrl+E` do the same thing in Emacs as they do in Readline and I assume the other keyboard shortcuts mostly do as well, though I tried out `Ctrl+W` and `Ctrl+U` in Emacs and they don’t do the same thing as they do in the terminal so I guess there are some differences.

There’s some more [history of the Readline project here][5].

### mode 3: another input library (like `libedit`)

On my Mac laptop, `/usr/bin/python3` is in a weird middle ground where it supports _some_ readline features (for example the arrow keys), but not the other ones. For example when I press `Ctrl+left arrow`, it prints out `;5D`, like this:

```

    $ python3
    >>> importt subprocess;5D

```

Folks on Mastodon helped me figure out that this is because in the default Python install on Mac OS, the Python `readline` module is actually backed by `libedit`, which is a similar library which has fewer features, presumably because Readline is [GPL licensed][6].

Here’s how I was eventually able to figure out that Python was using libedit on my system:

```

    $ python3 -c "import readline; print(readline.__doc__)"
    Importing this module enables command line editing using libedit readline.

```

Generally Python uses readline though if you install it on Linux or through Homebrew. It’s just that the specific version that Apple includes on their systems doesn’t have readline. Also [Python 3.13 is going to remove the readline dependency][7] in favour of a custom library, so “Python uses readline” won’t be true in the future.

I assume that there are more programs on my Mac that use libedit but I haven’t looked into it.

### mode 4: something custom

The last group of programs is programs that have their own custom (and sometimes much fancier!) system for editing text. This includes:

  * most terminal text editors (nano, micro, vim, emacs, etc)
  * some shells (like fish), for example it seems like fish supports `Ctrl+Z` for undo when typing in a command. Zsh’s line editor is called [zle][8].
  * some REPLs (like `ipython`), for example IPython uses the [prompt_toolkit][9] library instead of readline
  * lots of other programs (like `atuin`)



Some features you might see are:

  * better autocomplete which is more customized to the tool
  * nicer history management (for example with syntax highlighting) than the default you get from readline
  * more keyboard shortcuts



### custom input systems are often readline-inspired

I went looking at how [Atuin][10] (a wonderful tool for searching your shell history that I started using recently) handles text input. Looking at [the code][11] and some of the discussion around it, their implementation is custom but it’s inspired by readline, which makes sense to me – a lot of users are used to those keybindings, and it’s convenient for them to work even though atuin doesn’t use readline.

[prompt_toolkit][9] (the library IPython uses) is similar – it actually supports a lot of options (including vi-like keybindings), but the default is to support the readline-style keybindings.

This is like how you see a lot of programs which support very basic vim keybindings (like `j` for down and `k` for up). For example Fastmail supports `j` and `k` even though most of its other keybindings don’t have much relationship to vim.

I assume that most “readline-inspired” custom input systems have various subtle incompatibilities with readline, but this doesn’t really bother me at all personally because I’m extremely ignorant of most of readline’s features. I only use maybe 5 keyboard shortcuts, so as long as they support the 5 basic commands I know (which they always do!) I feel pretty comfortable. And usually these custom systems have much better autocomplete than you’d get from just using readline, so generally I prefer them over readline.

### lots of shells support vi keybindings

Bash, zsh, and fish all have a “vi mode” for entering text. In a [very unscientific poll][12] I ran on Mastodon, 12% of people said they use it, so it seems pretty popular.

Readline also has a “vi mode” (which is how Bash’s support for it works), so by extension lots of other programs have it too.

I’ve always thought that vi mode seems really cool, but for some reason even though I’m a vim user it’s never stuck for me.

### understanding what situation you’re in really helps

I’ve spent a lot of my life being confused about why a command line application I was using wasn’t behaving the way I wanted, and it feels good to be able to more or less understand what’s going on.

I think this is roughly my mental flowchart when I’m entering text at a command line prompt:

  1. Do the arrow keys not work? Probably there’s no input system at all, but at least I can use `Ctrl+W` and `Ctrl+U`, and I can `rlwrap` the tool if I want more features.
  2. Does `Ctrl+R` print `reverse-i-search`? Probably it’s readline, so I can use all of the readline shortcuts I’m used to, and I know I can get some basic history and press up arrow to get the previous command.
  3. Does `Ctrl+R` do something else? This is probably some custom input library: it’ll probably act more or less like readline, and I can check the documentation if I really want to know how it works.



Being able to diagnose what’s going on like this makes the command line feel a more predictable and less chaotic.

### some things this post left out

There are lots more complications related to entering text that we didn’t talk about at all here, like:

  * issues related to ssh / tmux / etc
  * the `TERM` environment variable
  * how different terminals (gnome terminal, iTerm, xterm, etc) have different kinds of support for copying/pasting text
  * unicode
  * probably a lot more



--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2024/07/08/readline/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://wiki.archlinux.org/title/Dash
[2]: https://www.man7.org/linux/man-pages/man3/readline.3.html#EDITING_COMMANDS
[3]: https://github.com/hanslub42/rlwrap
[4]: https://idris2.readthedocs.io/en/latest/tutorial/interactive.html#editing-at-the-repl
[5]: https://twobithistory.org/2019/08/22/readline.html
[6]: https://en.wikipedia.org/wiki/GNU_Readline#Choice_of_the_GPL_as_GNU_Readline's_license
[7]: https://docs.python.org/3.13/whatsnew/3.13.html#a-better-interactive-interpreter
[8]: https://zsh.sourceforge.io/Guide/zshguide04.html
[9]: https://python-prompt-toolkit.readthedocs.io/
[10]: https://atuin.sh/
[11]: https://github.com/atuinsh/atuin/blob/a67cfc82fe0dc907a01f07a0fd625701e062a33b/crates/atuin/src/command/client/search/interactive.rs#L382-L430
[12]: https://social.jvns.ca/@b0rk/112723846172173621
