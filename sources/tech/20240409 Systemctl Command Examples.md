[#]: subject: "Systemctl Command Examples"
[#]: via: "https://itsfoss.com/systemctl-command/"
[#]: author: "Sagar Sharma https://itsfoss.com/author/sagar/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Systemctl Command Examples
======

[![Warp Terminal][1]][2]

If you are using any popular Linux distribution including Debian, Ubuntu, Arch, openSUSE, or Fedora, your system uses systemd as its init system.

Sure, there are [controversies surrounding systemd][3]. But, it is the most used init system.

In a systemd-equipped distro, there is a command that could make your life easy. It is the **systemctl** command, used to interact with the systemd init service. System administrators always use this command, but it is also useful for end-users wishing to take control via the terminal.

For instance, you can use the systemctl command to [list services in Linux][4].

So in this tutorial, I will walk you through all the essentials you need to learn to use the systemctl command:

  * **The basic syntax and common flags.**
  * **Practical examples of the command.**
  * **Practice questions to get better at using the systemctl command.**



### Here's How to Use The Systemctl Command

To use the systemctl command, it is important to learn the syntax and available options.

Here's how the syntax looks like:

```

    systemctl <command> <service_name>

```

Here,

  * `<command>`: this is where you specify the action you want to execute over the service such as `stop`, `start`, etc.
  * `<service_name>`: this is where you specify the name of the service that you would like to work with.



To manage services, you have various commands to use with the systemctl command, here's a list of one of the most useful ones:

**Command** | **Description**
---|---
`systemctl start [service]` | Start a service and run it in the background.
`systemctl stop [service]` | Stop a currently running service.
`systemctl enable [service]` | Configure a service to start automatically at system boot.
`systemctl disable [service]` | Configure a service to not start automatically at system boot.
`systemctl status [service]` | Display the current status (running, stopped, etc.) of a service.
`systemctl restart [service]` | Stop a running service and then start it again.
`systemctl reload [service]` | Reload the configuration of a service without stopping it.
`systemctl mask [service]` | Prevent a service from being started, even manually.
`systemctl unmask [service]` | Allow a previously masked service to be started.
`systemctl set-default [target]` | Change the default system target (runlevel) for the next boot.
`systemctl list-unit-files` | List all installed unit files and their current state (enabled/disabled).
`systemctl list-dependencies [unit]` | Show the dependencies (other units) required for a specific unit.
`systemctl list-sockets` | List all active sockets (for inter-process communication).
`systemctl list-jobs` | Show all currently active systemd jobs (ongoing operations).
`systemctl list-units` | List all loaded and active systemd units (services, sockets, etc.).

Now, let's take a look at some practical examples of the systemctl command.

### Practical examples of the systemctl command

In this section, I share some practical examples of the systemctl command, ranging from the basics to the advanced ones.

Let's start with how you can start your service.

#### 1\. Start a service

In most cases, the installed service gets activated by default, but there are times when you are required to do that manually.

To start a service, you need to use the `start` flag with the systemctl command and append the name of the service, as shown here:

```

    sudo systemctl start <service_name>

```

Let's say I want to start the Apache server, I'll be using the following:

```

    sudo systemctl start apache2

```

![][5]

#### 2\. Enable a service

When you start a service, it will only be effective until the next boot. This means the service will be turned off when you reboot your system.

To tackle this situation, you want a service to start automatically when you boot your system and for that purpose, you can use the `enable` flag as shown here:

```

    sudo systemctl enable <service_name>

```

For example, if I want to enable Apache service, then I'll use the following:

```

    sudo systemctl enable apache2

```

![][6]

#### 3\. Stop a service

When you intend to modify an active service, the first step you have to perform is to stop the service and for that purpose, you use the `stop` flag as shown here:

```

    sudo systemctl stop <service_name>

```

For example, here's how you stop the Apache service:

```

    sudo systemctl stop apache2

```

![][7]

**Suggested Read 📖**

![][8]

#### 4\. Disable a service

If you've enabled a service in the past, and now you don't want it to be active at every system boot, you can disable it.

To disable a service, you use the `disable` flag as shown here:

```

    sudo systemctl disable <service_name>

```

To disable the Apache service, I use the following command:

```

    sudo systemctl disable apache2

```

![][9]

#### 5\. Check the status of a service

Checking the status before performing any action over a service is highly recommended and can save you a lot of time.

To check the status of a service, all you have to do is append the name of the service to the `status` flag as shown here:

```

    systemctl status <service_name>

```

Here, I check the status of the Apache service:

```

    systemctl status apache2

```

![][10]

As I disabled the Apache service earlier, the above output suggests that the service is disabled.

But depending on your service, you may receive a different status of the service, and here's what it means:

**Status** | **Description**
---|---
`active (running)` | The service is currently running in the background.
`active (exited)` | The service was a one-time or periodic task that has completed its execution.
`active (waiting)` | The service is running but waiting for a specific event or condition to occur before proceeding.
`inactive` | The service is not currently running.
`enabled` | The service is configured to start automatically when the system boots up.
`disabled` | The service is configured to not start automatically at system boot.
`static` | This service cannot be managed by systemd or the systemctl command; it needs to be managed manually.
`masked` | The service is masked, which means it is prevented from being started (needs to be unmasked before it can run).
`alias` | The service name is an alias, and the service is a symbolic link pointing to another unit file.
`linked` | The service or unit file is symbolically linked to another unit file.

#### 6\. Restart a service

Once you modify the service configuration, or if it is not responding, then restarting a service can be helpful.

To restart a service, you use the `restart` flag as shown here:

```

    sudo systemctl restart <service_name>

```

For example, my Apache server was not responding, so if I were to restart the service, then I use the following command:

```

    sudo systemctl restart apache2

```

**Related Read 📖**

![][8]

#### 7\. Reload a service

```

    sudo systemctl unmask <service_name>

```

You reload a service when you make changes to the service configuration, and you want to apply changes without restarting the entire service.

```

    sudo systemctl unmask <service_name>

```

To reload a service, you use the `reload` flag as shown here:

```

    sudo systemctl reload <service_name>

```

For example, I made a few changes to the Apache service and now if I were to reload the Apache service, here is what I type in the terminal:

```

    sudo systemctl reload apache2

```

#### 8\. Mask a service

Masking a service is the most efficient way to prevent that service from being started, either manually or automatically, during system boot.

Think of it as a more robust version of stopping the service 😉.

To mask a service, you use the `mask` flag as shown here:

```

    sudo systemctl mask <service_name>

```

Here's how the command would look for the Apache service:

```

    sudo systemctl mask apache2

```

![][11]

Whenever you mask the service, you see a symlink created which redirects the service's configuration file to the null device (`/dev/null`). This means you cannot start the service by any means until it is unmasked.

#### 9\. Unmask a service

If you want to start the masked service, it needs to be unmasked first!

To unmask a service, you use the `unmask` flag as shown here:

```

    sudo systemctl unmask <service_name>

```

Just type in the command like this:

```

    sudo systemctl unmask apache2

```

![][12]

As you can see, it removed the symlink pointing to `/dev/null`.

#### 10\. Set the default target

Setting a default target refers to changing the default operational mode or runlevel that the system will enter after booting up.

One good example of setting a default target is to choose the user interface to boot, such as you can either boot to CLI mode or GUI.

To set a default target, you use the `set-default` flag as shown here:

```

    sudo systemctl set-default <target-name>

```

For example, if you want to boot into the GUI, then I will set the default target to `graphical.target` as shown here:

```

    sudo systemctl set-default graphical.target

```

Apart from the GUI target, you have other options as well:

**Target** | **Description**
---|---
`multi-user.target` | This target starts the system with networking enabled, suitable for servers or non-graphical workstations.
`rescue.target` | This target is useful for system recovery or troubleshooting when the system cannot boot into the regular multi-user mode.
`emergency.target` | This target provides an emergency environment for system maintenance or repair when the system is in a critically broken state.
`reboot.target` | This is typically used for one-time reboots or in automated scripts.
`poweroff.target` | This is typically used for one-time shutdowns or in automated scripts.
`hibernate.target` | Sets the system to hibernate (save system state to disk and power off) as the default target, Only available if the system supports hibernation.
`hybrid-sleep.target` | Sets the system to enter a hybrid sleep mode (a combination of hibernation and sleep) as the default target, Only available if the system supports hybrid sleep.

**Suggested Read 📖**

![][8]

#### 11\. List unit files

Unit files are plain text configuration files that are used to define and manage system services and units.

You can list all the unit files by executing the following command:

```

    systemctl list-unit-files

```

![][13]

#### 12\. List of all active sockets

When you list all the active sockets, you get insight into the inter-process communication channels established on a systemd-based system.

To list all the active sockets, use the given command:

```

    systemctl list-sockets

```

![][14]

And there you have a list of all the sockets which are listening for the incoming requests.

### Practice questions 📓

Once you know the basics of the systemctl command, it is important to practice getting better at using the command.

Here are some practice questions for the systemctl command:

  1. How would you check the status of the `httpd` service using `systemctl`?
  2. Write the command to start the `sshd` service if it's not already running.
  3. You want to enable the `mysqld` service to start automatically at system boot. What command would you use to do this?
  4. Suppose you need to reload the configuration of the `nginx` service without interrupting its operation. What `systemctl` command would you use?
  5. Your system is currently set to boot into the `multi-user.target` by default. You want to change the default target to `graphical.target` for the next boot. How would you use to accomplish this?



If you encounter any difficulty solving the above questions, you can post your queries in [our community forum][15] or drop a comment below.

### Wrapping Up

Now that you know the essentials of systemctl command, what next?

Well, if you are all about exploring and experimenting, you can create your own systemd service. Here's how to [write your own systemd service in Linux:][16]

![][17]

Are you a new learner looking to explore Linux commands? You might want to start with the fundamentals:

![][8]

_💬 Did I miss a variation of the systemctl command important to you? How do you use it for your use-case? Please let me know in the comments._

--------------------------------------------------------------------------------

via: https://itsfoss.com/systemctl-command/

作者：[Sagar Sharma][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sagar/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp-terminal.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/systemd-init/
[4]: https://itsfoss.com/linux-list-services/
[5]: https://itsfoss.com/content/images/2024/04/Start-a-service-using-the-systemctl-command.png
[6]: https://itsfoss.com/content/images/2024/04/Enable-a-service-using-the-systemctl-command.png
[7]: https://itsfoss.com/content/images/2024/04/Stop-the-service-using-the-systemctl-command.png
[8]: https://itsfoss.com/content/images/size/w256h256/2022/12/android-chrome-192x192.png
[9]: https://itsfoss.com/content/images/2024/04/Disable-a-service-using-the-systemctl-command.png
[10]: https://itsfoss.com/content/images/2024/04/Check-the-status-of-a-service-using-the-systemctl-command.png
[11]: https://itsfoss.com/content/images/2024/04/Mask-a-service-using-the-systemctl-command.png
[12]: https://itsfoss.com/content/images/2024/04/Unmask-service-using-the-systemctl-command.png
[13]: https://itsfoss.com/content/images/2024/04/List-unit-files-in-linux.png
[14]: https://itsfoss.com/content/images/2024/04/List-all-the-active-sockets-using-the-systemctl-command.png
[15]: https://itsfoss.community/
[16]: https://linuxhandbook.com/create-systemd-services/
[17]: https://linuxhandbook.com/content/images/size/w256h256/2021/08/Linux-Handbook-New-Logo.png
