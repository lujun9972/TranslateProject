[#]: subject: "Use Multi-Cursor in VS Code to Edit Multiple Lines Simultaneously"
[#]: via: "https://itsfoss.com/vs-code-multi-cursor/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Use Multi-Cursor in VS Code to Edit Multiple Lines Simultaneously
======

[![Warp Terminal][1]][2]

Working with code often involves repetition, changing variable names, updating values, tweaking class names, or adding the same prefix across several lines.

If you find yourself making the same changes again and again, line by line, then multi-cursor editing in Visual Studio Code can help simplify that process. In this part of our ongoing VS Code series, we’ll take a closer look at this feature and how it can make everyday tasks quicker and more manageable.

### Why use multiple cursors?

Multi-cursor editing lets you place more than one cursor in your file so you can edit several lines at once.

Instead of jumping between lines or writing the same change repeatedly, you can type once and apply that change across multiple places. Here are a few common situations where it comes in handy:

  * Renaming a variable or function in multiple places.
  * Adding or removing the same snippet of code across several lines.
  * Editing repeated structures (like object keys, class names, or attribute values).
  * Commenting out a bunch of lines quickly.



Once you start using it, you’ll notice it helps reduce small repetitive tasks and keeps your focus on the code itself.

### Placing multiple cursors: mouse and keyboard

There are two main ways to place multiple cursors in VS Code using the mouse or keyboard shortcuts.

Let’s start with the mouse-based approach, which is more visual and straightforward for beginners.

Then, we’ll move on to keyboard shortcuts, which are faster and more efficient once you’re comfortable.

#### Method 1: Using the mouse

To place cursors manually using your mouse: Hold down `Alt` (Windows/Linux) or Option (Mac), then click anywhere you want to insert a new cursor.

![][3]

Each click places a new blinking cursor. You can now type, delete, or paste, and the change will reflect at all cursor positions simultaneously. To cancel all active cursors and return to a single one, press Esc. This method is handy for quick edits where the lines aren’t aligned or when you want more control over cursor placement.

#### Method 2: Using keyboard shortcuts

The mouse method is a good starting point, but learning keyboard shortcuts can save more time in the long run.

Below are a few keyboard-driven techniques to add and manage multiple cursors efficiently.

##### Add Cursors Vertically in a Column

When you want to add cursors above or below the current line to edit a block of similar lines (like inserting or deleting the same code at the beginning of each line), use this shortcut: `Ctrl+ Alt + Up/Down` arrow keys.

![][4]

This aligns cursors in a vertical column, making it easier to apply the same action to adjacent lines.

##### Select the next occurrence of the current word

To select and edit repeated words one by one such as variable names or function calls, place your cursor on the word and use: `Ctrl + D`

![][5]

Each press selects the next matching word and adds a cursor to it. You can press it repeatedly to continue selecting further matches.

##### Select all occurrences of a word in the file

If you want to update every instance of a word across the file at once, for example, replacing a class name or a repeated property, use: `Ctrl + Shift + L`

![][6]

This selects all matching words and places a cursor at each one. It’s powerful, but use with care in large files to avoid unintentional edits.

##### Editing with multiple cursors

Once your cursors are in place, editing works just like usual:

  * Type to insert text across all cursors.
  * Use Backspace or Delete to remove characters.
  * Paste snippets — they get applied to each cursor position.
  * Standard commands like cut, copy, undo, and redo all function as expected.



Just keep an eye on alignment. If cursors are placed unevenly across lines, your edits might not be consistent.

Since you seem to be interested, check out some of the [other VS Code keyboard shortcuts][7].

![][8]

### Wrapping Up

Multi-cursor editing is one of those small but effective features in VS Code that can make repetitive tasks less of a chore.

You don’t need to learn all the shortcuts right away. Start simple, try placing cursors with `Ctrl + D` or selecting multiple lines vertically and build from there. As you become more comfortable, these techniques will become second nature and help you focus more on writing logic and less on repeating edits.

--------------------------------------------------------------------------------

via: https://itsfoss.com/vs-code-multi-cursor/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/04/multiple-cursor-with-mouse.gif
[4]: https://itsfoss.com/content/images/2025/04/ctrl-alt-down-arrow-for-multiple-cursor.gif
[5]: https://itsfoss.com/content/images/2025/04/ctrl-d-for-next-occurence-of-word.gif
[6]: https://itsfoss.com/content/images/2025/04/ctrl-shift-l-for-same-occurence.gif
[7]: https://itsfoss.com/vs-code-shortcuts/
[8]: https://itsfoss.com/content/images/icon/android-chrome-192x192-418.png
