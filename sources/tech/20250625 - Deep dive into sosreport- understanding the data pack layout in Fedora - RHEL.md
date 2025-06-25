[#]: subject: "🔧 Deep dive into sosreport: understanding the data pack layout in Fedora & RHEL"
[#]: via: "https://fedoramagazine.org/%f0%9f%94%a7-deep-dive-into-sosreport-understanding-the-data-pack-layout-in-fedora-rhel/"
[#]: author: "Suraj Rajendra Patil https://fedoramagazine.org/author/suraj522/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

🔧 Deep dive into sosreport: understanding the data pack layout in Fedora & RHEL
======

![][1]

This article will describe the content and structure of the _sosreport_ output. The aim is to improve its usefullness through a better understanding of its contents.

## _**🧰 What is sosreport?**_

_sosreport_ is a powerful command-line utility available on Fedora, Red Hat Enterprise Linux (RHEL), CentOS, and other RHEL-based systems to collect a comprehensive snapshot of the system’s configuration, logs, services, and state. The primary use is for diagnosing issues, especially during support cases with Red Hat or other vendors.

When executed, _sosreport_ runs a series of modular plugins that collect relevant data from various subsystems like networking, storage, SELinux, Docker, and more. The resulting report is packaged into a compressed tarball, which can be securely shared with support teams to expedite troubleshooting.

In essence, _sosreport_ acts as a black box recorder for Linux — capturing everything from system logs and kernel messages to active configurations and command outputs — helping support engineers trace problems without needing direct access to the system.

## _**🛠️ How to Generate a sosreport**_

To use _sosreport_ on Fedora, RHEL, or CentOS, run the following command as root or with sudo:

```

    sudo sosreport

```

This command collects system configuration, logs, and command outputs using various plugins. After a few minutes, it generates a compressed tarball in /var/tmp/ (or a similar location), typically named like:

```

    sosreport-hostname-20250623-123456.tar.xz

```

You may be prompted to enter a case ID or other metadata, depending on your system configuration or support workflow.

The _sosreport_ generated tarball contains a detailed snapshot of the system’s health and configuration. It has a well-organized structure which reflects the data collected from the myriad Linux subsystems.

Exploring _sosreport_ output is challenging due to the sheer volume of logs, configuration files, and system command outputs it contains. However, understanding its layout is key for support engineers and sysadmins to quickly locate and interpret crucial diagnostic information.

## 📁 sosreport directory layout

When the tarball is unpacked, the directory structure typically resembles this:

```

    .
    ├── ./boot
    ├── ./etc
    ├── ./lib -> usr/lib
    ├── ./opt
    ├── ./proc
    ├── ./run
    ├── ./sos_commands
    ├── ./sos_logs
    ├── ./sos_reports
    ├── ./sos_strings
    ├── ./sys
    ├── ./usr
    ├── ./var
    └── ./EXTRAS

```

### CORE Breakdown:

  * Most directories mimic a standard Linux root filesystem and primarily contain configuration files.
  * The directories that _don’t_ appear in a regular root filesystem include:
    * sos_command
    * sos_logs
    * sos_reports
    * sos_strings
    * _EXTRAS_



### 🔍 Key directories in detail

#### 🔊 _sos_commands/_

This contains output from commands executed by each plugin. Its structure is plugin-specific:

```

    ./sos_commands/
    ├── apparmor/
    ├── docker/
    ├── memory/
    ├── networkmanager/
    ├── process/
    │ ├── lsof_M_-n_-l_-c
    │ ├── pidstat_-p_ALL_-rudvwsRU_--human_-h
    │ ├── ps_auxwwwm
    │ └── pstree_-lp

```

Each file name matches the Linux command used, with all options. The contents are the actual command output, making the plugin behavior transparent.

#### 📊 _sos_reports/_

This directory contains multiple formats that index and summarize the entire _sosreport_ :

  * _sos.json_ : A machine-readable index of all collected files and commands.
  * _manifest.json_ : Describes how _sosreport_ executed – timestamps, plugins used, obfuscation done, errors, etc.
  * HTML output for easy browsing via browser.



#### 📃 _sos_logs/_

Contains logs from the execution of _sosreport_ itself.

  * _sos.log_ : Primary log file that highlights any errors or issues during data collection.



#### 📰 _sos_strings/_

  * Contains journal logs for up to **30 days** , extracted using _journalctl_
  * Can be quite large, especially on heavily used systems
  * Structured into subdirectories like _logs/_ or _networkmanager/_



#### 🔒 _EXTRAS/_

This is not a default part of an _sosreport_. It is created by the _sos_extras_ plugin and used to collect any **custom user-defined files**.

## 🚀 Why this layout matters

  * **Speed** : Logical grouping of directories help engineers drill down without manually parsing GigaBytes of log files.
  * **Traceability** : Knowing where each file came from and what command produced it enhances reproducibility.
  * **Automation** : Tools like _soscleaner_ or _sos-analyzer_ rely on this structure for automated diagnostics.



## ✅ Final thoughts

While _sosreport_ is a powerful diagnostic tool, its effectiveness hinges on understanding its structure. With familiarity, engineers can isolate root causes of failures, uncover misconfigurations, and collaborate more efficiently with support teams. If you haven’t yet opened one up manually, try it — there’s a lot to learn from the insides!

_This is my first Fedora Magazine article, dedicated to my wife Rupali Suraj Patil — my constant source of inspiration._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/%f0%9f%94%a7-deep-dive-into-sosreport-understanding-the-data-pack-layout-in-fedora-rhel/

作者：[Suraj Rajendra Patil][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/suraj522/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/06/Fedora-1-816x345.jpg
