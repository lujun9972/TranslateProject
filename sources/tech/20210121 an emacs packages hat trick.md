[#]: subject: "an emacs packages hat trick"
[#]: via: "https://jao.io/blog/emacs-packages-hat-trick.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

an emacs packages hat trick
======

i've found these last days a handful of really useful little emacs packages:

  * [smartscan][1], a simple way of navigating programming modes

```
     (use-package smartscan
      :ensure t
      :commands smartscan-mode
      :init (add-hook 'prog-mode-hook #'smartscan-mode)
      :diminish)

```

  * [git-link][2], because i almost never look at files using the browser, but some people don't have my repos checked out. Specially nice the bit about being able to use git config variables.

```
     (use-package git-link
      :ensure t
      :custom ((git-link-default-remote "bigml")))

```

  * `visible-mode`, an Emacs built-in, especially useful in org buffers, where i hide markup and sometimes it's a chore to ascertain whether point is before or after a it. With a binding to this minor mode, it's a breeze to toggle them:

```
     (use-package visible-mode
      :bind (("s-v" . visible-mode)))

```




Tip of the hat to [Daniel Mai][3], for a couple of the above. You might find some other interesting tidbits in his config.

[Tags][4]: [emacs][5]

--------------------------------------------------------------------------------

via: https://jao.io/blog/emacs-packages-hat-trick.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: http://www.masteringemacs.org/article/smart-scan-jump-symbols-buffer
[2]: https://github.com/sshaw/git-link
[3]: https://github.com/danielmai/.emacs.d/blob/master/config.org
[4]: https://jao.io/blog/tags.html
[5]: https://jao.io/blog/tag-emacs.html
