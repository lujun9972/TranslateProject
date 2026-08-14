[#]: subject: "Test Days for Fedora 45: Help Us Test the Big Changes"
[#]: via: "https://fedoramagazine.org/test-days-for-fedora-45-help-us-test-the-big-changes/"
[#]: author: "Petr Sklenar https://fedoramagazine.org/author/psklenar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Test Days for Fedora 45: Help Us Test the Big Changes
======

![][1]

Fedora 45 has several system-level changes that need testing on real hardware. The first test day up is GNOME 51, starting on _17 August,_ with more events planned for RPM 6.1, installation media and others. You can participate with a VM for most tests; some hardware-specific testing is more useful on a real machine.

Details are contained in this article.

Fedora 45 is bringing several changes that deserve testing beyond CI and automated test suites. Here are some of the bigger ones:

  * **RPM 6.1** : update to 6.1, enforced signature checking, and DNF repo configs relocating to /usr.
  * **OpenSSL 4.0** — a major version bump that could affect anything doing TLS.
  * **Boot and live media** are being rebuilt from scratch with image-builder. This changes how the images are produced, so we want to make sure they still boot and install correctly across a range of hardware and virtualization setups.
  * **kmscon** replaces the kernel VT console (fbcon) as the default.
  * **Python 3.15** , **GRUB EFI for Confidential Computing** , and [more][2].



### Why we need community testing

Automated tests catch regressions in known scenarios, but they won’t tell us if the new boot.iso works on your particular laptop, or if enforced RPM signature checking breaks a workflow nobody on the team thought of. We need people trying this on real machines and in real scenarios.

That’s what test days are for. A few days focused on a specific change, developers on Matrix to help debug, and anyone can show up and run through the test cases. You don’t need to be a Fedora QA expert. If you can install Fedora, reproduce a problem and report what happened, you can help.

### What we’re planning for F45

At our [July 20 Quality meeting][3] (transcript), we went through the ChangeSet and picked out the changes that would benefit most from community testing. That turned into a [planning ticket on Forge][4] with individual tickets for each event.

**GNOME 51 Desktop** — **August 17-21** is the first test day this cycle and it’s happening right now . Desktop, graphics, peripherals, core applications. If you’re reading this in time, jump in. ([#GNOME_51_Desktop][5])

**I18n test week** — **September 7-13** input methods, locales, keyboard layouts. . ([#924][6])

**RPM 6.1** — NSS support for user/group lookups is back, queries work again during transactions, new macro modifiers for packagers, and better rpmkeys verification output. Looks like a smooth update, but RPM touches everything — worth making sure nothing slipped through. ([#917][7])

**Installation media** — boot.iso and live images, physical hardware, VMs. Try booting the new images on whatever hardware you have. Does the installer work? Does the live environment behave? ([#][8][9][8][18][8])

**KDE** — likely KDE 6.7. ([#922][9])

**Cockpit** — it’s been years since the last Cockpit test day. ([#920][10])

**GRUB EFI / Confidential Computing** — relevant mainly to specific hardware and VM environments. ([#919][11])

_**The list isn’t final**_. We’re still looking at kmscon, OpenSSL 4.0, CoreOS, and Kernel 7.2. Keep an eye on [testdays.fedoraproject][12][.][12][org][12] for the current schedule.

### What kind of testing helps most

Try upgrading your system to the latest packages. Boot the new boot.iso on physical hardware. Test suspend/resume, Wi-Fi, external displays, NVIDIA/AMD/Intel graphics, or whatever hardware you actually use. Each test day has a wiki page with specific test cases, but your own daily workflows are often where the interesting bugs hide.

You need a [Fedora Account][13] to report results. Pick a test day from the [schedule][12], follow the wiki instructions, report through the [test day app][12], and if you find something odd, come talk to us on Matrix in [#test-day:fedorapr][14][oject.org][14].

The test day app itself is open source at [quality/testdays-web][15] on Forge. If something about it bugs you or you have an idea, file a ticket.

### Propose a test day

This doesn’t all have to come from us. If you maintain a package with a big change in F45, or you see something in the ChangeSet that you think needs broader testing — propose a test day. Create a ticket at [forge.fedoraproject.org/quality/tickets][16], tag it “test days”, and tell us what you’d like to test. You don’t need test cases or wiki pages ready. The QA team will help with that.

### Testing beyond test days

Test days are focused events around specific changes, but testing Fedora is something you can do any day. [fedora-easy-karma][17] is a CLI tool that picks up testing updates already installed on your system and lets you submit karma to [Bodhi][18] right from your terminal. See the [installation instructions][19] to get started. Like the test day app, it’s an open source project hosted on Forge — feel free to report issues or suggest features.

### Links

  * [Test day schedule][12] [and results][12]
  * [Fedora 45 ChangeSet][2]
  * [F45 test][4] [day planning ticket][4]
  * [Test Days wiki][20]
  * [Matrix: #test-day:fedoraproject.org][14]
  * [Mailing list: test@lists.fedoraproject.org][21]



Catch you in [#test-day][14] on Matrix.

_**Note about AI usage:** I wrote this article myself. I used Claude (Anthropic) to significantly refine the grammar, wording, and sentence structure; the technical content and all claims are my own._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/test-days-for-fedora-45-help-us-test-the-big-changes/

作者：[Petr Sklenar][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/psklenar/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/01/Test_Days-816x345.jpg
[2]: https://fedoraproject.org/wiki/Releases/45/ChangeSet
[3]: https://meetbot-raw.fedoraproject.org//meeting_matrix_fedoraproject-org/2026-07-20/quality.2026-07-20-15.05.log.html
[4]: https://forge.fedoraproject.org/quality/tickets/issues/916
[5]: https://fedoraproject.org/wiki/Test_Day:2026-08-17_GNOME_51_Desktop
[6]: https://forge.fedoraproject.org/quality/tickets/issues/924
[7]: https://forge.fedoraproject.org/quality/tickets/issues/917
[8]: https://forge.fedoraproject.org/quality/tickets/issues/918
[9]: https://forge.fedoraproject.org/quality/tickets/issues/922
[10]: https://forge.fedoraproject.org/quality/tickets/issues/920
[11]: https://forge.fedoraproject.org/quality/tickets/issues/919
[12]: https://testdays.fedoraproject.org/
[13]: https://accounts.fedoraproject.org
[14]: https://chat.fedoraproject.org/#/room/#test-day:fedoraproject.org
[15]: https://forge.fedoraproject.org/quality/testdays-web
[16]: https://forge.fedoraproject.org/quality/tickets/issues
[17]: https://forge.fedoraproject.org/quality/fedora-easy-karma
[18]: https://bodhi.fedoraproject.org
[19]: https://forge.fedoraproject.org/quality/fedora-easy-karma#installation
[20]: https://fedoraproject.org/wiki/QA/Test_Days
[21]: https://lists.fedoraproject.org/archives/list/test@lists.fedoraproject.org/
