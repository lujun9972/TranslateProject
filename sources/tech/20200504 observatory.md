[#]: subject: "observatory"
[#]: via: "https://jao.io/blog/observatory.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

observatory
======

![][1]

i've been learning a tiny bit about web security at mozilla's [Web Security][2] pages, and used their [Mozilla Observatory][3] to analyize this site and make it a bit safer. it was just a matter of adding a handful of headers to the webserver configuration, to wit:

```

    Header always set Strict-Transport-Security "max-age=63072000; includeSubdomains;"
    Header always set X-Frame-Options DENY
    Header always set X-Content-Type-Options nosniff
    Header set X-XSS-Protection "1; mode=block"
    Header always set Content-Security-Policy \
      "default-src 'self'; img-src 'self'; font-src 'self'; object-src 'none'"

```

[Tags][4]: [sundry][5]

--------------------------------------------------------------------------------

via: https://jao.io/blog/observatory.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: https://jao.io/img/observatory.png
[2]: https://infosec.mozilla.org/guidelines/web_security#x-content-type-options
[3]: https://observatory.mozilla.org/
[4]: https://jao.io/blog/tags.html
[5]: https://jao.io/blog/tag-sundry.html
