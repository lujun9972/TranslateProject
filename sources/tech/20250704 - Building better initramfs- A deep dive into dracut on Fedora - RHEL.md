[#]: subject: "🧱 Building better initramfs: A deep dive into dracut on Fedora & RHEL"
[#]: via: "https://fedoramagazine.org/%f0%9f%a7%b1-building-better-initramfs-a-deep-dive-into-dracut-on-fedora-rhel/"
[#]: author: "Suraj Rajendra Patil https://fedoramagazine.org/author/suraj522/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

🧱 Building better initramfs: A deep dive into dracut on Fedora & RHEL
======

![][1]

Understanding how to use _dracut_ is critical for kernel upgrades, troubleshooting boot issues, disk migration, encryption, and even kernel debugging.

## 🚀 Introduction: What is _dracut_?

_dracut_ is a powerful tool used in Fedora, RHEL, and other distributions to create and manage _initramfs_ images—the initial RAM filesystem used during system boot. Unlike older tools like _mkinitrd_ , _dracut_ uses a modular approach, allowing you to build minimal or specialized initramfs tailored to your system.

## 📦 Installing dracut (if not already available)

_dracut_ comes pre-installed in Fedora and RHEL. If it is missing, install it with:

```

    $ sudo dnf install dracut

```

Verify the version:

```

    $ dracut --version

```

## 📂 Basic usage

### 📌 Regenerate the current initramfs

```

    $ sudo dracut --force

```

This regenerates the initramfs for the currently running kernel.

### 📌 Generate initramfs for a specific kernel

```

    $ sudo dracut --force /boot/initramfs-$(uname -r).img $(uname -r)

```

Or Manually!

```

    $ sudo dracut --force
    $ sudo dracut --force /boot/initramfs-5.14.0-327.el9.x86_64.img 5.14.0-327.el9.x86_64

```

## 🧠 Understanding key dracut options (with examples)

### –force

Force regeneration even if the file already exists:

```

    $ sudo dracut --force

```

### –kver <kernel-version>

Generate initramfs for a specific kernel:

```

    $ sudo dracut --force --kver 5.14.0-327.el9.x86_64

```

### –add <module> / –omit <module>

Include or exclude specific modules (e.g., _lvm_ , _crypt_ , _network_ ).

**Include LVM module only:**

```

    $ sudo dracut --force --add lvm

```

**Omit network module:**

```

    $ sudo dracut --force --omit network

```

### –no-hostonly

Build a generic initramfs that boots on any compatible machine:

```

    $ sudo dracut --force --no-hostonly

```

### –hostonly

Create a host-specific image for minimal size:

```

    $ sudo dracut --force --hostonly

```

### –print-cmdline

Show the kernel command line:

```

    $ dracut --print-cmdline

```

### –list-modules

List all available dracut modules:

```

    $ dracut --list-modules

```

### –add-drivers “driver1 driver2”

Include specific drivers:

```

    $ sudo dracut --add-drivers "nvme ahci" --force

```

## 🧪 Test cases and real-world scenarios

1\. **LVM root disk fails to boot after migration**

```

    $ sudo dracut --force --add lvm --hostonly

```

2\. **Initramfs too large**

Shrink it by omitting unused modules:

```

    $ sudo dracut --force --omit network --omit plymouth

```

3\. **Generic initramfs for provisioning**

```

    $ sudo dracut --force --no-hostonly --add network --add nfs

```

4\. **Rebuild initramfs for rollback kernel**

```

    $ sudo dracut --force /boot/initramfs-5.14.0-362.el9.x86_64.img 5.14.0-362.el9.x86_64

```

## 🪛 Advanced use: Debugging and analysis

Enable verbose output:

```

    $ sudo dracut -v --force

```

Enter the dracut shell if boot fails:

Use rd.break in the GRUB kernel line.

## 📖 Where is dracut configuration stored?

There are two locations where configuration setting may occur.

The global settings location is at:

/etc/dracut.conf

and the drop-in location is at:

/etc/dracut.conf.d/*.conf

Example using the drop-in location:

```

    $ cat /etc/dracut.conf.d/custom.conf

```

The contents might appear as follows for omitting and adding modules:

```

    omit_dracutmodules+=" plymouth network "
    add_dracutmodules+=" crypt lvm "

```

> ⚠️ **Note** : Always include a space at the beginning and end of the value when using += in these configuration files. These files are sourced as Bash scripts, so
>
> add_dracutmodules+=" crypt lvm "
>
> ensures proper spacing when multiple config files are concatenated. Without the spaces, the resulting string could concatenate improperly (e.g., mod2mod3) and cause module loading failures.

## 🧠 Deep dive: /usr/lib/dracut/modules.d/ – the heart of dracut

The directory _/usr/lib/dracut/modules.d_ includes all module definitions. Each contains:

  * A module-setup.sh script
  * Supporting scripts and binaries
  * Udev rules, hooks, and configs



List the modules using the following command:

$ ls /usr/lib/dracut/modules.d/

Example output:

```

    01fips/ 30crypt/ 45ifcfg/ 90lvm/ 95resume/
    02systemd/ 40network/ 50drm/ 91crypt-gpg/ 98selinux/

```

Inspect specific module content ( _module-setup.sh_ , in this example) using this:

```

    $ cat /usr/lib/dracut/modules.d/90lvm/module-setup.sh

```

You can also create custom modules at this location for specialized logic.

## 🏁 Final thoughts

_dracut_ is more than a utility—it’s your boot-time engineer. From creating lightweight images to resolving boot failures, it offers unparalleled flexibility.

Explore man dracut, read through /usr/lib/dracut/modules.d/, and start customizing.

> 💡 _This article is dedicated to my wife, Rupali Suraj Patil, for her continuous support and encouragement._

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/%f0%9f%a7%b1-building-better-initramfs-a-deep-dive-into-dracut-on-fedora-rhel/

作者：[Suraj Rajendra Patil][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/suraj522/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/06/dracut-816x345.jpeg
