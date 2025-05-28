[#]: subject: "How to use Authselect to configure PAM in Fedora Linux"
[#]: via: "https://fedoramagazine.org/how-to-use-authselect-to-configure-pam-in-fedora-linux/"
[#]: author: "Mario Atairu https://fedoramagazine.org/author/mariowritescode/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

How to use Authselect to configure PAM in Fedora Linux
======

![][1]

Photo by [Towfiqu barbhuiya][2] on [Unsplash][3] (edited)

Authselect is a utility tool that manages PAM configurations using profiles. Starting with Fedora 36, Authselect became a hard requirement for configuring PAM. In this article, you will learn how to configure PAM using Authselect.

### Introduction.

Unauthorized access is a critical risk factor in computer security. Cybercriminals engage in data theft, cyber-jacking, crypto-jacking, phishing, and ransomware attacks once they gain unauthorized access. A common vulnerability exploit for unauthorized access is poor configuration authentication. Pluggable authentication module (PAM) plays a critical role in mitigating this vulnerability, by acting as a middleware layer between your application and authentication mechanisms. For instance, you can use PAM to configure a server to deny login after 6pm, and any login attempts afterwards will require a token. PAM does not carry out authentication itself, instead it forwards requests to the authentication module you specified in its configuration file.

This article will cover the following three topics:

  1. PAM
  2. Authselect, and authselect profiles
  3. How to configure PAM



Prerequisites:

  * Fedora, Centos or RHEL server. This guide uses Fedora 41 server edition. Fedora, Centos, and RHEL servers are interchangeable.
  * A user account with sudo privileges on the server.
  * Command line familiarity.



#### What is PAM?

The Pluggable Authentication Modules (PAM) provides a modular framework for authenticating users, systems, and applications on Fedora Linux. Before PAM, file-based authentication was the prevalent authentication scheme. File-based authentication stores, usernames, passwords, id’s, names, and other optional information in one file. This was simple, and everyone was happy until security requirements changed, or new authentication mechanisms were adopted.

Here’s an excerpt from Red Hat’s PAM [documentation][4]:

> Pluggable Authentication Modules (PAMs) provide a centralized authentication mechanism which system applications can use to relay authentication to a centrally configured framework. PAM is pluggable because there is a PAM module for different types of authentication sources (such as Kerberos, SSSD, NIS, or the local file system). Different authentication sources can be prioritized.

PAM acts as a middleware between applications and authentication modules. It receives authentication requests, looks at its configuration files and forwards the request to the appropriate authentication module. If any module detects that the credentials do not meet the required configuration, PAM denies the request and prevents unauthorized access. PAM guarantees that every request is consistently validated before it denies or grants access.

#### Why PAM?

  1. Support for various authentication schemes using pluggable modules. These may include two-factor authentication (2FA), password authentication (LDAP), tokens (OAuth, Kerberos), biometrics (fingerprint, facial), Hardware (YubiKey), and much more.
  2. Support for stacked authentication. PAM can combine one or more authentication schemes.
  3. Flexibility to support new or future authentication technology with minimal friction.
  4. High performance, and stability under significant load.
  5. Support for granular/custom configuration across users and applications. For example, PAM can disallow access to an application from 5pm to 5am, if an authenticated user does not possess a role.



#### Authselect replaces Authconfig

Authselect was introduced in Fedora 28 to replace Authconfig. By Fedora 35 Authconfig was removed system-wide. In Fedora 36 Authselect became a hard dependency making it a requirement for configuring PAM in subsequent Fedora versions.

This tool does not configure your applications (LDAP, AD, SSH); it is a configuration management tool designed to set up and maintain PAM. Authselect selects and applies pre-tested authentication profiles that determine which PAM modules are active and how they are configured.

Here’s an excerpt from the Fedora 27 [changeset][5] which announced Authselect as a replacement for Authconfig

> Authselect is a tool to select system authentication and identity sources from a list of supported profiles.
>
> It is designed to be a replacement for authconfig but it takes a different approach to configure the system. Instead of letting the administrator build the pam stack with a tool (which may potentially end up with a broken configuration), it would ship several tested stacks (profiles) that solve a use-case and are well tested and supported.

From the same changeset, the authors report that Authconfig was error prone, hard to maintain due to technical debt, caused system regressions after updates, and was hard to test.

> Authconfig does its best to always generate a valid pam stack but it is not possible to test every combination of options and identity and authentication daemons configuration. It is also quite regression prone since those daemons are in active development on their own and independent on authconfig. When a new feature is implemented in an authentication daemon it takes some time to propagate this feature into authconfig. It also may require a drastic change to the pam stack which may easily introduce regressions since it is hard to test properly with so many possible different setups.

#### Authselect profiles, and what they do.

As mentioned above, Authselect manages PAM configuration using ready-made profiles. A profile is a set of features and functions that describe how the resulting system configuration will look. One selects a profile and Authselect applies the configuration to PAM.

In Fedora, Authselect ships with four profiles;

```

    $ authselect list
    - local          Local users only
    - nis            Enable NIS for system authentication
    - sssd           Enable SSSD for system authentication (also for local users only)
    - winbind        Enable winbind for system authentication

```

For descriptions of each profile, visit Authselect’s [readme][6] page for profiles, and the [wiki][7], available on GitHub.

You can view the current profile with;

```

    $ authselect current
    Profile ID: local
    Enabled features:
    - with-silent-lastlog
    - with-fingerprint
    - with-mdns4

```

You can change the current profile with;

```

    $ sudo authselect select local
    Profile "local" was selected.

```

List the features in any profile with;

```

    $ authselect list-features local
    with-altfiles
    with-ecryptfs
    with-faillock
    with-fingerprint
    with-libvirt
    with-mdns4
    with-mdns6
    with-mkhomedir
    with-pam-gnome-keyring
    with-pam-u2f
    with-pam-u2f-2fa
    with-pamaccess
    with-pwhistory
    with-silent-lastlog
    with-systemd-homed
    without-lastlog-showfailed
    without-nullok
    without-pam-u2f-nouserok

```

You can enable or disable features in a profile with;

```

    $ sudo authselect enable-feature with-fingerprint
    $ sudo authselect disable-feature with-fingerprint

```

### Configure PAM with Authselect.

_Scenario: You have noticed a high number of failed login attempts on your Fedora Linux server. As a preemptive action you want to configure PAM for lockouts. Any user with 3 failed login attempts, gets locked out of your server for 24 hours._

The pam_faillock.so module maintains a list of failed authentication attempts per user during a specified interval and locks the account in case there were more than the stipulated consecutive failed authentications.

The Authselect profile “with-faillock” feature handles failed authentication lockouts.

#### Step 1. Check if current profile on the server has with-faillock enabled;

```

    $ authselect current
    Profile ID: local
    Enabled features:
    - with-silent-lastlog
    - with-mdns4
    - with-fingerprint

```

As you can see, with-faillock is not enabled in this profile.

#### Step 2. Enable with-faillock

```

    $ sudo authselect enable-feature with-faillock
    $ authselect current
    Profile ID: local
    Enabled features:
    - with-silent-lastlog
    - with-mdns4
    - with-fingerprint
    - with-faillock

```

Authselect has now configured PAM to support lockouts. Check the /etc/pam.d/system-auth file, and the /etc/pam.d/password-auth files, to see that the files are updated by authselect.

From the vimdiff image below you can see the changes authselect added to /etc/pam.d/system-auth.

![][8]

Authselect added the following lines

```

    auth      required   pam_faillock.so preauth silent
    auth      required   pam_faillock.so authfail
    account   required   pam_faillock.so

```

#### Step 3. Check if the current configuration is valid.

```

    $ authselect check
    Current configuration is valid.

```

#### Step 4. Apply changes

```

    $ sudo authselect apply-changes
    Changes were successfully applied.

```

#### Step 5. Configure faillock

```

    $ vi /etc/security/faillock.conf

```

![][9]

Uncomment the file to match the following parameters

```

    silent
    audit
    deny=3
    unlock_time=86400
    dir = /var/run/faillock

```

#### Step 6. Test PAM configuration

##### 6.1 Attempt to login consecutive times with the wrong password, to trigger a lockout

![][10]

##### 6.2 Check failure records

![][11]

> Important: As a best practice, always backup your current Authselect profile before making any change.

Back up the current Authselect profile as follows;

```

    $ authselect select local -b
    Backup stored at /var/lib/authselect/backups/2025-05-23-22-41-33.UyM1lJ
    Profile "local" was selected.

```

To list backed up profiles;

```

    $ authselect backup-list
    2025-05-22-15-17-41.fe92T8 (created at Thu 22 May 2025 11:17:41 AM EDT)
    2025-05-23-22-41-33.UyM1lJ (created at Fri 23 May 2025 06:41:33 PM EDT)

```

Restore a profile from backup using this;

```

    $ authselect backup-restore 2025-05-23-22-41-33.UyM1lJ

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/how-to-use-authselect-to-configure-pam-in-fedora-linux/

作者：[Mario Atairu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mariowritescode/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/05/authselect_pam_config-816x345.jpg
[2]: https://unsplash.com/@towfiqu999999?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-golden-padlock-sitting-on-top-of-a-keyboard-FnA5pAzqhMM?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/system-level_authentication_guide/pluggable_authentication_modules
[5]: https://fedoraproject.org/wiki/Changes/Authselect
[6]: https://github.com/authselect/authselect/tree/master/profiles
[7]: https://github.com/authselect/authselect/wiki
[8]: https://fedoramagazine.org/wp-content/uploads/2025/05/systemauth-vimdff-1024x290.png
[9]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250524_012204.png
[10]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250522_174406.png
[11]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250522_174323-1.png
