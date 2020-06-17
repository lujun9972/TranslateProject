[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (My favorite 10 Node.js projects)
[#]: via: (https://opensource.com/article/20/6/nodejs-projects)
[#]: author: (Tejas Kaneriya https://opensource.com/users/tejas-kaneriya)

My favorite 10 Node.js projects
======
Find the right open source tool for your next Node.js project.
![Computer screen with files or windows open][1]

Experienced developers, much like skilled artisans, rely on a set of tools to help them get their job done effectively and efficiently. However, trying to select the right tools can be intimidating, especially when you have many options to choose from.

Such is the case with [Node.js][2], which is famous for its vibrant community that contributes code and tools for others to use, adding significant value to new generations of apps. However, with so many options out there, it isn't easy to find the most dependable projects to suit your development needs.

To give you some help, I'll share the 10 most useful open source Node.js projects to consider using in your development project.

### What is Node.js?

[Node.js][3] is an open source JavaScript runtime environment that is popular for writing server-side JavaScript applications. It is event-driven and works on a non-blocking I/O model, making it lightweight and efficient for building web applications. Introduced in 2009, Node.js became popular swiftly after its release, in part because its architecture, use cases, and advantages offered an edge over its predecessors. Large companies such as Netflix, Amazon, and eBay say their primary reasons for using Node.js are its modern features and its ability to [reduce startup time][4].

Since Node.js is an open source runtime environment, anyone can get started using it. This also makes it dependent on open source contributions and projects that are available for free use. Luckily, Node.js has a ton of such projects.

### Top 10 Node.js projects

Here are 10 of the most notable and useful open source Node.js projects you can use.

#### 1\. Express

[Express][5] is one of the most popular Node.js frameworks. It has been around for a while and is known for its simplicity and minimalism. Express offers tremendous value since it makes HTTP requests efficient even when you are working with JavaScript, an out-of-browser and server-side language.

Some of Express' more popular features include handlers to manage HTTP requests with diverse URL routes, rendering-engine integration for inserting template data, and middleware-request processing. Express is also an unopinionated framework, which means you won't have issues executing it because you are not confined to any "right way" of using it to solve a problem.

Many new developers adopt open source frameworks and later realize they are not actively updated. This can be a crucial problem for open source frameworks and poses a significant risk for the developers who adopt them. But you will be sailing in clear waters with Express, since it has a strong community that provides frequent updates. Over 17 different middleware and complex frameworks, including Feathers, ItemsAPI, KeystoneJS, Poet, and Kraken, and large companies, such as Uber, IBM, and Accenture, use Express.

#### 2\. Hapi

If you have been working with Node.js for a while, you may find [Hapi][6] to be an anomaly in the framework ecosystem. It's not as popular as Express, but that's mostly because Express is older, and Hapi has been catching up quickly in the last several years.

If performance is your core metric, you might prefer Express over Hapi. Though in my experience, the performance differences are barely noticeable, they still exist. If you're interested in features, Hapi's large number of them may make it your top choice.

Hapi is also relatively safer than Express to implement because Hapi is not dependent on any external code: Its most important feature is that it has zero need for middleware. Express relies on middleware to achieve its effectiveness and simplicity in execution. Hapi has taken a creative approach to this; instead of taking the conventional middleware route, it offers plugins that keep its portfolio of functionalities competitive. From routing to logins, Hapi has plugins for everything.

Working with Hapi will show you what a framework can do with the help of plugins and secure, frequently updated code.

#### 3\. Electron

If you are a web application developer, desktop product development may seem like a nightmare. While JavaScript makes it easier to work on apps that support multiple platforms, once a product scales into a company, you have to go to each platform and add features. [Electron][7], which is designed by GitHub, eliminates this hassle by pulling together a unified system.

If you are making client-side or web-based apps, Electron will greatly simplify the development process. Some people claim that Electron takes up more memory than conventional frameworks; in reality, with efficient programming, this is easy to avoid.

If a graphical user interface (GUI) is imperative for your app or product, Electron will be perfect for you. Since it deploys web technologies, it works very well, even with complex UI/UX modules. Development, deployment, updating, and maintenance of Electron-made apps are all simple because it provides a single codebase to manage your app across all platforms.

Electron uses JavaScript and Node.js, as well as HTML and CSS. It harnesses the power of the Chrome Engine (Chromium), so make sure to learn about Chromium's functionalities before you get started with Electron.

#### 4\. Visual Studio Code

[VSCode][8] is a language-agnostic source-code editor that works exceptionally well with JavaScript and Node.js. As compiled by Microsoft, it's licensed under the Microsoft Sofware License, but you can download the same application with an open source license from [VSCodium.com][9]. VSCode is language agnostic, supporting several languages and a vast number of extensions. It allows you to easily exclude unnecessary files from your project tree and integrates nicely with Git.

An exciting part of Visual Studio Code is that it uses the Electron framework with the [Blink][10] browser engine. As a source-code editor, it has excellent capacity for amplifying debugging, syntax highlighting, and code completion processes, which is why it was voted the most popular development environment tool in 2019 in [Stack Overflow][11]'s annual developer survey.

#### 5\. JavaScript Standard Style

If need is the mother of invention, simplicity is the mother of efficiency. After all, simplicity and standardization can help ensure that you are not at the whims of your mood when you are working on a continual development process.

[Standard JS][12] has a simple proposition: your code formatting should be consistent and standardized. It automatically formats your code to align with community guidelines to help you provide an appropriate contribution to the codebase whenever you update something.

Generally, if you are working on a project involving multiple people or one that you will contribute to for an extended time, it makes sense to have Standard JS by your side. If not, you will have to create and maintain style configuration files for every model, across all your projects. This can be tedious and exhausting when you're coding. No one wants to code for hours and not get the results they expect because of a style error.

Standard JS is used by many organizations, including GitHub, Zendesk, GoDaddy, and the UK government, so you can expect a safe, standardized environment and functionalities from it.

#### 6\. ESLint

Most programmers who love JavaScript are fond of the programming language because of its loosely typed nature. It yields results if you know what you are doing. This freedom becomes a problem for programmers who are just getting acquainted with the language because they do not yet have an intuitive process to avoid developer errors. This is where [ESLint][13] comes in.

ESLint is a linting tool for coding, which means it performs a static analysis on the code and finds errors, patterns, and lines that don't fit conventional style guidelines. This adds an extra level of checking that the code works before you execute it. Some compilers have basic linting functionalities, but ESLint takes it a notch higher.

Even though finding errors according to a language's conventional style guidelines is ESLint's primary offering, it is not the most critical one. ESLint's best feature is its customizability. You may need to incorporate some idiosyncratic style or project-specific rules across your codebase. ESLint comes with a default set of rules, but you can change them however and whenever you want. In terms of adoption, Facebook, Netflix, Atlassian, Zendesk, Box, and PayPal all use ESLint.

#### 7\. Sinon.JS

If you take a course on programming, testing always gets the least attention. After all, your primary responsibility as a programmer is to write code, right? Not exactly. Your primary responsibility is to write code that _works_. And testing is critically important to achieving that.

The biggest problem with testing a module or unit of your code is that it's not always feasible to do it. Scientists have to control all the variables to study causality. Similarly, programmers have to go through a ton of loops to ensure that their code works. But what if your code is not working?

For instance, imagine your code is time-sensitive, but it runs a second slow, and you need server access to check whether your code is functioning the way it should. This is an inefficient way to test, even for the most critical parts of your code.

Sinon helps you replace complex code with simple placeholder variables that act as "test-doubles". This allows you to conduct your tests while skipping over a lot of the complexity of what you're testing. [Sinon.JS][14] compounds JavaScript's ability to replace one element with another, without compromising its functionality. Sinon uses **Spies** to help you find the information you need on function calls without distorting their properties. **Stub** allows you to replace a function so that you can ask it to do something specific, and see how it turns out.

#### 8\. Mocha and 9. Chai

[Mocha][15] and [Chai][16] are generally used together and alongside Sinon.JS to ensure testing is accurate, functional, and runs independently of other unit tests.

There are two key reasons testing is both critical and challenging: First, you have to isolate the unit that is working from the one that isn't. Second, you have to separate it for the right reasons. You cannot afford to consider a unit functional if it's not (and vice versa). Much like lab testing, you can't afford false positives or false negatives in programming.

##### Mocha

Mocha adapts to these two constraints. It is a testing framework that helps you test the units of your code without disturbing unit behavior. You will see the tags `describe` and `it` across the test code you write in Mocha. `describe` highlights the test suite that focuses on testing one functionality, while `it` highlights whether the unit has passed the test or not.

##### Chai

The Chai framework empowers your testing process in a simple way: it gives the expected value of a unit. Chai's Assertion library contains all the primary functions and methods to help you test a unit. After you run your unit through Chai, it returns the unit's results and compares the expected vs. real results.

Although the application and principle that make Chai work are very simple—that your units should do what they are designed to do—it can help you plan the functionalities you expect from each unit. Later, as you scale the product, you will see how critical it is to ensure that each unit behaves according to your expectations before you integrate it into your codebase.

#### 10\. Hygen

[Hygen][17] is a code generator that helps you when you have less time to do more work. Developers have been toying with the idea of code generators for years now. Their essential purpose is clear: they generate code for you so you can be more efficient with your time. But until Hygen, no code generator ever produced a significant programming productivity bump.

Hygen sits quietly in your code until you invoke it. The code generator has contextual understanding, scalability, and language-agnosticism. With the right integration, Hygen can save you a ton of programming hours you would otherwise spend typing redundant code.

Hygen works well with Redux, Express.js, and React Native projects. Hygen comes with its own set of packages that can help you speed up the development for React Native and Express.js projects by generating common code used in such projects. Once you get acquainted with the details of your project, you can keep your code generation local. This can be of great help if you're working on a complex project or have a new or large team. Hygen takes care of the mundane code using the packages and generation rules you've set up.

### Conclusion

Looking at these projects can be overwhelming—either from the amount of information you have to process or from all the new ideas bouncing in your head about how you can use them. However, with these projects available, the world is your sandbox.

Good programming can help you build your project exactly the way you want. If you get stuck, these open source projects can help you in your quest to develop exceptional applications.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/nodejs-projects

作者：[Tejas Kaneriya][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/tejas-kaneriya
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/browser_screen_windows_files.png?itok=kLTeQUbY (Computer screen with files or windows open)
[2]: https://nodejs.org/en/
[3]: https://www.simform.com/what-is-node-js/
[4]: https://netflixtechblog.com/making-netflix-com-faster-f95d15f2e972
[5]: https://expressjs.com/
[6]: https://hapi.dev/
[7]: https://www.electronjs.org/
[8]: https://github.com/microsoft/vscode
[9]: https://vscodium.com
[10]: https://www.chromium.org/blink
[11]: https://insights.stackoverflow.com/survey/2019#development-environments-and-tools
[12]: https://standardjs.com/
[13]: https://eslint.org/
[14]: https://sinonjs.org/
[15]: https://mochajs.org/
[16]: http://chaijs.com/
[17]: http://www.hygen.io/
