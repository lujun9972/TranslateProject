[#]: subject: "Terminal colours are tricky"
[#]: via: "https://jvns.ca/blog/2024/10/01/terminal-colours/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Terminal colours are tricky
======

Yesterday I was thinking about how long it took me to get a colorscheme in my terminal that I was mostly happy with (SO MANY YEARS), and it made me wonder what about terminal colours made it so hard.

So I [asked people on Mastodon][1] what problems they’ve run into with colours in the terminal, and I got a ton of interesting responses! Let’s talk about some of the problems and a few possible ways to fix them.

### problem 1: blue on black

One of the top complaints was “blue on black is hard to read”. Here’s an example of that: if I open Terminal.app, set the background to black, and run `ls`, the directories are displayed in a blue that isn’t that easy to read:

![][2]

To understand why we’re seeing this blue, let’s talk about ANSI colours!

### the 16 ANSI colours

Your terminal has 16 numbered colours – black, red, green, yellow, blue, magenta, cyan, white, and “bright” version of each of those.

Programs can use them by printing out an “ANSI escape code” – for example if you want to see each of the 16 colours in your terminal, you can run this Python program:

```

    def color(num, text):
        return f"\033[38;5;{num}m{text}\033[0m"

    for i in range(16):
        print(color(i, f"number {i:02}"))

```

### what are the ANSI colours?

This made me wonder – if blue is colour number 5, who decides what hex color that should correspond to?

The answer seems to be “there’s no standard, terminal emulators just choose colours and it’s not very consistent”. Here’s a [screenshot of a table from Wikipedia][3], where you can see that there’s a lot of variation:

![][4]

### problem 1.5: bright yellow on white

Bright yellow on white is even worse than blue on black, here’s what I get in a terminal with the default settings:

![][5]

That’s almost impossible to read (and some other colours like light green cause similar issues), so let’s talk about solutions!

### two ways to reconfigure your colours

If you’re annoyed by these colour contrast issues (or maybe you just think the default ANSI colours are ugly), you might think – well, I’ll just choose a different “blue” and pick something I like better!

There are two ways you can do this:

**Way 1: Configure your terminal emulator** : I think most modern terminal emulators have a way to reconfigure the colours, and some of them even come with some preinstalled themes that you might like better than the defaults.

**Way 2: Run a shell script** : There are ANSI escape codes that you can print out to tell your terminal emulator to reconfigure its colours. [Here’s a shell script that does that][6], from the [base16-shell][7] project. You can see that it has a few different conventions for changing the colours – I guess different terminal emulators have different escape codes for changing their colour palette, and so the script is trying to pick the right style of escape code based on the `TERM` environment variable.

### what are the pros and cons of the 2 ways of configuring your colours?

I prefer to use the “shell script” method, because:

  * if I switch terminal emulators for some reason, I don’t need to a different configuration system, my colours still Just Work
  * I use [base16-shell][7] with base16-vim to make my vim colours match my terminal colours, which is convenient



The main advantage I can think of for configuring colours in your terminal emulator is that, if you use a popular terminal emulator, there are probably a lot of nice terminal themes out there that you can choose from. I think there are some more advantages I’m not thinking of though.

This is what my shell has looked like for probably the last 5 years (using the solarized light base16 theme), and I’m pretty happy with it. Here’s `htop`:

![][8]

Okay, so let’s say you’ve found a terminal colorscheme that you like. What else can go wrong?

### problem 2: programs using 256 colours

Here’s what some output of `fd`, a `find` alternative, looks like in my colorscheme:

![][9]

The contrast is pretty bad here, and I definitely don’t have that lime green in my normal colorscheme. What’s going on?

We can see what color codes `fd` is using using the `unbuffer` program to capture its output including the color codes:

```

    $ unbuffer fd . > out
    $ vim out
    [38;5;48mbad-again.sh[0m
    [38;5;48mbad.sh[0m
    [38;5;48mbetter.sh[0m
    out

```

`[38;5;48` means “set the foreground color to color `48`”. Terminals don’t only have 16 colours – many terminals these days actually have 3 ways of specifying colours:

  1. the 16 ANSI colours we already talked about
  2. an extended set of 256 colours
  3. a further extended set of 24-bit hex colours, like `#ffea03`



So `fd` is using one of the colours from the extended 256-color set. `bat` (a `cat` alternative) does something similar – here’s what it looks like by default in my terminal.

![][10]

This looks fine though and it really seems like it’s trying to work well with a variety of terminal themes.

### some newer tools seem to have theme support

I think it’s interesting that some of these newer terminal tools (`fd`, `cat`, `delta`, and probably more) have support for arbitrary custom themes. I guess the downside of this approach is that the default theme might clash with your terminal’s background, but the upside is that it gives you a lot more control over theming the tool’s output than just choosing 16 ANSI colours.

I don’t really use `bat`, but if I did I’d probably use `bat --theme ansi` to just use the ANSI colours that I have set in my normal terminal colorscheme.

### problem 3: the grays in Solarized

A bunch of people on Mastodon mentioned a specific issue with grays in the Solarized theme: when I list a directory, the base16 Solarized Light theme looks like this:

![][11]

but iTerm’s default Solarized Light theme looks like this:

![][12]

This is because in the iTerm theme, colors 9-14 (the “bright blue”, “bright red”, etc) are mapped to a series of grays, and when I run `ls`, it’s trying to use those “bright” colours to color my directories and executables.

I’m not sure why the iTerm Solarized theme is designed this way (there must be a reason!) but I’m pretty sure I prefer the version where the “bright” colours are actually colours instead of all being shades of gray.

### problem 4: a vim theme that doesn’t match the terminal background

If I my vim theme has a different background colour than my terminal theme, I get this ugly border, like this:

![][13]

This one is a pretty minor issue though and I think making your terminal background match your vim background is pretty straightforward.

### problem 5: programs setting a background color

A few people mentioned problems with terminal applications setting an unwanted background colour, so let’s look at an example of that.

Here `ngrok` has set the background to color #16 (“black”), but the `base16-shell` script I use sets color 16 to be bright orange, so I get this, which is pretty bad:

![][14]

I think the intention is for ngrok to look something like this:

![][15]

I think `base16-shell` sets color #16 to orange (instead of black) so that it can provide extra colours for use by [base16-vim][16]. This feels reasonable to me – I use `base16-vim` in the terminal, so I guess I’m using that feature and it’s probably more important to me than `ngrok` (which I rarely use) behaving a bit weirdly.

This particular issue is a maybe obscure clash between ngrok and my colorschem, but I think this kind of clash is pretty common when a program sets an ANSI background color that the user has remapped for some reason.

### a nice solution to contrast issues: “minimum contrast”

A bunch of terminals (iTerm2, [tabby][17], kitty’s [text_fg_override_threshold][18], and folks tell me also Ghostty and Windows Terminal) have a “minimum contrast” feature that will automatically adjust colours to make sure they have enough contrast.

Here’s an example from iTerm. This ngrok accident from before has pretty bad contrast, I find it pretty difficult to read:

![][14]

With “minimum contrast” set to 40 in iTerm, it looks like this instead:

![][19]

I didn’t have minimum contrast turned on before but I just turned it on today because it makes such a big difference when something goes wrong with colours in the terminal.

### problem 6: `TERM` being set to the wrong thing

A few people mentioned that they’ll SSH into a system that doesn’t support the `TERM` environment variable that they have set locally, and then the colours won’t work.

I think the way `TERM` works is that systems have a `terminfo` database, so if the value of the `TERM` environment variable isn’t in the system’s terminfo database, then it won’t know how to output colours for that terminal. I don’t know too much about terminfo, but someone linked me to this [terminfo rant][20] that talks about a few other issues with terminfo.

I don’t have a system on hand to reproduce this one so I can’t say for sure how to fix it, but [this stackoverflow question][21] suggests running something like `TERM=xterm ssh` instead of `ssh`.

### problem 7: picking “good” colours is hard

A couple of problems people mentioned with designing / finding terminal colorschemes:

  * some folks are colorblind and have trouble finding an appropriate colorscheme
  * accidentally making the background color too close to the cursor or selection color, so they’re hard to find
  * generally finding colours that work with every program is a struggle (for example you can see me having a problem with this with ngrok above!)



### problem 8: making nethack/mc look right

Another problem people mentioned is using a program like nethack or midnight commander which you might expect to have a specific colourscheme based on the default ANSI terminal colours.

For example, midnight commander has a really specific classic look:

![][22]

But in my Solarized theme, midnight commander looks like this:

![][23]

The Solarized version feels like it might be pretty disorienting if you’re expecting the “classic” look.

One solution Simon Tatham mentioned to this is using some palette customization ANSI codes (like the ones base16 uses that I talked about earlier) to change the color palette right before starting the program, for example remapping yellow to a brighter yellow before starting Nethack so that the yellow characters look better.

### problem 9: commands disabling colours when writing to a pipe

If I run `fd | less`, I see something like this, with the colours disabled.

![][24]

In generan I find this useful – if I pipe a command to `grep`, I don’t want it to print out all those color escape codes, I just want the plain text. But what if you want to see the colours?

To see the colours, you can run `unbuffer fd | less -r`! I just learned about `unbuffer` recently and I think it’s really cool, `unbuffer` opens a tty for the command to write to so that it thinks it’s writing to a TTY. It also fixes issues with programs buffering their output when writing to a pipe, which is why it’s called `unbuffer`.

Here’s what the output of `unbuffer fd | less -r` looks like for me:

![][25]

### problem 10: unwanted colour in `ls` and other commands

Some people mentioned that they don’t want `ls` to use colour at all, perhaps because `ls` uses blue, it’s hard to read on black, and maybe they don’t feel like customizing their terminal’s colourscheme to make the blue more readable or just don’t find the use of colour helpful.

Some possible solutions to this one:

  * you can run `ls --color=never`, which is probably easiest
  * you can also set `LS_COLORS` to customize the colours used by `ls`. I think some other programs other than `ls` support the `LS_COLORS` environment variable too.
  * also some programs support setting `NO_COLOR=true` (there’s a [list here][26])



Here’s an example of running `LS_COLORS="fi=0:di=0:ln=0:pi=0:so=0:bd=0:cd=0:or=0:ex=0" ls`:

![][27]

### some more problems I left out

I think there are a lot of issues around the intersection of multiple programs, like using some combination tmux/ssh/vim that I couldn’t figure out how to reproduce well enough to talk about them. Also I’m sure I missed a lot of other things too.

### okay, that was a lot

We talked about a lot in this post and while I think learning about all these details is kind of fun if I’m in the mood to do a deep dive, I find it SO FRUSTRATING to deal with it when I just want my colours to work! Being surprised by unreadable text and having to find a workaround is just not my idea of a good day.

Personally I’m a zero-configuration kind of person and it’s not that appealing to me to have to put together a lot of custom configuration just to make my colours in the terminal look acceptable. I’d much rather just have some reasonable defaults that I don’t have to change.

### base16 has really worked for me

I’ve personally had a lot of success with using [base16-shell][7] with [base16-vim][28] – I just need to add [a couple of lines][29] to my fish config to set it up (+ a few `.vimrc` lines) and then I can move on and accept any remaining problems that that doesn’t solve.

I don’t think base16 is for everyone though, some limitations I’m aware of with base16 that might make it not work for you:

  * it comes with a limited set of builtin themes and you might not like any of them
  * the Solarized base16 theme (and maybe all of the themes?) sets the “bright” ANSI colours to be exactly the same as the normal colours, which might cause a problem if you’re relying on the “bright” colours to be different from the regular ones
  * it sets colours 16-21, which could be a problem in terminals that don’t have 256-color support



Apparently there’s a community fork of base16 called [tinted-theming][30], which I haven’t looked into much yet.

### some other colorscheme tools

Just one so far but I’ll link more if people tell me about them:

  * [rootloops.sh][31] for generating colorschemes (and [“let’s create a terminal color scheme”][32])



### minimum contrast seems like an amazing feature

My one big takeaway from writing this was to turn on “minimum contrast” in my terminal, I think it’s going to fix most of the occasional accidental unreadable text issues I run into and I’m pretty excited about it.

--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2024/10/01/terminal-colours/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://social.jvns.ca/@b0rk/113226972156366201
[2]: https://jvns.ca/images/terminal-blue.png
[3]: https://en.m.wikipedia.org/wiki/ANSI_escape_code#Colors
[4]: https://jvns.ca/images/wikipedia.png
[5]: https://jvns.ca/images/terminal-yellow.png
[6]: https://github.com/chriskempson/base16-shell/blob/master/scripts/base16-solarized-light.sh
[7]: https://github.com/chriskempson/base16-shell
[8]: https://jvns.ca/images/terminal-my-colours.png
[9]: https://jvns.ca/images/terminal-problem-fd.png
[10]: https://jvns.ca/images/terminal-bat.png
[11]: https://jvns.ca/images/terminal-solarized-base16.png
[12]: https://jvns.ca/images/terminal-solarized-iterm.png
[13]: https://jvns.ca/images/terminal-vim-black-bg.png
[14]: https://jvns.ca/images/terminal-ngrok-solarized.png
[15]: https://jvns.ca/images/terminal-ngrok-regular.png
[16]: https://github.com/chriskempson/base16-vim/blob/3be3cd82cd31acfcab9a41bad853d9c68d30478d/colors/base16-solarized-light.vim
[17]: https://github.com/Eugeny/tabby
[18]: https://sw.kovidgoyal.net/kitty/conf/#opt-kitty.text_fg_override_threshold
[19]: https://jvns.ca/images/terminal-ngrok-solarized-contrast.png
[20]: https://twoot.site/@bean/113056942625234032
[21]: https://unix.stackexchange.com/questions/67537/prevent-ssh-client-passing-term-environment-variable-to-server
[22]: https://jvns.ca/images/terminal-mc-normal.png
[23]: https://jvns.ca/images/terminal-mc-solarized.png
[24]: https://jvns.ca/images/terminal-fd-bw.png
[25]: https://jvns.ca/images/terminal-fd-color.png
[26]: https://no-color.org/
[27]: https://jvns.ca/images/terminal-ls-colors.png
[28]: https://github.com/chriskempson/base16-vim
[29]: https://github.com/chriskempson/base16-shell?tab=readme-ov-file#fish
[30]: https://github.com/tinted-theming/home
[31]: https://rootloops.sh/
[32]: https://hamvocke.com/blog/lets-create-a-terminal-color-scheme/
