[#]: subject: "ace window"
[#]: via: "https://jao.io/blog/ace-window.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

ace window
======

As i've mentioned in a previous post, i organise my emacs sessions in workspaces, a.k.a. frames, a.k.a. a thematic tiling of windows. It is therefore important to have quick ways of jumping from a window to another. Until very recently, i used a home-cooked collection of shortcuts (`C-c 1`, `C-c 2` … `C-c n`) that would move my point to the nth window in the workspace (i trained myself to count them quick enough, i suppose), and used that together with the stock `C-x o` and with `C-x p` bound to `(other-window -1)`, for something similar to "previous window", to move around. But i've discovered a better way.

It's called [ace-window][1], and it's so easy to use that i'll just give you my configuration below:

```

    (use-package ace-window
      :ensure t
      :init (setq aw-keys '(?a ?s ?d ?f ?g ?h ?j ?k ?l)
                  aw-char-position 'left
                  aw-ignore-current nil
                  aw-leading-char-style 'char
                  aw-scope 'frame)
      :bind (("M-o" . ace-window)
             ("M-O" . ace-swap-window)))

```

With exwm, i also bind `s-o` and `s-O`, so i can jump when focus is on an X buffer. My only complain is that the character overlay is not visible for X buffers, but i use so few of them that it's nothing to worry about.

[Tags][2]: [emacs][3]

--------------------------------------------------------------------------------

via: https://jao.io/blog/ace-window.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: https://github.com/abo-abo/ace-window
[2]: https://jao.io/blog/tags.html
[3]: https://jao.io/blog/tag-emacs.html
