[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (urllibparse)
[#]: via: (https://theartofmachinery.com/2020/01/21/urllibparse.html)
[#]: author: (Simon Arneaud https://theartofmachinery.com)

urllibparse
======

TL;DR: I’ve translated Python’s [`urllib.parse`][1] to D for parsing, building and transforming URLs. [You can get it from Gitlab.][2]

URL handling is one of those things that most of the time can be done with a regex that mostly works. But sometimes I want a just-works tool when writing D, so I translated Python’s URL handling library. The API isn’t perfect (e.g., the `url_split` and `url_parse` distinction is a bit confusing), but it’s been tested against multiple RFCs and had plenty of real-world battle hardening.

My translation is meant to give the same output as Python does, so I’ve translated the Python test suite as well. I don’t plan to add any new features that aren’t in Python.

I hope someone else finds it useful.

--------------------------------------------------------------------------------

via: https://theartofmachinery.com/2020/01/21/urllibparse.html

作者：[Simon Arneaud][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://theartofmachinery.com
[b]: https://github.com/lujun9972
[1]: https://docs.python.org/3/library/urllib.parse.html
[2]: https://gitlab.com/sarneaud/urllibparse
