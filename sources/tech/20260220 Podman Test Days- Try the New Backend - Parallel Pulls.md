[#]: subject: "Podman Test Days: Try the New Backend & Parallel Pulls"
[#]: via: "https://fedoramagazine.org/podman-test-days-try-the-new-backend-parallel-pulls/"
[#]: author: "Petr Sklenar https://fedoramagazine.org/author/psklenar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Podman Test Days: Try the New Backend & Parallel Pulls
======

![][1]

The Podman team and the Fedora Quality Assurance team are organizing a **Test Week from Friday, February 27 through Friday, March 6, 2026**. This is your chance to get an early look at the latest improvements coming to Podman and see how they perform on your machine.

### What is Podman?

For those new to the tool, [Podman][2] is a daemonless, Linux-native engine for running, building, and sharing OCI containers. It offers a familiar command-line experience but runs containers safely without requiring a root daemon.

### What’s Coming in Podman 5.8?

The upcoming release includes updates designed to make Podman faster and more robust. Here is what you can look forward to, and what you can try out during this Fedora Test Day.

#### A Modern Database Backend (SQLite)

Podman is upgrading its internal storage logic by transitioning to **SQLite**. This change modernizes how Podman handles data under the hood, aiming for better stability and long-term robustness.

#### Faster Parallel Pulls

This release brings optimizations to how Podman downloads image layers, specifically when pulling multiple images at the same time. For a deep dive into the engineering behind this, check out the developer blog post on [Accelerating Parallel Layer Creation][3].

**Experiment and Explore:** Feel free to push the system a bit and try pulling several large images simultaneously to see if you notice the performance boost. Beyond that, please **bring your own workflows**. Don’t just follow the wiki instructions. Run the containers and commands you use daily. **Your specific use cases are the best way to uncover edge cases that standard tests might miss.**

### What do I need to do?

  * Make sure you have a [Fedora Account][4] (FAS).
  * Download test materials in advance where applicable, which may include some large files.
  * Follow the steps on the wiki test page one by one.
  * Send us your results through the app.



Details on how to test and report results are available at the Wiki Test Day site for **Podman 5.8 test day:**
<https://fedoraproject.org/wiki/Test_Day:2026-02-27_Podman_5.8>

**Test Week runs from Friday, February 27 through Friday, March 6, 2026**

Thank you for taking part in the testing of Fedora Linux 44!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/podman-test-days-try-the-new-backend-parallel-pulls/

作者：[Petr Sklenar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/psklenar/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/01/Test_Days-816x345.jpg
[2]: https://docs.podman.io
[3]: https://blog.podman.io/2025/12/accelerating-parallel-layer-creation/
[4]: https://accounts.fedoraproject.org/
