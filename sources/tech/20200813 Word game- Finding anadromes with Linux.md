[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Word game: Finding anadromes with Linux)
[#]: via: (https://www.networkworld.com/article/3570776/word-game-finding-anadromes-with-linux.html)
[#]: author: (Sandra Henry-Stocker https://www.networkworld.com/author/Sandra-Henry_Stocker/)

Word game: Finding anadromes with Linux
======
Using Linux commands to find words that, when reversed, turn into other words turned out to be an enjoyable mental challenge. How many can you find?
Undrey / Getty

In these stressful times, one way to distract ourselves from the gloom is by playing word games. With this thought in mind, I challenged myself to identify words that, spelled backwards, would still be words.

Instead of cheating by doing a simple Google search, I cheated by using my Linux commands skills. So, in this post, we’ll look at how Linux commands and resources can be used to identify such words.

### Defining the search

Before we get started on the Linux search technique, I should point out that what I was looking for were not just palindromes – words like “civic” and “deified” that read the same from left to right as they do right to left. Instead, I was also looking for words like “reward” and “decaf” that turn into different words – in this case, “drawer” and “faced” -- when one reads them backwards.

For the record, one of the many terms that people have used to define words that are reversible in this way is “anadromes” and the longest known anadromes in English are “stressed” and “desserts” (confirmed by my little project). I'm also including palindromic words.

### Using the words file

For my word resource, I used the Linux **words** file. It might be **/usr/dict/words** or **/usr/share/dict/words** on your system. The words file on the system I’m using for this post has over 100,000 words. You can use the **wc** command to do the counting.

```
$ wc -l /usr/share/dict/words
102403 /usr/share/dict/words
```

One of the peculiarities of the words file is that it contains single-letter separator lines between each group of words starting with the same letter (for words with initial caps and initial lowercase letters). Here, as examples, are the start of both the **B** and **b** sections:

```
B            b
B's             baa
BBB             baa’s
BBB's           baaed
BMW             baaing
BMW's           baas
```

The words file also includes a lot of proper names, acronyms and abbreviations. Proper names (like “Ada”) won’t work as anadromes because names don’t generally qualify as “words” and because reversals would capitalize the final latter (like “adA”). The words file also contains words with **'s** at the end (possessives and contractions like “isle's” and “isn't”). Since I don’t count any of these entries as words, I crafted my technique to avoid considering them.

In addition, the only legitimate single-letter words are “a” and “I”. Since these _should_ count toward the total, I added these to my word reversal list in some initials steps to make the remainder of the processing easier by discounting the single letter section headings while looping through the words file.

While omitting single-letter entries, words in all caps and possessives, the script that I put together to find the reversible words runs through all of the remaining words, reverses each of them and then looks back at the words file to see if the reversed word is also in the file.

### Starting the script

At the beginning of the script, I set the starting count to 2 and display the words “a” and “I”:

```
#!/bin/bash

# start with 2 for "a" and "I" (single letters avoided below)
count=2
echo a
echo I
```

### Looping through the words file

I then run through the words file. The easiest way to select only the words that might qualify (no caps, no apostrophes and so on), was to use the grep expression **grep -E '^[a-z]{2,23}*$'**. This selects all lowercase words with from 2 to 23 letters. I had separately determined that the longest word in the words file (electroencephalograph's) has 23 letters.

```
for word in `cat /usr/share/dict/words | grep -E '^[a-z]{2,23}*$'`
```

### Reversing each word

I use the **rev** command to reverse each word the for loop produced. If I were doing this manually, a reversal might look like this:

```
$ echo caviar | rev
raivac
```

Here’s the reversal in the script:

```
revword=`echo $word | rev`
```

I then look for the word in its reversed form to see if it also exists in the words file. This grep command displays the word if it’s found. If grep doesn’t find the word, no output is generated. The ^ and second $ sign ensure that it’s only finding complete words.

```
grep ^$revword$ /usr/share/dict/words
```

### Counting the finds

If the **grep** command succeeds (i.e., if it finds the reversal of the word), we know the reversal is a word too and add it to our count. Note that **$?** represents the exit status generated by the **grep** command and **0** indicates that no errors were encountered (i.e., the word was found).

```
if [ $? -eq 0 ]; then
   ((count=count+1))
fi
```

I then end the loop through the words file and display the count of anadromes. Words that are palindromic (like “civic”), will have been counted once. Words that are not palindromic will have been counted twice (once for each of the words). As a result, the final count might be an odd or an even number.

```
echo $count reversible words found
```

### Calculating the percentage

To satisfy my curiosity, I also added some commands at the end of the script to calculate the percentage of entries in the words file that qualify as anadromes.

```
# determine the percentage
words=`wc -l /usr/share/dict/words`
percent=`echo $count $words | awk '{print $1/$2*100}'`
echo -n "Percentage: "
echo $percent%
```

The percentage in my case turned out to be **.399%**. That’s a little less than half a percent – less than one word in every 200. Still, I was surprised that there were so many.

### The script

The script in its entirety is shown below and includes a few comments to add to its readability. In this version of the script, I put all of the located anadromes into a file.

```
#!/bin/bash

output="anadromes"

# start with 1 for "a" (single letter entries avoided below)
count=2
echo a > $output
echo I >> $output

# find words that, when reversed, are still words
for word in `cat /usr/share/dict/words | grep -E '^[a-z]{2,23}*$'`
do
   revword=`echo $word | rev`
   grep ^$revword$ /usr/share/dict/words >> $output
   if [ $? -eq 0 ]; then
      ((count=count+1))
   fi
done

# display a word count
echo $count reversible words found

# determine percentage
words=`wc -l /usr/share/dict/words`
percent=`echo $count $words | awk '{print $1/$2*100}'`
echo -n "Percentage: "
echo $percent%
```

### What did I see?

If you run the script as shown above, you can use the **column** command to get a nicely formatted listing of the anadromes that it has identified. Here’s the start of what I found:

```
$ column anadromes
a               ogre            dim             redder          wets
I               ate             slim            warder          knits
tuba            eve             denim           deer            loots
raga            live            minim           leer            pots
ha              relive          mom             fer             spots
aha             ewe             doom            refer           parts
raja            eye             room            lager           warts
ma              decaf           um              denier          desserts
era             ref             gum             eviler          ports
sera            golf            mum             timer           sports
…
```

The script found 409 anadromes in the words file.

### Wrap-Up

A simple challenge turned out to be a script that exercised some of my Linux skills. These included:

  * Looping through the words file
  * Crafting a **grep** command that would capture only what I wanted
  * Reversing each of the words (last letters first)
  * Counting the anadromes found
  * Calculating the percentage of words that match my criteria



I’m not yet sure what tomorrow’s challenge will be, but solving problems with Linux tools is a very satisfying mental exercise!

### Now see

Join the Network World communities on [Facebook][1] and [LinkedIn][2] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3570776/word-game-finding-anadromes-with-linux.html

作者：[Sandra Henry-Stocker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Sandra-Henry_Stocker/
[b]: https://github.com/lujun9972
[1]: https://www.facebook.com/NetworkWorld/
[2]: https://www.linkedin.com/company/network-world
