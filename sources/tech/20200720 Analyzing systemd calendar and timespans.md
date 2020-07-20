[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Analyzing systemd calendar and timespans)
[#]: via: (https://opensource.com/article/20/7/systemd-calendar-timespans)
[#]: author: (David Both https://opensource.com/users/dboth)

Analyzing systemd calendar and timespans
======
Learn how systemd uses calendar time, timestamps, and timespans to
control when things happen.
![Calendar close up snapshot][1]

In my previous seven articles in this series about systemd, and especially in the [most recent][2] article, time and date have come up in multiple contexts. systemd uses calendar time, specifying one or more moments in time to trigger events (such as a backup program), as well as timestamped entries in the journal. It can also use timespans, which define the amount of time between two events but are not directly tied to specific calendar times.

In this article, I will look in more detail at how time and date are used and specified in systemd. Also, because systemd uses two slightly different, non-compatible time formats, I will explain how and when they are used.

### Definitions

Following are some important time- and calendar-related systemd terms to understand:

  * **Absolute timestamp:** A single unambiguous and unique point in time defined in the format `YYYY-MM-DD HH:MM:SS`. The timestamp format specifies points in time when events are triggered by timers. An absolute timestamp can represent only a single point in time, such as `2025-04-15 13:21:05`.

  * **Accuracy** is the quality of closeness to the true time; in other words, how close to the specified calendar time an event is triggered by a timer. The default accuracy for systemd timers is defined as a one-minute timespan that starts at the defined calendar time. For example, an event specified to occur at the `OnCalendar` time of 09:52:17 might be triggered at any time between then and 09:53:17.

  * **Calendar events** are one or more specific times specified by a systemd timestamp in the format `YYYY-MM-DD HH:MM:SS`. It can be a single point in time or a series of points that are well-defined and for which the exact times can be calculated. systemd journals use timestamps to mark each event with the exact time it occurred.

In systemd, exact time is specified in the timestamp format `YYYY-MM-DD HH:MM:SS`. When only the `YYYY-MM-DD` portion is specified, the time defaults to 00:00:00. When only the `HH:MM:SS` portion is specified, the date is the next calendar instance of that time. If the time specified is before the current time, the next instance will be tomorrow, and if the specified time is later than the current time, the next instance will be today. This is the format systemd timers use to express `OnCalendar` times.

Recurring calendar events can be specified using special characters and formats that represent fields with multiple value matches. For example, `2026-08-15..25 12:15:00` represents 12:15pm on the 15th through the 25th of August 2026 and would trigger 11 matches. Calendar events can also be specified with an absolute timestamp.

  * **Timespan** is the amount of time between two events or the duration of something like an event or the time between two events. Timespans can be used to specify the desired accuracy for an event to be triggered by a timer and to define the time to elapse between events. systemd recognizes the following time units:

    * usec, us, µs
    * msec, ms
    * seconds, second, sec, s
    * minutes, minute, min, m
    * hours, hour, hr, h
    * days, day, d
    * weeks, week, w
    * months, month, M (defined as 30.44 days)
    * years, year, y (defined as 365.25 days)



The `systemd.time(7)` man page has a complete description of time and date expressions in timers and other systemd tools.

### Calendar event expressions

Calendar event expressions are a key part of triggering timers at repetitive times. systemd and its timers don't use the same style for time and date expressions as crontab uses. systemd is also more flexible than crontab and allows fuzzy dates and times similar to the `at` command.

The format `OnCalendar=` uses for calendar event expressions is `DOW YYYY-MM-DD HH:MM:SS`. DOW (day of the week) is optional, and other fields can use an asterisk (`*`) to match any value for that position. If the time is not specified, it is assumed to be 00:00:00. If the date is not specified but the time is, the next match might be today or tomorrow, depending upon the current time. All the various calendar time-expression formats are converted to a normalized form, and the `systemd-analyze calendar` command shows the normalized form of the time expression.

systemd provides an excellent tool for validating and examining calendar events used in an expression. The `systemd-analyze calendar` tool parses a calendar time event expression and provides the normalized form and other information, such as the date and time of the next "elapse" (i.e., match) and the approximate amount of time before it reaches the trigger time.

> **Note:** All the following commands can be performed by non-root users and the times for "Next elapse" and "UTC" will differ based on your local time zone.

First, look at the syntax of the `systemd-analyze calendar` command. Start with a date in the future without a time. Because all the date unit fields are explicitly specified, this is a one-time event:


```
[student@testvm1 ~]$ systemd-analyze calendar 2030-06-17
  Original form: 2030-06-17                
Normalized form: 2030-06-17 00:00:00        
    Next elapse: Mon 2030-06-17 00:00:00 EDT
       (in UTC): Mon 2030-06-17 04:00:00 UTC
       From now: 10 years 0 months left    
```

Add a time (in this example, the date and time are analyzed separately as non-related entities):


```
[root@testvm1 system]# systemd-analyze calendar 2030-06-17 15:21:16
  Original form: 2030-06-17                
Normalized form: 2030-06-17 00:00:00        
    Next elapse: Mon 2030-06-17 00:00:00 EDT
       (in UTC): Mon 2030-06-17 04:00:00 UTC
       From now: 10 years 0 months left    

  Original form: 15:21:16                  
Normalized form: *-*-* 15:21:16            
    Next elapse: Mon 2020-06-15 15:21:16 EDT
       (in UTC): Mon 2020-06-15 19:21:16 UTC
       From now: 3h 55min left
```

To analyze the date and time as a single entity, enclose them together in quotes:


```
[student@testvm1 system]# systemd-analyze calendar "2030-06-17 15:21:16"
Normalized form: 2030-06-17 15:21:16        
    Next elapse: Mon 2030-06-17 15:21:16 EDT
       (in UTC): Mon 2030-06-17 19:21:16 UTC
       From now: 10 years 0 months left  
```

Specify one time earlier than the current time and one later. In this example, the current time is 16:16 on 2019-05-15:


```
[student@testvm1 ~]$ systemd-analyze calendar 15:21:16 22:15
  Original form: 15:21:16
Normalized form: *-*-* 15:21:16
    Next elapse: Fri 2019-05-17 15:21:16 EDT
       (in UTC): Fri 2019-05-17 19:21:16 UTC
       From now: 23h left

  Original form: 22:15
Normalized form: *-*-* 22:15:00
    Next elapse: Thu 2019-05-16 22:15:00 EDT
       (in UTC): Fri 2019-05-17 02:15:00 UTC
       From now: 5h 59min left
```

The `systemd-analyze calendar` tool does not work on timestamps. So things like "tomorrow" or "today" will cause errors if you use them with the calendar sub-command because they are timestamps rather than `OnCalendar` time formats:


```
[student@testvm1 ~]$ systemd-analyze calendar "tomorrow"
Failed to parse calendar expression 'tomorrow': Invalid argument
Hint: this expression is a valid timestamp. Use 'systemd-analyze timestamp "tomorrow"' instead?
```

The term "tomorrow" will always resolve to tomorrow's date and a time of 00:00:00. You must use the normalized expression format, `YYYY-MM-DD HH:MM:SS`, for this tool to work in calendar mode. Despite this, the `systemd-analyze calendar` tool can still help you understand the structure of the calendar time expressions used by systemd timers. I recommend reading the `systemd.time(7)` man page for a better understanding of the time formats that can be used with systemd timers.

Why would using a statement like `OnCalendar=tomorrow` fail when used in a timer?

### Timestamps

Whereas calendar times can be used to match single or multiple points in time, timestamps unambiguously represent a single point in time. For example, timestamps in the systemd journal refer to a precise moment when each logged event occurs:


```
[student@testvm1 ~]$ journalctl -S today
Hint: You are currently not seeing messages from other users and the system.
      Users in groups 'adm', 'systemd-journal', 'wheel' can see all messages.
      Pass -q to turn off this notice.
\-- Logs begin at Wed 2020-06-17 10:08:41 EDT, end at Wed 2020-06-17 10:13:55 EDT. --
Jun 17 10:08:41 testvm1.both.org systemd[1137785]: Started Mark boot as successful after the user session has run 2 minutes.
Jun 17 10:08:41 testvm1.both.org systemd[1137785]: Started Daily Cleanup of User's Temporary Directories.
Jun 17 10:08:41 testvm1.both.org systemd[1137785]: Reached target Paths.
Jun 17 10:08:41 testvm1.both.org systemd[1137785]: Reached target Timers.
&lt;SNIP&gt;
Jun 17 10:13:55 testvm1.both.org systemd[1137785]: systemd-tmpfiles-clean.service: Succeeded.
Jun 17 10:13:55 testvm1.both.org systemd[1137785]: Finished Cleanup of User's Temporary Files and Directories.
```

The `systemd-analyze timestamp` command can be used to analyze timestamp expressions the same way it analyzes calendar expressions. Here is an example from the journal data stream:


```
[student@testvm1 ~]$ systemd-analyze timestamp "Jun 17 10:08:41"
Failed to parse "Jun 17 10:08:41": Invalid argument
[student@testvm1 ~]$ systemd-analyze timestamp Jun 17 10:08:41
Failed to parse "Jun": Invalid argument

Failed to parse "17": Invalid argument
Hint: this expression is a valid timespan. Use 'systemd-analyze timespan "17"' instead?

  Original form: 10:08:41                  
Normalized form: Wed 2020-06-17 10:08:41 EDT
       (in UTC): Wed 2020-06-17 14:08:41 UTC
   UNIX seconds: @1592402921                
       From now: 11min ago
```

Why is the data copied from the journal not considered to be a valid timestamp? I have no idea. It seems pretty dumb to print the timestamps for the journal in a format that cannot be used by the tool designed to analyze timestamps. But look at the time specified as the beginning of the log:


```
[student@testvm1 ~]$ systemd-analyze timestamp "Wed 2020-06-17 10:08:41"
  Original form: Wed 2020-06-17 10:08:41    
Normalized form: Wed 2020-06-17 10:08:41 EDT
       (in UTC): Wed 2020-06-17 14:08:41 UTC
   UNIX seconds: @1592402921                
       From now: 15min ago                  
[student@testvm1 ~]$
```

OK, so that time is a valid timestamp. The key is that the `systemd-analyze` tool only recognizes the `DOW YYYY-MM-DD HH:MM:SS` format. As the error messages state, it does not recognize month names or standalone days of the month, such as 17. It is very exacting because the only way to ensure events are triggered by timers at desired points in time or intervals is to be completely accurate with how they are specified.

Any unambiguously expressed time, such as `2020-06-17 10:08:41`, is a timestamp because it can only occur once. A timestamp that will occur in the future can also be used in a systemd timer, and that timer will only trigger its defined action once.

A time expressed somewhat more ambiguously, such as `2025-*-* 22:15:00`, can only be a calendar time used in the `OnCalendar` statement in a timer unit file. This expression will trigger an event every day in the year 2025 at 22:15:00 (10:15:00pm).

But still—why not use valid timestamps in the journal output? I _still_ don't know, but with a bit of command-line manipulation, you can convert the default time display into valid timestamps. The `journalctl` command tool has some options that can display the timestamps in a format you can easily use with the `systemd-analyze` tool:


```
[root@testvm1 ~]# journalctl -o short-full
&lt;SNIP&gt;
Fri 2020-06-26 12:51:36 EDT testvm1.both.org systemd[1]: Finished Update UTMP about System Runlevel Changes.
Fri 2020-06-26 12:51:36 EDT testvm1.both.org systemd[1]: Startup finished in 2.265s (kernel) + 4.883s (initrd) + 22.645s (userspace) = 29.793s.
Fri 2020-06-26 12:51:36 EDT testvm1.both.org audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=systemd-update-utmp-runlevel&gt;
Fri 2020-06-26 12:51:36 EDT testvm1.both.org audit[1]: SERVICE_STOP pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=systemd-update-utmp-runlevel &gt;
Fri 2020-06-26 12:51:36 EDT testvm1.both.org crond[959]: (CRON) INFO (running with inotify support)
Fri 2020-06-26 12:51:36 EDT testvm1.both.org ModemManager[759]: &lt;info&gt;  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:03.0': not &gt;
Fri 2020-06-26 12:51:37 EDT testvm1.both.org VBoxService[804]: 16:51:37.196960 timesync vgsvcTimeSyncWorker: Radical guest time change: -14 388 436 32&gt;
Fri 2020-06-26 12:51:39 EDT testvm1.both.org chronyd[827]: Selected source 192.168.0.52
Fri 2020-06-26 12:51:39 EDT testvm1.both.org chronyd[827]: System clock TAI offset set to 37 seconds
&lt;SNIP&gt;
```

You can now use the timestamps like this:


```
[root@testvm1 ~]# systemd-analyze timestamp "2020-06-26 12:51:36"
  Original form: 2020-06-26 12:51:36        
Normalized form: Fri 2020-06-26 12:51:36 EDT
       (in UTC): Fri 2020-06-26 16:51:36 UTC
   UNIX seconds: @1593190296                
       From now: 2h 37min ago              
[root@testvm1 ~]#
```

You can also display the journal timestamps in a monotonic format that shows the number of seconds since boot:


```
[root@testvm1 ~]# journalctl -o short-monotonic
[    0.000000] testvm1.both.org kernel: Linux version 5.6.6-300.fc32.x86_64 ([mockbuild@bkernel03.phx2.fedoraproject.org][3]) (gcc version 10.0.1 20200328 &gt;
[    0.000000] testvm1.both.org kernel: Command line: BOOT_IMAGE=(hd0,msdos1)/vmlinuz-5.6.6-300.fc32.x86_64 root=/dev/mapper/VG01-root ro resume=/dev/&gt;
[    0.000000] testvm1.both.org kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] testvm1.both.org kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] testvm1.both.org kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.000000] testvm1.both.org kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] testvm1.both.org kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[    0.000000] testvm1.both.org kernel: BIOS-provided physical RAM map:
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dffeffff] usable
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x00000000dfff0000-0x00000000dfffffff] ACPI data
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
[    0.000000] testvm1.both.org kernel: BIOS-e820: [mem 0x0000000100000000-0x00000003373fffff] usable
[    0.000000] testvm1.both.org kernel: NX (Execute Disable) protection: active
[    0.000000] testvm1.both.org kernel: SMBIOS 2.5 present.
[    0.000000] testvm1.both.org kernel: DMI: innotek GmbH VirtualBox/VirtualBox, BIOS VirtualBox 12/01/2006
[    0.000000] testvm1.both.org kernel: Hypervisor detected: KVM
&lt;SNIP&gt;
[28829.016018] testvm1.both.org NetworkManager[760]: &lt;info&gt;  [1593219095.3936] dhcp4 (enp0s3): option requested_time_offset =&gt; '1'
[28829.016062] testvm1.both.org NetworkManager[760]: &lt;info&gt;  [1593219095.3936] dhcp4 (enp0s3): option requested_wpad       =&gt; '1'
[28829.016106] testvm1.both.org NetworkManager[760]: &lt;info&gt;  [1593219095.3936] dhcp4 (enp0s3): option routers              =&gt; '192.168.0.254'
[28829.016155] testvm1.both.org NetworkManager[760]: &lt;info&gt;  [1593219095.3936] dhcp4 (enp0s3): option subnet_mask          =&gt; '255.255.255.0'
[28829.016201] testvm1.both.org NetworkManager[760]: &lt;info&gt;  [1593219095.3936] dhcp4 (enp0s3): state changed extended -&gt; extended
[28829.019332] testvm1.both.org systemd[1]: Starting Network Manager Script Dispatcher Service...
[28829.028205] testvm1.both.org audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=NetworkManager-dispatcher comm="systemd" &gt;
[28829.028406] testvm1.both.org systemd[1]: Started Network Manager Script Dispatcher Service.
[28839.014035] testvm1.both.org systemd[1]: NetworkManager-dispatcher.service: Succeeded.
[28839.014496] testvm1.both.org audit[1]: SERVICE_STOP pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=NetworkManager-dispatcher comm="systemd" e&gt;
[29336.998580] testvm1.both.org systemd[1]: Starting system activity accounting tool...
[29337.443114] testvm1.both.org audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=sysstat-collect comm="systemd" exe="/usr/&gt;
[29337.443347] testvm1.both.org audit[1]: SERVICE_STOP pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=sysstat-collect comm="systemd" exe="/usr/l&gt;
[29337.443404] testvm1.both.org systemd[1]: sysstat-collect.service: Succeeded.
[29337.443504] testvm1.both.org systemd[1]: Finished system activity accounting tool.
[29394.784506] testvm1.both.org CROND[2253]: (root) CMD (run-parts /etc/cron.hourly)
[29394.792113] testvm1.both.org run-parts[2256]: (/etc/cron.hourly) starting 0anacron
[29394.799468] testvm1.both.org run-parts[2262]: (/etc/cron.hourly) finished 0anacron
```

Read the `journalctl` man page for a complete list of the timestamp format options (among other things).

### Timespans

Timespans are primarily used in systemd timers to define a specific span of time between events. This could be used to trigger events so that they occur a specified amount of time after system startup or after a previous instance of the same event. For example, here is a sample expression in the timer unit file to trigger an event 32 minutes after system startup:


```
`OnStartupSec=32m`
```

The default accuracy for triggering systemd timers is a time window starting at the specified time and lasting one minute. You can increase trigger timespan accuracy to within a microsecond by adding a statement like the following to the Timer section of the timer-unit file:


```
`AccuracySec=1us`
```

The `systemd-analyze timespan` command can help ensure you are using a valid timespan in the unit file. These samples will get you started:


```
[student@testvm1 ~]$ systemd-analyze timespan 15days
Original: 15days      
      μs: 1296000000000
   Human: 2w 1d        
[student@testvm1 ~]$ systemd-analyze timespan "15days 6h 32m"
Original: 15days 6h 32m
      μs: 1319520000000
   Human: 2w 1d 6h 32min
```

Experiment with these and some of your own:

  * `"255days 6h 31m"`
  * `"255days 6h 31m 24.568ms"`



### Final thoughts

Timespans are used to schedule timer events a specified interval after a defined event such as startup. Calendar timestamps can be used to schedule timer events on specific calendar days and times, either as one-offs or repeating. Timestamps are also used on systemd journal entries, although not in a default format that can be used directly in tools like `systemd-analyze`.

All of this was more than just a little confusing to me when I started working with systemd timers and creating calendar and timestamp expressions to trigger events. That was partly because of the similar—but not quite identical—formats used for specifying timestamps and calendar event trigger times. I hope that this has helped to clarify all of this for you.

In my next article, I will explore systemd journaling and related tools in more detail

### Resources

There is a great deal of information about systemd available on the internet, but much is terse, obtuse, or even misleading. In addition to the resources mentioned in this article, the following webpages offer more detailed and reliable information about systemd startup.

  * The Fedora Project has a good, practical [guide][4] [to systemd][4]. It has pretty much everything you need to know in order to configure, manage, and maintain a Fedora computer using systemd.
  * The Fedora Project also has a good [cheat sheet][5] that cross-references the old SystemV commands to comparable systemd ones.
  * For detailed technical information about systemd and the reasons for creating it, check out [Freedesktop.org][6]'s [description of systemd][7].
  * [Linux.com][8]'s "More systemd fun" offers more advanced systemd [information and tips][9].



There is also a series of deeply technical articles for Linux sysadmins by Lennart Poettering, the designer and primary developer of systemd. These articles were written between April 2010 and September 2011, but they are just as relevant now as they were then. Much of everything else good that has been written about systemd and its ecosystem is based on these papers.

  * [Rethinking PID 1][10]
  * [systemd for Administrators, Part I][11]
  * [systemd for Administrators, Part II][12]
  * [systemd for Administrators, Part III][13]
  * [systemd for Administrators, Part IV][14]
  * [systemd for Administrators, Part V][15]
  * [systemd for Administrators, Part VI][16]
  * [systemd for Administrators, Part VII][17]
  * [systemd for Administrators, Part VIII][18]
  * [systemd for Administrators, Part IX][19]
  * [systemd for Administrators, Part X][20]
  * [systemd for Administrators, Part XI][21]



--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/systemd-calendar-timespans

作者：[David Both][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/dboth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/calendar.jpg?itok=jEKbhvDT (Calendar close up snapshot)
[2]: https://opensource.com/article/20/6/systemd-timers
[3]: mailto:mockbuild@bkernel03.phx2.fedoraproject.org
[4]: https://docs.fedoraproject.org/en-US/quick-docs/understanding-and-administering-systemd/index.html
[5]: https://fedoraproject.org/wiki/SysVinit_to_Systemd_Cheatsheet
[6]: http://Freedesktop.org
[7]: http://www.freedesktop.org/wiki/Software/systemd
[8]: http://Linux.com
[9]: https://www.linux.com/training-tutorials/more-systemd-fun-blame-game-and-stopping-services-prejudice/
[10]: http://0pointer.de/blog/projects/systemd.html
[11]: http://0pointer.de/blog/projects/systemd-for-admins-1.html
[12]: http://0pointer.de/blog/projects/systemd-for-admins-2.html
[13]: http://0pointer.de/blog/projects/systemd-for-admins-3.html
[14]: http://0pointer.de/blog/projects/systemd-for-admins-4.html
[15]: http://0pointer.de/blog/projects/three-levels-of-off.html
[16]: http://0pointer.de/blog/projects/changing-roots
[17]: http://0pointer.de/blog/projects/blame-game.html
[18]: http://0pointer.de/blog/projects/the-new-configuration-files.html
[19]: http://0pointer.de/blog/projects/on-etc-sysinit.html
[20]: http://0pointer.de/blog/projects/instances.html
[21]: http://0pointer.de/blog/projects/inetd.html
