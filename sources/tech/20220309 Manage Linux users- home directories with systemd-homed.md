[#]: subject: "Manage Linux users' home directories with systemd-homed"
[#]: via: "https://opensource.com/article/22/3/manage-users-home-directory-systemd-homed"
[#]: author: " "
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Manage Linux users' home directories with systemd-homed
======
Sysadmins can use the systemd-homed service for a secure form of
management of roaming users' home directories.
![people in different locations who are part of the same team][1]

The entire systemd concept and implementation have introduced many changes since it began to replace the old SystemV startup and init tools. Over time, systemd has been extended into many other segments of the Linux environment.

One relatively new service, systemd-homed, extends the reach of systemd into the management of users' home directories. The feature enforces human user access only and restricts system users in the User ID (UID) range between 0 and 999. I support the [systemd plan to take over the world][2], but I wondered if this was a bit excessive. Then I did some research.

### What is systemd-homed?

The systemd-homed service supports user account portability independent of the underlying computer system. A practical example is to carry around your home directory on a USB thumb drive and plug it into any system which would automatically recognize and mount it. According to Lennart Poettering, lead developer of systemd, access to a user's home directory should not be allowed to anyone unless the user is logged in. The systemd-homed service is designed to enhance security, especially for mobile devices such as laptops. It also seems like a tool that might be useful with [containers][3].

This objective can only be achieved if the home directory contains all user metadata. The ~/.identity file stores user account information, which is only accessible to systemd-homed when the password is entered. This file holds all of the account metadata, including everything Linux needs to know about you, so that the home directory is portable to any Linux host that uses systemd-homed. This approach prevents having an account with a stored password on every system you might need to use.

The home directory can also be encrypted using your password. Under systemd-homed, your home directory stores your password with all of your user metadata. Your encrypted password is not stored anywhere else thus cannot be accessed by anyone. Although the methods used to encrypt and store passwords for modern Linux systems are considered to be unbreakable, the best safeguard is to prevent them from being accessed in the first place. Assumptions about the invulnerability of their security have led many to ruin.

This service is primarily intended for use with portable devices such as laptops. Poettering states, "Homed is intended primarily for client machines, i.e., laptops and thus machines you typically ssh from a lot more than ssh to, if you follow what I mean." It is not intended for use on servers or workstations that are tethered to a single location by cables or locked into a server room.

The systemd-homed service is enabled by default on new installations—at least for Fedora, which is the distro that I use. This configuration is by design, and I don't expect that to change. User accounts are not affected or altered in any way on systems with existing filesystems, upgrades or reinstallations that keep the existing partitions, and logical volumes.

### Creating controlled users

Traditional tools such as `useradd` create accounts and home directories that systemd-homed does not manage. Therefore, if you continue to use the conventional user management tools, the home directories on your home directories are not managed by systemd-homed. This is also the case with the non-root user account created during a new installation.

### The homectl command

The `homectl` command creates user accounts that systemd-homed manages. Using the `homectl` command to create a new account generates the metadata needed to make the home directory portable.

The `homectl` command man page has a good explanation of the objectives and function of the systemd-homed service. However, reading the `homectl` man page is quite interesting, especially the Example section. Of the five examples, three show how to create user accounts with specific limits imposed, such as a maximum number of concurrent processes or a maximum amount of disk space.

In a non-homectl setup, the `/etc/security/limits.conf` file imposes these limits. The only advantage I can see to this is that it adds a user and applies the limits with a single command. With the traditional method, the sysadmin must configure the `limits.conf` file manually.

### Limitations

The only significant limitation I am aware of is that it is not possible to access a user home directory remotely using OpenSSH. This limitation is due to the current inability of [PAM][4] to provide access to a home directory managed by `homectl`. Poettering seems doubtful that this can be overcome. This issue would prevent me from using systemd-homed for my home directory on my primary workstation or even my laptop. I typically log into both computers remotely several times per day using SSH, so this is a showstopper for me.

The other concern I can see is that you still need a Linux computer for use with a USB thumb drive with your home directory on it, and that computer needs to have systemd-homed running.

### It is optional

You don't have to use it, however. I plan to continue using the traditional tools for user management to support my workflow. The default for the few distros I have some little knowledge of, including Fedora, is for the systemd-homed service to be enabled and running. _You can disable and stop the systemd-homed service without impacting traditional user accounts._

### Final thoughts

Sysadmins can use the systemd-homed service for a secure form of management of roaming users' home directories. It is useful on portable devices like laptops and can be especially useful for users who carry a thumb drive containing only their home directories to plug it into any convenient Linux computer.

The primary limitation of using systemd-homed is that it is impossible to log in remotely using SSH. And even though the systemd-homed is enabled by default, it does not affect home directories created with the `useradd` command. I do need to point out that—like many systemd tools—systemd-homed is optional. So I just stopped and disabled the service.

If I need to take my home directory in a package smaller than my laptop, I can just use a live USB with persistent storage.

#### Resources

  * <https://systemd.io/HOME_DIRECTORY/>
  * <https://www.freedesktop.org/software/systemd/man/homectl.html>
  * <https://www.freedesktop.org/software/systemd/man/systemd-homed.service.html>
  * <https://wiki.archlinux.org/title/Systemd-homed>



--------------------------------------------------------------------------------

via: https://opensource.com/article/22/3/manage-users-home-directory-systemd-homed

作者：[][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: 
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/connection_people_team_collaboration.png?itok=0_vQT8xV (people in different locations who are part of the same team)
[2]: https://opensource.com/article/21/5/systemd
[3]: https://opensource.com/tags/containers
[4]: https://www.redhat.com/sysadmin/pluggable-authentication-modules-pam
