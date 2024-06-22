[#]: subject: "I Put GitButler To The Test: A New Kind of Git Client by GitHub's Co-Founder"
[#]: via: "https://news.itsfoss.com/gitbutler/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

I Put GitButler To The Test: A New Kind of Git Client by GitHub's Co-Founder
======
A git client that provides a unique workflow. Is this something you were
looking for?
[![][1]][2]

Most of you might be familiar with Git. For those who aren't, it is one of the most popular version controls systems out there that has redefined how developers across the globe create and distribute software.

And, it's no surprise that open-source is at the core of it, pushing Git forward, while also enabling it to further the fundamental goals of FOSS thanks to its collaborative nature.

There's no doubt that there are plenty of GUI Git clients for Linux, such as [Gittyup][3], [gitg][4], [Guitar][5], etc.

But, there's a new Git client in town called **GitButler** , which aims to be different from the others with what it tries to accomplish with its feature set.

As the brainchild of GitHub Co-founder [Scott Chacon][6], GitButler is marketed as “ _a code concierge_ ” which can handle all your code like a dependable personal assistant.

So, let's see what's it all about.

🚧

This is a work in progress piece of software that's not recommended for production use.

### GitButler: Overview ⭐

Offered under a 2-year-long [Functional Source License][7] (FSL), GitButler is following this approach to avoid “[competitive risk][8]”, while also being open enough that individual users can easily take advantage of it, allowing them to fork the project, and build off it.

For developers, **GitButler serves as a Git client that allows them to work on multiple branches at the same time** , while also enabling them to refine their workflow with effortless file organization.

#### Key Features

In terms of what it can do, here are some notable highlights:

  * **It's cross-platform.**
  * **Stores project history.**
  * **Has generative AI capabilities.**
  * **Offers an intuitive branch workflow.**



There was even a [recent release][9] that brought about many improvements, like a lane-based commit view, undo timeline feature, advanced commit editing, new AI features, and more.

#### Initial Impressions 👨‍💻

I started off by installing the official AppImage on my Ubuntu 22.04.4 LTS system, and forked an existing GitHub project to test how the GitHub integration for GitButler worked.

For this test, I chose to go with [Dosage][10], a very useful medication tracker app. Of course, that's not mandatory, and you can use GitButler with other Git workflows.

Before we proceed, do keep in mind that I am a newbie when it comes to using [Git][11], and I may have made mistakes along the way. But, I tried my best to showcase what GitButler is capable of.

So, when I started up GitButler it showed me **a screen to opt-out of the various telemetry options** that it had.

![][12]

Subsequently, I created an account on GitButler just for checking things out, and linked my GitHub account to it. Remember, all of that is optional, no need to do it if you are privacy conscious.

![][13]

After that was done, it asked me to add a new project. So, I cloned [my fork][14] of Dosage into local storage and clicked on the “Add new project” button and added the folder to get started.

![][15]

It then asked me whether I wanted to enable GitButler features for taking advantage of automatic branch creation and AI-powered commit message generation.

I did enable that, but, one of those didn't pan out, more on that later.

![][16]

After the project was set, I was shown that everything was up-to-date on the base branch, and that any edits would automatically create a new [Virtual Branch][17].

![][18]

I then proceeded to make some minor changes to the README file using VS Code, and, to my surprise, there was **a GitButler integration** for it, which paved the way for what followed next.

![][19]

The changes I did show up on a newly created Virtual Branch, with an option to commit the changes to my repo with the ability to add a title and a message for it.

There was an option to use AI 🤖 to generate the commit message, but, it was greyed out.

I checked out the settings, and it turns out that the default option was OpenAI, with a GitButler API; _maybe that was not working?_

There were other options to choose from too. There was [Anthropic][20], and [Ollama][21], which can act as decent alternatives to OpenAI.

![][22]

To successfully commit a change, **I had to authenticate with GitHub** by using my username and a personal token. The screenshot above shows it in action, but, from a previous commit that I had made.

![][23]

After the commit was a success, I was able to create a new PR for merging the Virtual Branch into the repo from within GitButler itself. I merged it to the repo by using the “Merge pull request” button.

![][24]

As you can see above, every merge that I carried out was successful, and GitButler prompted me to merge into common base to bring it on par with the repository, at least that is what I think that was.

![][25]

This is [the result][26] of the final merge I did. GitButler even closed the PR for me, which, I think, is a pretty neat thing for it to do.

Overall, **GitButler did what I wanted it to do** , and I didn't really face any weird issues with it. Of course, I did not push any code-related changes using it, but, that's just my rusty coding skills hiding in the corner.

### 📥 Get GitButler

Currently, GitButler is offered for free to individual users, with plans to offer team-focused features aimed at enterprises in the near future. Before you get started, the [documentation][27] is a must-read.

Then, you can head to the [official website][28] to get the latest GitButler release for **Linux** , **Windows** , and **macOS**.

[GitButler][28]

If you are interested in contributing to the project, then you can refer to its [GitHub][29] repo.

_💬 I am excited to see such an innovative Git client. What about you? Know of anything similar?_

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/gitbutler/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://murmele.github.io/Gittyup/
[4]: https://flathub.org/apps/org.gnome.gitg
[5]: https://github.com/soramimi/Guitar
[6]: https://scottchacon.com/
[7]: https://fsl.software/
[8]: https://blog.gitbutler.com/opening-up-gitbutler/#:~:text=either%20taking%20on-,competitive%20risk,-or%20keeping%20it
[9]: https://blog.gitbutler.com/gitbutler-0-12-release/
[10]: https://news.itsfoss.com/dosage/
[11]: https://git-scm.com/
[12]: https://news.itsfoss.com/content/images/2024/06/GitButler_1.png
[13]: https://news.itsfoss.com/content/images/2024/06/GitButler_2.png
[14]: https://github.com/nova-666/Dosage-Fork-GitButler-Test
[15]: https://news.itsfoss.com/content/images/2024/06/GitButler_3.png
[16]: https://news.itsfoss.com/content/images/2024/06/GitButler_4.png
[17]: https://docs.gitbutler.com/features/virtual-branches
[18]: https://news.itsfoss.com/content/images/2024/06/GitButler_5.png
[19]: https://news.itsfoss.com/content/images/2024/06/GitButler_6.png
[20]: https://www.anthropic.com/
[21]: https://itsfoss.com/ollama-setup-linux/
[22]: https://news.itsfoss.com/content/images/2024/06/GitButler_7.png
[23]: https://news.itsfoss.com/content/images/2024/06/GitButler_8.png
[24]: https://news.itsfoss.com/content/images/2024/06/GitButler_9.png
[25]: https://news.itsfoss.com/content/images/2024/06/GitButler_10.png
[26]: https://github.com/nova-666/Dosage-Fork-GitButler-Test/pull/2
[27]: https://docs.gitbutler.com/
[28]: https://gitbutler.com/
[29]: https://github.com/gitbutlerapp/gitbutler
