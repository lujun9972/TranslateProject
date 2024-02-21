[#]: subject: "Microblog: TestMain can cause one to question reality"
[#]: via: "https://dave.cheney.net/2024/02/22/microblog-testmain-can-cause-one-to-question-reality"
[#]: author: "Dave Cheney https://dave.cheney.net/author/davecheney"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Microblog: TestMain can cause one to question reality
======

This morning a one line change had several of us tearing up the fabric of reality trying to understand why a failing test wasn’t failing, or, in fact, being run at all. Increasingly frantic efforts to upgrade/downgrade Go, run the tests on another machine, run the tests in CI, all served to only unnerve us further.

Can you spot the bug?

```

    package gosh_darn_important_test

    import (
        "testing"
        "go.uber.org/goleak"
    )

    func TestMain(m *testing.M) {
    //  goleak.VerifyTestMain(m)
    }

    ...

```

Pages: 1 [2][1]

--------------------------------------------------------------------------------

via: https://dave.cheney.net/2024/02/22/microblog-testmain-can-cause-one-to-question-reality

作者：[Dave Cheney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://dave.cheney.net/author/davecheney
[b]: https://github.com/lujun9972
[1]: https://dave.cheney.net/2024/02/22/microblog-testmain-can-cause-one-to-question-reality/2
