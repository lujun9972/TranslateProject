[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (What I learned while teaching C programming on YouTube)
[#]: via: (https://opensource.com/article/20/8/teaching-c)
[#]: author: (Jim Hall https://opensource.com/users/jim-hall)

What I learned while teaching C programming on YouTube
======
Sharing knowledge with others is often a great way to refresh and update
your own expertise.
![Person reading a book and digital copy][1]

The act of breaking something down in order to teach it to others can be a great way to reacquaint yourself with some old concepts and, in many cases, gain new insights.

I have a [YouTube channel][2] where I demonstrate FreeDOS programs and show off classic DOS applications and games. The channel has a small following, so I tend to explore the topics directly suggested by my audience. When several subscribers asked if I could do more videos about programming, I decided to launch a new video series to teach C programming. I learned a lot from teaching C, and in the process, I came across some meaningful takeaways I think others will appreciate.

### Make a plan

[For my day job][3], I lead training and workshops to help new and emerging IT leaders develop new skills. Outside of regular work, I also enjoy teaching as an adjunct professor. So I'm very comfortable constructing a course outline and designing a curriculum. That's where I started. If you want to teach a subject effectively, you can't just wing it.

Start by writing an outline of what topics you want to cover and figure out how each new topic will build on the previous ones. The "building block" method of adding new knowledge is key to an effective training program.

To teach C programming as a "follow along" video series, I created this initial outline:

  1. Introduction to C programming—`#include`, `#define`, `main()`, data types, and operators
  2. Flow control—flow control and loops
  3. Functions—user-defined, standard library, and recursion
  4. Arrays—fixed-size arrays, pointers, and variable-sized arrays
  5. Files—reading and writing files
  6. Advanced programming—`realloc`, `getline`, and binary
  7. Console programming—`conio`
  8. Putting it together—writing a turn-based game



Each topic builds upon previous topics, and by the end of the series, we have learned enough about C programming to write a full-screen game.

### Show and tell

I originally planned to just record a video series about C programming, but I quickly realized that people would need some kind of written tutorial; there's just too much information to include in a one-hour video. To accompany each week's video, I decided to write a short programming guide to explain the week's topics in more detail. The guide also included lists of new library functions or programming concepts that provided a "quick reference" to learning C.

Fortunately, this worked in my favor. Recording an hour-long video requires planning, and I like to plan. A few days before recording the next video, I wrote out the topics I wanted to cover, and the sample code I wanted to demonstrate on screen. This gave me an outline to narrow the focus of the video. After recording the video, I expanded my notes into a programming guide that I posted online.

### Make it immediately applicable

Most people learn best by doing; that's why each "chapter" or "unit" in the series includes several example programs that you can follow to learn about programming. I didn't want the series to be just about the theory of writing programs, but also about actually doing it. For example, in the first chapter, Introduction to C programming, we learn by writing programs to calculate the area of a circle, and how to divide two numbers with a remainder.

Every unit also ends with several "practice programming" tasks that help users to exercise their new knowledge. These exercises directly apply concepts that I introduced in that week's video to reinforce what we learned.

Most importantly, I demonstrate how to write actual FreeDOS programs as part of the video series. For example, in the video where I introduce loops, I also show how to use a `do-while` loop to write a version of the FreeDOS PAUSE command to wait for the user to press Enter. Throughout the rest of the series, I write versions of FreeDOS ECHO, TYPE, MORE, FIND, CLS, and COPY to demonstrate how to apply new concepts.

### Be willing to learn

As I continued in the series, I found it fascinating to explore new topics for myself. For example, because I learned C so long ago, and exercised my C programming by writing programs using C compilers on DOS, I never learned the `getline` function. This is a newer function that reads a line of arbitrary length from the user. `getline` is a preferred method to read user input over the `fgets` function and the more dangerous `gets` function. But before recording the videos, I didn't know much about `getline`.

Interestingly, I'd actually written my own versions of `getline` to use on my own, as I'm sure countless other programmers have. But I didn't realize it was part of the newer C standard, having been added around 2010. In teaching C programming, which by nature requires reading user input, I also learned a "new to me" C programming function.

I also honed my own developer skills. As a self-taught programmer, I know I picked up bad habits early on. Some of those habits were best practices when coding in other programming languages, but aren't great habits in C. AppleSoft BASIC limits variable names to two letters. Fortran can assume variables that start with I-N will be integer variables. So, my default when writing my own programs is to use a simply-named variable like `i` to iterate through a list, or `max` to store a maximum value for something.

But in teaching C programming to someone else, I wanted to demonstrate good programming behaviors. I eventually broke my bad habit of short variable names. By the end of the programming video series, I was writing descriptive variable names like `colornum` to store an index to a list of colors, `player` to indicate "Player 1" or "Player 2," and `message` to store a message. I think I've finally broken most of the bad habits of 20+ years of self-taught programming.

Teaching very often goes both ways—as you share knowledge, you pick up new facts and perspectives. No matter your skill or familiarity with a topic, never be afraid to pick up the "teacher" mantle and help someone else learn.

If you want to learn C yourself, you can find the C programming series [here][4].

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/teaching-c

作者：[Jim Hall][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/jim-hall
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/read_book_guide_tutorial_teacher_student_apaper.png?itok=_GOufk6N (Person reading a book and digital copy)
[2]: https://www.youtube.com/freedosproject
[3]: https://opensource.com/article/19/9/business-creators-open-source-tools
[4]: https://www.freedos.org/books/cprogramming/
