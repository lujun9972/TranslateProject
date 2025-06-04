[#]: subject: "My Favorite Obsidian Plugins and Their Hidden Settings"
[#]: via: "https://itsfoss.com/obsidian-plugins/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

My Favorite Obsidian Plugins and Their Hidden Settings
======

[![Warp Terminal][1]][2]

In an earlier article, I wrote about [using plugins in Obsidian][3]. In this one, let me share a few of my favorite plugins. I recommend them but only use the ones that fit your needs.

Just to recall, [Obsidian][4] has two kinds of plugins:

  * **Core plugins** : Officially developed and maintained by the Obsidian team.
  * **Community Plugins** : Created by users in the Obsidian community



🚧

Note that some plugins may make your Markdown notes fully readable only in Obsidian as they add extra features that are not available in usual Markdown. This can be a vendor lock in. Use plugins only according to your needs.

### Essential Core Plugins

At the time of writing this article, I see 28 core plugins in my Obsidian installation.

I have picked only a handful of them. It doesn't mean others are not good. All core plugins have some use case for a particular set of users!

Several of the plugins I discuss here are enabled by default. But these plugins have settings of their own and I share these settings that have enhanced my note management experience in Obsidian.

✋

****Non-FOSS Warning!**** Obsidian is not an open source software but it is loved and used by many open source developers and Linux users.

#### Backlinks

The backlinks are among Obsidian's greatest features. It is crucial for managing interconnected notes and data.

I know that the backlink plugin is enabled by default but there is a useful feature that you'll have to manually enable. It is “Show backlinks at the bottom of notes” option.

Enable it by going to **Backlinks** plugin settings.

![Enable backlinks][5]

Now, under each note, backlinks will be shown.

0:00

/0:18

1×

Backlinks in Obsidian

It is particularly useful if you are creating new notes from a single place like Daily Notes, which is our next plugin!

#### Daily Notes

Daily Notes is like diary pages. It will create a Markdown page for each day and you can write your thoughts here.

By default, you can access the daily notes from the Obsidian ribbon menu. But a more efficient way is to open daily notes whenever you open Obsidian.

Go to the **Daily Notes** settings. Here, enable the "Open daily note on startup" toggle button.

![Daily Notes Settings][6]

In the screenshot above, you can see some other settings have been changed.

  * Date Format: How the title of the daily note appear. You can get the date format options [here][7].
  * New file location: I have created a separate folder called **Journals** in my Obsidian vault to store all the daily notes.



#### Page Preview

This is enabled by default for you. With this plugin, you can hover over a note while pressing the CTRL key to get a preview.

You can also quickly edit the note in the preview or go to another sub-preview, etc. Very useful tool if you are deep into note interlinking.

0:00

/0:23

1×

Preview page in Obsidian

#### Slash Commands

This plugin is disabled by default. Go to the **Core Plugins** in Obsidian settings and enable this plugin.

Once enabled, you can press the `/` key when typing a note to access commands. For example, insert attachment, insert code block, etc. A simple preview is shown in the below video.

0:00

/0:24

1×

Slash command in Obsidian

Notion, Ghost and many modern editors use this feature.|

#### Web Viewer

This is a cool plugin that allows you to visit web links from within Obsidian. More than that, you can save a website to vault using this core plugin.

It is not enabled by default, so do that first. Once enabled, click on the settings gear adjacent to the plugin to go to the plugin settings.

![Web viewer settings button][8]

Here, you can set further options like where to save the page by default, search engine, etc.

![Web Viewer Settings][9]

You can see some examples in the video below.

Web viewer in Obsidian

### Interesting community plugins I like

Now, let's take a look at some cool community plugins that can enhance your knowledge base, as they do for me.

#### Calendar

If you are a daily notes writer, this is a must-have plugin. Even if you are not into diary writing, it is still pretty cool to have a calendar placed on Obsidian.

![Calendar View][10]

You can visit notes of any date simply by clicking on that date. If there is no note, it will prompt you to create one!

There are many more features that you can explore, like a meter to track how much you have written on a particular day.

💡

If you press CTRL key and hover over a date, those day's notes will be shown in a preview.

[Calendar Plugin][11]

#### QuickAdd

QuickAdd is a much needed automation tool in Obsidian. It offers features like templates, captures, macros, multis, etc. which essentially allow users to create notes quickly.

For example, the template feature can create a note based on a given template in a specified directory. All you have to do is invoke the command.

The screenshot below shows three templates created by me for my use cases.

![Created Templates][12]

Use the settings gear to change additional settings like where to create a note, open the note automatically, etc.

The video below shows how it quickly creates a note on a specified location.

0:00

/0:13

1×

QuickAdd Working

With macros, you can even assign key bindings to make your workflow even faster!

[QuickAdd][13]

#### Iconize

Emojis and icons are all the rage these days. From GitHub to changelogs, you'll see them everywhere. How about adding them to Obsidian?

Obsidian organizes notes into folders and subfolders. With the Iconize plugin, you can set icons to folders.

![Icons applied to folders][14]

You can add new icon packs by going to the **Settings → Community plugins → Installed plugins -→Iconize -→Settings gear → Icon packs**.

![Icon packs added in Iconize][15]

Right-click on a folder or file and use the **Change icon** option to add a new icon to that folder/file.

[Iconize][16]

#### Highlightr

Remember highlighting important stuff in a book? You can do the same in your notes on Obsidian.

Highlight text in Vimeo

It also provides different styles of highlighting, all selectable from the plugin settings.

[Highlightr][17]

#### Callout Manager and Callout Suggestions

These are two different plugins which, when used together, are a great way to add callouts.

📋

If you are not aware, callout blocks can improve your notes by making specific visually separated blocks for tips, warnings, etc. Like this 'note' callout block I used for telling you about callouts.

By default, obsidian has some callouts like Note, Tips, Warnings, etc.

[Callout Manager][18] allows you to create more callout blocks. Say you want to create a new callout block called "Read Later" and assign a particular color and icon. You can do that with this plugin.

![Callout blocks from Callout Manager][19]

The [Callout Suggestions][20] plugins will help you access these defined callout blocks easily in your notes.

You can press `>!` and a dropdown menu will appear asking what block to use.

0:00

/0:23

1×

Inserting Callouts in Obsidian

#### PDF++

Annotating a PDF document is a must-have feature in any PDF viewer. How about doing it in Obsidian? PDF++ is a great tool for this purpose.

You can add your PDF notes to your vault and start annotating!

Once the plugin is installed and enabled, make sure you have enabled the PDF editing feature.

![PDF++ plugin settings][21]

Now, you can select text and then right-click to get the annotation menu. **Unlike other plugins, this has a slight learning curve and plenty of options to tweak. Use it carefully.**

![Annotate PDF in Obsidian][22]

[PDF++][23]

#### LanguageTool Integration

This is for those who want to create notes without grammatical errors or spelling mistakes.

[LanguageTool][24] is a proofreading software that checks the grammar, style, and spelling in over 20 languages. With this plugin, you can get error notifications for your text in Obsidian.

If you have a premium subscription for LanguageTool, you can use it here as well.

![Spell check in Obsidian][25]

🚧

You should disable the Obsidian spell check (Settings → Editor → Behavior → Spell Check) feature if you want to use this plugin.

[LanguageTool Integration][26]

#### Tasks

You can use Obsidian as a task/to-do manager. That's no secret.

However, Tasks is plugin that can do a lot more than just simple to-dos. It supports scheduling tasks, recurring tasks etc.

You can also list all the tasks, today's tasks, etc. by using simple tasks specific queries.

To create a task, you can enter CTRL+P (open command in Obsidian) and search for **Tasks**.

![Using the Tasks plugin to create tasks][27]

You can retrieve tasks as shown in the small video below:

0:00

/0:28

1×

Retrieve tasks in Obsidian

[Tasks][28]

#### Excalidraw

Excalidraw is a plugin to edit and view [Excalidraw][29] drawings in Obsidian. This sketching solution can make wonderful diagrams within Obsidian, embed drawings into your documents and much more.

![An Excalidraw drawing in Obsidian][30]

You can find a huge list of settings for this plugin in the Obsidian settings. If you are into creative note-taking, look no further.

[Excalidraw][31]

#### Honorable mentions

  * [Style Settings][32]: Allows you to tweak several themes in Obsidian. One such theme that I am using and is heavily customizable is [**Border**][33].
  * [Git][34]: Allows you to version control your notes. You can pull changes from and push changes to GitHub, GitLab, etc.
  * [Dataview][35]: Dataview is a live index and query engine over your personal knowledge base. You can query data from your Obsidian vault.
  * [QuickAdd][13]: QuickAdd is like a super-smart shortcut button in Obsidian that lets you quickly create new notes or add stuff to existing ones using pre-made templates and automated steps you set up.
  * [Kanban][36]: This plugins created a Markdown-based Kanban board.



There are many other plugins, enabled/disabled in a default Obsidian installation. What I mentioned above are a couple of special ones. Don't forget to read the descriptions and try others too.

Now I let you share your favorite Obsidian plugin in the comments.

--------------------------------------------------------------------------------

via: https://itsfoss.com/obsidian-plugins/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/obsidian-use-plugin/
[4]: https://itsfoss.com/obsidian-markdown-editor/
[5]: https://itsfoss.com/content/images/2025/05/enable-backlinks-in-backlink-plugin.png
[6]: https://itsfoss.com/content/images/2025/05/daily-notes-core-plugin-settings-1.png
[7]: https://momentjs.com/docs/#/displaying/format/
[8]: https://itsfoss.com/content/images/2025/05/web-viewer-options-gear.png
[9]: https://itsfoss.com/content/images/2025/05/web-viewer-plugin-settings.png
[10]: https://itsfoss.com/content/images/2025/05/calendar-view-in-obsidian.png
[11]: https://github.com/liamcain/obsidian-calendar-plugin
[12]: https://itsfoss.com/content/images/2025/06/created-templates.png
[13]: https://github.com/chhoumann/quickadd
[14]: https://itsfoss.com/content/images/2025/05/icons-in-obsidian.png
[15]: https://itsfoss.com/content/images/2025/05/icon-packs-added-in-iconize-obsidian.png
[16]: https://github.com/FlorianWoelki/obsidian-iconize
[17]: https://github.com/chetachiezikeuzor/Highlightr-Plugin
[18]: https://github.com/eth-p/obsidian-callout-manager
[19]: https://itsfoss.com/content/images/2025/05/callout-manager-callout-blocks-1.png
[20]: https://github.com/cwfryer/obsidian-callout-suggestions
[21]: https://itsfoss.com/content/images/2025/05/enable-pdf-editing.png
[22]: https://itsfoss.com/content/images/2025/05/annotate-pdf.png
[23]: https://github.com/RyotaUshio/obsidian-pdf-plus
[24]: https://itsfoss.com/languagetool-review/
[25]: https://itsfoss.com/content/images/2025/05/checking-spelling-and-grammer-in-obsidian-1.png
[26]: https://github.com/Clemens-E/obsidian-languagetool-plugin
[27]: https://itsfoss.com/content/images/2025/05/creating-a-task.png
[28]: https://github.com/obsidian-tasks-group/obsidian-tasks
[29]: https://excalidraw.com/
[30]: https://itsfoss.com/content/images/2025/05/excalidraw-obsidian.png
[31]: https://github.com/zsviczian/obsidian-excalidraw-plugin
[32]: https://github.com/mgmeyers/obsidian-style-settings
[33]: https://github.com/Akifyss/obsidian-border
[34]: https://github.com/Vinzent03/obsidian-git
[35]: https://github.com/blacksmithgu/obsidian-dataview
[36]: https://github.com/mgmeyers/obsidian-kanban
