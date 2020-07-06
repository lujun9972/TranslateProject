[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (PSA: Please Just Close Your Files)
[#]: via: (https://theartofmachinery.com/2020/07/06/please_close_files.html)
[#]: author: (Simon Arneaud https://theartofmachinery.com)

PSA: Please Just Close Your Files
======

An article called “[Contrarian view on closing files][1]” is on the front page of Hacker News right now with over 60 upvotes. It starts off with a quote from the [Google Python style guide][2]:

> Explicitly close files and sockets when done with them. Leaving files, sockets or other file-like objects open unnecessarily has many downsides […]

The article’s main complaint is that “this advice is applying a notably higher standard of premature optimization to file descriptors than to any other kind of resource”. It complains that it’s “depressingly commonplace” to see code like this:

```
with open("README.md") as readme:
    long_description = readme.read()
```

Sure, if it’s a one-off read of a doc file, you can almost certainly get away with just `open("README.md").read()`, but I honestly have no idea what’s depressing about code that just works reliably.

Leaving files and sockets open is something that you can usually get away with, until weird stuff happens. And, no, it’s not just about running out of file descriptors (although that does happen, too). I’ve previously written about [servers that mysteriously ran out of disk space because (spoiler) they were deleting files that hadn’t been closed properly][3]. Regardless of how awesome your computer and network equipment are, the number of TCP connections you can make to a given host and port are limited by a 16 bit integer (and practically always limited more by your [network settings][4]), then you get network failures. Writing to files that you don’t explicitly close (or flush) is especially dicey — the write might actually happen straight away, then on another day or another environment it might get delayed.

Sure, these failure modes aren’t very common, but they definitely happen. I can think of three examples right now from the past few years of my day job. Closing files as a habit is easier than figuring out when it’ll go wrong.

The article has an example of a function that lazily loads JSON given a file path string. Sure, it doesn’t work properly if you close the file inside the function, but I’d say the problem is in the API design: the file handle resource straddles the interface.

The first good alternative is to keep the file handle completely inside: take a path argument, load the data eagerly, close the file and return the parsed data. The other good alternative is to keep the file handle completely outside: take a file handle as argument and return it wrapped in a lazy JSON parser. Either way makes it easier to see how and where the file should be closed.

The Google advice is pretty solid: when you’re done with a file or socket, just close it. I’ll add: sure, maybe it won’t always be obvious when you’re done with a handle, but perhaps that code design is making life more “exciting” than necessary. Production failures are more depressing than file closing code ever will be.

--------------------------------------------------------------------------------

via: https://theartofmachinery.com/2020/07/06/please_close_files.html

作者：[Simon Arneaud][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://theartofmachinery.com
[b]: https://github.com/lujun9972
[1]: https://coady.github.io/posts/closing-files/
[2]: https://google.github.io/styleguide/pyguide.html#311-files-and-sockets
[3]: https://theartofmachinery.com/2018/12/05/gc_not_enough.html
[4]: https://ma.ttias.be/linux-increase-ip_local_port_range-tcp-port-range/
