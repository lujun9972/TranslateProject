[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Set up a Wekan kanban server on Linux)
[#]: via: (https://opensource.com/article/20/9/linux-wekan)
[#]: author: (Srujan Gudisa https://opensource.com/users/srujangudisaicloudcom)

Set up a Wekan kanban server on Linux
======
Manage your projects with an open source kanban application.
![two women kanban brainstorming and brainmapping with post-it notes on a whiteboard ][1]

[Wekan][2] is an open source kanban board application that allows you to manage your daily tasks with (virtual) cards. You can create boards and cards and move them between columns as you make progress on each task. You can also add people who work with you to the tasks on the board. Like other kanban tools, Wekan also allows you to use colored labels on cards to facilitate grouping, filtering, and assigning them to specific people. Because Wekan is open source (distributed under an MIT License), it's easy to modify and use.

This article demonstrates how to install Wekan on a Linux computer to create a Kanban project management server. These instructions use [Fedora][3], but they also work for any Linux distribution with minor changes for the different package managers.

### 1\. Install a web server

Wekan is a web-based tool, so you must have a web server installed to run it. While you can use any open source web server, I use [Nginx][4] because I think it's easy to install and configure. Install it with:


```
`$ sudo dnf install nginx`
```

### 2\. Enable and start the web server

Enable your web server services at boot, so you don't have to start the service every time you restart your computer. To enable and start the Nginx service, use `systemctl`:


```
`$ sudo systemctl enable --now nginx`
```

### 3\. Install the snap command

There are two ways to build Wekan: from source or using Snap. Building it from source code requires several dependencies and a lot of configuration. It's easier to install a prepared package with the `snap` command. Install Snap with:


```
`$ sudo dnf install snapd`
```

On Fedora, Snap requires you to create a manual symlink:


```
`$ sudo ln -s /var/lib/snapd/snap /snap`
```

Check your Snap version using `snap version` to confirm it is properly installed.

Restart your computer to ensure Snap detects the libraries.

### 4\. Install Wekan

Now you're ready to install Wekan. Do this with `snap` rather than `dnf`:


```
`$ sudo snap install wekan`
```

### 5\. Set the port number

A port number is needed to access Wekan through your browser. Set a port number to one that isn't in use. You can use whatever port you want—I use port 3001—but don't use a common one, like 22, 25, 443, 80, etc. You can find a full list of ports and what's expected to run on them on this [Internet Assigned Numbers Authority page][5]. (Although port 3001 is reserved, it's for a service I don't ever anticipate running, so you can use your best judgment.)


```
`$ sudo snap set wekan port='3001'`
```

### 6\. Assign the URL

If you're installing Wekan on a server that you want to access remotely, you must set the internet protocol (IP) address that Wekan will run on:


```
$ sudo snap set wekan \
root_url="http://&lt;Ip Address of Server&gt;"
```

### 7\. Restart the Wekan services

Wekan currently uses the MongoDB database to store data. MongoDB's license is not OSI-approved, although MongoDB asserts it is a valid copyleft license. You can read more about this debate on the [OSI licensing mailing list][6] and draw your own conclusions. Work is being done to [permit other databases in Wekan][7].

For now, MongoDB is what's available, so start it, and then restart Wekan:


```
$ sudo systemctl restart snap.wekan.mongodb
$ sudo systemctl restart snap.wekan.wekan
```

### 8\. Access Wekan

Open a browser and navigate to `http://localhost:3001` or `http://<ip address of server>:3001`.

![Wekan login/registration page][8]

(Srujan Gudisa, [CC BY-SA 4.0][9])

If you are logging in for the first time, click on **Register**, and you will see the **Create an Account** page.

![Wekan create registration page][10]

(Srujan Gudisa, [CC BY-SA 4.0][9])

Complete the information and click on **Register**. You may get an error; don't worry, just ignore it.

Click the **Sign In** link, and you'll see the sign-in page again. Enter the information you used for registration to log in and get started.

### 9\. Start creating your boards

Use the user interface to set up boards to start using the software.

![Wekan create board][11]

(Srujan Gudisa, [CC BY-SA 4.0][9])

If you have any boards from other kanban software like Trello, you can import them into Wekan.

  1. Click on the **+** sign at the top of the Menu bar.

  2. Click **Import**.

![Wekan create/import board page][12]

(Srujan Gudisa, [CC BY-SA 4.0][9])

  3. Follow the instructions to import your data.

![Wekan import board screen][13]

(Srujan Gudisa, [CC BY-SA 4.0][9])




I hope you find this information useful and it helps you manage your projects more easily—while leveraging the power of open source.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/9/linux-wekan

作者：[Srujan Gudisa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/srujangudisaicloudcom
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/whiteboard-brainstorming-brainmapping-design-thinking-postits-kanban.png?itok=Is2Tg1Jk (Brainstorming with post-it notes on a whiteboard)
[2]: https://wekan.github.io/
[3]: http://getfedora.org/
[4]: https://www.nginx.com/
[5]: https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml
[6]: http://lists.opensource.org/pipermail/license-review_lists.opensource.org/2019-March/003989.html
[7]: https://github.com/wekan/wekan/issues/787
[8]: https://opensource.com/sites/default/files/uploads/wekan-login.png (Wekan login/registration page)
[9]: https://creativecommons.org/licenses/by-sa/4.0/
[10]: https://opensource.com/sites/default/files/uploads/wekan_create-account.png (Wekan create registration page)
[11]: https://opensource.com/sites/default/files/uploads/wekan_add-board.png (Wekan create board)
[12]: https://opensource.com/sites/default/files/uploads/wekan_create-board.png (Wekan create/import board page)
[13]: https://opensource.com/sites/default/files/uploads/wekan_import-board.png (Wekan import board screen)
