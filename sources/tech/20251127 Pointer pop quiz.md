[#]: subject: "Pointer pop quiz"
[#]: via: "https://dave.cheney.net/2025/11/27/pointer-pop-quiz"
[#]: author: "Dave Cheney https://dave.cheney.net/author/davecheney"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Pointer pop quiz
======

Here’s a silly example extracted from real code.

```

    package main

    import "fmt"

    type Location int

    const (
        KITCHEN Location = iota
        BATHROOM
    )

    type Ingredient struct {
        name     string
        location Location
    }

    func (i *Ingredient) Location() *Location {
        return &i.location
    }

    func main() {
        sausage := Ingredient{name: "bratwurst", location: KITCHEN}
        legume := Ingredient{name: "chic pea", location: KITCHEN}
        fmt.Println(sausage.Location() == legume.Location())
    }

```

Does this program print `true` or `false`?

Pages: 1 [2][1]

--------------------------------------------------------------------------------

via: https://dave.cheney.net/2025/11/27/pointer-pop-quiz

作者：[Dave Cheney][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://dave.cheney.net/author/davecheney
[b]: https://github.com/lujun9972
[1]: https://dave.cheney.net/2025/11/27/pointer-pop-quiz/2
