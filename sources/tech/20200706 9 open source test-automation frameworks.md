[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (9 open source test-automation frameworks)
[#]: via: (https://opensource.com/article/20/7/open-source-test-automation-frameworks)
[#]: author: (Amit Dua https://opensource.com/users/amitdua)

9 open source test-automation frameworks
======
Get some advice to choose the right test-automation framework for your
organization.
![gears and lightbulb to represent innovation][1]

A test-automation framework is a set of best practices, common tools, and libraries that help quality-assurance testers assess the functionality, security, usability, and accessibility of multiple web and mobile applications. In a "quick-click" digital world, we're accustomed to fulfilling our needs in a jiffy. This is one reason why the software market is flooded with hundreds of test-automation frameworks.

Although teams could build elaborate automated testing frameworks, there's usually little reason to spend the money, resources, and person-hours to do so when they can achieve equal or even better results with existing open source tools, libraries, and testing frameworks. Other reasons to use existing open source test-automation frameworks is that they are:

  * Reusable
  * Easy to maintain
  * In need of minimum manual intervention
  * Stable in a volatile environment
  * Scalable



### How to select a test-automation framework

Because different businesses have different needs, it's difficult to pinpoint all the things you will want in a test-automation framework. However, there are some key criteria that most organizations will look for in a test-automation framework:

  1. **Ease of script development:** A testing framework must support agile processes and short iterations.
  2. **Cross-team compatibility:** Since software testing isn't confined to a single department, a testing framework must be compatible across roles and request inputs from both development and QA testers.
  3. **Support for multiple languages:** The framework should include language support for different app platforms. In other words, a testing framework must support Objective-C/Swift for iOS, Java for Android, and any other coding languages essential to your work.
  4. **Support for the latest platform capabilities:** An open source testing framework should be updated regularly and remain compatible with the latest operating system features to avoid framework gaps around testing.



Selecting the best test-automation framework for your organization can be difficult. To help you evaluate features against your needs and narrow down your options, below I've outlined my top nine open source business automation tools and frameworks.

### Appium

[Appium][2] is an open source test-automation framework based on a WebDriver protocol for testing mobile applications. Built around the idea of uniformity, it allows you to write tests for different platforms using the same APIs.

**Major features:**

  * Eliminates the need for recompiling applications
  * Offers options for choosing different coding languages and frameworks to run tests
  * Allows testers to create element repositories and manage them accordingly
  * Supports reusable code and tests (written in Node.js) between iOS, Android, and Windows test suites



### Carina

[Carina][3] is a popular Java-based test-automation framework built on top of [Selenium][4]. Because it doesn't rely on a specific technology stack, software developers, QA, and testers can reuse test-automation code between iOS and Android up to 70% of the time.

**Major features:**

  * Unites all testing layers, including mobile (native and hybrid), web applications, REST services, and even databases, into one application
  * Supports both rational and non-rational databases (MySQL, Oracle, and SQL Servers)
  * Leverages the FreeMarker template engine to give testers tremendous flexibility in generating REST requests



### Galen

If your test-automation efforts are mainly aimed towards improving the user experience (UX), [Galen][5] is the test-automation framework to put to work. Galen specifically caters to UX testing, with specific syntax for testing and verifying your mobile or web application's layout.

**Major features:**

  * Enables you to specify browser windows' size to run tests on layout specifications
  * Writes test files in Galen syntax, JavaScript, or Java
  * Generates detailed HTML reports with thorough heatmap analysis



### Gauge

[Gauge][6], a relatively new test-automation tool, is lightweight and cross-platform. Its beauty is that it's built on a plugin architecture, so it can be used with any language, IDE, and ecosystem.

**Major features:**

  * Offers easy setup; you can get a framework up and running with a single command
  * Executes automation texts in simple language syntax
  * Supports modular architecture with myriad extended plugins
  * Creates text documentation in simple Markdown, i.e., devoid of any particular structure



### Katalon

If you're looking for a straightforward yet detail-oriented test-automation framework, consider [Katalon][7]. It is an open source testing framework with support for web, mobile, and API automation testing.

**Major features:**

  * Offers extended support for multiple scripting languages, including Groovy and Java
  * Supports Jira implementation
  * Automatically generates test scripts by analyzing and recording web actions and capturing associated objects (similar to [robotic process automation][8] (RPA))



### Robot Framework

If you need a Python-based test-automation framework, you can't go wrong with the [Robot Framework][9]. Albeit generic in terms of acceptance-test-driven development (ATDD), Robot Framework is considered a mature solution for software developers and QA testers. This test-automation framework's main feature is its keyword-driven approach to creating tests that are easy to read and write.

**Major features:**

  * Provides rich integration of APIs, generic text libraries, and tools
  * Tests myriad things including websites, FTP, MongoDB, Android, Apium, and more
  * Integrates with Jython (Java) and IronPython (.NET), even though it's Python-based
  * Supports tabular data syntax



### Selenium

[Selenium][10] is indisputably the most popular open source test-automation framework for web applications. Because it is cross-compatible across multiple operating systems, you can write test scripts in multiple languages, which is one reason Selenium is the basis for an enormous number of testing tools and automation frameworks.

**Major features:**

  * Highly customizable due to the integration of a wide range of APIs and coding languages, including Java, Python, .NET, C#, Ruby, and more
  * Comes integrated with a playback tool, Selenium IDE, that enables test authoring without learning specific scripts
  * Is compatible across platforms, operating systems, and browsers



### Serenity

[Serenity][11] (formerly known as Thucydides) is an open source Java-based test-automation framework that helps with writing automating acceptance and regression tests. If you're searching for a tool that easily integrates with behavior-driven development (BDD), Serenity might be a good fit for automating your software testing.

**Major features:**

  * Facilitates writing BDD and Selenium tests by abstracting boilerplate code
  * Enables you to test multiple scenarios at a high level while sustaining lower-level record details
  * Comes with pre-built functions, including WebDriver management, Jira integration, running parallel processes, and more



### Testproject.io

If you're new to software test automation and are seeking a free platform with a robust community around it, you can't go wrong with [Testproject.io][12].

It's built on two open source tools (Selenium and Appium) with the goal of enticing new testers and allowing them to run tests using commonly used automation actions.

**Major features:**

  * Supports multiple languages, including Python, JavaScript, Java, C++, and more
  * Enables seamless sharing of software tests and APIs with testers around the globe
  * Includes features including test recording, global automation grid, and automation building blocks to support QA testers who are new to programming



### Closing thoughts

There are so many open source test-automation frameworks and tools available that listing all of them in a single article isn't feasible. These nine tools stand out to me, but keep in mind that not all tools and frameworks are created equally. The two areas where these frameworks and tools shine are their support for different operating systems and different scripting languages.

As automation testing gains more traction, new challenges and opportunities will come to the surface. For example, AI, [RPA][13], and machine learning are expected to grow significantly in the next few years. Therefore, it's wise to consider the benefits and risks of automation, including test-automation frameworks and [RPA solutions][14], in your business.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/open-source-test-automation-frameworks

作者：[Amit Dua][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/amitdua
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/innovation_lightbulb_gears_devops_ansible.png?itok=TSbmp3_M (gears and lightbulb to represent innovation)
[2]: https://github.com/appium/appium
[3]: https://github.com/qaprosoft/carina
[4]: tmp.WPdrnjRpt5#Selenium
[5]: https://github.com/galenframework/galen
[6]: https://github.com/getgauge/gauge
[7]: https://github.com/katalon-studio
[8]: https://www.signitysolutions.com/blog/rpa-robotic-process-automation/
[9]: https://github.com/robotframework/robotframework
[10]: https://github.com/SeleniumHQ/selenium
[11]: https://github.com/serenity-bdd/serenity-core
[12]: https://github.com/testproject-io
[13]: https://enterprisersproject.com/tags/rpa
[14]: https://www.signitysolutions.com/robotic-process-automation-rpa/
