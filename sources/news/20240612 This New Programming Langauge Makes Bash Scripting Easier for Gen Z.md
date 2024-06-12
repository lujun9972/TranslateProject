[#]: subject: "This New Programming Langauge Makes Bash Scripting Easier for Gen Z"
[#]: via: "https://news.itsfoss.com/amber-lang/"
[#]: author: "Abhishek https://news.itsfoss.com/author/root/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This New Programming Langauge Makes Bash Scripting Easier for Gen Z
======
Bash scripting but with high-level scripting syntax for new-age cloud
engineers.
[![][1]][2]

Does Bash scripting need an improvement?

Maybe not, but Amber thinks it can at least let you write bash scripts in a high-level programming language.

A high-level programming language is closer to the human, written in a language that is easier for us to understand and write the code.

So Amber makes it easier for you to write Bash scripts using a high level programming language. How? Let's explore.

### Amber: A programming language that compiles to Bash

🚧

This project is in the early stages of development with only an alpha release at the moment. Experiment with it if you want but don't use it in a production environment.

That's what [Amber][3] is. You write your scripts in a modern high level programming language and it is compiled as a bash shell script. It's as if you ran a bash script in the first place.

Amber is designed based on the ECMA script syntax. [ECMA aims to standardize the syntax][4] for general-purpose scripting languages. This way, you get a familiar syntax across various scripting languages that adhere to ECMA syntax.

So, you write your script into a high level language which is then compiled into a bash script. You can either run the amber script directly:

```

    amber script.ab

```

If you want, you can compile an Amber script into a bash shell script and then use this bash shell script wherever you want.

For example, I took a sample Amber script:

```

    // Define variables
    let name = "John"
    let age = 30

    // Display a greeting
    echo "Hello, my name is {name}"

    // Perform conditional checks
    if age < 18 {
        echo "I'm not an adult yet"
    } else {
        echo "I'm an adult"
    }

    // Loop through an array
    let fruits = ["apple", "banana", "cherry", "date"]
    echo "My favorite fruits are:"
    loop fruit in fruits {
        echo fruit
    }

```

And then compiled it into a Bash script:

```

    amber test.ab test.sh

```

And the generated `test.sh` file contained:

```

    __0_name="John";
    __1_age=30;
    echo "Hello, my name is ${__0_name}";
    if [ $(echo ${__1_age} '<' 18 | bc -l | sed '/\./ s/\.\{0,1\}0\{1,\}$//') != 0 ]; then
        echo "I'm not an adult yet"
    else
        echo "I'm an adult"
    fi;
    __AMBER_ARRAY_0=("apple" "banana" "cherry" "date");
    __2_fruits=("${__AMBER_ARRAY_0[@]}");
    echo "My favorite fruits are:";
    for fruit in "${__2_fruits[@]}"
    do
        echo "${fruit}"
    done

```

Needless to say both scripts produced the same result on my system.

Amber also aims to provide you a type-safe and runtime-safe programming language that could handle bugs and mistakes during the compilation.

The warning it throws is a lot easier to understand than the wild guessing game while dealing with a bash scripting syntax error. I mean "syntax error: unexpected end of file" is not enough to understand the syntax errors in your bash scripting, is it?

That feature itself would save major headaches for those who are new to bash scripting.

Amber is an open source project licensed under GPL 3.0.

[Exlopre Amber Language][3]

### Installing Amber on Linux

To install Amber language on Linux, you can use this bash script (amusing irony). You'll need sudo access here.

```

    curl -s "https://raw.githubusercontent.com/Ph0enixKM/AmberNative/master/setup/install.sh" | bash

```

Those emojis in the output indicate that Amber targets (or is written by) Gen Z Linux users. Typical sysadmin would have used echo commands with colored output 😉

![][5]

Amber has a pretty decent documentation that would help you get started with this scripting language.

![][6]

### Conclusion

It seems that 2024 is the year when we are seeing more new tools tailored toward the Gen-Z people (sorry for overusing the Gen Z term). It reminds me of [Warp terminal][7] that is for people who are not comfortable with the classic Linux terminals.

![][8]

Like Warp, Amber too is for new-age techies who want to enter the cloud and DevOps field without bothering much about learning and dealing with classic bash scripting.

You may scoff at it, but there is a new breed of DevOps who probably have never seen a Linux terminal or at least don't see it very often. They work on tools that abstract the underlying mechanism. While a seasoned sysadmin could say this could be done with a bunch of bash scripts, the tools make things easier.

Amber is not for everyone. It is definitely not for someone who regularly writes bash scripts. I think you would have to forget bash scripting first to use Amber.

But it could be a choice of tool for some who don't feel too comfortable with bash scripts but must write them in their workflow.

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/amber-lang/

作者：[Abhishek][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/root/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods.jpg
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://amber-lang.com/
[4]: https://262.ecma-international.org/5.1/
[5]: https://news.itsfoss.com/content/images/2024/06/install-amber-linux.png
[6]: https://docs.amber-lang.com/internal/favicon.png
[7]: https://news.itsfoss.com/warp/
[8]: https://news.itsfoss.com/content/images/size/w256h256/2022/08/android-chrome-192x192.png
