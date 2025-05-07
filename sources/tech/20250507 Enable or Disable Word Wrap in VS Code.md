[#]: subject: "Enable or Disable Word Wrap in VS Code"
[#]: via: "https://itsfoss.com/vs-code-word-wrap/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Enable or Disable Word Wrap in VS Code
======

[![Warp Terminal][1]][2]

W **ord wrap** automatically breaks a long line of text so it fits within your current editor window, without you needing to scroll horizontally. It doesn’t add line breaks to your file; it just wraps it visually.

Picture this: You’re writing a long JavaScript function or a long SQL query. Without word wrap, you’d be endlessly dragging that horizontal scrollbar. With it, everything folds neatly within view.

This is especially useful when:

  * You're working on a small screen.
  * You want cleaner screenshots of your code.
  * You prefer not to lose track of long lines.



Now, let's see how to turn it on or off when needed.

### Method 1: The quickest toggle - Alt + Z

Yep, there’s a shortcut for it!

  1. Open any file in VS Code.
  2. Press `Alt + Z` on your keyboard.



![][3]

And that’s it! Word wrap is toggled. Hit it again to switch it off.

### Method 2: Use the command palette

Prefer something a bit more visual? The Command Palette is your go-to.

  1. Press `Ctrl + Shift + P` (or `Cmd + Shift + P` on macOS).
  2. Type `Toggle Word Wrap`.
  3. Click the option when it appears.



![][4]

This is ideal if you’re not sure of the shortcut or just want to double-check before toggling.

### Method 3: Set a default from settings

Want word wrap always on (or always off) when you open VS Code? You can change the default behavior.

1\. Go to `File > Preferences > Settings`

![][5]

2\. Search for “word wrap.”

3\. Under Editor: Word Wrap, choose from the following options:

  * `off`: Never wrap.
  * `on`: Always wrap.
  * `wordWrapColumn`: Wrap at a specific column number.
  * `bounded`: Wrap at viewport or column, whichever is smaller.



![][6]

💡

****What’s “wordWrapColumn” anyway?****
It lets you define a column (like 20) at which VS Code should wrap lines. Great for keeping things tidy in teams with coding standards.

You can also tweak `"editor.wordWrap"` in `settings.json` if you prefer working directly with config files.

### Wrapping up!

Word wrap might seem like a tiny detail, but it’s one of those “small things” that can make coding a lot more pleasant. Take the indentation settings for example, another crucial piece for code readability and collaboration. Yes, the tabs vs spaces debate lives on 😄

We’ll continue exploring more quick yet powerful tips to help you make the most of VS Code.

Until then, go ahead and wrap those words your way.

--------------------------------------------------------------------------------

via: https://itsfoss.com/vs-code-word-wrap/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/content/images/2025/04/alt-z-for-quick-word-wrap.gif
[4]: https://itsfoss.com/content/images/2025/04/toggle-wordwrap.png
[5]: https://itsfoss.com/content/images/2025/04/settings-for-wordwrap.png
[6]: https://itsfoss.com/content/images/2025/04/wordwrap-settings-default.png
