[#]: subject: "15 VS Code Tips and Tricks to Make Your Coding Experience Better"
[#]: via: "https://itsfoss.com/vs-code-tips/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

15 VS Code Tips and Tricks to Make Your Coding Experience Better
======

[![Warp Terminal][1]][2]

VS Code is the top choice for developers these days and I don't have to tell you why so.

If you are a VS Code user, let me share a few tips and tweaks that could improve your workflow and help your programming experience improve.

This collection is more than just the [VS Code keyboard shortcuts][3] that we discussed earlier. Although, several of the tips utilize shortcuts.

![][4]

Intrigued? Let's see them one by one.

### 1\. Integrated shell and multiple profile

Firstly, to get an integrated terminal in VS Code, you can use the shortcut CTRL+`.

Function | Shortcut
---|---
To enable an integrated terminal | CTRL+`
To open a location in an external terminal | CTRL + SHIFT + C

Now, you can choose the shell you want from the dropdown menu as shown below.

0:00

/0:27

1×

Selecting shell in VS Code integrated terminal

You can also split the terminal with different profiles. Click on the dropdown near the Plus button on the top of the integrated terminal and select **Split terminal**. Here, you can select the required profile.

![Split terminal][5]

### 2\. Split the editor

VS Code supports split view of editors and editor groups.

Normally, you can split the view on VS Code using the command CTRL+\\. This will split the view horizontally for two side-by-side editors.

Function | Shortcut
---|---
Split the editors in VS Code | CTRL+\
Close an active split | CTRL+W
Create a split on the upper side | CTRL+K CTRL+\
Switch between splits | CTRL+1/2/3..

0:00

/0:05

1×

Split view in VS Code editor

Now, each split can have their own files opened, making editor groups possible.

Alternatively, you can create several other layouts for split, like grid layout. For this, click on **View → Editor Layout → Select a Layout**.

![Editor layout selection][6]

Now, once a layout is selected, drag and drop the files to each grid like the example below.

💡

You can split the current editor without creating a new editor group with the View: Split Editor in Group command (Ctrl+K Ctrl+Shift+\\).

### 3\. Create files on the go

If you have a file specified in a code, you can open that file by pressing the CTRL key and clicking on it.

💡

If the item is a web link, it will be opened on your default web browser.

If the file is not present on the location, you will get a prompt to create that file and then open it on a new tab.

0:00

/0:08

1×

Create a new file on the go

No need to open a file manager or a terminal the specified new file.

### 4\. Scroll fast

If you are skimming through a huge code file, it will be beneficial to scroll a bit fast to reach a particular position. In VS Code, when you press the ALT key and then scroll using your mouse scroll wheel, you will get a 5x speed.

### 5\. Synchronize scrolling

When you are comparing two files side-by-side, synchronizing the scroll speed across the editors will help a lot.

First, open the command prompt by pressing CTRL + SHIFT + P. Here, search for “Toggle Locked Scrolling Across Editors”. Press enter on this setting.

That's it! Now, when you scroll one editor, the other editors will also start scrolling at the same pace.

### 6\. Sticky scroll

This is useful, especially when you are dealing with huge files with different sections.

For example, I am working with a markdown file that has a lot of chapters in headings.

If the Sticky scroll is enabled, when you scroll, each main section you are currently editing are stuck to the top of the editor. Thus, it is both a reminder and a navigation helper.

To enable this, open the command prompt by using CTRL + SHIFT + P. Now, search and then press Enter on “Toggle Editor Sticky Scroll”.

![Sticky Scroll][7]

In the above screenshot, I am editing inside the _Sixth Subheading_ , and it neatly sticks that to the top for easy access.

### 7\. Multi-cursor editing

This is a popular item in many code editors and IDE, allowing users to edit using multiple cursors simultaneously.

For this, you can press the ALT key and click on multiple locations to select multiple cursor positions.

0:00

/0:23

1×

Multi-cursor editing

Similarly, instead of selecting each location manually, you can add additional cursors to all occurrences of the current selection with `Ctrl+Shift+L`.

![Multiple Cursors][8]

In the above image, you can see that there is multiple cursor for all the `messageFour` variable name.

Another useful trick here is by using the `Ctrl+D` shortcut multiple times to only select the next occurrence after the one you selected, so you can add selections one by one.

Function | Shortcut
---|---
ALT + Leftclick | Select multiple cursor location
CTRL + SHIFT + L | Additional cursors to all occurance of current selection
CTRL + D | Select only current and next occurance of selected item.

### 8\. Markdown preview

VS Code can preview the markdown file you are editing both in a new tab and as a live preview.

Use the shortcut CTRL + SHIFT + V to get a markdown preview in a new tab. Or use `CTRL+K V` to get the markdown preview as a split view.

Function | Shortcut
---|---
Preview Markdown file in a tab | CTRL + SHIFT + V
Live preview Markdown file | CTRL + K V

![Markdown Preview][9]

### 9\. The Zen mode

VS Code has a cluttered interface with lots and lots of buttons and menus. Did you feel like this? Then the Zen mode is for you.

On an editor, press CTRL + K and then press Z. Now, you will get a focussed editor view, with nothing other than your code.

Function | Shortcut
---|---
Enable Zen Mode | CTRL + K Z
Exit Zen Mode | ESC key twice

![VS Code Zen Mode][10]

To escape, press ESC key twice.

### 10\. Move a line upwards or downwards

You can use the shortcut mentioned below to move a line to a line above or below.

Function | Shortcut
---|---
Move a line up | ALT + Up
Move a line down | ALT + Down

0:00

/0:10

1×

Moving Lines Up and Down

🚧

It is possible to copy a line down or up using a shortcut. This key is disabled by default in Ubuntu, because of conflict with system default shortcuts.

### 11\. Rename function/variable

To rename a variable, select that variable and press F2. Now, enter the new name. When you press Enter, the variable name will be changed on all occurrences.

0:00

/0:23

1×

Rename a Variable/Function

### 12\. Format whole document

To format an entire document, you can use the shortcut CTRL + SHIFT + I.

Function | Shortcut
---|---
Format whole document | CTRL + SHIFT + I

0:00

/0:10

1×

Format whole document

### 13\. Comment/Uncomment multiple lines

In order to comment or uncomment multiple lines, you can use the shortcut CTRL + SHIFT + A.

Function | Shortcut
---|---
Comment multiple lines | CTRL + SHIFT + A (Linux only)

🚧

This shortcut is only valid for Linux. For other OS, there is specific shortcuts.

0:00

/0:15

1×

Comment/Uncomment multiple lines

### 14 Simple Browser

VS Code provide a Simple Browser bundled extension, that is primarily meant to be used by other extensions for showing simple web content.

This is a basic browser preview using an iframe embedded in a webviewW.

You can access it by first going to the command prompt (CTRL + SHIFT + P) and searching _Simple Browser_.

### 15\. Double click keeps the file active

Here's the thing. You browse your files from the project explorer in the left. You click on the file and it is opened in the editor. You just read it and don't modify it. Next, you open another file the same way and you'll notice that the previously opened file has been automatically closed.

This is the default behavior so that the editor is not cluttered with tens of unmodified text files like browser tabs.

If you want to read a file as well as keep them active, just double click on them while opening them. This way, they will remain active in the editor regardless of whether they were modified or not.

### Share your favorite VS Code tip

Not all the tips would be applicable to your scenario but I have a feeling that you'll find some useful tips in this list. If that's the case, which one do you like the most here?

Do you also know some lesser known VS Code tip that you are proud of? Why not share it with us?

--------------------------------------------------------------------------------

via: https://itsfoss.com/vs-code-tips/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/vs-code-shortcuts/
[4]: https://itsfoss.com/content/images/icon/android-chrome-192x192-67.png
[5]: https://itsfoss.com/content/images/2024/08/split-the-terminal.png
[6]: https://itsfoss.com/content/images/2024/08/editor-layout-selection-in-vscode.png
[7]: https://itsfoss.com/content/images/2024/08/sticky-scroll.png
[8]: https://itsfoss.com/content/images/2024/08/multiple-cursor-at-selected-words.png
[9]: https://itsfoss.com/content/images/2024/08/markdown-side-by-sidew-preview.png
[10]: https://itsfoss.com/content/images/2024/08/zen-mode.png
