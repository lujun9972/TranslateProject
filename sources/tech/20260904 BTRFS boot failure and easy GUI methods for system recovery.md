[#]: subject: "BTRFS boot failure and easy GUI methods for system recovery"
[#]: via: "https://fedoramagazine.org/btrfs-boot-failure-and-easy-gui-methods-for-system-recovery/"
[#]: author: "Alex Genovese https://fedoramagazine.org/author/alex-genovese/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

BTRFS boot failure and easy GUI methods for system recovery
======

![][1]

**A few short how-to’s with screenshots, showing easy ways to boot up off a USB live ISO and return back to previous points in time** **with BTRFS**.

Many Linux distributions now default to BTRFS as the standard installation filesystem. Fedora Linux is no exception to that.

2022/23 saw a lot of articles extolling its virtues of easy rollback, stability and so forth. All complete with paragraphs of command line instructions.

Times have changed, the BTRFS infrastructure has matured, and there are now easy to use GUI tools at our fingertips.

### No special tools or skills

You may use any standard Fedora Linux ISO image and USB stick.

This article is for people new to Fedora Linux and for those who are familiar with ext4 and Timeshift.

### Easy to follow instructions

My experience with Linux goes back quite a long way.

There used to be a time when the Fedora Linux help links often routed to Red Hat Enterprise. This generally targeted the needs of network managers and other system professionals.

Thankfully, for ordinary users the situation has now improved. The Fedora Magazine is one of those reasons.

In the last few years I have been using Fedora Linux as test-bed virtual machines and I have been using Fedora Kinoite on a secondary laptop.

As a daily driver, the thing that most recently stopped me switching to Fedora Linux was not being able to find easy to follow instructions on snapshot recovery during system boot failure.

This article lists the solutions that I finally pieced together.

## How to start

![][2]

First, make sure that you do actually have your OS running with BTRFS.

This is now normally the case but if you have had your installation for a few years, or someone else installed it for you, it is wise to check.

On Fedora Workstation, with Gnome, try _disks_ or _gparted_. These two will also install readily on KDE and many users actually prefer them to the _KDE partion manager_.

Many people welcomed the [20][3][25][3] decision by the Fedora steering committee to promote KDE to parity status with (Gnome) Workstation. This guide covers both official versions.

If you don’t have Fedora Linux yet, there are also a few notes on general setup as well.

### Getting help from the assistant

You may have seen _btrfs-assistant_ mentioned in forum discussions. If you don’t already have **this program installed, then now is the time to look at doing it.

![][4]

The package only takes a tiny amount of space and also installs _snapper_. About 4MB in total. Either Gnome Software or KDE Discover are fine. Or you can use _dnf_ on the the command line.

Up and running:

![][5]

### Sub-Volumes

Registration of existing sub-volumes is automatic:

![][6]

By default, Fedora creates two sub-volume sections on standard installation. We can only see them in the file manager when we boot via a USB live ISO, otherwise we see the volume contents only.

Partition managers such as _gparted_ may show the partition as complete but the file system won’t work unless we have set up the logical sub-volume overlay inside of it.

If you are using Gnome Workstation you may probably see an additional sub-volume ‘ _/root/var/lib/machines_ ‘ which, unless you are working with container built machines, will be empty. It’s just there to exclude temporary files from any snapshot processes and can be ignored too.

### Alternative layouts

_Anaconda_ is the in-house installer and I have been quite impressed with its recent incarnations.

The default installation route is decidedly the easier option at present.

However, for users wanting to add extra sub-volumes, the best method may be right at the start when you are offered the _Storage Editor_ option. If using pre Fedora Linux 45, you can also find it at the top right corner of the interface.

Fedora Linux will happily install alongside your current setup if you want to try things out.

I have found that the best method is to use _gparted_ to prepare a section of non-allocated disk space to offer the installer to work with, rather than offering it a ready made partition.

### Post-install adjustments

Creating new sub-volumes requires the command line. This is for advanced users only.

In theory, _Blivet-gui_ claims to be able to do this task but I am yet to be convinced. B _trfs-assistant_ leaves this bit well alone, which is what we are going to do.

### Backups

There isn’t much that we can do with the actual sub-volumes, as they stand. The Copy On Write (CoW) mechanism is there and working. That’s about it.

But backups are always good to have, so make sure that you have got one before you start setting things up for real. We’ll have a look at this in detail later on.

There are _btrfs_ command line methods for sub-volumes using _send_ and _receive_ but the concepts can get quite complex.

Making standard partition backups are much easier using _dd_ or Gnome _Disks_ , just as if we were using ext4, and they are equally effective for basic needs.

## Snapshots

These are what really sets BTRFS rollback into a totally different league compared to using Timeshift.

To get this working we are going to use _Snapper_ :

![][7]

You may find mention on forums about using Timeshift on Fedora Linux BTRFS with Ubuntu style @ sub-volumes. This now no longer works unless you are using something like Linux Mint. It was never probably a good idea to start with but it does illustrate the extents to which people have gone to, and just to get some kind of easy GUI recovery setup going.

We need to set up _Snapper_ before things go wrong.

If you have arrived at this article through a web search and are in difficulties, unless you have previously setup snapshots, you are going to be restricted to using the command line.

Command line _btrfs_ is actually the foundation program used to create and manage the overlay sections. _Snapper_ helps us work with the _btrfs_ snapshots.

Several command line articles are available: <https://fedoramagazine.org/?s=btrfs>

### Snapper configs

The place to start is at the _Snapper Settings_ tab. Click ‘new’ and fill in the details, one for ‘root’ and one for ‘home’:

![][8]

The backup and target paths must both be on the same partition. Otherwise, the [docs][9] say that you can place sub-volumes anywhere. BTRFS uses hidden sub-volumes, so placing ‘root’ at ‘/’ and ‘home’ at ‘/home’ is as good a place as any, probably.

In our setup, _root_ means everything except the _home_ folder. And the home folder will neatly hold the home snapshots.

Snapper will place its config files at ‘/etc/snapper’ if you need to find them.

Enable timeline, cleanup and boot. Click the save button.

### Numbers

The first config save will set up the config file. We now have to set the numbers.

![][10]

I don’t know if is intentional for [Snapper][11] to default to saving 10 whole years of snaps and nothing weekly. Perhaps it’s something to do with openSUSE and and their long term server support program?

For everyday use, these figures need changing. And the root volume needs to be treated differently from the home one.

I am currently evaluating the above set for root, with 15, 10, 5, 3, 1, 50 for home. Although, I am wondering if these these figures could be a bit too high …

The number defines how many snapshots the timeline cleanup algorithm should keep, counting from the youngest.

When done, **save again, then apply systemd changes.**

### Hoarding Junk

Make sure that you don’t get carried away. Snapshots are very easy to take. We’ve all probably seen stories of people filling their houses with 20 years of old newspapers.

One or two snapshots of old kernels and firmware updates might get us out of problems but we don’t really need to keep Gigabytes of these for months on end. Conversely, it could be invaluable to find some small but important documents that got accidentally deleted a few months back without us realizing.

The dangers of system bloat could well be one of the reasons that Fedora Linux doesn’t have snapper already installed.

### Creating the snapshots

This is normally fully automated and happens in micro-seconds. A very different scale to ext4 and Timeshift where we are frequently talking of minutes.

Manual snaps are great as well. Maybe just before doing something that could go wrong is a good idea.

If you set up the Snapper boot config option, an instant snapshot will be taken at every boot time, so any errant updates can be very easy to reverse too.

Different copy on write file systems can have both subtle or major differences but the basic b-tree principles tend to remain. If you want a deep dive into [the theory,][12] there’s lots out there.

The BTRFS system is continually working on records of what is happening, so data processing requirements are very small. In **simple** **terms** we can look at this as making tag at a point in time on a type of continuous and interconnected meta-data event log. When we roll back, we return to the tag and restart the recording on a new branch.

### Browsing

Select the Snapper tab and then the sub-tab for Browse/Restore:

![][13]

Find the snapshot that you think you need and click on Browse to see what’s in there. The Browse function also lets you restore individual files rather than whole snaps. Keep an eye on the target drop down which will change when you switch tabs.

### Deleting

BTRFS is night and day faster than the qcow2 systems used on virtual machines. The same for Timeshift. Only a couple of seconds are needed, even for very old snapshots.

### Maintenance

On this tab, **scrub** is probably the only important one. The [docs][14] say this should run at least monthly. If you have done a lot of snapshot rewinding then a manual scrub is a good idea.

Balance is for balancing RAID devices and you only really need defrag if you are running on a mechanical hard drive. An SSD will have its own optimising system built in but you could run defrag manually every year or two if you want.

![][15]

## Live booting

There are some operations that we simply can’t do on an operating system when it’s in use. Instead, we need to use _Fedora Media Writer_ or Gnome _Disks_ to put a downloaded Live ISO onto a USB stick and run things from there. For _Disks_ , right click on the ISO and select open-with _Disk Image Writer_.

Many of you will be very familiar with this process. But not everybody is aware that many live ISO’s will also allow you to install small amounts of software onto them. This little trick will in fact go on to form a keystone to how we do our system failure recovery.

Downloaded ISO images from [https://fedoraproject.org][16]

If preferred, try the Manjaro KDE ISO from <https://manjaro.org/products/download/x86> which will also have most of the needed software already there.

### Restarts

The next stage is to get your computer to boot with the USB; you will need to have either already set your UEFI/BIOS to allow a trigger key during initial starting, usually delete, or you will need to go to the OS settings and request a UEFI restart there:

![][17]

## Staying safe

It’s basic standard good practice to have a recent full backup when doing anything to your system.

Once you have booted the live ISO, if you don’t have a backup, then make sure that you do.

Using _Disk_ ‘s GUI interface allows the making of partition images to be fairly straight forward. Gnome Workstation ISO’s will already have _Disks_ ready for you to use. If you are using KDE, set it up using _KDE Discover_. Otherwise use _dnf_. The installation is just a few MB.

![][18]

Select the partition, standard click the options button and choose ‘create partition image’.

Backup the boot partitions too. BTRFS makes no copies of these.

The usual cautions if you are thinking of using _dd_ and have never used it before. You need to **always** pay attention to your input ‘if=’ and your output ‘of=’ or it changes from being a useful disk duplicator into it’s other guise of disk destroyer ….

Also, place your backups on to something reliable. A good quality USB hard-drive is generally viewed as a good choice. They are more resistant to time fading than SSD’s even if they are slower. If you have not heard of ‘bit rot’ there are lots of articles on the web. SSD’s will lose data if they are not regularly powered up.

### Partition sizes

You may want to consider partition size adjustment at this point. But do the initial backup first, if you can.

Keeping the size of the OS partition reduced down will make backing up much easier. And you are still going to need further full backups, even with Copy On Write running things.

For more experienced users, there are methods to compress partition backups using _dd_. Also creating a ‘ _/dev/zero_ ‘ temp file will help compress even more. You can save lots of space but the .img files have to be fully decompressed in order to mount them, which is a slight down side.

## Virtual machines

Problems with computer speed and with excess data can occur when having a two concurrent CoW systems running together. A kind of snowball effect from the host system continually backing up copies of the other backups.

According to the Qemu [docs][19], when keeping virtual machines on a BTRFS partition it is recommend to use the ‘ _nocow_ ‘ option to avoid performance issues.

For those of you using _Gnome Boxes_ , which comes pre-installed on Workstation, any adjustment of the config files and VM locations is **not** needed.

_Boxes_ likes to keep its virtual machines out of view in a hidden _home_ folder called _‘.local/share/gnome-boxes/images’_ and it tends to work best when left that way. All the image files will already have had CoW disabled.

I can’t say that I have noticed any significant problems when I have carried out short tests. However, the issue is there nevertheless and a general look on the web will yield some quite lively discussion on the matter.

Advanced users may wish to consider running their VMs on a separate ext4 partition as another option.

The _nocow_ +C flag can be easily checked by using _lsattr_ against the image file, if required.

## Swap files

Fedora Linux now uses the faster and more modern _zram_ system which compresses the RAM data instead of swapping it to storage.

BTRFS snapshotting will **not** work if traditional swap files are present in the sub-volume.

If you are running short of RAM, your first option should be adjusting the _zram_ allocation ratios. If you still find that you need a swap file, you will need to create a separate sub-volume to contain it.

## Recovery

Having arrived at this point, you should now find this section to be fairly intuitive.

However, do remember to pay attention to root/home continuity. Remember that _home_ will still contain hidden system and config files that are used by programs installed in the root section.

![][20]

For small problems, where the system still boots, load _btrfs-assistant_ on standard load and roll back to a previous good point.

**Importantly** , for USB running, start the file manager and mount the partition that you need to fix **before** installing or running btrfs-assistant or it will fail to work.

In both cases you will be advised to reboot for the request to take effect. The whole process is fairly quick and compared to Timeshift, pretty much instant.

## Choosing the right tools

System failure happens to the best of us, given enough time to press enough buttons or to adjust one configuration file too many. But sometimes the failures are caused from upstream, from an unnoticed upstream bug perhaps.

If you are still able to boot into your system, Fedora Linux already features a very quick package reversal system as built-in standard. Sometimes we don’t need to use snapshots at all.

There is a GUI program to run this called _dnfdragora_ :

![][21]

For the sake of completeness, this does need mentioning. However, I would probably argue that in this case the command line is quicker and more intuitive:

![][22]

Downgrades work on a simple **temporary** basis only, so there is no need to re-instate anything at a later stage. When the next batch of updates are available, hopefully with a fix, the package and its associated files become automatically re-upgraded.

## Conclusion

This article hopefully updates us to the start of H2 2026.

Should Red Hat support Fedora Linux putting their support behind _btrfs-assistant_ and should we have s _napper_ and snapshots already setup on new installations?

I think the answer to that is yes, and that this is probably going to be happening. But for exactly how and when, we will have to wait to see.

Further improvements will always be in the pipeline.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/btrfs-boot-failure-and-easy-gui-methods-for-system-recovery/

作者：[Alex Genovese][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/alex-genovese/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/08/gui-btrfs-management-and-recovery-1-816x345.jpg
[2]: https://fedoramagazine.org/wp-content/uploads/2026/08/stdpartitions-1024x427.png
[3]: https://discussion.fedoraproject.org/t/f42-change-proposal-promote-kde-plasma-desktop-variant-to-edition-self-contained/142526
[4]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-assist-discover.png
[5]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-assistant.png
[6]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-initial-snaps.png
[7]: https://fedoramagazine.org/wp-content/uploads/2026/08/snapper-configs-1024x751.jpg
[8]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-snapper-settings-new.png
[9]: https://btrfs.readthedocs.io/en/latest/Subvolumes.html
[10]: https://fedoramagazine.org/wp-content/uploads/2026/08/snapper-numbers-refined.png
[11]: http://snapper.io/manpages/snapper-configs.html
[12]: https://btrfs.readthedocs.io/en/latest/dev/dev-btrfs-design.html
[13]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-restore-1.png
[14]: https://btrfs.readthedocs.io/en/latest/Scrub.html
[15]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-maintain-select.png
[16]: https://fedoraproject.org/
[17]: https://fedoramagazine.org/wp-content/uploads/2026/08/system-settings-boot-to-uefi-1.png
[18]: https://fedoramagazine.org/wp-content/uploads/2026/08/backing-up-using-gnome-disks.png
[19]: https://www.qemu.org/docs/master/system/qemu-block-drivers.html#cmdoption-qcow2-arg-nocow
[20]: https://fedoramagazine.org/wp-content/uploads/2026/08/btrfs-restore.png
[21]: https://fedoramagazine.org/wp-content/uploads/2026/09/dnfdragora-install.png
[22]: https://fedoramagazine.org/wp-content/uploads/2026/09/dnf-downgrade-thermald-1024x348.png
