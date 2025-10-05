[#]: subject: "mailbox spring cleaning with notmuch"
[#]: via: "https://jao.io/blog/mailbox-spring-cleaning-with-notmuch.html"
[#]: author: "jao https://jao.io"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

mailbox spring cleaning with notmuch
======

After many years of switching between email systems, service providers, backup and sychronisation strategies, mail folders layouts, protocols and inadvertent replications, i ended up with a sizeable amount of local email folders containing, i was quite sure, lots of duplicates. My current email handling systems of choice, Gnus with nnml and notmuch, are pretty good at hiding them from me in normal operation, but i know those dups are there, lurking in the dark, and periodically look for a way to uncover and kill them.

I know about the sophisticated [mail-deduplicate][1] utility, but I guess it's too sophisticated for me :) Turns out the solution was in front of my eyes: notmuch knows about duplicates, and can list them easily:

```

    notmuch search --duplicate=2 --output=files '*'`

```

That command will list the full path to the second file in duplicate pairs found by notmuch. So, getting rid of them is as easy as

```

    for f in  `notmuch search --duplicate=2 --output=files '*'``; do
      rm $f;
    done
    notmuch new

```

After doing that (note we rebuild notmuch's database at the end, searching again for level-2 duplicates might discover new files if you have emails duplicated more than twice (i had). Rinse and repeat.

[Tags][2]: [sundry][3]

--------------------------------------------------------------------------------

via: https://jao.io/blog/mailbox-spring-cleaning-with-notmuch.html

作者：[jao][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jao.io
[b]: https://github.com/lujun9972
[1]: https://github.com/kdeldycke/mail-deduplicate
[2]: https://jao.io/blog/tags.html
[3]: https://jao.io/blog/tag-sundry.html
