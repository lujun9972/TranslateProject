[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (5 modern alternatives to essential Linux command-line tools)
[#]: via: (https://opensource.com/article/20/6/modern-linux-command-line-tools)
[#]: author: (Ricardo Gerardi https://opensource.com/users/rgerardi)

5 modern alternatives to essential Linux command-line tools
======
Gain new benefits by improving your old command-line tools with updated
alternatives.
![Person using a laptop][1]

In our daily use of Linux/Unix systems, we use many command-line tools to complete our work and to understand and manage our systems—tools like `du` to monitor disk utilization and `top` to show system resources. Some of these tools have existed for a long time. For example, `top` was first released in 1984, while `du`'s first release dates to 1971.

Over the years, these tools have been modernized and ported to different systems, but, in general, they still follow their original idea, look, and feel.

These are great tools and essential to many system administrators' workflows. However, in recent years, the open source community has developed alternative tools that offer additional benefits. Some are just eye candy, but others greatly improve usability, making them a great choice to use on modern systems. These include the following five alternatives to the standard Linux command-line tools.

### 1\. ncdu as a replacement for du

The NCurses Disk Usage (`ncdu`) tool provides similar results to `du` but in a curses-based, interactive interface that focuses on the directories that consume most of your disk space.

`ncdu` spends some time analyzing the disk, then displays the results sorted by your most used directories or files, like this:


```
ncdu 1.14.2 ~ Use the arrow keys to navigate, press ? for help
\--- /home/rgerardi ------------------------------------------------------------
   96.7 GiB [##########] /libvirt
   33.9 GiB [###       ] /.crc
    7.0 GiB [          ] /Projects
.   4.7 GiB [          ] /Downloads
.   3.9 GiB [          ] /.local
    2.5 GiB [          ] /.minishift
    2.4 GiB [          ] /.vagrant.d
.   1.9 GiB [          ] /.config
.   1.8 GiB [          ] /.cache
    1.7 GiB [          ] /Videos
    1.1 GiB [          ] /go
  692.6 MiB [          ] /Documents
. 591.5 MiB [          ] /tmp
  139.2 MiB [          ] /.var
  104.4 MiB [          ] /.oh-my-zsh
   82.0 MiB [          ] /scripts
   55.8 MiB [          ] /.mozilla
   54.6 MiB [          ] /.kube
   41.8 MiB [          ] /.vim
   31.5 MiB [          ] /.ansible
   31.3 MiB [          ] /.gem
   26.5 MiB [          ] /.VIM_UNDO_FILES
   15.3 MiB [          ] /Personal
    2.6 MiB [          ]  .ansible_module_generated
    1.4 MiB [          ] /backgrounds
  944.0 KiB [          ] /Pictures
  644.0 KiB [          ]  .zsh_history
  536.0 KiB [          ] /.ansible_async
 Total disk usage: 159.4 GiB  Apparent size: 280.8 GiB  Items: 561540
```

Navigate to each entry by using the arrow keys. If you press **Enter** on a directory entry, `ncdu` displays the contents of that directory:


```
\--- /home/rgerardi/libvirt ----------------------------------------------------
                         /..
   91.3 GiB [##########] /images
    5.3 GiB [          ] /media
```

You can use that to drill down into the directories and find which files are consuming the most disk space. Return to the previous directory by using the **Left** arrow key. By default, you can delete files with `ncdu` by pressing the **d** key, and it asks for confirmation before deleting a file. If you want to disable this behavior to prevent accidents, use the `-r` option for read-only access: `ncdu -r`.

`ncdu` is available for many platforms and Linux distributions. For example, you can use `dnf` to install it on Fedora directly from the official repositories:


```
`$ sudo dnf install ncdu`
```

You can find more information about this tool on the [`ncdu` web page][2].

### 2\. htop as a replacement for top

`htop` is an interactive process viewer similar to `top` but that provides a nicer user experience out of the box. By default, `htop` displays the same metrics as `top` in a pleasant and colorful display.

By default, `htop` looks like this:

![htop screen][3]

(Ricardo Gerardi, [CC BY-SA 4.0][4])

In contrast to default `top`:

![top screen][5]

(Ricardo Gerardi, [CC BY-SA 4.0][4])

In addition, `htop` provides system overview information at the top and a command bar at the bottom to trigger commands using the function keys, and you can customize it by pressing **F2** to enter the setup screen. In setup, you can change its colors, add or remove metrics, or change display options for the overview bar.

While you can configure recent versions of `top` to achieve similar results, `htop` provides saner default configurations, which makes it a nice and easy to use process viewer.

To learn more about this project, check the [`htop` home page][6].

### 3\. tldr as a replacement for man

The `tldr` command-line tool displays simplified command utilization information, mostly including examples. It works as a client for the community [tldr pages project][7].

This tool is not a replacement for `man`. The man pages are still the canonical and complete source of information for many tools. However, in some cases, `man` is too much. Sometimes you don't need all that information about a command; you're just trying to remember the basic options. For example, the man page for the `curl` command has almost 3,000 lines. In contrast, the `tldr` for `curl` is 40 lines long and looks like this:


```
$ tldr curl

# curl
  Transfers data from or to a server.
  Supports most protocols, including HTTP, FTP, and POP3.
  More information: &lt;[https://curl.haxx.se\&gt;][8].

\- Download the contents of an URL to a file:

  curl <http://example.com> -o filename

\- Download a file, saving the output under the filename indicated by the URL:

  curl -O <http://example.com/filename>

\- Download a file, following [L]ocation redirects, and automatically [C]ontinuing (resuming) a previous file transfer:

  curl -O -L -C - <http://example.com/filename>

\- Send form-encoded data (POST request of type `application/x-www-form-urlencoded`):

  curl -d 'name=bob' <http://example.com/form>                                                                                            
\- Send a request with an extra header, using a custom HTTP method:

  curl -H 'X-My-Header: 123' -X PUT <http://example.com>                                                                                  
\- Send data in JSON format, specifying the appropriate content-type header:

  curl -d '{"name":"bob"}' -H 'Content-Type: application/json' <http://example.com/users/1234>

... TRUNCATED OUTPUT
```

TLDR stands for "too long; didn't read," which is internet slang for a summary of long text. The name is appropriate for this tool because man pages, while useful, are sometimes just too long.

In Fedora, the `tldr` client was written in Python. You can install it using `dnf`. For other client options, consult the [tldr pages project][7].

In general, the `tldr` tool requires access to the internet to consult the tldr pages. The Python client in Fedora allows you to download and cache these pages for offline access.

For more information on `tldr`, you can use `tldr tldr`.

### 4\. jq as a replacement for sed/grep for JSON

`jq` is a command-line JSON processor. It's like `sed` or `grep` but specifically designed to deal with JSON data. If you're a developer or system administrator who uses JSON in your daily tasks, this is an essential tool in your toolbox.

The main benefit of `jq` over generic text-processing tools like `grep` and `sed` is that it understands the JSON data structure, allowing you to create complex queries with a single expression.

To illustrate, imagine you're trying to find the name of the containers in this JSON file:


```
{
  "apiVersion": "v1",
  "kind": "Pod",
  "metadata": {
    "labels": {
      "app": "myapp"
    },
    "name": "myapp",
    "namespace": "project1"
  },
  "spec": {
    "containers": [
      {
        "command": [
          "sleep",
          "3000"
        ],
        "image": "busybox",
        "imagePullPolicy": "IfNotPresent",
        "name": "busybox"
      },
      {
        "name": "nginx",
        "image": "nginx",
        "resources": {},
        "imagePullPolicy": "IfNotPresent"
      }
    ],
    "restartPolicy": "Never"
  }
}
```

If you try to `grep` directly for `name`, this is the result:


```
$ grep name k8s-pod.json
        "name": "myapp",
        "namespace": "project1"
                "name": "busybox"
                "name": "nginx",
```

`grep` returned all lines that contain the word `name`. You can add a few more options to `grep` to restrict it and, with some regular-expression manipulation, you can find the names of the containers. To obtain the result you want with `jq`, use an expression that simulates navigating down the data structure, like this:


```
$ jq '.spec.containers[].name' k8s-pod.json
"busybox"
"nginx"
```

This command gives you the name of both containers. If you're looking for only the name of the second container, add the array element index to the expression:


```
$ jq '.spec.containers[1].name' k8s-pod.json
"nginx"
```

Because `jq` is aware of the data structure, it provides the same results even if the file format changes slightly. `grep` and `sed` may provide different results with small changes to the format.

`jq` has many features, and covering them all would require another article. For more information, consult the [`jq` project page][9], the man pages, or `tldr jq`.

### 5\. fd as a replacement for find

`fd` is a simple and fast alternative to the `find` command. It does not aim to replace the complete functionality `find` provides; instead, it provides some sane defaults that help a lot in certain scenarios.

For example, when searching for source-code files in a directory that contains a Git repository, `fd` automatically excludes hidden files and directories, including the `.git` directory, as well as ignoring patterns from the `.gitignore` file. In general, it provides faster searches with more relevant results on the first try.

By default, `fd` runs a case-insensitive pattern search in the current directory with colored output. The same search using `find` requires you to provide additional command-line parameters. For example, to search all markdown files (`.md` or `.MD`) in the current directory, the `find` command is this:


```
`$ find . -iname "*.md"`
```

Here is the same search with `fd`:


```
`$ fd .md`
```

In some cases, `fd` requires additional options; for example, if you want to include hidden files and directories, you must use the option `-H`, while this is not required in `find`.

`fd` is available for many Linux distributions. Install it in Fedora using the standard repositories:


```
`$ sudo dnf install fd-find`
```

For more information, consult the [`fd` GitHub repository][10].

### Great alternatives alongside proven utilities

While I still use all the old essential tools regularly, especially when connecting remotely to servers, the alternative tools provide some extra benefits that are valuable in many scenarios. They particularly help me manage and work on my Linux desktop and laptop machines.

Do you use any other tools that help your workflow? Add them in the comments section below.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/6/modern-linux-command-line-tools

作者：[Ricardo Gerardi][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/rgerardi
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/laptop_screen_desk_work_chat_text.png?itok=UXqIDRDD (Person using a laptop)
[2]: https://dev.yorhel.nl/ncdu
[3]: https://opensource.com/sites/default/files/uploads/htop_small.png (htop screen)
[4]: https://creativecommons.org/licenses/by-sa/4.0/
[5]: https://opensource.com/sites/default/files/uploads/top_small.png (top screen)
[6]: https://hisham.hm/htop/
[7]: https://tldr.sh/
[8]: https://curl.haxx.se\>
[9]: https://stedolan.github.io/jq/
[10]: https://github.com/sharkdp/fd/
