[#]: subject: "How I am Using Git and Obsidian for Note Version Management"
[#]: via: "https://itsfoss.com/git-with-obsidian/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How I am Using Git and Obsidian for Note Version Management
======

[![Warp Terminal][1]][2]

Git is a powerful tool that helps you keep track of changes in your files over time. While it is highly popular among the developer community, you can use Git as a note storage vault.

In this case, the source files are [Obsidian][3] markdown files.

When you [use Obsidian for note-taking][4], Git can be very useful to manage different versions of your notes. You can easily go back to previous versions, undo mistakes, and even collaborate with others.

In this tutorial, I'll share how I set up Git with Obsidian on a Linux system, connect it with GitHub or GitLab, and use the Obsidian Git plugin to make version control simple and accessible right inside your notes app.

✋

****Non-FOSS Warning!**** Obsidian is not open source software. Although it is hugely popular among Linux users and that's why we have covered it here. If you want a similar open source application, [try Logseq][5].

This is all at the beginner level, where all you are doing is setting up Git for your knowledge base version management.

🚧

I am assuming you are taking simpler markdown notes, where individual note and file sizes are less. If you are using large notes, you may want to try GitHub Large File Storage, which is out of scope of this article.

### Step 1: Create a remote repository

📋

I am going to use GitHub in the examples here. If you use a [GitHub alternative repository][6] like GitLab, similar steps should also be valid.

Go to the GitHub official webpage and log in to your account. Now, on the profiles page, click on the "Create repository" button.

![Create a new repository][7]

Provide all the details. **Make sure you have set the repository to private**. Once you've entered the necessary details, click on the **Create Repository** button.

![Enter Details and Create][8]

That's it. You have a new private repository, which only you can access.

### Step 2: Create a simple README

You need to create a simple README file in the newly created repo. For this, click on the **Create a new file** button.

![Create a new file][9]

On the next page, enter the name of the file and add placeholder text.

![Enter file contents][10]

Click on **Commit changes** and add a message when asked. Done! You have added a simple README to your repo.

### Step 3: Install Git in your system

Now, let's install Git on your system. I also suggest installing the GitHub or GitLab CLI plugin. Since you are into version control, these CLI tools can greatly improve your experience.

💡

With the GitHub or GitLab CLI tool, you can commit and push changes to GitHub/GitLab from the terminal also, in case there is a failure in the Obsidian GUI.

In Ubuntu, you can install both Git and the GitHub CLI using the command:

```

    sudo apt install git gh

```

For Fedora, use:

```

    sudo dnf install git gh

```

For Arch Linux, the package name is a bit different.

```

    sudo pacman -S git github-cli

```

If you are using GitLab instead of GitHub, instead of the `gh/github-cli` package, install `glab` package. The name is the same on all three of the above Linux distributions.

### Step 4: Authenticate GitHub

Once you have Git and the GitHub tool installed, you need to authenticate it with user credentials.

First, you need to make sure the GitHub credentials are properly saved. For this, you can use `libsecret`.

```

    git config --global credential.helper libsecret

```

Now, let's set the username and email so that Git can understand who is committing changes. Open a terminal and run:

```

    git config --global user.name "your username"
    git config --global user.email "your email"

```

![Add username and email][11]

Run the GitHub CLI:

```

    gh auth login

```

If you are using GitLab, use:

```

    glab auth login

```

🚧

For the rest, I am using GitHub. So. GitLab users should follow their on-screen instructions.

It will ask some questions, and you can select a choice and press enter. This is shown in the screenshot below:

![Initial choices][12]

When you press enter, it will open in the browser. You will be prompted to continue as the logged in account.

![Continue website login][13]

On the next page, enter the code you are provided in the terminal.

![Enter the code][14]

This will ask you to verify the details before proceeding. Check once again and press **Authorize github**.

![Confirm login][15]

That's it. Your device is connected. Close the browser. You can view the terminal got updated with the successful login message.

![Device connection success][16]

### Step 5: Clone the repository

Now that you have set up GitHub, it's time to clone the private notes repo to somewhere convenient for you. I am cloning the repo on my `~/Documents` directory.

```

    cd ~/Documents
    git clone git clone https://your-git-remote-repo-link.git

```

You will get a message that you have cloned into an empty repo. This is what we need.

![Cloned the repository][17]

You can open it in file manager to see that the only content in the cloned directory is a `.git` directory and a README file.

### Step 6: Copy contents

Now, you have to copy your markdown notes from the earlier location to this new vault location. You can do this using your file manager.

While copying, **make sure that you copy the`.obsidian` folder as well**. Because your rest of plugins and settings are in the `.obsidian` directory.

The folder is hidden, so use `CTRL+H` to [enable the hidden items][18] and then select all.

![Copy all contents from existing vault][19]

### Step 7: Create a .gitignore

Once you copy all the contents to the new section, you will notice that you have a `.obsidian` folder that contains all the plugins and cache files.

Usually, this does not need to be pushed to GitHub. So, we will create a `.gitignore` file in the root vault location.

Inside this file, add the content:

```

    # to exclude Obsidian's settings (including plugin and hotkey configurations)
    .obsidian/

    # to only exclude plugin configuration. Might be useful to prevent some plugin from exposing sensitive data
    .obsidian/plugins

    # OR only to exclude workspace cache
    .obsidian/workspace.json

    # to exclude workspace cache specific to mobile devices
    .obsidian/workspace-mobile.json

    # Add below lines to exclude OS settings and caches
    .trash/
    .DS_Store

```

📋

The above `gitignore` code is directly taken from the git plugin documentation.

### Step 8: Open a new vault in Obsidian

Open Obsidian and click on your vault name in the bottom and select **Manage Vaults**.

![Select Manage][20]

From the new window, select the **open** button adjacent to "Open a folder as vault".

![Open an existing vault][21]

In the file chooser, select the directory you have cloned recently. A new Obsidian is opened with notes in the new location, which is empty as of now.

You will be asked to trust the author. This is because you have copied all the contents, including plugins, from previous notes. So, in order for the plugin to work, you need to enable the community plugins, and that needs user permission.

Accept that you trust the plugins and continue.

![Trust author][22]

### Step 9: Install the Obsidian Git Plugin

We need to [get plugins in Obsidian][23] for Git version control. Click on the settings button in Obsidian.

![Click on the settings button.][24]

Go to **Community plugins**. Click on browse. Here, search for the Git plugin and install it.

![Search and Install Git][25]

Once installed, enable it.

![Enable Git Plugin][26]

You have set the basics of Git with Obsidian. Click on the Git button in Obsidian to see the Git status.

![Obsidian Git Status][27]

As you can see, there is a `.gitignore` file under changes.

### Step 10: Stage changes

I suggest you stage changes in batches and commit. To stage a file, you can either press the `+` button adjacent to that file or use the `+` button on the top menu to stage all.

![Stage Changes][28]

Everything is under staged now for me:

![Stage everything][29]

### Step 11: Commit and Push

🚧

I am assuming you are the only one managing the notes, and there is no other collaborator.

If you are a solo user of your personal notes, then you can commit the changes and push them to the remote repository. For this, once all changes are staged, use the commit button.

![Commit all staged changes][30]

When commit is finished, use the Push button.

![Push Changes][31]

### Step 12: Pull Changes

Let's say you have edited the notes in another system and pushed the changes to GitHub from there. In this case, when you start on the original system, you should pull the item first from GitHub.

Use the Pull button in the Obsidian Git control panel.

![Pulled files from remote][32]

Now that your local copy is in sync with the main, you can work effortlessly.

### Wrapping Up

The Git plugin also allows you to automatically commit/pull/push at pre-defined times. But I prefer keeping things under my control and thus prefer following the manual method of handpicking my files.

But it's up to you how you want to go about it. Integrating Git with Obsidian is a great way of syncing your notes in the cloud without additional cost.

--------------------------------------------------------------------------------

via: https://itsfoss.com/git-with-obsidian/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://obsidian.md/
[4]: https://itsfoss.com/obsidian-tips/
[5]: https://itsfoss.com/logseq/
[6]: https://itsfoss.com/github-alternatives/
[7]: https://itsfoss.com/content/images/2025/09/create-a-new-repo-button-github.png
[8]: https://itsfoss.com/content/images/2025/09/create-a-new-private-repo-with-details.png
[9]: https://itsfoss.com/content/images/2025/09/create-an-new-file-readme.png
[10]: https://itsfoss.com/content/images/2025/09/enter-file-contents.png
[11]: https://itsfoss.com/content/images/2025/09/add-username-and-email.png
[12]: https://itsfoss.com/content/images/2025/09/login-1-github.png
[13]: https://itsfoss.com/content/images/2025/09/login-2-github-page.png
[14]: https://itsfoss.com/content/images/2025/09/login-3-enter-code.png
[15]: https://itsfoss.com/content/images/2025/09/login-4-confirm-login.png
[16]: https://itsfoss.com/content/images/2025/09/login-6-connection-success.png
[17]: https://itsfoss.com/content/images/2025/09/clone-notes-repo-new.png
[18]: https://itsfoss.com/show-hidden-files-linux/
[19]: https://itsfoss.com/content/images/2025/09/copy-all-contents.png
[20]: https://itsfoss.com/content/images/2025/09/click-on-vault-and-select-manage.png
[21]: https://itsfoss.com/content/images/2025/09/select-open-a-existing-vault.png
[22]: https://itsfoss.com/content/images/2025/09/trust-author-and-enable-plugin.png
[23]: https://itsfoss.com/obsidian-use-plugin/
[24]: https://itsfoss.com/content/images/2025/09/click-on-settings-obsidian.png
[25]: https://itsfoss.com/content/images/2025/09/search-and-install-git.png
[26]: https://itsfoss.com/content/images/2025/09/enable-git-plugin.png
[27]: https://itsfoss.com/content/images/2025/09/obsidian-with-gitignore.png
[28]: https://itsfoss.com/content/images/2025/09/stage-changes.png
[29]: https://itsfoss.com/content/images/2025/09/everything-is-under-staged.png
[30]: https://itsfoss.com/content/images/2025/09/commit-all-staged.png
[31]: https://itsfoss.com/content/images/2025/09/push-change.png
[32]: https://itsfoss.com/content/images/2025/09/pulled-files-from-repo.png
