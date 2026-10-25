[#]: subject: "This Newly Proposed Linux Filesystem Can Fix Corrupted Data"
[#]: via: "https://itsfoss.com/news/beamfs-linux-filesystem-proposal/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

This Newly Proposed Linux Filesystem Can Fix Corrupted Data
======

[![Warp Terminal][1]][2]

The kernel's filesystem mailing list has received an 18-patch proposal this week from [Aurelien Desbrieres][3], the creator of [BeamFS][4]. It takes the place of FTRFS, an earlier filesystem he had proposed back in April.

Aurelien says he used Anthropic's Claude to write the code, the tool that checks the patches, and [the cover letter][5].

He also points out that every patch carries an `Assisted-by` tag. You might remember that is the disclosure the kernel's [AI coding assistants policy][6] asks for. The same policy keeps the human submitter responsible for the code.

### How does it fix data?

![][7]

Filesystems that can repair damage, like _Btrfs_ and _ZFS_ , usually do it by falling back on a spare copy of the data. BeamFS skips that and stores [Reed-Solomon][8] error-correcting codes inside every block.

Every read gets checked against those codes, and small amounts of damage are corrected before the data reaches the application. If the filesystem can tell the damage is beyond repair, the read fails with an error instead of returning the wrong bytes.

The idea started with satellite computers. They keep data on a single drive and cannot fit a second copy. The same case is made for radiotherapy rooms.

[Neutrons][9] from treatment machines can flip bits in the computers there, including the ones handling imaging and records. Aurelien argues a silently wrong byte does more damage in that setting than a failed read.

**BeamFS has not been tested in a real radiation environment yet**. The tests done so far simulated the damage by flipping single bits in data as it was read on virtual machines and USB flash drives.

In his [technical report][10], _ext4_ and _ext3_ returned wrong data without any error, while _Btrfs_ refused to read the file. BeamFS returned the correct file every time except once, when a flip hit a pointer to the file’s data and it refused the read.

Do keep in mind that the comparison is uneven. Each filesystem received a different number of flips, and the report makes it clear that **it is not a ranking**.

### Is it close to landing?

Nope, this is a request for comments (RFC). Aurelien is asking for feedback, not calling for a merge, and he has two questions for the maintainers.

The first is whether it should be a separate filesystem or be proposed for an existing one.

The second is the journal, the log other filesystems use to recover from crashes. BeamFS lacks one and relies on its `fsck` tool after an unclean shutdown. Aurelien asks whether it has to come before further review or can be submitted afterward.

So far, the only reply [in the thread][11] is about where the `MAINTAINERS` entry sits alphabetically.

The project's [README][12] has a warning of its own. It lists bugs that can lose data, open security holes, and crash the kernel, **advising against trusting the code with anything important**.

Enjoyed this update? Support independent Linux news coverage

It's FOSS has been helping people use Linux for the past 14 years. Help us stay independent from big tech. Become a Plus member, enjoy ad-free reading and get 5 eBooks.

Plus yearly

Ad-free, FREE ebooks

[Join yearly][13]

Best value

Plus lifetime

Pay once, Enjoy forever

[Go lifetime][14]

Buy us a coffee

Any amount, no commitment

[Support on Ko-fi][15]

Skip the AI slop and SEO spam in your Google results

Tell Google you prefer It's FOSS, and it will show our Linux news and tutorials, created by experienced Linux users, more often when you search. It takes just a click.

[Set as preferred source][16]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/beamfs-linux-filesystem-proposal/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://github.com/roastercode
[4]: https://github.com/roastercode/beamfs
[5]: https://lore.kernel.org/lkml/20261019041728.327785-1-aurelien@hackers.camp/
[6]: https://itsfoss.com/news/linux-ai-coding-assistants-policy/
[7]: https://itsfoss.com/content/images/2026/10/beamfs-github-repo.png
[8]: https://en.wikipedia.org/wiki/Reed%E2%80%93Solomon_error_correction
[9]: https://www.britannica.com/science/neutron
[10]: https://zenodo.org/records/23253350
[11]: https://lore.kernel.org/lkml/4ebbbb17-7833-4a2c-9e7e-b3c731873caf@infradead.org/
[12]: https://github.com/roastercode/beamfs/blob/main/README.md
[13]: https://itsfoss.com/#/portal/signup
[14]: https://itsfoss.com/lifetime-membership/
[15]: https://ko-fi.com/itsfoss
[16]: https://www.google.com/preferences/source?q=itsfoss.com
