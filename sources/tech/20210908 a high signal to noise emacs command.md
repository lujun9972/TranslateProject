[#]: subject: "a high signal to noise emacs command"
[#]: via: "https://jao.io/blog/high-signal-to-noise-emacs-command.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

a high signal to noise emacs command
======

Over the years, i've written perhaps hundreds of little emacs commands. Most of them looked useful at the time (why, i absolutely _needed_ them!), but just faded away after a few weeks. There are a handful though that i use all the time, and i specially like it when their signal (features, usefulness) to noise (lines of code) ratio is above average. Here's one with a surprisingly high one:

```

    (defun jao-buffer-same-mode (&rest modes)
      "Pop to a buffer with a mode among MODES, or the current one if not given."
      (interactive)
      (let* ((modes (or modes (list major-mode)))
             (pred (lambda (b)
                     (let ((b (get-buffer (if (consp b) (car b) b))))
                       (member (buffer-local-value 'major-mode b) modes)))))
        (pop-to-buffer (read-buffer "Buffer: " nil t pred))))

```

[Tags][1]: [emacs][2]

--------------------------------------------------------------------------------

via: https://jao.io/blog/high-signal-to-noise-emacs-command.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: https://jao.io/blog/tags.html
[2]: https://jao.io/blog/tag-emacs.html
