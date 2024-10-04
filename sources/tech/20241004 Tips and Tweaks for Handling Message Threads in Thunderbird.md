[#]: subject: "Tips and Tweaks for Handling Message Threads in Thunderbird"
[#]: via: "https://itsfoss.com/thunderbird-threading/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Tips and Tweaks for Handling Message Threads in Thunderbird
======

[![Warp Terminal][1]][2]

Starting with version 102, Thunderbird offers _Message Threading_ as a feature to solve this issue.

In Message Threading, the individual conversations will be arranged in a tree-like structure. So, for a particular sender, you can view the messages and replies under one big conversation thread.

Here is a list of uses of the Message Threading view.

  * Organize the conversation.
  * Easy to access all messages of a conversation.
  * Easy to delete a whole conversation in one go.
  * Never miss a message in a particular conversation.
  * Ignore a thread, which will hide it and disable notification for new replies.
  * Ignore a sub-thread, thereby ignoring replied from selected message onwards.



In this tutorial, I'll share some tips and tweaks on message threads in Thunderbird.

### Enable and disable message threading for a folder

As said earlier, from version 102 onwards, [Thunderbird][3] enables message threading by default. If that is not the case for you, let's see how to enable it.

Click on the _Message list display option_ button on the top bar of Thunderbird.

![Message List Display Option \(Click to expand\)][4]

Go to **Sort By → Threaded**.

![Enable Threaded View \(Click to expand\)][5]

The effect would be like this:

![Threaded View for a Conversation \(Click to expand\)][6]

As you can see in the screenshot above, I have enabled threaded view in the **Inbox** folder. Now, what if you want to manage the thread view in a separate folder?

Let's say you have a filter to move all messages from a particular sender to a dedicated folder called **Personal Messages**. Select that folder from the sidebar and repeat the previous step.

That is, **Message List button → Sort By -→Threaded**.

![Enable threading on a new folder \(Click to expand\)][7]

This will enable the threaded view for that folder.

![Threaded View Enabled on a Folder \(Click to expand\)][8]

#### Disable threading

To disable the threading view for the current folder, select the folder of your choice and then do **Message list options button → Sort By → Unthreaded**.

![Disable Thread view for a folder \(Click to expand\)][9]

### Enable and disable message threading for multiple folders

As you can see above, you can change the per-folder threading view in Thunderbird. Now, at times, it will be beneficial to apply the threading view settings to multiple folders on the go.

This is possible in Thunderbird.

#### Enable table view in Thunderbird

For this, first, you need to be on the Table view. Click on the _Message list display options_ button and select the Table View.

![Enable Table View \(Click to expand\)][10]

Now, you will get the Table view with some default columns.

![Table view in Thunderbird \(Click to expand\)][11]

#### Enable and disable message threading in the folder

You first need to apply the threading settings to the current folder. To toggle on or off threading, you can use the regular _Message list button → Sort By → Threaded_.

But in this view, there is a catch. You can toggle the message view easily by clicking on the **Toggle message thread** button on the far-left column.

![Toggle Threaded View \(Click to expand\)][12]

#### Apply threading to folders

In the table view, click on the _Select columns to display_ button (far-right of the column header). Select _Apply current view to_ option and hover over _Folders_.

![Apply Current View to Option \(Click to expand\)][13]

On the Folders option, select your mail account and then select the folder to which you want to apply the view.

![Select Folder of choice \(Click to expand\)][14]

This will ask for a confirmation. Click OK to apply.

![Apply view confirmation dialog box \(Click to expand\)][15]

The view will be applied to your selected folder.

#### Apply to folders and subfolders

Do you have a bunch of folders and subfolders and want to change to threaded view? It is possible in Thunderbird.

Set the thread view enabled/disabled on a folder, as we saw in the above section. Now, click on _Select columns to display_ → _Apply current view to_.

Now, instead of folders, select _Folder and its children_ option. Go to your account and then select the parent folder to which you want to apply the view.

![Select Folder and its children option \(Click to expand\)][16]

This will ask for your permission to apply the view to the folder and its sub-folders or children.

Give permission by clicking on the OK button.

![Asking permission to apply view \(Click to expand\)][17]

That's it. You have applied it successfully.

💡

This way, you can apply a view setting to an entire email account as well.

### Changing the default thread view

In Thunderbird, you can force the newly created folders to follow either Threaded or Unthreaded. This way, you can keep the view for existing folders and change the view for new folders.

To do this, click on the top-right hamburger menu and then select Settings.

![Select Thunderbird Settings \(Click to expand\)][18]

Go to the General tab, scroll down to the bottom, and select **Config Editor** option.

![Click on Config Editor \(Click to expand\)][19]

On the search bar, search for **mailnews.default_view_flags**. Then click on the editor button as shown below.

![Edit the Flag \(Click to expand\)][20]

Here, value **0** means _Unthreaded_ and a value **1** means **Threaded** view.

As you can see in the above screenshot, this is **1** by default. Let's change it to **0** so that new folders will follow an Unthreaded view. Click on the Tick button to apply the change.

![Change value of the flag \(Click to expand\)][21]

To reset it to default (1), just press the reset button adjacent to the flag.

![Reset the flag value \(Click to expand\)][22]

### Working with threads

You have seen several ways you can toggle the thread view in Thunderbird. Now, let's see some common uses of threads in Thunderbird.

#### Ignore a thread

You can ignore a particular thread so that it will be hidden from view. Further notifications for replies in that thread will be disabled for you.

Right-click on a message thread and select **Threads → Ignore Thread**.

![Ignore a Thread \(Click to expand\)][23]

That's it. The thread will disappear from your view.

To view the ignored threads, first press the ALT key on your keyboard to make the main menu appear. Now, from the main menu, select **View → Threads → Ignored Threads**.

![View Ignored Threads \(Click to expand\)][24]

Now, you will be able to see the ignored message on the selected folder, with a small red minus sign on the left side. When hovered over, it will say “This thread message is ignored”.

![Thread Ignored Notification \(Click to expand\)][25]

💡

Right-click on an ignored message and then unchecking ****Ignore Thread**** will remove the ignore of that thread.

#### Ignore a subthread

Ignoring a subthread means you can ignore further notifications for replies from a selected message onwards. This is good, especially when a conversation goes out of hand and you don't want to continue it in any way.

Expand the threaded message and then select a message from where you want to ignore.

![Ignore a Subthread \(Click to expand\)][26]

You can view the ignored threads by using the method mentioned in the previous section.

### Wrapping Up

Thunderbird is the [most prominent and well-maintained email client available for Linux][27]. It offers numerous customization options that can only be explored and experimented with.

We hope to bring you more such feature discovery in your favorite open source software. Suggestions are welcome 😄

--------------------------------------------------------------------------------

via: https://itsfoss.com/thunderbird-threading/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.thunderbird.net/en-GB/
[4]: https://itsfoss.com/content/images/2024/08/select-message-list-display-option-1.png
[5]: https://itsfoss.com/content/images/2024/08/sort-by-threaded-in-thunderbird.png
[6]: https://itsfoss.com/content/images/2024/08/messaging-with-threaded-view.png
[7]: https://itsfoss.com/content/images/2024/08/enable-thread-on-a-new-folder.png
[8]: https://itsfoss.com/content/images/2024/08/threaded-view-enabled-in-a-folder.png
[9]: https://itsfoss.com/content/images/2024/08/disable-threaded-view-for-a-folder.png
[10]: https://itsfoss.com/content/images/2024/08/select-table-view-in-thunderbird.png
[11]: https://itsfoss.com/content/images/2024/08/table-view-in-thunderbird.png
[12]: https://itsfoss.com/content/images/2024/08/click-on-thread-toggle.png
[13]: https://itsfoss.com/content/images/2024/08/select-apply-current-view-to-option.png
[14]: https://itsfoss.com/content/images/2024/08/select-a-folder-where-this-setting-need-to-be-applied.png
[15]: https://itsfoss.com/content/images/2024/08/apply-view-confirmation.png
[16]: https://itsfoss.com/content/images/2024/08/folder-and-its-children.png
[17]: https://itsfoss.com/content/images/2024/08/ask-permission-apply-folder-and-sub-folders.png
[18]: https://itsfoss.com/content/images/2024/08/select-thunderbird-settings.png
[19]: https://itsfoss.com/content/images/2024/08/click-on-config-editor.png
[20]: https://itsfoss.com/content/images/2024/08/edit-the-flag.png
[21]: https://itsfoss.com/content/images/2024/08/change-value-flag.png
[22]: https://itsfoss.com/content/images/2024/08/reset-the-flag-value-1.png
[23]: https://itsfoss.com/content/images/2024/08/ignore-a-thread-in-thunderbird-1.png
[24]: https://itsfoss.com/content/images/2024/08/view-ignored-threads.png
[25]: https://itsfoss.com/content/images/2024/08/this-thread-is-ignored.png
[26]: https://itsfoss.com/content/images/2024/08/ignore-a-subthread.png
[27]: https://itsfoss.com/best-email-clients-linux/
