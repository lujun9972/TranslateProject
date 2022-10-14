[#]: subject: "consulting hunks"
[#]: via: "https://jao.io/blog/consulting-hunks.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

consulting hunks
======

I use Dmitry Gutov's [diff-hl][1] to highlight (with fringe marks) modified hunks in my files under git revision control. The package comes with a command, `diff-hl-next-hunk`, that one can use to navigate them. So, taking a peek at `consult-lines`, it was straightforward to put together a consult function to navigate, with completion and preview (although i disable the latter) the hunks in the current file:

```

    (defun jao-consult--diff-lines (&optional backward)
      (let ((candidates)
            (width (length (number-to-string
                            (line-number-at-pos (point-max)
                                                consult-line-numbers-widen)))))
        (save-excursion
          (while (ignore-errors (diff-hl-next-hunk backward))
            (let* ((str (buffer-substring (line-beginning-position)
                                          (line-end-position)))
                   (no (line-number-at-pos (point)))
                   (no (consult--line-number-prefix (point-marker) no width)))
              (push (concat no str) candidates))))
        (if backward candidates (nreverse candidates))))

    (defun jao-consult-hunks ()
      "Search for modified hunks in the current buffer."
      (interactive)
      (let ((candidates (append (jao-consult--diff-lines)
                                (jao-consult--diff-lines t))))
        (unless candidates (error "No changes!"))
        (consult--jump (consult--read candidates
                                      :prompt "Go to hunk: "
                                      :category 'consult--encode-location
                                      :require-match t
                                      :lookup #'consult--line-match
                                      :state (consult--jump-state)))))

    (global-set-key (kbd "C-x v c") #'jao-consult-hunks)

```

i am sure i've taken one or two detours there that can be coded better using consult's API, but it was so nice to be able to have a working command in fifteen minutes that i couldn't resist showing off :)

[Tags][2]: [emacs][3]

--------------------------------------------------------------------------------

via: https://jao.io/blog/consulting-hunks.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: https://github.com/dgutov/diff-hl
[2]: https://jao.io/blog/tags.html
[3]: https://jao.io/blog/tag-emacs.html
