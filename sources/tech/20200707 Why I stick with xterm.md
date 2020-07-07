[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Why I stick with xterm)
[#]: via: (https://opensource.com/article/20/7/xterm)
[#]: author: (Yedidyah Bar David https://opensource.com/users/didib)

Why I stick with xterm
======
With many new terminal options available, here's why one programmer
chooses to keep it simple.
![Terminal window with green text][1]

What's my terminal of choice?

I use xterm. That's right, xterm. It may seem like an old school choice, and I do use GNOME 3 now as well, but after many years of trying some and ignoring others, then going back to old standbys, I find I don't need (or like) newer stuff like GNOME Terminal.

My philosophy: Start simple, improve over time, and aim for productivity.

### Background and foreground

I start up xterm with this script:


```
#!/bin/bash
bg=rgbi:`dd if=/dev/urandom bs=1 count=3 2&gt;/dev/null | od -tu1 | awk
'{b=0.1/256; printf("%s/%s/%s\n", $2*b, $3*b, $4*b); exit(0)}'`
exec xterm -bg $bg -fg white "$@"
```

The `-bg` option sets a relatively dark random background, while `-fg` sets the foreground (the text) to white.

I like to set my monitor to be rather dark (contrast 70, brightness 10) because pure white on black is a bit too dark for me, while a lighter background is a bit too much light.

### Clicks

One thing I like about xterm is how [selection][2] works. A double-click of the left mouse button (LMB) selects a word, a triple-click selects "longer words" (see the configuration), four clicks selects lines, a middle-click pastes (or shift-insert), and finally, a right-click extends.

When extending, it continues to obey the "rules" for existing selections. If you double-click, the left button extends the selection to the whole word it contains. This is the relevant part of `$HOME/.Xresources`:


```
XTerm*on2Clicks: word
XTerm*on3Clicks: regex [^ \n]+
XTerm*on4Clicks: line
```

The concept of a "word" (for a double-click selection) is a narrow definition. When double-clicking on part of a file path, only that part is selected. A triple-click selects the full path.

### Alternate screen

I like to disable the alternate screen. Why is that, you ask?

Suppose that you open a terminal, and you want to run some command, but then decide you have to look something up in its manpage first. So you run `man somecommand`, find what you want, exit `less` with `q`, and suddenly the `man` text is gone!

If you had intended to copy and paste from it, you have to start it again, or else open it in a separate terminal window.

I can see why this function was added in the past—to return you to your previous context—but I don't like this behavior.

So, I disable it with this code in `.Xresources`:


```
XTerm*titeInhibit:      true
```

### Fonts

I use xterm with a custom bitmapped font that I created by adapting the standard 10x20 Unicode one and editing the Hebrew letters to suit my taste. I guess it's about time I looked for a more modern scalable font; I'll probably have no choice soon, what with HiDPI monitors and Wayland becoming prevalent, but my custom font works well for now.

### Colors for Vim

With the white text on a dark background, colors are usually too dark for me, especially with Vim's default syntax highlighting. I prefer to set them to something a little lighter:


```
! red, green, yellow, blue, magenta, cyan
XTerm*VT100*Color1:     #ff8080
XTerm*VT100*Color2:     #b0ffb0
XTerm*VT100*Color3:     #ffffb0
XTerm*VT100*Color4:     #b0b0ff
XTerm*VT100*Color5:     #ffb0ff
XTerm*VT100*Color6:     #b0ffff
! bright: red, green, yellow, blue, magenta, cyan
XTerm*VT100*Color9:     #ffd0d0
XTerm*VT100*Color10:    #d0ffd0
XTerm*VT100*Color11:    #ffffd0
XTerm*VT100*Color12:    #d0d0ff
XTerm*VT100*Color13:    #ffd0ff
XTerm*VT100*Color14:    #d0ffff
```

### X selection and clipboard

I want selections to be present in both the X selection and in the clipboard, so I don't have to think about what the target application (where I want to paste) wants to use, or how it wants to use it.


```
XTerm*VT100*selectToClipboard:  true
```

### Login action

In the rather distant past, the login process on X automatically [loaded the resources for you][3] from `$HOME/.Xresources`. I'm not sure what's left of this practice by default, but it didn't work for me on RHEL8 with GNOME 3. Here's how I fixed that.

First, I placed this script in `$HOME/bin/xrdb-merge-resources`:


```
#!/bin/sh
xrdb -merge $HOME/.Xresources
```

Then I created the file `$HOME/.config/autostart/xrdb-merge-resources.desktop`:


```
[Desktop Entry]
Name=xrdb-merge-resources
Exec=/home/ybardavi/bin/xrdb-merge-resources
Type=Application
```

Finally, I set it to autoload by adding it to GNOME's startup applications.

### xterm

Xterm is more customizable than you might expect, which is one of its many benefits. Get comfortable with it, and it'll reward you for your effort.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/xterm

作者：[Yedidyah Bar David][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/didib
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/osdc_terminals_0.png?itok=XwIRERsn (Terminal window with green text)
[2]: https://en.wikipedia.org/wiki/X_Window_selection
[3]: https://en.wikipedia.org/wiki/X_resources
