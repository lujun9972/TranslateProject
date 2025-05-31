[#]: subject: "How I Run JavaScript in VS Code"
[#]: via: "https://itsfoss.com/vs-code-run-javascript/"
[#]: author: "Abhishek Kumar https://itsfoss.com/author/abhishek-kumar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I Run JavaScript in VS Code
======

[![Warp Terminal][1]][2]

In one of my earlier articles, I showed [how you can preview HTML files inside Visual Studio Code][3]. That setup worked well for testing static pages, but what if you want to go beyond markup and bring interactivity into the mix?

With JavaScript being the backbone of the modern web and countless developers now diving into frameworks like React, [Vue][4], and Svelte, being able to run JavaScript code directly inside VS Code becomes almost essential.

Running JavaScript in the editor helps you avoid constant context-switching, reduces distractions, and gives you immediate feedback when debugging.

There are two approaches here:

  * **Running JavaScript inside VS Code using Node.js:** most efficient and editor-native approach.
  * **Run it in a browser or using extensions** : handy for quick tests or visual feedback.



Let's see about using them.

### Understanding the role of Node.js

JavaScript was originally designed to run inside browsers, which come with their own JavaScript engines (like V8 in Chrome).

[Node.js][5] takes that same V8 engine and brings it to your local machine. This lets you run JavaScript outside the browser, directly from the command line or terminal.

It’s particularly useful for backend work, automation scripts, or just quick testing without the overhead of an HTML shell.

If you're unsure whether Node.js is already installed on your system, open a terminal and type:

```

    node -v

```

If you see a version number, you’re all set. If not, you’ll need to [download Node.js][6] and follow the installation instructions for your operating system.

We have [covered node installation on Ubuntu][7].

![][8]

### Set up a JavaScript project

Once everything’s installed, open VS Code and create a new folder for your project. Inside it, launch the terminal (`Ctrl + ~` or `Terminal > New Terminal`) and run `npm init -y`.

This initializes a basic project and creates a `package.json` file, which will be useful for managing your scripts and dependencies later.

![][9]

With the environment ready, create a new file named `app.js` and add a bit of JavaScript, for example:

```

    console.log("Hello, VS Code!");

```

To run it, simply type `node app.js` in the terminal.

![][10]

The output will appear immediately in the console, confirming that Node is executing your file properly.

### Add a custom script for simpler runs

To make things smoother, especially as your project grows, it’s a good idea to define a **custom script** in your `package.json` file. Open that file and find the `"scripts"` section, then add:

```

    "start": "node app.js"

```

![][11]

This allows you to run your script just by typing `npm start`, instead of repeating the filename every time.

![][12]

### Optional: Using the Code Runner extension

![][13]

If you prefer a quick way to execute small snippets without setting up a project, Code Runner can help. It’s a lightweight VS Code extension that runs code in a sandboxed output window.

To get started:

  * Open the Extensions tab in VS Code.
  * Search for “Code Runner” and install it.
  * Open a `.js` file, write some code, right-click, and select “Run Code.”



![][14]

For example, a file like `example.js` with:

```

    console.log("Hello from Code Runner!");

```

It will output directly to VS Code’s "Output" tab.

![][15]

The main limitation here is that it doesn’t use the integrated terminal like we used above, which can restrict input/output behavior for more complex scripts.

### Wrapping up

With Node.js set up inside VS Code, running JavaScript becomes a seamless part of your workflow, no browser tabs or external tools required.

Whether you're testing a quick function or building out a larger project, using the terminal and custom npm scripts keeps things fast and distraction-free.

Extensions like Code Runner can help for quick one-off tests, but for anything serious, sticking to the Node-powered method inside VS Code gives you more control, better error output, and a real development feel.

Once this setup becomes second nature, jumping into frameworks like React or Express will feel a lot more natural too.

Now that you’ve got the tools, go ahead, experiment, break stuff, debug, and build.

--------------------------------------------------------------------------------

via: https://itsfoss.com/vs-code-run-javascript/

作者：[Abhishek Kumar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek-kumar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/vs-code-run-html/
[4]: https://vuejs.org/
[5]: https://nodejs.org/en
[6]: https://nodejs.org/
[7]: https://itsfoss.com/install-nodejs-ubuntu/
[8]: https://itsfoss.com/content/images/icon/android-chrome-192x192-417.png
[9]: https://itsfoss.com/content/images/2025/04/initalize-directory-npm-1.png
[10]: https://itsfoss.com/content/images/2025/04/running-app-js-1.png
[11]: https://itsfoss.com/content/images/2025/04/editing-package-json.png
[12]: https://itsfoss.com/content/images/2025/04/running-npm-start-1.png
[13]: https://itsfoss.com/content/images/2025/04/code-runner-extension.png
[14]: https://itsfoss.com/content/images/2025/04/run-code-inside-code-runner.png
[15]: https://itsfoss.com/content/images/2025/04/running-examplejs-coderunner.png
