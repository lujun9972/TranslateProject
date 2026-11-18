[#]: subject: "Hacking Wordle: A New User's Guide to the Power of the Linux Terminal"
[#]: via: "https://fedoramagazine.org/hacking-wordle-a-new-users-guide-to-the-power-of-the-linux-terminal/"
[#]: author: "Thomas Cummings https://fedoramagazine.org/author/tncummings/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Hacking Wordle: A New User's Guide to the Power of the Linux Terminal
======

![][1]

Photo by [Nils Huenerfuerst][2] on [Unsplash][3] [cropped]

For new Linux users the terminal can be like the Sphinx, quiet, mysterious, and offering no help to those who do not already speak its language. Here we'll show you how to get comfortable with the terminal by using some common commands to analyze a text file of words used by the popular online game, [Wordle][4].

This analysis has real tasks to work on, giving you hands-on experience with the Linux command line. You'll be able to apply this experience to also work with logs, configuration files, and search for text inside files. These are fundamental skills an experienced user needs. Plus, you'll have some fun with Wordle.

### I've Been Living Under A Rock. What's Wordle?

Wordle is an oddly addictive word game hosted by the New York Times. The goal of Wordle is to guess a five-letter word in no more than six guesses. The rules are simple. Guess a five-letter word. Wordle will mark letters that are not used, letters used but in the incorrect location, and letters in the correct location with different colors. Guess another word using the previous word's clues. Keep guessing until you've guessed the word or run out of guesses.

Wordle uses a curated list of words, so not every possible five-letter word can be a Wordle word. Offensive words, words with special characters or spaces, words using non-American spellings, and names (words that should be capitalized) are not used. Only certain plural and past tense words are accepted. Take a look at the [full Wordle rules][5]. These word rules narrow down possible Wordle words from some 20,000 dictionary five-letter words to about 2,500 words in the curated list.

Can the tools shown here be used to cheat at Wordle? If you play against others, the answer is yes. Being smart and clever about games is fun. Cheating is not fun....for anyone. Use this power for good only.

### The Sphinx Speaks - First Look at the Terminal

If you're new to the terminal, let's take a quick tour. The application that let's you access the terminal from your desktop is a terminal emulator. On Fedora Workstation it is called Terminal. Fedora KDE uses a terminal emulator called Konsole. Open your terminal emulator application, and let's take a look around.

At the top left of the terminal window you see the prompt. The blinking cursor shows you where to type commands. The terminal uses software called a shell to communicate with the operating system. The terminal can use different shells, but we're going to use the default shell used by almost all Linux distributions, bash. You are probably already using bash, but let's confirm. To check your shell, type this command and hit Enter:

```

    user@host:~$ echo $SHELL
    /bin/bash

```

If the response is /bin/bash, you're set. If you get other responses (e.g., /bin/csh, /bin/ksh/, /bin/zsh), you're using a different shell. You may have problems with some of the tools we'll use. You can still follow along and run most of the commands, but you may encounter some issues.

The echo command just tells the terminal to "echo back" the item ($SHELL) to you. The item in question is a variable the system uses to hold the location to the preferred shell of the logged-in user.

Assuming you are using bash on Fedora, your prompt should look something like this:

```

    user@host:~$

```

On some other Linux distributions, you may see a prompt that looks like this:

```

     [user@host ~]$

```

Either way, the prompt gives us four pieces of important information:

  1. The username of the current user in to the terminal. In the example this is "user".
  2. The hostname of the system. In the example the hostname is "host".
  3. The current working directory is user's home directory (~). You will see the tilde (~) used frequently in the terminal. It represents the /home/user/ directory. Remember, there's no place like ~.
  4. The $ at the end tells us we currently have non-root permissions. We're not going to make any system-wide changes, so this is perfect for us. It also indicates the shell is ready for more input.



### Put the Terminal to Work - Create a Workspace

Let's make a directory we can store our data in. We'll assume you have a standard desktop install with pre-made folders like Documents, Music, Pictures, Downloads, etc. We're going to put our work in the Documents folder. Inside the Documents folder, we're going to make a new folder called 'wordle'. We use the terms 'folder' and 'directory' to mean the same thing. Old school Linux users prefer 'directory' as that is how they are referred to on the command line. Keep an eye on your prompt to see how it changes when you change directories.

First, change directories (cd) to the Documents directory:

```

    user@host:~$ cd Documents

```

Now, make a new directory (mkdir) called 'wordle':

```

    user@host:~/Documents$ mkdir wordle

```

Change directories (cd) to 'wordle':

```

    user@host:~/Documents$ cd wordle

```

Your new working directory should be /Documents/wordle. Let's confirm that. Tell the terminal to print the name of the current working directory (pwd):

```

    user@host:/Documents/wordle$ pwd
    /home/user/Documents/wordle

```

Knowing which directory the terminal is in is important. The commands you issue will happen inside the current working directory unless you explicitly tell the command to use a different directory. Everything we're going to do should happen inside this directory.

Anytime you need help with a command, type the command followed by a space and --help to get a brief note on the basics of the command. Most linux commands have these flags you can use to modify the basic command. Some flags, like --help, are whole words and prefixed by two dashes. Other flags are just one letter preceded by a single dash. These flags are known as options. Try it with:

```

    user@host:~/Documents/wordle$ pwd --help

```

You can also try using the --help option with other commands:

```

     mkdir --help

```

Now that you have your workspace set, we won't show the whole prompt. We'll show only the commands issued, like the one above.

Practice with the --help option as much as you want with the commands we've already used - cd, mkdir, pwd. Warning: If you try

```

    echo --help

```

Well, see what happens. To get the help text for echo, use:

```

    help echo

```

If you move out of the directory or close the terminal, you can easily get back to our 'wordle' directory by issuing the command:

```

    cd ~/Documents/wordle

```

### Let's Go Surfing - Finding a Wordle Word List to Analyze

Your Linux system comes with its own dictionary. It is a list of words applications can use to do things like check spelling. Wordle uses a curated word list, so the system dictionary won't be much help. There are many such curated Wordle word lists on the Internet, but you don't need to go searching for one. We've found a good list for you. Just open this link in a new browser tab:
<https://raw.githubusercontent.com/Kinkelin/WordleCompetition/refs/heads/main/data/official/shuffled_real_wordles.txt>

Take a few moments to study the file in the browser. Note the following things:

  1. The first line in the file starts with a #, but the rest of the file is five-letter words (all in lowercase) with each word on its own line. That may seem like a waste of visual space, but this is exactly the type of file Linux loves. Word processor documents, spreadsheets, tables, and columns all make the job of reading the file harder for Linux. This simple text file is perfect for us.
  2. The first line says the file has 2,315 words. Pretty close to the number of curated words used by Wordle.
  3. The words are not in alphabetical order. That might nag at our human sense of order, but it won't affect the analysis Linux will do.
  4. What about letter pairs (th, ou)? How often do they come up? In English, letter pairs are called digraphs. If both lettters are vowels, the pair is called a dipthong (shoutout to English teachers everywhere).



Ok, this is a good list. Let's download it into our workspace.

### Back to the Terminal!

Click back into the terminal. Make sure you are in the correct workspace, the directory called wordle. Tell the terminal to download the file.

```

     wget https://raw.githubusercontent.com/Kinkelin/WordleCompetition/refs/heads/main/data/official/shuffled_real_wordles.txt

```

The command wget is a tool for downloading files from web servers. When the command tells you its done, confirm you have the file in the directory with a ls command. The ls command tells the terminal to list files and directories in a directory:

```

    ls
    shuffled_real_wordles.txt

```

We can also look at the contents of the file in the terminal. The cat (from the word catenate) command will do that, but it has a small hitch. See if you can spot it when we run the command:

```

    cat shuffled_real_wordles.txt

```

As you can see, the cat command just spits out the entire file contents. And since the file has 2,000+ lines, you can't see the whole thing. We should use the less command.

```

    less shuffled_real_wordles.txt

```

Aha! Now you see the top of the file, but not the end of the file. The less command shows you just one page of the file at a time. If you want to see the next page, just hit the _spacebar_ or the _PgDn/PgUp_ keys. The down/up arrow keys work, too, but only move one line at a time. You can do this as much as you like until you quit less. Move up and down a few pages and lines using the different navigation key options. To quit less, just tap the _Q_ key. By the way, less is known as a pager command, because it shows output in pages.

One more command we want to use to inspect this file is wc or word counter. wc does exactly what its name says -- it counts words in a file. Try it:

```

    wc shuffled_real_wordles.txt
    2316 2335 14000 shuffled_real_wordles.txt

```

wc displays line, word, and then byte counts. The three numbers match up with our expectations -- 2,315 lines plus a one-line description at the top, for a total of 2,316 lines and 2,335 words. If we want wc to show only lines, use wc -l or for words, wc -w. Try it:

wc -l shuffled_real_wordles.txt
2316 shuffled_real_wordles.txt

```

    wc -w shuffled_real_wordles.txt
    2335 shuffled_real_wordles.txt

```

Use wc --help to see how to count characters. We won't use it here, but it may be good to know.

See how that first sentence is keeping us from exactly matching the number of Wordle words? It's going to confuse Linux, too. We don't want that sentence in our analysis, so let's edit our file and get rid of it.

### Terminal, Edit Me a Story

A good practice to follow before we edit a file is to make a copy of it first. That will let us have an original copy. In the terminal, we'll do this with the cp (copy command). In this case, we're going to give the command two filenames -- the original name and the new name. Also, let's give our working copy a shorter name:

```

    cp shuffled_real_wordles.txt words.txt

```

When we get no messages back, we can assume the command worked.

Now we edit our working file with with nano. Nano is the current default editor in Fedora. There are other editors that can be run in the terminal -- vim, emacs, micro, just to name a few. If you want to use a different editor, that's OK. We'll stick with nano here.

```

     nano words.txt

```

Once you are in nano, there are two important commands to remember. _CTRL+O_ will write/save the file. Nano will ask you to confirm the name. Hit _enter_. The second command quits nano -- _CTRL+X_. If you make changes and try to quit without saving, nano will ask you if you want to save changes to the file (Save modified buffers?). You can press _Y_ , _N_ , or _CTRL+C_ (cancel and return to nano), depending on what you want to do.

Delete that first line. Don't leave any blank spaces between the first word and the top of the file. Save the file and exit nano.

Let's check the wc output now:

```

    wc -lw words.txt
    2315 2315 words.txt

```

Perfect. 2,315 lines and 2,315 words. See how we combined the _-l_ and _-w_ options? Many commands will let us do this. Keep this in mind as you gain experience with the terminal.

### Let the Analyzing Begin!

Analysis is an intimidating word that just means asking questions and finding answers about a thing by breaking that thing down into its component parts. Take another look at our word list and its component parts, letters. What questions could we ask about them? Here are the questions we're going to work on in our analysis.

  1. What is the total letter frequency in the possible word list?
  2. What are the most frequent letters at the start of a word?
  3. What are the most frequent letters at the end of a word?
  4. What about letter pairs (th, ou)? How often do they come up?
In English, letter pairs are called digraphs. If the letters are both vowels, the pair is called a dipthong (shoutout to English teachers everywhere).



You could easily come up with more questions. Make a note of them. After you get some experience, start hunting for answers on your own. For now, we'll focus on some simple text analysis questions.

### I'll Grep You, My Pretty

The grep command's function is simple and powerful. It finds text based on a pattern you give it, and outputs what it finds. It can find exactly what we're looking for, or it can find things that come close to what we're looking for. In fact, grep is going to be the cornerstone of our analysis work, so we should spend some time learning the basics.

You tell grep what you want to find in the file by giving it a pattern or regular expression (also called a regex) and a place to search. Let's say you want to see if the word 'eater' is in our words.txt file. A recommended practice is to put the pattern in quotes, so we'll do that here:

```

    grep "eater" words.txt
    eater

```

The response shows us grep found 'eater' in the file. Try this one:

```

    grep "eaton" words.txt

```

grep found nothing so nothing is returned. Remember, Wordle does not use proper nouns, so that makes sense (sorry, Eaton, Ohio).

What if we want to find all of the words with 'eat' in them? Simple enough:

```

    grep "eat" words.txt
    treat
    wheat
    cleat
    heath
    great
    bleat
    eater
    eaten
    cheat
    death
    sweat
    pleat
    meaty

```

Wow! Now we can begin to see the true power of grep.

When we are building our search pattern for grep, we can use special characters called wildcards and anchors. A wildcard is a placeholder for unspecified letters. We can use a dot (.) to represent any single character. The star/asterisk (*) character represents the previous character any number of times, including no character at all. Combine the dot and star (.*) to match any number of any character. Let's try wildcards out to see how they work with grep.

Words with a single character between 'e' and 'at':

```

    grep "e.at" words.txt
    begat
    elate

```

Words with any number of (including zero) characters between 'e' and 'at'

```

    grep "e.*at" words.txt
    treat
    wheat
    cleat
    heath
    great
    bleat
    eater
    eaten
    cheat
    death
    sweat
    begat
    elate
    pleat
    meaty
    eclat

```

The "e.*at" pattern matches all of the words the "eat" pattern PLUS begat, elate, and eclat.

Anchors tell grep where we want the search to be focused in a line. We can tell grep to search at the start (^) of the line or at the end of the line ($). This is exactly what we'll need when we check for the most frequent starting and ending letters in our words. Let's search for words with 'eat' at the start of the line in our words.txt file:

```

    grep "^eat" words.txt
    eater
    eaten

```

How about words with 'eat' and the end of the line?

```

    grep "eat$" words.txt
    treat
    wheat
    cleat
    great
    bleat
    cheat
    sweat
    pleat

```

The grep command has several available options, but we need to be aware of two of them. If you read grep --help, you'll see that grep has a count (-c) option that reports the number of lines matched by the pattern. If a word has two of the same letter, it will match that, but only count the line once.

```

    grep -c "a" words.txt
    909

```

The grep command found 909 words that contain the letter 'a.'

The second grep option we need is -o, which prints out every match of the pattern it finds. Given a single line with two matches, the grep -o command prints out both matches. Let's see how it works:

```

    grep -o "a" words.txt
    a
    a
    a
    .....

```

That time we asked grep to print out every occurence of a. It did that dutifully, printing out 'a' more times than we want to count. Let's give grep a little help with a _pipe_. We'll review pipes in greater detail next, but let's just add one to our last command.

```

    grep -o "a" words.txt | wc -l
    979

```

Here, we took our never ending lines of 'a' and sent them to wc to count. We came up with 979 occurrences. So, we can say that the letter 'a' is found in 909 words, but appears 979 times, thanks to repeated letters in words (e.g., alarm).

### Say Hello to My Little Friend(s) -- Pipes and Filter Commands

The pipe symbol (|) tells the terminal to start the pipe process. The pipe tells the first command to send its output to the next command. The second command then receives the input, processes it, and spits it out in its own format. The commands and pipes together are called a pipeline. The commands receiving the output are filter commands. Almost any command can be a filter command, but there are a few commonly used filter commands we want to focus on -- sort, uniq, head, column, and tee. Briefly, here's what each does:

  * sort orders input. When used with -n, it can sort numbers, and with -r it can do a reverse sort.
  * uniq identifies and acts on repeated matches. When used with the -c option, it returns the occurence and the number of times the occurence was found.
  * head just displays the first 10 lines of ouput. The command can be adjusted to show a specific number of lines. head has a brother called tail that works on the last lines.
  * column formats input into multiple columns. This command is a gem when dealing with a long list of simple outputs.
  * tee copies output sent to our display and sends it to another location, like a file. It does not supress the output to the terminal. This helps us capture the output in a more permanent way, while still displaying output in the terminal.



#### Let's build a pipeline as an example

Say we want the output of one of our grep command to appear in alphabetical order, and we just want to see the first 5 lines.

```

    grep "eat" words.txt | sort | head -5
    bleat
    cheat
    cleat
    death
    eaten

```

Remember how the command grep -o "a" words.txt just printed out 'a' repeatedly? We piped the number of lines to wc -l to count the lines. The uniq -c does something similar, with a slightly different output:

```

    grep -o "a" words.txt | uniq -c
    979 a

```

The uniq command has the advantage over wc -l of being able to group together and count matching output. That will let us get the output of a grep command using wildcards while keeping an accurate count of each letter.

Let's count all the letters. We can use the (.) wildcard instead of typing every single letter. We'll add head to the end of our pipeline to keep our terminal tidy:

```

    grep -o "." words.txt | uniq -c | head
    1 s
    1 c
    1 o
    1 w
    1 l
    1 w
    1 a
    1 g
    1 e
    1 r

```

What happened? grep sent the uniq command the data for each line. So, uniq told us the word 'scowl' has one 's', one 'c', etc. We want to know the total occurences for letters in all lines, not just the individual letters. We have to insert a sort to arrange the output of grep by letter before it gets sent to uniq. We'll use head to keep from filling the terminal with so much output:

```

    grep -o "." words.txt | sort | uniq -c | head
    979 a
    281 b
    477 c
    393 d
    1233 e
    230 f
    311 g
    389 h
    671 i
    27 j

```

We're getting warm. We see that the letters are listed alphabetically, rather than by order of frequency. Let's throw in another sort. This one will sort the output by frequency or count. Remember to use a reverse number sort, so the letters are listed by order of their frequency, highest to lowest. This time, we want to see data on all of the letters, so let's replace head with column:

```

    grep -o "." words.txt | sort | uniq -c | sort -nr | column
    1233 e   729 t   575 n  393 d   311 g   195 w   29 q
    979  a   719 l   477 c  389 h   281 b   153 v   27 j
    899  r   671 i   467 u  367 p   230 f   40 z
    754  o   669 s   425 y  316 m   210 k   37 x

```

That's it! We have listed letters in our Wordle words.txt file by order of frequency. Let's store this output in a file with the tee command.

```

    grep -o "." words.txt | sort | uniq -c | sort -nr | column | tee letter-freq.txt

```

We see in the display the same output as earlier. Check the letter-freq.txt file:

```

    cat letter-freq.txt

```

Bingo! Question #1 of our analysis is complete!

### Now we need to answer questions #2 and #3.

Recall they are:

  2. What are the most frequent letters at the start of a word?
  3. What are the most frequent letters at the end of a word?



Since we've already figured out how to get total letter frequency in the file, all we have to do is adjust our grep command to check the first and last letters of each word. As we mentioned before, we can tell grep to do this by using the caret (^) or dollar sign ($) characters in our search pattern. Let's try it first before committing the results to a file.

```

    grep -o "^." words.txt | sort | uniq -c | sort -nr | column
    366 s   142 p   111 d   83 w   41 o   23 q   3 z
    198 c   141 a   107 m   72 e   37 n   20 k
    173 b   136 f   105 r   69 h   34 i   20 j
    149 t   115 g    88 l   43 v   33 u   6 y

```

Too easy! Let's add the output to another file.

```

    grep -o "^." words.txt | sort | uniq -c | sort -nr | column | tee starting-letter-freq.txt

```

The terminal should display the same output as the previous command but the output is also stored in the file starting-letter-freq.txt.

Now, let's do the ending letters:

```

    grep -o ".$" words.txt | sort | uniq -c | sort -nr | column | tee ending-letter-freq.txt

```

We now have three files -- letter-freq.txt, starting-letter-freq.txt, and ending-letter-freq.txt -- that answer our first three questions.

### Looking For Letter Pairs

In the final part of our analysis, question #4, we want to see which letter pairs are used most frequently. This time, instead of counting each instance of a letter pair, including repeated appearances in a single word, we only want to count the number of words that contain a specific letter pair. Using grep -c, we can create letter pairs once, and then count the number of words that contain that pair. Given that all of our words have only five letters, it's reasonable to conclude that our word count will not be too different from a total letter pair count. The only downside with the word count is that we'll find several letter pairs are not used at all. We can live with that. Let's get to work.

We can make letter pairs right in the terminal, automatically. We'll use a bash function called "brace expansion" to do just that. If you're using a shell other than bash, you'll have to check the documentation to see how your shell does brace expansion.

Brace expansion in bash is designed to generate unique strings given a base string and two or more items in a list. Typically, you'd want to use this to name related files. Here's an example:

```

    echo {dinner,lunch,breakfast}-menu.txt
     dinner-menu.txt lunch-menu.txt breakfast-menu.txt

```

A nice feature of brace expansion is that bash understands sequential letter and number braces with a little shorthand trick:

```

    echo {a..z}
     a b c d e f g h i j k l m n o p q r s t u v w x y z

```

and

```

    echo {1..7}
     1 2 3 4 5 6 7

```

So, bash treats {a..z} as all of the letters of the English alpahabet in order, lowercase, and {1..7} as all numbers 1-7 in order.

How can we apply this to our letter pair problem? Let's try something simple first, like creating all the possible letter pairs that begin with 'a'. How about:

```

    echo a{a..z}
    aa ab ac ad ae af ag ah ai aj ak al am an ao ap aq ar as at au av aw ax ay az

```

We're on the right track, but we want all letter pairs.

```

    echo {a..z}{a..z}
    aa ab ac ad ae af ag ah ai aj ak al am an ao ap aq ar as at au av aw ax ay az ba bb bc bd be bf bg bh bi bj bk bl bm bn bo bp bq br bs bt bu bv bw bx by bz ca cb cc cd ce cf cg ch ci cj ck cl cm cn co cp cq cr cs ct cu cv cw cx cy cz da db dc dd de df dg dh di dj dk dl dm dn do dp dq dr ds dt du dv dw dx dy dz ea eb ec ed ee ef eg eh ei ej ek el em en eo ep eq er es et eu ev ew ex ey ez fa fb fc fd fe ff fg fh fi fj fk fl fm fn fo fp fq fr fs ft fu fv fw fx fy fz ga gb gc gd ge gf gg gh gi gj gk gl gm gn go gp gq gr gs gt gu gv gw gx gy gz ha hb hc hd he hf hg hh hi hj hk hl hm hn ho hp hq hr hs ht hu hv hw hx hy hz ia ib ic id ie if ig ih ii ij ik il im in io ip iq ir is it iu iv iw ix iy iz ja jb jc jd je jf jg jh ji jj jk jl jm jn jo jp jq jr js jt ju jv jw jx jy jz ka kb kc kd ke kf kg kh ki kj kk kl km kn ko kp kq kr ks kt ku kv kw kx ky kz la lb lc ld le lf lg lh li lj lk ll lm ln lo lp lq lr ls lt lu lv lw lx ly lz ma mb mc md me mf mg mh mi mj mk ml mm mn mo mp mq mr ms mt mu mv mw mx my mz na nb nc nd ne nf ng nh ni nj nk nl nm nn no np nq nr ns nt nu nv nw nx ny nz oa ob oc od oe of og oh oi oj ok ol om on oo op oq or os ot ou ov ow ox oy oz pa pb pc pd pe pf pg ph pi pj pk pl pm pn po pp pq pr ps pt pu pv pw px py pz qa qb qc qd qe qf qg qh qi qj qk ql qm qn qo qp qq qr qs qt qu qv qw qx qy qz ra rb rc rd re rf rg rh ri rj rk rl rm rn ro rp rq rr rs rt ru rv rw rx ry rz sa sb sc sd se sf sg sh si sj sk sl sm sn so sp sq sr ss st su sv sw sx sy sz ta tb tc td te tf tg th ti tj tk tl tm tn to tp tq tr ts tt tu tv tw tx ty tz ua ub uc ud ue uf ug uh ui uj uk ul um un uo up uq ur us ut uu uv uw ux uy uz va vb vc vd ve vf vg vh vi vj vk vl vm vn vo vp vq vr vs vt vu vv vw vx vy vz wa wb wc wd we wf wg wh wi wj wk wl wm wn wo wp wq wr ws wt wu wv ww wx wy wz xa xb xc xd xe xf xg xh xi xj xk xl xm xn xo xp xq xr xs xt xu xv xw xx xy xz ya yb yc yd ye yf yg yh yi yj yk yl ym yn yo yp yq yr ys yt yu yv yw yx yy yz za zb zc zd ze zf zg zh zi zj zk zl zm zn zo zp zq zr zs zt zu zv zw zx zy zz

```

And there is our letter pair list, all 676 of them.

So how are we going to run all of these through grep? The pipeline commands we used would work, but we would have to manually enter each letter pair as the pattern. We need something to send the output of the brace expansion to grep. And we have just such a solution called a "for loop". Let's take a look at a simple for loop in the terminal:

```

    for n in {1..5}; do echo $n; done
    1
    2
    3
    4
    5

```

What's happening here? We tell bash for each number (n) in the list created by the brace expansion of {1..5}, do the echo command on that number, then finish.

You see that each step in the loop construct is separated by a semicolon. We gave the individual items in the brace expansion a name (n). The n is called a variable, and when we use it again, we refer to it as $n so bash knows it is a variable name.

This is a lot of work going on in one line, so bash allows us to use new lines instead of the semicolons, as shown below. When you hit enter after the first line, bash knows you haven't given it a full command yet, so it goes to the next line, and adds a '>' to the front of the display. When you've given bash a complete command, after you type 'done,' bash goes to work.

```

    for n in {1..5}
     >do echo $n
    >done
    1
    2
    3
    4
    5

```

Multiple commands can occur in the loop. We just add them to the list of commands after the 'do', like this:

```

    for n in {1..5}
     do echo "The number is..."
     echo $n
     done
     The number is...
    1
     The number is...
    2
     The number is...
    3
     The number is...
    4
     The number is...
    5

```

As easy as this is to do, it's still a bunch of typing. Any mistakes we make will mean we have to go back and re-type the whole command. We should put it into a file that we can execute without typing the whole thing out.

#### Welcome to shell scripting!

We could write the script just like we've done in the terminal, but that won't be very readable for humans. Let's use a couple readability tricks for our script. When scripting a for loop, many experienced scripters use this format:
for n in {1..5}; do
echo "The number is..."
echo $n
done

We put the "for" and "do" statements on the same line, separated by a semicolon. This lets the reader see a loop is coming, and keeps the list of commands in the format we would use directly on the command line, one command per line. We also indented each command, so they are nestled between the 'for/do' and 'done' statements.

Now we're ready to create a shell script to count letter pair frequency. Let's create a filename called 'lpcount.sh' The '.sh' at the end is called a filename extension. It will tell the terminal this is a script file.

```

    nano lpcount.sh

```

Add this text to the file:

```

    #!/bin/bash
    for n in {a..z}{a..z}; do
      pcount=$(grep -c $n words.txt)
      echo $pcount $n
    done

```

Save and close the file with CTRL+O, ENTER, CTRL+X. Next, we have to make the file executable. We do this with the chmod (change file mode bits):

```

    chmod +x ctofive.sh

```

We have our first script! Don't dismiss the script because of its small size. you'll find other situations where short scripts like these can save you tons of time. Experienced users usually have a collection of these home-made scriptlets or snippets to make their work easier. Let's finish up our analysis by using our new script in a pipeline.

First, we just want to test the script to make sure it works. We'll use the head command in a pipeline so we only get the first 10 lines, rather than all 676.

```

    ./lpcount.sh | head
     0 aa
     29 ab
     52 ac
     49 ad
     1 ae
     18 af
     26 ag
     2 ah
     47 ai
     2 aj

```

Perfect! Let's run the command again. This time, we'll do a reverse number sort, format the output into columns and send the output of all 676 letter pair word counts to a file.

Question 4 has been answered! Later, you may want to look for starting or ending letter pairs. We've already done starting and ending single letters, so finding starting and ending letter pairs won't be too difficult.

### Summary and Next Steps

We took our first steps into the linux terminal and bash by doing some analysis on a Wordle word list. You can easily apply these skills to other tasks, like log and config file reviews. The techniques used here are useful, but in some cases, not optimal. As you learn bash, you'll find better ways to do the simple things we've done here. You also wrote a small program that does something useful. If I've whetted your appetite to do more text analysis, I recommend you learn a dedicated language like Python or Perl. As powerful as bash scripting is, those two programming languages will outstrip bash in capability and speed very quickly when it comes to text analysis.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/hacking-wordle-a-new-users-guide-to-the-power-of-the-linux-terminal/

作者：[Thomas Cummings][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/tncummings/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/11/hacking_worlde_2-816x346.jpg
[2]: https://unsplash.com/@nhuenerfuerst?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/a-white-cell-phone-E-IQ1nbpzZo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://www.nytimes.com/games/wordle/index.html
[5]: https://help.nytimes.com/24611727334932-Wordle
