[#]: subject: "Full Steam Ahead with RISC-V and Fedora Linux 42"
[#]: via: "https://fedoramagazine.org/full-steam-ahead-with-risc-v-and-fedora-linux-42/"
[#]: author: "Neil Hanlon https://fedoramagazine.org/author/neil/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Full Steam Ahead with RISC-V and Fedora Linux 42
======

![][1]

Photo by [Tommy L][2] on [Unsplash][3]

The Fedora RISC-V SIG is excited to share that our RISC-V images for Fedora Linux 42 have landed on-time and without delay! If you’ve been watching our progress over the past few releases, you know that staying on schedule is a big deal, especially given our goals of eventually gaining “primary” status for RISC-V as an available Fedora Linux architecture. Previous RISC-V builds of Fedora Linux were released with a small delay compared to the other architectures, but with Fedora Linux 42, we’re right on track.

Today, we’re announcing the general availability of pre-built Fedora Linux 42 images for all our supported boards, QEMU, and container images. You can read more about these images in our [previous post][4] and under the [Hardware][5] section of the RISC-V team’s wiki. These **non-official** images are brought to you by the Fedora RISC-V Community.

### Big Improvements, Smaller Numbers

Behind the scenes, the data tells an even more exciting story.

One way to measure and compare our efforts over time is by analyzing the number of “unresolved dependencies” in the build root. When a package is built, it typically has access to a repository containing every package built for that Fedora release–we call this the build root. Running the dnf repoclosure procedure against this buildroot by itself allows us to quantify the number of dependencies that are being fulfilled for a given build using a package built for a previous Fedora release.

  * In Fedora Linux 40, the RISC-V buildroot had over **6,900** unresolved dependencies.


  * Fedora Linux 41 slashed that nearly in half to around **3,800**.


  * Now, with Fedora Linux 42, we’re down to just **357** unresolved dependencies across 126 packages.



In other words, there are now only 357 subpackages from 126 packages in the RISC-V Koji which were not built directly for Fedora Linux 42 — a nearly 95% decrease in just one year.

That’s not just progress — it’s momentum.

These numbers represent the steady roll toward a complete and clean buildroot for RISC-V in Fedora. Every fix, every patch, and every accepted change brings us closer.

### Upstream, Together

Our upstreaming work continues apace, and we want to acknowledge that none of this progress would be possible without the incredible collaboration from maintainers across the Fedora Project and beyond. Thank you to everyone who reviewed, accepted, merged, and built our patches. Your support makes this architecture possible.

We’re also excited about just how many packages build cleanly without special treatment or overlay repositories that need to be cared for. RISC-V is becoming just another architecture, and that’s exactly how it should be.

### Get Involved

If you’ve got RISC-V hardware (or want to try it out via QEMU), there’s never been a better time to jump aboard the RISC-V train. Install the image, test your favorite packages, file bugs, and drop by [the RISC-V Matrix channel][6] to help us keep this locomotive rolling down the tracks.

Check out [the RISC-V wiki page][7] for more information, and we hope to see you on Matrix and helping us shape the future of Fedora Linux on open hardware.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/full-steam-ahead-with-risc-v-and-fedora-linux-42/

作者：[Neil Hanlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/neil/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/04/risc-v-2-816x345.jpg
[2]: https://unsplash.com/@0x746f6d6d796a746c?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-close-up-of-a-computer-chip-l7fpTjm3ZOQ?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/risc-v-and-fedora-all-aboard/)
[5]: https://fedoraproject.org/wiki/Architectures/RISC-V/Hardware
[6]: https://matrix.to/#/#risc-v:fedoraproject.org
[7]: https://fedoraproject.org/wiki/Architectures/RISC-V
