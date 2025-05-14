[#]: subject: "Handling Indentation in VS Code"
[#]: via: "https://itsfoss.com/vs-code-indentation/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Handling Indentation in VS Code
======

[![Warp Terminal][1]][2]

**Indentation** is how code is visually spaced. It helps define structure, scope, and readability. For example, Python _requires_ indentation to define blocks of code.

Other languages might not _require_ it, but [messy indentation can make code really hard to read][3] (and debug). Common indentation styles include:

  * **2 spaces** (popular in JS, HTML, CSS)
  * **4 spaces** (common in Python, Java)
  * **Tabs** (some devs swear by them)



VS Code lets you customize indentation per file, per language, or globally.

Let’s explore all the ways to tweak that!

### 1\. Change indentation via the status bar (per-file basis)

This is the easiest method and perfect when you're editing just one file.

  1. **Open a file** in VS Code.
  2. Look at the bottom-right corner of the window. You’ll see something like `Spaces: 4` or `Tab Size: 4`.



![][4]

  1. Click that label, a menu pops up!



Now, you can choose:

  * Indent Using Tabs
  * Indent Using Spaces



![][5]

And below that, choose how many spaces (2, 4, 8 - up to you).

Just changing the indentation setting doesn’t automatically re-indent the whole file. You’ll want to reformat the document too.

Here’s how:

  * Press `Ctrl + Shift + P` (Linux/Windows) or `Cmd + Shift + P` (macOS).
  * Type `Format Document` and select it.



![][6]

  * Or use the shortcut:
    * `Ctrl + Shift + I` on Linux
    * `Shift + Alt + F` on Windows
    * `Shift + Option + F` on macOS



Boom! The file gets prettied up with your chosen indentation.

### 2\. Set global indentation in user settings

Want to make your indentation choice apply to _all new files_ in VS Code? Here’s how:

  1. Open Command Palette with `Ctrl + Shift + P` or `F1`.
  2. Type `Preferences: Open User Settings`.



![][7]

  1. In the Settings UI, search for Tab Size and set it (e.g., 4).



![][8]

  1. Then search Insert Spaces and make sure it’s checked.



![][9]

This tells VS Code:

> “Whenever I press Tab, insert 4 spaces instead.”

Also check for **Detect Indentation,** if it’s ON, VS Code will override your settings based on the file content. Disable it if you want consistency across files.

### 3\. Set project-specific indentation (Workspace settings)

Maybe you want different indentation just for one project, not globally.

  1. Open the project folder in VS Code.
  2. Go to the Command Palette and select `Preferences: Open Workspace Settings`.



![][10]

  1. Switch to the `Workspace` tab.
  2. Search and set the same **Tab Size** , **Insert Spaces** , and **Detect Indentation** options.



![][11]

These get saved inside your project’s `.vscode/settings.json` file.

Perfect if you want 2-space indentation in a JS project but 4 spaces in a Python project you're working on separately.

### 4\. Set indentation based on programming language

Now, here's the power-user move. Let’s say you want:

  * 4 spaces for Python
  * 2 spaces for JavaScript and TypeScript



Easy!

  1. Open the Command Palette → `Preferences: Open User Settings (JSON)`



![][12]

  1. Add this snippet:



```

    "[python]": {
      "editor.tabSize": 4
    },
    "[javascript]": {
      "editor.tabSize": 2
    },
    "[typescript]": {
      "editor.tabSize": 2
    }

```

This overrides the indentation per language.

![][13]

You can find all language identifiers in the VS Code docs if you want to customize more.

You can also drop this into your .vscode/settings.json file if you want project-level overrides.

### Bonus Tip: Convert tabs to spaces (and vice versa)

Already working on a file but the indentation is inconsistent?

  * Open the Command Palette → Type `Convert Indentation`
  * Choose either:
    * `Convert Indentation to Spaces`
    * `Convert Indentation to Tabs`



![][14]

You can also do this from the status bar at the bottom.

If you need to convert _all_ tabs in the file to spaces:

  1. Press `Ctrl + F`
  2. Expand the search box
  3. Enable **Regex** (.* icon)
  4. Search for `\t` and replace it with two or four spaces



### Wrapping up

Like word wrapping in VS Code, indentation may seem like a small thing, but it's one of the cornerstones of clean, readable code.

Whether you're coding solo or collaborating on big projects, being consistent with indentation helps avoid annoying bugs (especially in Python!) and keeps the codebase friendly for everyone.

VS Code makes it super easy to control indentation your way, whether you want to set it globally, per project, or even per language.

We’ll be back soon with another helpful tip in our VS Code series.

--------------------------------------------------------------------------------

via: https://itsfoss.com/vs-code-indentation/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://stackoverflow.com/questions/2472553/why-is-there-so-much-poorly-indented-code-out-there
[4]: https://itsfoss.com/content/images/2025/04/spaces-column-in-vs-code-1.png
[5]: https://itsfoss.com/content/images/2025/04/spaces-column-in-vs-code.gif
[6]: https://itsfoss.com/content/images/2025/04/format-document.png
[7]: https://itsfoss.com/content/images/2025/04/user-settings.png
[8]: https://itsfoss.com/content/images/2025/04/default-indentation-tab-size.png
[9]: https://itsfoss.com/content/images/2025/04/insert-spaces.png
[10]: https://itsfoss.com/content/images/2025/04/toggling-workspace-settings.png
[11]: https://itsfoss.com/content/images/2025/04/workspace-indentation-setting.png
[12]: https://itsfoss.com/content/images/2025/04/user-settings-1.png
[13]: https://itsfoss.com/content/images/2025/04/indentation-based-on-programming-language.png
[14]: https://itsfoss.com/content/images/2025/04/quick-convert-indentation.png
