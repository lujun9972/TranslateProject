[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Getting Started with Haskell on Fedora)
[#]: via: (https://fedoramagazine.org/getting-started-with-haskell-on-fedora/)
[#]: author: (Tristan de CACQUERAY https://fedoramagazine.org/author/tdecacqu/)

Getting Started with Haskell on Fedora
======

![][1]

[Haskell][2] is a functional programming language. To create a program, the user applies and composes functions, in comparison to imperative languages, which use procedural statements.

Haskell features state-of-the-art programming paradigms that can be used for general purpose programs, research, and industrial applications. Most notably, it is purely functional using an advanced type system, which means that every computation, even the ones that produce side-effecting IO operations, are defined using pure functions in the mathematical sense.

Some of the main reasons for Haskell’s increasing popularity are ease of maintenance, extensive packages, multi-core performance, and language safety against some bugs, such as null pointers or deadlock. So let’s see how to get started with Haskell on Fedora.

### Install Haskell in Fedora

Fedora provides an easy way to install the Glasgow Haskell Compiler (GHC) via the official repository:

```
$ sudo dnf install -y ghc
$ ghc --version
The Glorious Glasgow Haskell Compilation System, version 8.6.5
```

Now that GHC is installed, let’s write a simple program, compile it, and execute it.

### First program in Haskell

Let’s write the traditional “Hello, World!” program in Haskell. First, create a _main.hs_ file, and then type or copy the following.

```
main = putStrLn ("Hello, World!")
```

Running this program is quite simple.

```
$ runhaskell main.hs
Hello, World!
```

Building an executable of the program is as simple as running it.

```
$ ghc main.hs
[1 of 1] Compiling Main             ( main.hs, main.o )
Linking main ...
$ ./main
Hello, World!
```

GHC provides a Read Eval Print Loop (REPL) command to interactively evaluate Haskell expressions.

```
$ ghci
Prelude> :load main.hs
[1 of 1] Compiling Main             ( main.hs, interpreted )
Ok, one module loaded.
*Main> main
Hello, World!
*Main> :type putStrLn
putStrLn :: String -> IO ()
*Main> :info String
type String = [Char]    -- Defined in ‘GHC.Base’
*Main> :help
...
```

The most common REPL commands are:

  * _:load_ loads a file.
  * _:reload_ reloads loaded files.
  * _:type_ shows the type of an expression.
  * _:info_ displays information about a name.
  * _:browse_ lists the loaded functions.



### Using Haskell packages

Haskell features a package system to share functions.

To show how to use packages, let’s write a new one. First, create a _MyPackage.hs_ file, and then, type or copy the following.

```
module MyPackage where

greet name = putStrLn ("Hello, " ++ name ++ "!")
```

Next, modify the _main.hs_ file as follow:

```
import MyPackage

main = greet ("Fedora")
```

In the modified _main.hs_, instead of using the standard _putStrLn_ function to print the “Hello, World!” the application now uses the greet function from the newly created package:

```
$ runhaskell main.hs
Hello, Fedora!
```

GHC automatically looks for packages in the current working directory, and it can also looks for packages installed globally on the system. To use a Fedora package in your Haskell project, you need to install the development files. For example, let’s use the _ansi-wl-pprint_ library to add color:

```
$ sudo dnf install -y ghc-ansi-wl-pprint-devel
```

Next, modify the _MyPackage.hs_ file:

```
module MyPackage where

import Text.PrettyPrint.ANSI.Leijen

greet name = putDoc (green (text ("Hello, " ++ name ++ "!\n")))
```

Then you can build a small executable using dynamic links:

```
$ ghc -dynamic main.hs -o greet && strip greet
[1 of 2] Compiling MyPackage        ( MyPackage.hs, MyPackage.o )
[2 of 2] Compiling Main             ( main.hs, main.o )
Linking greet ...
$ du --si greet
17k     greet
$ ./greet
Hello, Fedora!
```

This concludes how to get started with Haskell on Fedora. You can find the Haskell SIG ([Special Interests Groups][3]) on Freenode IRC in #fedora-haskell, or in the [mailing list][4]

### Learning resources

Haskell may be daunting because it supports many advanced concepts such as _GADTs_ or _type-level programing_. However, the basics are quite accessible and they are more than enough to reap the majority of benefits and reliably deliver quality software.

To learn more about the language, here are some further resources:

  * [Why Haskell Matter][5]
  * [What I Wish I Knew When Learning Haskell][6]
  * [Shell programming, Haskell-style][7]
  * [Yorgey’s cis194 course][8]
  * [Haskell Programming from First Principles][9]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/getting-started-with-haskell-on-fedora/

作者：[Tristan de CACQUERAY][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/tdecacqu/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2020/06/haskell-gettingstarted-on-fedora-816x346.png
[2]: https://www.haskell.org/
[3]: https://fedoraproject.org/wiki/Category:SIGs
[4]: https://lists.fedoraproject.org/mailman/listinfo/haskell
[5]: https://github.com/thma/WhyHaskellMatters
[6]: http://dev.stephendiehl.com/hask/
[7]: https://hackage.haskell.org/package/turtle-1.5.18/docs/Turtle-Tutorial.html
[8]: https://www.seas.upenn.edu/~cis194/spring13/lectures.html
[9]: https://lorepub.com/product/haskellbook
