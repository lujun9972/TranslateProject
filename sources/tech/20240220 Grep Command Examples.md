[#]: subject: "Grep Command Examples"
[#]: via: "https://itsfoss.com/grep-command/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Grep Command Examples
======

" _Everything is a file in Linux_ " and that is the reason most Linux users spend a large chunk of time tinkering the file contents.

This is where the importance of the grep command plays a crucial role by letting you **search and match patterns within text files** or get an output.

So in this tutorial, I will walk you through all the essentials required to learn the grep command:

  * **The basic syntax and popular flags of the command**
  * **Practical examples of the command**
  * **Practice questions for grep command**



### Here's How to Use the grep command

To use the grep command, it is important to know the syntax.

So here's the basic syntax of the grep command:

```

    grep [OPTIONS] PATTERN <Filename>

```

Here,

  * `[OPTIONS]`: using the given set of options, you can change the default behavior of the grep command such as using the `-i` enables case-insensitive search.
  * `PATTERN`: Here's where you specify the text you are looking for from the file or the command output. It can also be a regular expression for more complex patterns.
  * `<Filename>`: Here you specify the file you want to search within and if you don't specify any file then it will search from the standard input.



Now, let's take a look at some commonly used options with the grep command:

**Option** | **Description**
---|---
`-i` | Ignores case sensitivity in the search.
`-v` | Prints lines that don't match the pattern.
`-n` | Displays the line number of each matching line.
`-w` | Matches only whole words, not parts of words.
`-c` | Counts the number of matching lines, doesn't print the lines.
`-r` | Searches through directories recursively.
`-A n` | Prints n lines after each matching line.
`-B n` | Prints n lines before each matching line.
`-C n` | Prints n lines before and after each matching line.
`-f Filename` | Reads search patterns from a file, one per line.
`-o` | Prints only the matched part of the line.

You might be wondering — what happens when you use the grep command without any options? Well, it simply prints the lines containing the pattern.

For example, here, I want to search for the `error` keyword within the file named `error.log` , and without any additional options, it gave me this output:

![][1]

Did you see that? It highlights the found pattern and also prints the lines containing the pattern.

To make this tutorial easy to follow, I will use a sample file named `error.log` which includes the following lines:

```

    This is a log file with various messages.
    An error occurred at 10:00 AM.
    The system encountered an unexpected issue.
    Everything is working normally now.
    Another error message at 11:30 AM.
    Warning: Please check disk usage.
    Log closed at 12:00 PM

```

### Practical examples of the grep command

In this section, I cover various examples of the grep command so you can have a better idea of how you can use the grep command.

#### 1\. Case-insensitive search

By default, the grep command patterns are case-sensitive, and for the most part, it works well, but you may want to turn off the case sensitivity.

To do so, you can use the `-i` flag as shown here:

```

    grep -i PATTERN Filename

```

To demonstrate this, I will use `ERROR` as a search pattern, and it will show matching patterns irrespective of case sensitivity:

```

    grep -i ERROR error.log

```

![][2]

#### 2\. Show `n` lines before and after the matching lines

By default, the grep command only prints the matching lines, but sometimes you want the context of the matched lines. So you print the lines before and after the matching lines.

###### Print `n` lines before the matching lines

To print n number of lines before matching lines, you use the `-B` flag and specify the number of lines to print as shown here:

```

    grep -B <number_of_lines> PATTERN Filename

```

For example, here, I printed the one line before every matching line:

```

    grep -B 1 error error.log

```

![][3]

###### Print `n` lines after the matching lines

To print the n number of lines after the matching lines, you use the `-A` flag and specify the number of lines as shown here:

```

    grep -A <number_of_lines> PATTERN Filename

```

If I want to print one line after the matching lines, then I will use the following:

```

    grep -A 1 error error.log

```

![][4]

###### Print `n` lines before and after matching lines

If you want to print lines before and after altogether, then you use the `-C` flag and specify the number of lines to print as shown here:

```

    grep -C <number_of_lines> PATTERN Filename

```

Let's say I want to display 1 line before and 1 line after the matching pattern line, then I will be using the following:

```

    grep -C 1 error error.log

```

![][5]

#### 3\. Show lines that do not match the pattern

For the most part, you'll be using the grep command to match patterns, but it also allows you to invert the search results.

In simple terms, you specify the search term, and it will print lines that do not match the given pattern and for that purpose, you use the `-v` flag as shown here:

```

    grep -v PATTERN Filename

```

For example, if I want to print every line that does not contain the `error` term, then I will use the following:

```

    grep -v error error.log

```

![][6]

#### 4\. Display the number of matched lines

To display the number of matched lines, all you have to do is use the `-n` flag as shown:

```

    grep -n PATTERN Filename

```

![][7]

#### 5\. Display the total number of matched results

If you want to know the number of matched results, then you can use the `-c` flag as shown:

```

    grep -c PATTERN Filename

```

For example, here, I wanted to find how many times the term `error` is mentioned in the `error.log` file, so I used the following command:

```

    grep -c error error.log

```

![][8]

#### 6\. Search for a pattern in multiple files

If you wish to search for a pattern from multiple files, then all you have to do is append multiple files to search, as shown here:

```

    grep PATTERN File1 File2

```

For example, here, I searched for the `error` string from two files: `error.log` and `error.txt` and it gave me the following output:

```

    grep error error.log error.txt

```

![][9]

#### 7\. Search pattern from every file in the directory

If you want to search for a specific pattern from every file present in the directory, then you can use the grep command recursively, and it will search the given pattern from every file present in that specific directory.

To enable recursive search, use the `-r` flag as shown:

```

    grep -r PATTERN <Directory or path to directory>

```

For example, here, I have searched for the `error` string in the current directory:

```

    grep -r error .

```

![][10]

#### 8\. Search for the exact word

By default, the grep command will print all the matching patterns, which is not what you always want. Sounds strange? Allow me to explain.

Suppose you want to search for the term `Orange` but if the specific file also contains the term `Oranges` then the line containing the term `Oranges` will also be shown as an output.

To overcome this problem, you can use the `-w` option and specify the pattern:

```

    grep -w PATTERN Filename

```

For example, here, I intend to find the term `err` so I will use the `-w` flag and will also show you the difference between what happens when you don't use it.

```

    grep -w err error.log

```

![][11]

When I used the `-w` flag to find the `err` string, it returned no results, as it does not exist.

But in the second attempt where I removed the `-w` flag, it returned two results displaying content where the string pattern is a part of another string (not separate).

#### 9\. Use regex pattern for advanced search

If the normal search is not doing justice, then you can use the regex pattern ( _sequence of characters_ ) to have better control over your search. You can use the `-e` flag to use the regex pattern, whereas `-E` let you use the extended regex:

```

    grep -e/-E PATTERN Filename

```

For example, here I have used the extended regex to find two vowels used together in the file:

```

    grep -e '[aeiouAEIOU]{2}' error.log

```

![][12]

**Suggested Read 📖**

![][13]

#### 10\. Specify multiple patterns using the OR operator

You can use the OR operator to specify multiple patterns, which is quite helpful when you want to search for multiple patterns efficiently.

To specify multiple patterns, use the OR operator (|) in the following manner:

```

    grep 'PATTERN_1\|PATTERN_2' Filename

```

💡

You can press Shift + Backslash key to get the OR operator.

Let's say I wish to look for two patterns: `error` and `Please` then I will be using the following:

```

    grep 'error\|Please' error.log

```

![][14]

### Practice questions 📓

Practicing is the best way you can learn, and that's why I'm about to share some practice questions for the grep command.

You can use the `error.log` file which I mentioned at the beginning of this guide to solve the following questions:

  1. Find the `error` string from every file present in your working directory.
  2. Find lines that do not contain the term `success`.
  3. Search for lines in a file that contain either `error` or `issue`.
  4. Find the term `log` by disabling case-sensitive search and redirecting the output to a file.
  5. How do you print only the last 2 results ignoring everything else? (Hint: [use the tail command][15])



If you discover any difficulties solving the above problems, reach out to us through the comments or post your query in [our community forum.][16]

You can download a [grep command cheat sheet][17] for more examples and info:

![][13]

### Are You An Advanced User? Try ripgrep

The ripgrep command does everything the grep command does but has some additional benefits like performance and features including the ability to search within the zip file.

Sounds cool? Here's [how to install and use ripgrep in Linux][18]:

![][13]

Moreover, if you are new to Linux, I suggest you to also go through our [command tutorial for beginners][19].

![][20]

💬 _Share your thoughts on the command, your experience with it, and what do you prefer as an alternative to grep?_

--------------------------------------------------------------------------------

via: https://itsfoss.com/grep-command/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/content/images/2024/02/Effect-of-using-the-grep-command-without-any-options.png
[2]: https://itsfoss.com/content/images/2024/02/case-insensitivity-in-the-grep-command.png
[3]: https://itsfoss.com/content/images/2024/02/Show-lines-before-matching-pattern-in-grep-command.png
[4]: https://itsfoss.com/content/images/2024/02/Print-lines-after-the-matching-pattern-in-grep-command.png
[5]: https://itsfoss.com/content/images/2024/02/Print-one-line-before-and-one-line-after-the-matching-pattern-line-using-grep.png
[6]: https://itsfoss.com/content/images/2024/02/print-everything-except-the-given-pattern-using-the-grep-command.png
[7]: https://itsfoss.com/content/images/2024/02/display-the-number-of-the-matched-lines-using-the-grep-commadn-in-linux.png
[8]: https://itsfoss.com/content/images/2024/02/Find-the-number-of-matched-results-via-grep.png
[9]: https://itsfoss.com/content/images/2024/02/Search-pattern-from-the-multiple-files-using-the-grep-command.png
[10]: https://itsfoss.com/content/images/2024/02/recursive-search-using-the-grep-command.png
[11]: https://itsfoss.com/content/images/2024/02/Find-the-exact-word-using-the-grep-command.png
[12]: https://itsfoss.com/content/images/2024/02/Use-regex-with-grep-command.png
[13]: https://linuxhandbook.com/content/images/size/w256h256/2021/08/Linux-Handbook-New-Logo.png
[14]: https://itsfoss.com/content/images/2024/02/Use-multiple-patterns-with-the-grep-command.png
[15]: https://linuxhandbook.com/tail-command/
[16]: https://itsfoss.community/
[17]: https://linuxhandbook.com/grep-command-cheatsheet/
[18]: https://linuxhandbook.com/ripgrep/
[19]: https://itsfoss.com/tag/terminal-basics/
[20]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
