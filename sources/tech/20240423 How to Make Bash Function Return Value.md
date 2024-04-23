[#]: subject: "How to Make Bash Function Return Value"
[#]: via: "https://itsfoss.com/bash-function-return-value/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to Make Bash Function Return Value
======

[![Warp Terminal][1]][2]

If you have prior experience of programming and you are just getting started with bash, there's one thing that you may find a little odd.

**Unlike other programming languages, functions in bash do not return any value. Instead, it returns exit status or a numeric value indicating the success or failure of execution.**

But the question here is how you make the function return value in bash.

Sure, if I'm writing this tutorial, I must have a solution (read workaround) to tackle this issue but before that, let's understand the problem first.

### The problem we're dealing with

First, let me share a simple C program to explain how programming languages return value through a bash function:

```

    #include <stdio.h>

    // Function declaration with return type int
    int add(int x, int y) {
        return x + y;
    }

    int main() {
        // Call the function and store the result in a variable
        int result = add(3, 4);

        // Print the result
        printf("%d\n", result);

        return 0;
    }

```

If you run the above C program, it will return `7` as shown here:

![][3]

In the above C program, I created a function named `add` that takes two values and uses the return statement to add two values.

Sadly, functions in bash do not work that way and what they give you is the exit status of the last command used in the function and the exit status can be 0 (success) or non-zero (failure).

To know the exit bash, there's a [special variable in the bash][4] `$?` to know the exit status. So let me quickly share how you can use it:

```

    #!/bin/bash

    # Defining the function
    function test {
      echo "A demo function created to check the exit status"
    }

    # Calling function
    test

    # Checking the status
    echo "The exit status of the test is: $?"

```

![][5]

As you can see, it returned `0` indicating the function was executed successfully!

Now, let's have a look at how you can make the bash function return value.

### How to make bash functions return a value

There are two ways in which you can make the bash functions return a value:

  * Using the standard output data stream (involves usage of echo or print command)
  * Using global variable



Of course, it's not the same as returning values in C or other programming languages but it may help you in many cases.

So let's start with the first one.

#### Method 1: Using the standard output data stream

If you are unaware of data streams, there are 3 data streams in Linux: input, output, and error. Each is meant for a different task.

As the title suggests, I will use the standard output data stream using the echo or the printf command in this method.

Still confused? In simple words, I will be sending the output of the function to the standard output data stream to print the output (there's where the usage of the printf or echo command).

First, let me share a bash script:

```

    #!/bin/bash

    # Function definition
    function demo {
      local namaste="Namaste from Bash!"
      echo "${namaste}"
    }

    # Call the function and capture its output
    output=$(demo)

    # Print the captured output
    echo "${output}"

```

When executed, it will give you the following output:

![][6]

Now, let's have a look at the explanation part.

First, I created a function `demo` in which there was a local variable `namaste` containing the string that I wanted to print.

Later, I used the echo command to print the data inside of the `namaste` variable.

In the next part, I called the function inside of the `$()` notion which will execute the `demo` function in the subshell and the output is captured by the `output` variable.

Finally, [the echo command][7] was used to print the captured output of the `ouptut` variable.

Pretty easy. Right?

#### Method 2: Using a global variable

By default, every variable in the bash is global and to use the local variable, you have to use the term `local` before assigning any value to it.

But the question is how you use a global variable to return value in the bash function. Well, let me show a simple bash script that uses a global variable for that purpose:

```

    #!/bin/bash

    # Global variable to store the result
    output=""

    # Function definition
    function generate_greeting {
      local name=$1  # Function parameter

      # Assign the greeting to the global variable
      output="Hello, ${name}!"
    }

    # Call the function with a name as an argument
    generate_greeting "$USER"

    # Access the global variable
    echo "${output}"

```

The above script simply greets the currently logged-in user and when you execute the above script, you can expect the following output:

![][8]

Now, let's break down the script.

First, the empty global variable `output` was declared.

Then, the function named `generate_greeting` was created that takes one parameter `name` and in the next line, the greeting text with username was assigned to the `output` variable.

Next, the script will call the function `generate_meeting` with the `$USER` argument to get the name of the currently logged-in user.

Finally, using the echo command the value of the global variable `output` was printed.

Yep, that's all it takes you to use a global variable to make a function return value in bash.

### Which method to use? (in my opinion)

I personally don't like the idea of using a global variable to make the bash functions return a value and there's a simple reason why.

Global variables by their nature can be accessed and modified anywhere in the script which may cause trouble, especially if the script is complex and it may be changed by the user in between.

So what I'd recommend is to use the first method, which utilizes the standard output data stream.

I hope you will find this guide helpful.

### New to bash scripting? Start here 👇

![][9]

--------------------------------------------------------------------------------

via: https://itsfoss.com/bash-function-return-value/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2023/11/How-functions-in-C-programs-returns-value.png
[4]: https://linuxhandbook.com/bash-special-variables/
[5]: https://itsfoss.com/content/images/2023/11/Check-the-exit-status-in-bash.png
[6]: https://itsfoss.com/content/images/2023/11/Use-the-standard-output-data-stream-to-make-the-bash-function-return-value.png
[7]: https://linuxhandbook.com/echo-command/
[8]: https://itsfoss.com/content/images/2023/11/Use-global-variable-to-make-the-bash-function-return-value.png
[9]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
