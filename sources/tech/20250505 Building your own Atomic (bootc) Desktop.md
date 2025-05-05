[#]: subject: "Building your own Atomic (bootc) Desktop"
[#]: via: "https://fedoramagazine.org/building-your-own-atomic-bootc-desktop/"
[#]: author: "Daniel Mendizabal https://fedoramagazine.org/author/sigulete/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Building your own Atomic (bootc) Desktop
======

![][1]

Photo by [Jason Dela Cueva][2] on [Unsplash][3] (cropped)

Bootc and associated tools provide the basis for building a personalised desktop. This article will describe the process to build your own custom installation.

### Disclaimer

Building and using a custom installation is “at your own risk”. Your installation may be harder to find support for when compared with a mainstream solution.

### Motivation

There has been an increasing interest in atomic distros, which offer significant benefits in terms of stability and security.

These distros apply updates as a single transaction, known as atomic upgrades, which means if an update doesn’t work as expected, the system can instantly roll back to its last stable state, saving users from potential issues. The immutable nature of the filesystem components reduces the risk of system corruption and unauthorised modifications as the core system files are read-only, making them impossible to modify.

If you are planning to spin off various instances from the same image (e.g. setting up computers for members of your family or work), atomic distros provide a reliable desktop experience where every instance of the desktop is consistent with each other, reducing discrepancies in software versions and behaviour.

Mainstream sources like Fedora and Universal Blue offer various atomic desktops with curated configurations and package selections for the average user. But what if you’re ready to take control of your desktop and customise it entirely, from packages and configurations to firewall, DNS, and update schedules?

Thanks to bootc and the associated tools, building a personalised desktop experience is no longer difficult.

### What is bootc?

Using existing container building techniques, bootc allows you to build your own OS. Container images adhere to the [OCI specification][4] and utilise container tools for building and transporting your containers. Once installed on a node, the container functions as a regular OS.

The filesystem structure follows ostree specifications:

  * The _/usr_ directory is read-only, with all changes managed by the container image.
  * The _/etc_ directory is editable, but any changes applied in the container image will be transferred to the node unless the file was modified locally.
  * Changes to _/var_ (including _/var/home_ ) are made during the first boot. Afterwards, _/var_ remains untouched.



You can find the full documentation for bootc here: <https://bootc-dev.github.io/bootc/>

### Creating your own bootc desktop

The approach described in this article uses _quay.io/fedora/fedora-bootc_ as a base image to create a customizable container for building your personalised Fedora KDE atomic desktop.

Although tailored to KDE Plasma, most of the concepts and methodologies described here also apply to other desktop environments.

### The kde-bootc repository

I published [kde-bootc][5] as a repository available in GitHub, and I will use it as a reference. It will help this explanation providing additional details, and a source to clone and experiment. You may wish to clone kde-bootc to following along.

**Folder structure:**

  * scripts/
  * system/
  * systemd/
  * Containerfile



_**scripts:**_ Scripts to be ran from the _Containerfile_ during building
_**system:**_ Files to be copied to _/usr_ and _/etc_
_**systemd:**_ Systemd unit files to be copied to _/usr/lib/systemd_

Each file follows a specific naming convention. For instance a file _/usr/lib/credstore/home.create.admin_ is named as _usr__lib__credstore__home.create.admin_

### Explaining the Containerfile

The following will describe and show, step by step, the contents of the example _[Containerfile][6]_ created.

#### Image base

The fedora-bootc project is part of the Cloud Native Computing Foundation (CNCF) Sandbox projects and generates reference “base images” of bootable containers designed for use with the bootc project.

In this example, I’m using _quay.io/fedora/fedora-bootc_ as the base image. The containerfile starts off with:

FROM quay.io/fedora/fedora-bootc

#### Setup filesystem

If you plan to install software on day 2, i.e. after the kde-bootc installation is complete, you may need to link _/opt_ to _/var/opt_. Otherwise, _/opt_ will remain an immutable directory that you can only populate from the container build.

RUN rmdir /opt
RUN ln -s -T /var/opt /opt

In some cases, for successful package installation, the _/var/roothome_ directory must exist. If this folder is missing, the container build may fail. It is advisable to create this directory before installing the packages.

RUN mkdir /var/roothome

#### Prepare packages

To simplify the installation, and to have a record of installed and removed packages for future reference, I found it useful to keep them as a resource under _/usr/share_.

  * All additional packages to be installed on top of fedora-bootc and the KDE environment are documented in _packages-added_.



COPY --chmod=0644 ./system/usr__local__share__kde-bootc__packages-added /usr/local/share/kde-bootc/packages-added

  * Packages to be removed from fedora-bootc and the KDE environment are documented in _packages-removed_.



COPY --chmod=0644 ./system/usr__local__share__kde-bootc__packages-removed /usr/local/share/kde-bootc/packages-removed

  * For convenience, the packages included in the base fedora-bootc are documented in _packages-fedora-bootc_.



RUN jq -r .packages[] /usr/share/rpm-ostree/treefile.json > /usr/local/share/kde-bootc/packages-fedora-bootc

#### Install repositories

This section handles adding extra repositories needed before installing packages.

In this example, I’m adding Tailscale, but the same principle applies to any other source you may add to your repositories.

Adding repositories uses the config-manager verb, available as a DNF5 plugin. This plugin is not pre-installed by default in fedora-bootc, so it will need to be installed beforehand.

RUN dnf -y install dnf5-plugins
RUN dnf config-manager addrepo --from-repofile=<https://pkgs.tailscale.com/stable/fedora/tailscale.repo>

#### Install packages

For clarity and task separation, I divided the installation into two steps:

Installation of environment and groups.

RUN dnf -y install @kde-desktop-environment

And the installation of all other individual packages. The script will select all lines not starting with # passing them as arguments to _dnf -y install_. The _\--allowerasing_ option is necessary for cases like installing _vim-default-editor_ , which would conflict with _nano-default-editor_ , removing the latter first.

RUN grep -vE '^#' /usr/local/share/kde-bootc/packages-added | xargs dnf -y install –-allowerasing

**PACKAGES-ADDED**
### LibreOffice
libreoffice
libreoffice-help-en
### Utilities
vim-default-editor
git
....

#### Remove packages

Some of the standard packages included in _@kde-desktop-environment_ don’t behave well and sometimes conflict with an immutable desktop, so we will remove them.

This is also an opportunity to remove software you may never use, saving resources and storage.

RUN grep -vE '^#' /usr/local/share/kde-bootc/packages-removed | xargs dnf -y remove
RUN dnf -y autoremove
RUN dnf clean all

The criteria used to remove some packages is listed below:

**Conflict with bootc and its immutable nature.**
plasma-discover-offline-updates
plasma-discover-packagekit
PackageKit-command-not-found

**Bring unwanted dependencies.**
tracker
tracker-miners
mariadb-server-utils
abrt
at
dnf-data

**Deprecated services.**
iptables-services
iptables-utils

**Packages that are resource-heavy, or bring unnecessary services.**
rsyslog
dracut-config-rescue

#### Configuration

This section will copy all necessary configuration files to _/usr_ and _/etc_. As recommended by the bootc project, prioritise using _/usr_ and use _/etc_ as a fallback if needed.

Bash scripts that will be used by systemd services are stored in _/usr/local/bin_ :

COPY --chmod=0755 ./system/usr__local__bin/* /usr/local/bin/

Custom configuration for new users’ home directories will be added to _/etc/skel/_. As an example you can customise bash.

COPY --chmod=0644 ./system/etc__skel__kde-bootc /etc/skel/.bashrc.d/kde-bootc

If you’re building your container image on GitHub and keeping it private, you’ll need to create a GITHUB_TOKEN to download the image. Further information is available at [GitHub container registry.][7]

COPY --chmod=0600 ./system/usr__lib__ostree__auth.json /usr/lib/ostree/auth.json

#### Users

I opted for systemd-homed users because they are better suited than regular users for immutable desktops, preventing potential drift in case of local modifications in _/etc/passwd_. Additionally, each user home benefits from LUKS encrypted volume.

The process begins when firstboot-setup runs, triggered by firstboot-setup.service during boot. It executes _homectl firstboot_ , which checks if any regular home areas exist. If none are found, it searches for service credentials starting with _home.create._ to create users at boot.

The parameter below imports service credentials into the systemd service:

**FIRSTBOOT-SETUP.SERVICE**
...
ImportCredential=home.create.*

For more details, refer to the _homectl_ and _systemd.exec_ manual pages.

The homed identity file ( _usr__lib__credstore__home.create.admin_ ) sets the user’s parameters, including username, real name, storage type, etc.

##### Common systemd-homed parameters:

  * userName: A single word for your username and home directory. In this example, it is admin.
  * realName: Full name for the user
  * diskSize: The size of the LUKS storage volume, calculated in bytes. For instance, 1 GB equals 1024x1024x1024 bytes, which is 1073741824 bytes.
  * rebalanceWeight: Relevant only when multiple user accounts share the available storage. If diskSize is defined, this parameter can be set to false.
  * uid/gid: User and Group ID. The default range for regular users is 1000-6000, and for systemd-homed users, it is 60001-60513. However, you can assign uid/gid for systemd-homed users from both ranges.
  * memberOf: The groups the user belongs to. As a power user, it should be part of the wheel group.
  * hashedPassword: This is the hashed version of the password stored under secret. Setting up an initial password allows homectl firstboot to create the user without prompting. This password should be changed afterwards (homectl passwd admin). The hash password can be created using the mkpasswd utility.



We are storing the identity file in one of the directories where systemd-homed expects to find credentials.

COPY --chmod=0644 ./system/usr__lib__credstore__home.create.admin /usr/lib/credstore/home.create.admin

For more information on user records, visit: <https://systemd.io/USER_RECORD/>

This section also creates a temporary password for the root user. As I will explain later, having a root user as an alternative login is important.

echo "Temp#SsaP" | passwd root -s

##### Subuid and Subgid:

Another key parameter to set up is the range for _/etc/subuid_ and _/etc/subgid_ for the _admin_ user. This range is necessary for running rootless containers since each uid inside the container will be mapped to a uid outside the container within this range. Systemd-homed predefines ranges for uid/gid.

The available range is 524288…1879048191. Choosing 1000001 makes it easy to identify the service running in the container. For instance, if the container is running Apache with uid=48, the volume or folder bound to it will have uid=1000048.

echo "admin:1000001:65536">/etc/subuid
echo "admin:1000001:65536">/etc/subgid

For more information on available ranges, visit: <https://systemd.io/UIDS-GIDS/>

The next step will set up _authselect_ to enable authenticating the _admin_ user on the login page. To achieve this, we need to enable the features _with-systemd-homed_ and _with-fingerprint_ (if your computer has a fingerprint reader) for the local profile.

authselect enable-feature with-systemd-homed
authselect enable-feature with-fingerprint

#### Systemd services

I decided to install at least two services; One to complete the configuration during machine boot, to run commands that require systemd ( _firstboot-setup.service_ ), and the other one to automate updates ( _bootc-fetch.service_ ).

We are enabling, by default, the first systemd service _firstboot-setup_ :

COPY --chmod=0644 ./systemd/usr__lib__systemd__system__firstboot-setup.service /usr/lib/systemd/system/firstboot-setup.service
RUN systemctl enable firstboot-setup.service

**USR__LIB__SYSTEMD__SYSTEM__FIRTBOOT-SETUP.SERVICE**
[Unit]
Description=Setup USERS and /VAR at boot
After=multi-user.target
[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/local/bin/firstboot-setup
ImportCredential=home.create.*
[Install]
WantedBy=multi-user.target

And it runs the script below:

**FIRSTBOOT-SETUP**
### Setup hostname
HOST_NAME=kde-bootc
hostnamectl hostname $HOST_NAME
### Create user(s)
homectl firstboot
### Setup firewall to allow kdeconnect to functions
firewall-cmd --set-default-zone=public
firewall-cmd --add-service=kdeconnect --permanent

We are triggering _bootc-fetch_ daily by a timer as a second systemd service:

COPY --chmod=0644 ./systemd/usr__lib__systemd__system__ bootc-fetch.service /usr/lib/systemd/system/bootc-fetch.service
COPY --chmod=0644 ./systemd/usr__lib__systemd__system__bootc-fetch.timer /usr/lib/systemd/system/bootc-fetch.timer

**USR__LIB__SYSTEMD__SYSTEM__BOOTC-FETCH.TIMER**
[Unit]
Description=Fetch bootc image daily
[Timer]
OnCalendar=*-*-* 12:30:00
Persistent=true
[Install]
WantedBy=timers.target

**USR__LIB__SYSTEMD__SYSTEM__BOOTC-FETCH.SERVICE**
[Unit]
Description=Fetch bootc image
After=network-online.target
[Service]
Type=oneshot
ExecStart=/usr/bin/bootc update --quiet

This service replaces _bootc-fetch-apply-updates_ , which would download and apply updates as soon as they are available. This approach is problematic because it causes your computer to shut down without warning, so it is better to disable by masking the timer:

RUN systemctl mask bootc-fetch-apply-updates.timer

### How to create an ISO?

The instructions that follow will build the container locally. You need to do it as root so _bootc-image-builder_ can use the image to make the ISO.

cd /path-to-your-repo
sudo podman build -t kde-bootc .

Then, outside the repository on a different directory, create a folder named _output_ for the ISO image. And also you need to create the configuration file _config.toml_ to feed the installer.

**CONFIG.TOML**
[customizations.installer.kickstart]
contents = "graphical"

[customizations.installer.modules]
disable = [
"org.fedoraproject.Anaconda.Modules.Users"
]

It instructs the installer to use the graphical interface and disable the module for user creation. We do not need to set up a user during installation, as this is already being taken care of.

Within the directory where _./output/_ and _./config.toml_ exists, run bootc-image-builder utility which is available as a container. It must be run as root.

sudo podman run --rm -it --privileged --pull=newer \
\--security-opt label=type:unconfined_t \
-v ./output:/output \
-v /var/lib/containers/storage:/var/lib/containers/storage \
-v ./config.toml:/config.toml:ro \
quay.io/centos-bootc/bootc-image-builder:latest \
\--type iso \
\--chown 1000:1000 \
localhost/kde-bootc

If everything goes well, the ISO image will be available in the _./output_ directory. You can use Fedora Media Writer to create a USB and put your images on a portable drive such as flash disk.

At the time of writing, the installer uses Anaconda and functions like any other Fedora flavor installation.

For more information on bootc-image-builder, visit: <https://github.com/osbuild/bootc-image-builder>

### Post installation

The first step is to restore the SELinux context for the systemd-homed home directory. Without this, you may not be able to log in as _admin_. To complete this task, log in as root, activate admin home area, and then run restorecon to restore the SELinux context.

homectl activate admin
<< enter password for admin
restorecon -R /home/admin
homectl deactivate admin

At this point, you can change the passwords for _root_ and _admin_ :

passwd root
homectl passwd admin

After completing these steps, you can log out from _root_ and log in to _admin_.

If your computer has a fingerprint reader, setting it up is not possible from Plasma’s user settings, as systemd-homed is not yet recognised by the desktop. However, you can manually enroll your fingerprint by running _fprintd-enroll_ and placing your finger on the reader as you normally would.

sudo fprintd-enroll admin

Same as above, you cannot set up the avatar from Plasma’s user settings, but you can copy an available avatar (PNG file) from Plasma’s avatar directory to the account service’s directory. The file name needs to be the same as the username:

/usr/share/plasma/avatars/<avatar.png> -> /var/lib/AccountsService/icons/admin

Finally, enable the service to keep your system updated and any other desired services:

systemctl enable --now bootc-fetch.timer
systemctl enable --now tailscaled

### Troubleshooting

#### Drifts on /etc

Please note that a configuration file in _/etc_ drifts when it is modified locally. Consequently, bootc will no longer manage this file, and new releases won’t be transferred to your installation. While this might be desired in some cases, it can also lead to issues.

For instance, if _/etc/passwd_ is locally modified, uid or gid allocations for services may not get updated, resulting in service failures.

Use _ostree admin config-diff_ to list the files in your local _/etc_ that are no longer managed by bootc, because they are modified or added.

If a particular configuration file needs to be managed by bootc, you can revert it by copying the version created by the container build from _/usr/etc_ to _/etc_.

#### Adding packages after first installation

The _/var_ directory is populated in the container image and transferred to your OS during initial installation. Subsequent updates to the container image will not affect _/var_. This is the expected behavior of bootc and generally works fine. However, some RPM packages execute scriptlets after installation, resulting in changes to _/var_ that will not be transferred to your OS.

Instead of trying to identify and update the missing bits in _/var_ , I found it easier to overlay _/usr_ ( _bootc usr-overlay_ ) and reinstall the packages ( _dnf reinstall .._ ) after updating and rebooting bootc.

### References

GitHub – kde-bootc: [https://github.com/sig][5][u][5][lete/kde-bootc][5]
GitHub – bootc: <https://github.com/bootc-dev/bootc>
GitLab – fedora-bootc: <https://gitlab.com/fedora/bootc>

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/building-your-own-atomic-bootc-desktop/

作者：[Daniel Mendizabal][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/sigulete/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/05/atomic_desktop-816x345.jpg
[2]: https://unsplash.com/@jasondcva17?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/black-flat-screen-computer-monitor-turned-on-beside-black-computer-keyboard-6Vx0ME-CtxU?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://opencontainers.org/about/overview/
[5]: https://github.com/sigulete/kde-bootc
[6]: https://github.com/sigulete/kde-bootc/blob/main/Containerfile
[7]: https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry
