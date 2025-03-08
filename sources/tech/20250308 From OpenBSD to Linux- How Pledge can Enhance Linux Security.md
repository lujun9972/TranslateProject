[#]: subject: "From OpenBSD to Linux: How Pledge can Enhance Linux Security"
[#]: via: "https://itsfoss.com/pledge-linux-port/"
[#]: author: "Community https://itsfoss.com/author/community/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

From OpenBSD to Linux: How Pledge can Enhance Linux Security
======

[![Warp Terminal][1]][2]

Imagine a scenario, you downloaded a new binary called _ls_ from the internet. The application could be malicious by intention. Binary files are difficult to trust and run over the system. It could lead to a system hijacking attack, sending your sensitive files and clipboard information to the malicious server or interfere with the existing process of your machine.

Won’t it be great if you’ve the tool to run and test the application within the defined security parameter. Like, we all know, ls command list the files in the current working directory. So, why would it require a network connection to operate? Does it make sense?

That’s where the tool, Pledge, comes in. Pledge restricts the system calls a program can make. Pledge is natively supported on OpenBSD systems. Although it isn’t officially supported on Linux systems, I’ll show you a cool hack to utilize pledge on your Linux systems.

🚧

As you can see, this is rather an advanced tool for sysadmins, network engineers and people in the network security field. Most desktop Linux users would not need something like this but that does not mean you cannot explore it out of curiosity.

### What makes this port possible?

Thanks to the remarkable work done by [Justine Tunney][3]. She is the core developer behind the project- [Cosmopolitan Libc][4].

Cosmopolitan makes it a bridge for compiling a **c programs** for 7 different platforms (Linux + Mac + Windows + FreeBSD + OpenBSD 7.3 + NetBSD + BIOS) at one go.

Utilizing Libc Cosmopolitan, she was able to port OpenBSD Pledge to the Linux system. Here's the [nice blog done by her][5].

📋

****A quick disclaimer**** : Just because you can compile a C program for 7 different platforms doesn’t mean you would be able to successfully run on all these platforms. You need to handle program dependencies as well. For instance, Iptables uses Linux sockets, so you can’t expect it to work magically on Windows systems unless you come up with a way to establish Linux socket networking to Windows.

### Restrict system calls() with Pledge

You might be surprised to know one single binary can run on 7 different platforms - Windows, Linux, Mac, FreeBSD, OpenBSD, NetBSD and BIOS.

These binary files are called [**Actually Portable Executable**][6] **(APE).** You can [check out this blog for more information][6]. These binary files have the _.com_ suffix and it’s necessary to work.

This guide will show how to use `pledge.com` binary on your Linux system to restrict system calls while launching any binaries or applications.

#### Step 1: Download pledge.com

You can download pledge-1.8.com from the url- <http://justine.lol/pledge/pledge-1.8.com>.

You can rename the file `pledge-1.8.com` to `pledge.com`.

#### Step 2: Make it executable

Run this command to make it executable.

```

    chmod +x ./pledge.com

```

#### Step 3: Add pledge.com to the path

A quick way to accomplish this is to move the binary in standard `/usr/local/bin/` location.

```

    sudo mv ./pledge.com /usr/local/bin

```

#### Step 4: Run and test

```

    pledge.com curl http://itsfoss.com

```

I didn’t assign any permission (called promises) to it so it would fail as expected. But it gives us a hint on what system calls are required by the binary ‘curl’ when it is run.

![][7]

With this information, you can see if a program is requesting a system call that it should not. For example, a file explorer program asking for dns. Is it normal?

Curl is a tool that deals with URLs and indeed requires those system calls.

Let's assign promises using the `-p` flag. I'll explain what each of these promises does in the next section.

```

    pledge.com -p 'stdio rpath inet dns tty sendfd recvfd' \
    curl -s http://itsfoss.com

```

![][8]

📋

The debug message _****error:pledge inet for socket****_ is mis-leading. Even a similar open [issue exists][9] at the project's GitHub repo. It is evident that after providing these sets of promises _****"stdio rpath inet dns tty sendfd recvfd"****_ to our curl binary, it works as expected.

It’s successfully redirecting to the https version of our website. Let’s try to see, if with the same set of promises, it can talk to https enabled websites or not.

```

    pledge.com -p 'stdio rpath inet dns tty sendfd recvfd' \
    curl -s https://itsfoss.com

```

![][10]

Yeah! It worked.

### A quick glance at promises

In the above section, we used 7 promises to make our curl request successful. Here’s a quick glimpse into what each promises intended for:

  * stdio: Allows reading and writing to standard input/output (like printing to the console).
  * rpath: Allows reading files from the filesystem.
  * inet: Allows network-related operations (for example, connecting to a server).
  * dns: Allows resolving DNS queries.
  * tty: Allows access to the terminal.
  * sendfd: Allow sending file descriptors.
  * recvfd: Allow received file descriptors



To know what other promises are supported by the pledge binary, [head over to this blog][11].

![][12]

### Conclusion

OpenBSD’s pledge follows the Least Privilege model. It prevents programs from mis-utilizing system resources. Following this security model, the damage done by a malicious application can be quite limited. Although Linux has [seccomp][13] and apparmor in its security arsenal, I find pledge more intuitive and easy to use.

With Actually Portable Executable (APE), Linux users can now enjoy the simplicity of pledge to make their systems more secure. Users can provide more granular control over what processes can do within these environments would add an extra layer of defense.

#### Author Info

![][14]

Bhuwan Mishra is a Fullstack developer, with Python and Go as his tools of choice. He takes pride in building and securing web applications, APIs, and CI/CD pipelines, as well as tuning servers for optimal performance. He also has passion for working with Kubernetes.

--------------------------------------------------------------------------------

via: https://itsfoss.com/pledge-linux-port/

作者：[Community][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/community/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/jart
[4]: https://justine.lol/cosmopolitan/index.html
[5]: https://justine.lol/pledge/
[6]: https://justine.lol/ape.html
[7]: https://itsfoss.com/content/images/2025/02/pledge-with-curl-1.png
[8]: https://itsfoss.com/content/images/2025/02/pledge-with-curl-2.png
[9]: https://github.com/jart/pledge/issues/6
[10]: https://itsfoss.com/content/images/2025/02/pledge-with-curl-3.png
[11]: https://justine.lol/pledge/#promises
[12]: https://itsfoss.com/content/images/icon/apple-touch-icon.png
[13]: https://man7.org/linux/man-pages/man2/seccomp.2.html
[14]: https://itsfoss.com/content/images/2025/03/bhuwan.png
