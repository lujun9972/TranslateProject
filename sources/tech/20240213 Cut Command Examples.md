[#]: subject: "Cut Command Examples"
[#]: via: "https://itsfoss.com/cut-command/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Cut Command Examples
======

The cut command is used to cut a specific part of a file and print it to the standard output **without changing the actual file.**

In other words, you can pull out a specific number of words or characters from a file using the cut command.

Fret not, I walk you through the essentials to help you know more about it:

  * **The basic syntax of the command**
  * **Practical examples of using the cut command**
  * **Practice questions for the cut command**



So, let's get started.

### Here's How to use the cut command

To use the cut command, it is important to know the syntax.

So here's the basic syntax you need to follow to use the cut command:

```

    cut [option] <Filename or path to file>

```

Here,

  * `[option]`: it is used to change the default behavior of the cut command.
  * `Filename`: it is where you append the filename or the path to the file to work with the cut command.



If you are curious, here's a list of popular options used with the cut command:

**Option** | **Description**
---|---
`-d ` | Sets the field delimiter (default is tab).
`-f ` | Specifies which fields to extract (e.g., `-f 2` for the second field).
`-b ` | Cuts specific bytes or byte ranges.
`-c ` | Cuts specific characters or character ranges.
`-s` | Only prints lines containing delimiters (default prints empty lines).
`--complement` | Cuts everything except the specified bytes, characters, or fields.

To keep the tutorial easy to follow, I will be using one text file named `Haruki.txt` throughout all the examples, which contains the following content:

```

    Book_Name       Year
    Hear the Wind Sing (A Wild Sheep Chase) (1973)
    Pinball,        (1973)
    Norwegian Wood  (1987)
    A Walk to the Bakery    (1982)
    Hard-Boiled Wonderland and the End of the World (1985)
    The Wind-Up Bird Chronicle      (1994-1995)
    Sputnik Sweetheart      (1999)
    Kafka on the Shore      (2002)
    After Dark      (2004)
    1Q84    (2009-2010)
    Colorless Tsukuru Tazaki and His Years of Pilgrimage    (2013)
    Killing Commendatore    (2017)
    First Person Singular   (2020)

```

Now, let's take a look at some examples of using the cut command in Linux.

### 1\. Cut by bytes

📋

1 character = 1 byte.

The simplest way you can cut the characters using the cut command is to specify the byte of space in memory occupied by a text and cut the desired part of the file.

To cut by bytes, you can use the `-b` flag, and then you specify the position in-terms of terms of indexing:

```

    cut -b <nth byte> Filename

```

For example, if I want to cut the **fifth character** , then use the following:

```

    cut -b 5 Haruki.txt

```

![][1]

In simple terms, use the bytes as the index number. Let's say you would like to cut the seventh character, then you specify `7` along with the `-b` flag.

###### Cut multiple characters from each line

You can cut multiple characters from each line using the `-b` flag, where you specify the multiple bytes separated by commas.

For example, if I want to cut the third, sixth, and seventh character from each line, then I'll use the following:

```

    cut -b 3,6,7 Haruki.txt

```

![][2]

###### Cut a range of characters

With the cut command, you can also specify the range of the characters that need to be cut.

For example, if I wish to cut from the third to seventh character, then I will use the following:

```

    cut -b 3-7 Haruki.txt

```

![][3]

###### Cut everything except specific bytes

You can use the `--complement` flag to cut everything but not the specific bytes by which you can ignore the specified bytes and print everything else.

To use the `--complement` flag, you'd have to follow the given syntax:

```

    cut -b <bytes> --complement Filename

```

Let's say I want to ignore the first five bytes, then I will use the following:

```

    cut -b 1-5 --complement Haruki.txt

```

![][4]

###### Specify the starting or end point to cut

Using the cut command, you can also specify the starting point from where you intend to start cutting the characters or the endpoint to stop.

To specify the starting point, you use the `n-` where the `n` is the number from where you want to start cutting off the characters until the end of the line:

```

    cut -b n- Filename

```

For example, if I wish to cut from the fifth character until the end of the line, then I will use the following:

```

    cut -b 5- Haruki.txt

```

![][5]

To specify the endpoint, you use the `-n` ( _notice the dash before n_ ) where the `n` is the last character indicating the borderline to cut:

```

    cut -b -n Filename

```

For example, if I want to cut until the seventh character, I will use the following:

```

    cut -b -7 Haruki.txt

```

![][6]

**Suggested Read 📖**

![][7]

### 2\. Cut by characters

This is exactly like the byte option but here, it utilizes character indexing rather than byte indexing which is helpful, especially in cases where a single character uses multiple bytes.

For example, if I want to cut the first five characters, then I will use the `-c` flag in the following manner:

```

    cut -c 5 Haruki.txt

```

![][8]

You can also specify the range of the characters using the `-c` flag. Let's say I would like to cut from the seventh to tenth character, then I will be using the following:

```

    cut -c 7-10 Haruki.txt

```

![][9]

Furthermore, you can also cut by specifying the starting and endpoint as I explained earlier. Here's how I will cut till the 10th character using the `-c` flag:

```

    cut -c -10 Haruki.txt

```

![][10]

You can also specify what characters to ignore and print everything else using the `--complement` flag.

For example, here, I printed everything ignoring 10th to 15th character:

![][11]

### 3\. Cut by the fields

By default, when you want to cut by field, it will use a tab space as a delimiter. Sure you can use a different delimiter, which I will also mention.

To cut by the field, use the `-f` flag as shown here:

```

    cut -f <number of fields> Filename

```

For example, if I wish to cut 1 field, then I will be using the following:

```

    cut -f 1 Haruki.txt

```

![][12]

To change the delimiter, you have to use the `-d` flag followed by the delimiter you want to use:

```

    cut -d "delimiter" -f <number of fields> Filename

```

For example, here, I have used `a` as a character so it will print until the character `a` appears in the line:

```

    cut -d "a" -f 1 Haruki.txt

```

![][13]

### 4\. Concatenate output using delimiter

When you use a delimiter, it concatenates output without using a delimiter, so you end up having output separated by space.

You can change this behavior using the `--output-delimite` flag.

📋

The --output-delimite flag will only with when the output is divided into two or more columns.

To use the `--output-delimite` flag, use the following syntax:

```

    cut <options for cutting file> --output-delimite=delimiter Filename

```

For example, here, I used the `-c` flag to cut different parts of the file and then use the `--output-delimite` flag to concatenate output with the `@`:

```

    cut -c 1-5,9,11-14 --output-delimiter=@ Haruki.txt

```

![][14]

Did you see that? First I used the `-c` flag to print the 1 to 5, then 9th, and then 11 to 14th characters, and then merged the whole output with the `@`.

### Practice questions 🗒️

In this section, I share some practice questions that you can use to get better at using the cut command:

  1. Save the output of the cut command by [redirecting it to a file.][15]
  2. How do you print the first 5 characters of the file using the cut command?
  3. Print everything ignoring the following range of characters: 2-6, 10, 12-15.
  4. Use `e` as a delimiter and divide the file into 2 parts.



### Wrapping Up

This tutorial went through the basics of using the cut command, including the syntax, practical examples, and practice questions. You can explore more examples in our blog post at Linux Handbook:

![][16]

If you are starting out, you might want to refer to our [Linux command guide for beginners][17]:

![][7]

--------------------------------------------------------------------------------

via: https://itsfoss.com/cut-command/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/content/images/2024/01/image-7.png
[2]: https://itsfoss.com/content/images/2024/01/image-8.png
[3]: https://itsfoss.com/content/images/2024/01/image-9.png
[4]: https://itsfoss.com/content/images/2024/01/image-15.png
[5]: https://itsfoss.com/content/images/2024/01/image-6.png
[6]: https://itsfoss.com/content/images/2024/01/image-10.png
[7]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[8]: https://itsfoss.com/content/images/2024/01/image-11.png
[9]: https://itsfoss.com/content/images/2024/01/image-12.png
[10]: https://itsfoss.com/content/images/2024/01/image-13.png
[11]: https://itsfoss.com/content/images/2024/01/image-16.png
[12]: https://itsfoss.com/content/images/2024/01/image-14.png
[13]: https://itsfoss.com/content/images/2024/01/image-17.png
[14]: https://itsfoss.com/content/images/2024/01/image-18.png
[15]: https://linuxhandbook.com/command-output-to-file/
[16]: https://linuxhandbook.com/content/images/size/w256h256/2021/08/Linux-Handbook-New-Logo.png
[17]: https://itsfoss.com/tag/terminal-basics/
