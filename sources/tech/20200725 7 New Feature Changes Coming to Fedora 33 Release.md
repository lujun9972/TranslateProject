[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (7 New Feature Changes Coming to Fedora 33 Release)
[#]: via: (https://itsfoss.com/fedora-33/)
[#]: author: (Abhishek Prakash https://itsfoss.com/author/abhishek/)

7 New Feature Changes Coming to Fedora 33 Release
======

Development for Fedora 33 is in progress and looking at the proposed changes, it looks to be one of the biggest release ever.

Fedora 33 should be releasing in mid to late October 2020. But there is no specific release date or schedule like Ubuntu here.

Let’s see what are these changes that make Fedora 33 a release worth following.

### New features in Fedora 33

![][1]

Most of the features listed here are confirmed changes. I’ll update the article with more feature changes in the future.

#### Btrfs is the new default filesystem

In a surprising move, [Fedora announced that it will be using Btrfs as the default filesystem][2] for the new installations starting with Fedora 33.

This is a big move and not everyone agrees with. You should still be able to use Ext4 filesystem while installing Fedora 33 but you have to do a bit of effort for that.

#### Nano is the default terminal-based text editor

![][3]

More ‘defaults’ changing in Fedora 33. Until now, Vi was the default editor in the terminal. This is changing as well.

Starting with Fedora 33, [Nano][4] will be the default text editor in the terminal. If you are not familiar with it, try the [Nano beginner’s guide][5] I have written earlier.

Keep in mind that you can still [change the default text editor in terminal][6] if you don’t like Nano.

#### Swap on zRAM by default

Fedora 33 will utilize zram instead of swap partition by default. zram is RAM drive that uses compression. Due to compression, it uses half as much memory as its size.

So when the RAM is full and the system needs more memory, instead of using swap partition, Fedora will use the zram device (usually under /dev/zram0). Here’s the [explanation on the change][7]:

The system will use RAM normally up until it’s full, and then start paging out to swap-on-zram, same as a conventional swap-on-drive. The zram driver starts to allocate memory at roughly 1/2 the rate of page outs, due to compression. But, there is no free lunch. This means swap-on-zram is not as effective at page eviction as swap-on-drive, the eviction rate is ~50% instead of 100%. But it is at least an order of magnitude faster than drive based swap.

zram has about 0.1% overhead or ~1MiB/1GiB. If the workload never touches swap, this overhead is the sole cost. In practice when not used at all, feature owner has experienced ~0.04% overhead.

#### systemd-resolved enabled by default

Fedora is trying to standardize on upstream systemd service. Standardizing reduces behavior differences between different Linux distributions.

In that effort, Fedora 33 is going to use [systemd-resolved][8] by default. This [systemd service][9] provides network name resolution.

#### Improved hardening for 64-bit ARM devices

Fedora 33 changes [enables support][10] for newer ARMv8.3~8.5-level code hardening features in order to enhance the security. This [should serve][11] to make Fedora more resistant to a couple further classes of runtime attacks.

#### GNOME 3.38 and all the visual changes it brings

![Default wallpaper in GNOME 3.38][12]

GNOME version 3.38 should be released by mid-September. This means that Fedora 33 will have this new release.

There will be some performance improvements and visual changes to it. They even plan to add touchpad gesture for switching workspaces.

#### Animated background based on time of day

This is not a serious change but a little eye candy is not a bad deal. Fedora 33 will use animated background that will change the color shades based on the time of the day.

This feature is getting quite popular and if I remember correctly, [Manjaro Linux 20][13] also uses it.

#### Dropping legacy BIOS support (under discussion)

Fedora developers are also discussing dropping legacy BIOS support and go with UEFI-only approach. Before you get outraged, do keep in mind that [Intel is ending legacy BIOS support in 2020][14].

This change is not confirmed yet and it is still [under discussion][15].

#### Other changes

Fedora is also updating the system-wide crypto policy to further disable legacy cryptographic protocols (TLS 1.0 and TLS 1.1), weak Diffie-Hellman key exchange sizes (1024 bit), and use of the SHA-1 hash in signatures.

Apart from that, there are some software changes that you might find interesting:

  * Latest MinGW
  * GNU Make 4.3
  * Ruby on Rails 6.0
  * Boost 1.73
  * Golang 1.15
  * glibc 2.32
  * Java 11
  * LLVM 11
  * Node.js 14.x series
  * Perl 5.32
  * Include Python 3.9, drop Python 2.6 and 3.4
  * RPM 4.16



#### Do you agree with the changes?

As I mentioned earlier, Fedora 33 should be released in late October this year. [Existing Fedora 32 users should be able to upgrade to the new release][16] when the stable version is available.

Which Fedora 33 feature you like the most? Do you agree with changing the default filesystem and the editor? Do share your views in the comment section.

--------------------------------------------------------------------------------

via: https://itsfoss.com/fedora-33/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://i0.wp.com/itsfoss.com/wp-content/uploads/2020/07/fedora-33-features.png?ssl=1
[2]: https://itsfoss.com/btrfs-default-fedora/
[3]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/05/nano-editor-save-while-writing.png?ssl=1
[4]: https://www.nano-editor.org/
[5]: https://itsfoss.com/nano-editor-guide/
[6]: https://linuxhandbook.com/install-vim-ubuntu/
[7]: https://fedoraproject.org/wiki/Changes/SwapOnZRAM
[8]: https://wiki.archlinux.org/index.php/Systemd-resolved
[9]: https://linuxhandbook.com/systemd-list-services/
[10]: https://www.phoronix.com/scan.php?page=news_item&px=Fedora-33-AArch64-Code-Hard
[11]: https://fedoraproject.org/wiki/Changes/Aarch64_PointerAuthentication
[12]: https://i1.wp.com/itsfoss.com/wp-content/uploads/2020/07/adwaita-wallpaper.jpg?resize=800%2C450&ssl=1
[13]: https://itsfoss.com/manjaro-20-release/
[14]: https://www.phoronix.com/scan.php?page=news_item&px=Intel-Legacy-BIOS-EOL-2020
[15]: https://lists.fedoraproject.org/archives/list/devel@lists.fedoraproject.org/thread/QBANCA2UAJ5ZSMDVVARLIYAJE66TYTCD/
[16]: https://itsfoss.com/upgrade-fedora-version/
