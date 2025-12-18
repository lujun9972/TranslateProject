[#]: subject: "Pop quiz: what time was it?"
[#]: via: "https://dave.cheney.net/2025/12/18/pop-quiz-what-time-was-it"
[#]: author: "Dave Cheney https://dave.cheney.net/author/davecheney"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Pop quiz: what time was it?
======

Here’s a small quiz derived from some incorrect advice from an AI coding assistant.

```

    package main

    import (
        "fmt"
        "time"
    )

    func main() {
        fmt.Println(time.Now())
        defer fmt.Println(time.Now())
        time.Sleep(10 * time.Second)
    }

```

This program prints two timestamps; will they be

a. Roughly the same time (ie, the same second)
b. Roughly 10 seconds apart
c. Something else

Answer after the fold

Pages: 1 [2][1]

--------------------------------------------------------------------------------

via: https://dave.cheney.net/2025/12/18/pop-quiz-what-time-was-it

作者：[Dave Cheney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://dave.cheney.net/author/davecheney
[b]: https://github.com/lujun9972
[1]: https://dave.cheney.net/2025/12/18/pop-quiz-what-time-was-it/2
