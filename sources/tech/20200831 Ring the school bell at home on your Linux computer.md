[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Ring the school bell at home on your Linux computer)
[#]: via: (https://opensource.com/article/20/9/linux-school-bell)
[#]: author: (Alan Formy-Duval https://opensource.com/users/alanfdoss)

Ring the school bell at home on your Linux computer
======
Bring familiar sounds from school to your virtual students with these
Linux tools.
![Alarm clocks with different time][1]

Many students are used to the bell ringing to signal the beginning of each school day, class changes, and dismissal time. There's no feeling quite like that last bell at the end of last period telling you are free to leave the building. But virtual and homeschool students probably don't get to hear that familiar ring and may even miss it. We're all trying to restore a bit of normalcy these days for the kids who may be longing for the sights, smells, and sounds of their school building.

There is a simple way to use a Linux computer to ring that bell. The project has only three steps: First, download a sound file for a bell, tone, or sound of your choice. Second, locate or install a simple audio player. Finally, enter your child's schedule into a cron configuration.

### The bell

The first task is to locate a good bell sound. I found an MP3 file from the [Free Sounds Library][2], where all the sound files are under the Creative Commons license. I downloaded and saved the file to my home directory:


```
$ unzip short-school-bell-sound-effect.zip
Archive:  short-school-bell-sound-effect.zip
  inflating: Read.txt                
  inflating: short-school-bell-sound-effect.mp3
```

### The player

There are several command-line tools for playing audio from the Linux command prompt. So, this might be an area of user preference since everyone has a favorite.

I wanted an audio player that would be very simple and not output anything to standard out (stdout). The SDL Library includes the playsound command, which is very easy to use. So, I installed the [SDL_sound][3] package.

I installed it on my Fedora 32 workstation, along with several required dependencies, using `dnf`:


```
$ sudo dnf install SDL_sound
[sudo] password for alan:
Dependencies resolved.
==============================================================================
 Package         Architecture       Version          Repository    Size
==============================================================================
Installing:
 SDL_sound       x86_64             1.0.3-25.fc32    fedora        113 k
Installing dependencies:
 SDL             x86_64             1.2.15-43.fc32   fedora        213 k
 libmikmod       x86_64             3.3.11.1-8.fc32  fedora        154 k
 physfs          x86_64             3.0.2-3.fc32     fedora         85 k

Transaction Summary
==============================================================================
Install  4 Packages
```

One nice thing is these are small files, much smaller than the feature-rich GUI audio players such as [Rhythmbox][4] and [Audacious][5].

After installing SDL_sound, I quickly tested the capability to play the bell sound MP3 file. Turn up your volume!


```
`$ playsound short-school-bell-sound-effect.mp3`
```

### The schedule

The last step uses the Linux cron scheduler, using commands that coincide with the school schedule. For example, suppose that the school bell rings Monday through Friday at 8:15am to signal the beginning of classes, then hourly for class period changes, and finally at 2:30pm to end the day.

Use the command `crontab -e` to edit the configuration. Cron does not interpret the commented lines; they only clarify how each line tells cron to behave:


```
# Once at 8:15AM, Monday thru Friday
15 8 * * 1-5 playsound ~/short-school-bell-sound-effect.mp3
# Hourly from 9:00AM thru 2:00PM, Monday thru Friday
00 9-14/1 * * 1-5 playsound ~/short-school-bell-sound-effect.mp3
# Once at 2:30PM, Monday thru Friday
30 14 * * 1-5 playsound ~/short-school-bell-sound-effect.mp3
```

Tailor the configuration for your student's schedule.

The syntax used by the cron scheduling mechanism can take some time to learn. You can check out this [online assistant][6] for help.

Once you save the configuration, you can view it with the command `crontab -l`, which produces output exactly as it appears above.

### That's it!

The bell will now ring throughout your virtual student's day, just like if they were sitting in their classroom.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/9/linux-school-bell

作者：[Alan Formy-Duval][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/alanfdoss
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/clocks_time.png?itok=_ID09GDk (Alarm clocks with different time)
[2]: https://www.freesoundslibrary.com
[3]: https://github.com/Ancurio/SDL_sound
[4]: https://wiki.gnome.org/Apps/Rhythmbox
[5]: https://audacious-media-player.org/
[6]: http://corntab.com
