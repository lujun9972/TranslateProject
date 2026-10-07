[#]: subject: "Podman Test Week: Help test the Rust-based conmon v3"
[#]: via: "https://fedoramagazine.org/podman-test-week-help-test-the-rust-based-conmon-v3/"
[#]: author: "Petr Sklenar https://fedoramagazine.org/author/psklenar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Podman Test Week: Help test the Rust-based conmon v3
======

![][1]

The Podman and Fedora Quality teams are organizing a test week from **Monday, October 12, through Sunday, October 18, 2026**. We want your help testing conmon v3, the Rust-based container monitor used with Podman. If you use Podman, try the same containers and commands with conmon v3 and report any differences.

### Why we’re testing conmon v3

Conmon is the small process that keeps watching a container after the Podman command that started it has finished. Podman uses an [OCI runtime][2] such as [crun][3] or [runc][4] to start the container; conmon attaches to its input and output, provides the connection for podman attach, collects logs, and records its exit status.

Conmon v3 replaces the C implementation with a Rust version. This helps prevent common memory errors in safe code. It also gives the logging backends a shared interface, making them easier to extend and test.

We already run Podman’s system tests against conmon v3. Now we’d like help checking development containers, interactive sessions, and Quadlet services on other people’s setups.

### Getting started

We’ve prepared a [test week wiki page][5] with setup instructions, links to the test cases, and information on reporting results. Start there to check the Fedora and package requirements, then use a test machine or VM with no important data.

Install the new monitor with this command:

```

    sudo dnf install conmon-v3

```

To select it system-wide, create _/etc/containers/containers.conf.d/99-conmon-v3.conf_ with the following content:

```

    [engine]
     conmon_path = ["/usr/bin/conmon-v3"]

```

Run _podman info_ and check that the conmon path is _/usr/bin/conmon-v3_ and its version starts with _3_. If you use both rootless and rootful Podman, check _sudo podman info_ as well. User configuration can override the system setting.

Start new test containers after making this change. Containers that are already running retain their existing monitor.

To switch back after testing, remove the drop-in. New containers will then use your previous configuration.

### What to test

Here are the areas we’d particularly like you to check:

  * Open an interactive shell, resize the terminal, and detach and attach again.
  * Run _podman exec_ , including interactive commands, and check the output and exit status.
  * Check file and journald logs with large output and lines without a final newline.
  * Start, stop, and restart containers, including services managed by Quadlet or systemd.
  * Try rootless or rootful Podman, and crun or runc where available.



Watch for hangs, missing output, incorrect exit statuses, unexpected CPU usage, or behaviour that differs from conmon v2. The [wiki][5] links to the test cases, which include the conmon-specific checks.

### Results and help

Record your results in the [test day application][6]. Please record successful tests too. They tell us which setups have been checked.

Report conmon problems in the [conmon v3 issue tracker][7]. For other Podman issues, follow the bug-reporting instructions on the [wiki page][5]. Include your Fedora version, relevant package versions, reproduction steps, relevant logs, and the output of this command:

```

    podman info --debug

```

Link the bug report when submitting your test result.

For help with testing or reporting a problem, join us on Matrix in [#podman:fedoraproject.org][8].

* * *

_This article was co-written by Petr Sklenar and Jan Kaluza._

_Note about AI usage: **:** The core technical content and claims are completely our own. Claude (Anthropic) was used only as an editing tool to enhance grammar and readability._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/podman-test-week-help-test-the-rust-based-conmon-v3/

作者：[Petr Sklenar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/psklenar/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/podman-2-816x389.jpg
[2]: https://github.com/opencontainers/runtime-spec
[3]: https://github.com/containers/crun/blob/main/crun.1.md
[4]: https://github.com/opencontainers/runc/releases
[5]: https://fedoraproject.org/wiki/Test_Day:2026-10-12_Podman_Conmon-v3
[6]: https://testdays.fedoraproject.org/testday/29
[7]: https://github.com/containers/conmon-v3/issues
[8]: https://chat.fedoraproject.org/#/room/#podman:fedoraproject.org
