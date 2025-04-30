[#]: subject: "Journals and Contents: Two Special Pages in Logseq"
[#]: via: "https://itsfoss.com/logseq-journals-contents/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Journals and Contents: Two Special Pages in Logseq
======

[![Warp Terminal][1]][2]

Logseq is different from the conventional note-taking applications in many aspects.

Firstly, it follows a note block approach, rather than a page-first approach for content organization. This allows Logseq to achieve data interlinking at the sentence level. That is, you can refer to any sentence of a note in any other note inside your database.

Another equally important feature is the “Special Pages”. These are the “Journals” and “Contents” pages. Both of these special pages have use-cases far higher than what their names indicate.

### The Journals page

The “Journals” is the first page you will see when you open Logseq. Here, you can see dates as headings. The [Logseq documentation][3] suggests that a new user, before understanding Logseq better, should use this Journals page heavily for taking notes.

![Journals Page][4]

As the name suggests, this is the daily journals page. Whatever you write under a date will be saved as a separate Markdown file with the date as the title. You can see these pages in your file manager, too. Head to the location you use for Logseq, then visit the `journals` page.

![Journals Markdown Files in File Manager][5]

Let's see how to make this Journals page most useful.

#### Journal page as a daily diary

Let's start with the basics. The “Journals” page can be used as your daily diary page.

If you are a frequent diary writer, Logseq is the best tool to digitize your life experiences and daily thoughts.

Each day, a new page will be created for you.

If you need a page for a day in the past, Just click on the **Create** button on the bottom of Logseq window and select “New page”.

![Click on Create → New Page][6]

In the dialog, enter the date for the required journal in the format, `Mar 20th, 2023`. Press enter. This will create the Journal page for the specified that for you!

![Create Journal page for an old date][7]

#### Journal as a note organizer

If you have read the [Logseq Pages and Links article in this series][8], you should recall the fact that Logseq considers the concept of Pages, Tags, etc. in almost similar manner. If you want to create a new note, the best way is to use the keyboard method:

```

    #[[Note Title Goes Here]]

```

The above creates a page for you. Now, the best place to create a new page is the Journals page.

Logseq has a powerful backlink feature. With this, if you use the Journals page to create a new page, you don't need to add any date references inside the page separately, since at the very end of the page, you will have a backlink to that day's journal.

![Note with date reference][9]

This is beneficial because you can recall when a note was first created easily.

#### Journal as a to-do organizer

Logseq can be used as a powerful task manager application as well, and the Journals page plays a crucial role in it.

If you come across any task while you are in the middle of something, just open the Journals page in Logseq and press the `/` key.

Search and enter `TODO`. Then type the task you are about to do.

Once done, press `/` again and search for `Date Picker`. Select a date from the calendar.

0:00

/0:29

1×

Creating a TODO task in Logseq

That's it. You have created a to-do item with a due date. Now, when the date arrives, you will get a link on that day's Journal page. Thus, when you open Logseq on that day, you will see this item.

It will also contain the link to the journal page from where you added the task.

Other than that, you can search for the `TODO` page and open it to see all your task list, marked with TODO.

0:00

/0:23

1×

Search for the TODO page to list all the to-do tasks

#### Journal to manage tasks

Task management is not just adding due date to your tasks. You should be able to track a project and know at what stage a particular task is. For this, Logseq has some built-in tags/pages. For example, `LATER`, `DOING`, `DONE`, etc.

These tags can be accessed by pressing the `/` key and searching for the name.

For example, if you have some ideas that should be done at a later date, but not sure when exactly, add these with the `LATER` tag, just like the TODO tag explained above.

Now, you can search for the `LATER` tag to know what all tasks are added to that list.

0:00

/0:22

1×

Using the LATER tag in Logseq

Using the Journal page is beneficial here because you will be able to recollect on what date a particular task was added, allowing you to get more insight about that task. This will help you more, if you have entered your thoughts of that day in the Journal.

### The Contents Page

Logseq has a special **Contents** page type, but don't confuse it with the usual table of contents. That is not its purpose. Here, I will mention the way I use the contents page. You can create your own workflows once you know its potential.

You can think of the Contents page as a manually created Dashboard to your notes and database. Or, a simple home page from where you can access contents needed frequently.

The most interesting thing that sets the contents page apart from others is the fact that it will always be visible in the right sidebar. Therefore, if you enable the sidebar permanently, you can see the quick links in the contents all the time.

#### Edit the Contents page

As said above, the Contents page is available on the right sidebar. So click on the sidebar button in the top panel and select **Contents**. You can edit this page from this sidebar view, which is the most convenient way.

![Click on the Sidebar button and select Contents][10]

All the text formatting, linking, etc., that work on Logseq pages works on this page as well.

#### 1\. Add all important pages/tags

The first thing you can do is to add frequently accessed pages or tags.

For example, let's say you will be accessing the **Kernel** , **Ubuntu** , and **APT** tags frequently. So, what you can do is to add a Markdown heading:

```

    ## List of Tags

```

Now, link the tags right in there, one per line:

```

    #Kernel
    #Ubuntu
    #APT

```

For better arrangement, you can use the Markdown horizontal rule after each section.

```

    ---

```

#### 2\. Link the task management pages

As discussed in the Journals section, you can have a variety of task related tags like TODO, LATER, WAITING, etc. So you can link each of these in the contents page:

```

    ## List of Tasks

    #TODO
    #LATER
    #WAITING
    ---

```

🚧

Please note the difference between the Markdown heading and the Logseq tags. So, don't forget to add a space after the `#` if you are creating a Markdown header.

#### 3\. Quick access links

If you are visiting some websites daily, you can bookmark these websites on the contents page for quickly accessing them.

```

    ## Quick access links

    [It's FOSS](https://itsfoss.com/)
    [It's FOSS Community](https://itsfoss.community/)
    [Arch Linux News](https://archlinux.org/)
    [GitHub](https://github.com/)
    [Reddit](https://www.reddit.com/)

```

After all this, your contents page will look like this:

![Contents page in Logseq][11]

### Wrapping Up

As you can see, you can utilize these pages in non-conventional ways to get a more extensive experience from Logseq. That's the beauty of this open-source tool. The more you explore, the more you discover, the more you enjoy.

In the next part of this series, I'll share my favorite Logseq extensions.

--------------------------------------------------------------------------------

via: https://itsfoss.com/logseq-journals-contents/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://hub.logseq.com/getting-started/uQdEHALJo7RWnDLLLP7uux/how-to-get-started-in-logseq/pE1BPPvKGbWkSRXsprRnxM
[4]: https://itsfoss.com/content/images/2025/02/journals-page-in-logseq.png
[5]: https://itsfoss.com/content/images/2025/02/journal-pages-in-folder.png
[6]: https://itsfoss.com/content/images/2025/02/click-on-create-and-select-new-page.png
[7]: https://itsfoss.com/content/images/2025/02/create-a-journal-page-for-an-old-date.png
[8]: https://itsfoss.com/logseq-pages-links-tags-blocks/
[9]: https://itsfoss.com/content/images/2025/02/note-showing-the-date-as-journal-reference-link.png
[10]: https://itsfoss.com/content/images/2025/02/click-on-sidebar-and-select-contents-1.png
[11]: https://itsfoss.com/content/images/2025/02/Contents-page-in-logseq-1.png
