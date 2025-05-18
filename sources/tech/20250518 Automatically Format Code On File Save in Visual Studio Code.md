[#]: subject: "Automatically Format Code On File Save in Visual Studio Code"
[#]: via: "https://itsfoss.com/vs-code-auto-format-code/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Automatically Format Code On File Save in Visual Studio Code
======

[![Warp Terminal][1]][2]

Manually formatting code can be tedious, especially in fast-paced or collaborative development environments.

While consistent formatting is essential for readability and maintainability, doing it by hand slows you down and sometimes leads to inconsistent results across a project.

In this article, I’ll walk you through the steps to configure Visual Studio Code to automatically format your code each time you save a file.

We'll use the VS Code extension called [Prettier][3], one of the most widely adopted tools for enforcing code style in JavaScript, TypeScript, and many other languages.

By the end of this guide, you'll have a setup that keeps your code clean with zero extra effort.

### Step 1: Install Prettier extension in VS Code

To start, you'll need the **Prettier - Code Formatter** extension. This tool supports JavaScript, TypeScript, HTML, CSS, React, Vue, and more.

Open VS Code, go to the **Extensions** sidebar (or press `Ctrl + Shift + X`), and search for [**Prettier**][4].

Click on **Install** and reload VS Code if prompted.

![][5]

### Step 2: Enable format on save

Now that Prettier is installed, let’s make it run automatically whenever you save a file.

Open **Settings** via `Ctrl + ,` or by going to **File > Preferences > Settings**.

![][6]

In the search bar at the top, type `format on save` and then Check the box for **Editor: Format On Save**.

![][7]

This tells VS Code to auto-format your code whenever you save a file, but that’s only part of the setup.

### Troubleshooting

If saving a file doesn’t automatically format your code, it’s likely due to multiple formatters being installed in VS Code. Here’s how to make sure Prettier is set as the default:

  * Open any file in VS Code and press `Ctrl + Shift + P` (or `Cmd + Shift + P` on Mac) to bring up the Command Palette.
  * Type **“Format Document”** and select the option that appears.



![][8]

  * If multiple formatters are available, VS Code will prompt you to choose one.



![][9]

  * Select **“Prettier - Code formatter”** from the list.



![][10]

Now try saving your file again. If Prettier is correctly selected, it should instantly reformat the code on save.

In some cases, you might want to save a file _without_ applying formatting, for example, when working with generated code or temporary formatting quirks. To do that, open the Command Palette again and run **“Save Without Formatting.”**

![][11]

### Optional: Advanced configuration

Prettier works well out of the box, but you can customize how it formats your code by adding a `.prettierrc` configuration file at the root of your project.

Here’s a simple example:

```

    {
      "singleQuote": true,
      "trailingComma": "es5",
      "semi": false
    }

```

This configuration tells Prettier to use single quotes, add trailing commas where valid in ES5 (like in objects and arrays), and omit semicolons at the end of statements.

There are many other options available such as adjusting print width, tab width, or controlling how JSX and HTML are handled.

You can find the full list of supported options in [Prettier’s documentation][12], but for most projects, a few key settings in `.prettierrc` go a long way.

### Try It Out

Create or open any file, JavaScript, TypeScript, HTML, etc. Add some poorly formatted code.

```

    <html><head><style>body{background:#fff;color:#333;font-family:sans-serif}</style></head><body><h1>Hello</h1><script>document.querySelector("h1").addEventListener("click",()=>{alert("Hello World!")})</script></body></html>

```

![][13]

Then simply save the file (`Ctrl + S` or `Cmd + S`), and watch Prettier instantly clean it up.

![][14]

As you can see, Prettier neatly indents and spaces each part of the html code, even across different embedded languages.

### Wrapping Up

It doesn't matter if [you are vibe coding][15] or doing everything on your own, proper formatting is a sign of writing good code.

We’ve already covered the fundamentals of writing clean, consistent code - [indentation][16], spacing, and [word wrap][17], and automatic formatting builds directly on top of those fundamentals.

Once configured, it removes the need to think about structure while coding, letting you focus on the logic.

If you're also wondering how to actually run JavaScript or [HTML inside VS Code][18], we've covered that as well, so check those guides if you're setting up your workflow from scratch.

If you’re not already using automatic formatting, it’s worth making part of your workflow.

And if you use a different tool or approach, I’d be interested to hear how you’ve set it up, let us know in the comments. 🧑‍💻

--------------------------------------------------------------------------------

via: https://itsfoss.com/vs-code-auto-format-code/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://prettier.io
[4]: https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode
[5]: https://itsfoss.com/content/images/2025/05/prettier-vscode-extension.png
[6]: https://itsfoss.com/content/images/2025/05/accessing-settings.png
[7]: https://itsfoss.com/content/images/2025/05/format-on-save.png
[8]: https://itsfoss.com/content/images/2025/05/format-document-1.png
[9]: https://itsfoss.com/content/images/2025/05/configure-formatter.png
[10]: https://itsfoss.com/content/images/2025/05/multiple-formatter.png
[11]: https://itsfoss.com/content/images/2025/05/save-without-format-1.png
[12]: https://prettier.io/docs/configuration
[13]: https://itsfoss.com/content/images/2025/05/html-code-unformatted-1.png
[14]: https://itsfoss.com/content/images/2025/05/saving-unformatter-html-code-file.gif
[15]: https://itsfoss.com/vibe-coding-editors/
[16]: https://itsfoss.com/vs-code-indentation/
[17]: https://itsfoss.com/vs-code-word-wrap/
[18]: https://itsfoss.com/vs-code-run-html/
