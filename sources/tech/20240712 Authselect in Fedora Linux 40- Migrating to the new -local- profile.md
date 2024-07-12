[#]: subject: "Authselect in Fedora Linux 40: Migrating to the new “local” profile"
[#]: via: "https://fedoramagazine.org/authselect-in-fedora-linux-40-migrating-to-the-new-local-profile/"
[#]: author: "Mateus Rodrigues Costa https://fedoramagazine.org/author/mateusrodcosta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Authselect in Fedora Linux 40: Migrating to the new “local” profile
======

![][1]

Photo by [Florian Berger][2] on [Unsplash][3]

Of the many changes in Fedora Linux 40, there is one important under-the-hood [Authselect][4] profile change that is applied to new Fedora Linux 40 installations. The active Authselect profile will not be changed for upgrades. A new Authselect profile — _local_ — will replace the _minimal_ profile and it will be the default profile for fresh installations of Fedora Linux 40+.

To understand why this change is important and why it might make sense to manually migrate your current installation to use the new profile, this article will explain how the Linux authentication system works and compare and contrast the _sssd_ * and _local_ profiles.

* _sssd_ was the default Authselect profile for installations prior to Fedora Linux 40.

### An overview of Linux authentication

The first system component we should look into is PAM. Here’s an excerpt from Red Hat’s [PAM documentation][5]:

Pluggable Authentication Modules (PAMs) provide a centralized authentication mechanism which system applications can use to relay authentication to a centrally configured framework. PAM is pluggable because there is a PAM module for different types of authentication sources (such as Kerberos, SSSD, NIS, or the local file system). Different authentication sources can be prioritized.

So, PAM is a system of modules which you can combine to manage how authentication works. But why is that useful?

Several features can be enabled, either by adding new PAM modules, or by reconfiguring existing ones. Examples include:

  * auto mounting disks or paths (encrypted or not)
  * running a command on login
  * Active Directory integration
  * [U2F][6] (generic or Yubikey-specific)
  * fingerprint reader support
  * autologin



There are two drawbacks (depending on the experience level of the user/sysadmin) to managing the PAM configuration manually — the syntax used in configuration files is somewhat complex and if they are misconfigured, it might not be possible to log back into the system and undo the mistake.

With that in mind, we arrive at the legacy Authconfig tool. A description of [the Authconfig tool][7] from Red Hat is:

The Authconfig tool can help configure what kind of data store to use for user credentials, such as LDAP. On Red Hat Enterprise Linux, Authconfig has both GUI and command-line options to configure any user data stores. The Authconfig tool can configure the system to use specific services — SSSD, LDAP, NIS, or Winbind — for its user database, along with using different forms of authentication mechanisms.

Authconfig was as a tool that operated above the PAM layer and it was used to configure the authentication for a system. However, it has since been replaced by Authselect.

Some insight into Authselect can be gained by reading the rationale for its introduction to Fedora Linux 27. Here is an excerpt from the Fedora Linux 27 [change set][8]:

Authselect is a tool to select system authentication and identity sources from a list of supported profiles.

It is designed to be a replacement for Authconfig but it takes a different approach to configuring the system. Instead of letting the administrator build the PAM stack with a tool (which may potentially end up with a broken configuration), it would ship several tested stacks (profiles) that solve a use-case and are well tested and supported. At the same time, some obsolete features of Authconfig would not be supported by Authselect.

With the addition of profiles, Authselect simplifies the task of configuring system authentication and it makes authentication failures due to human error when editing PAM configuration files less likely.

To recap:

  * PAM is the underlying system for authentication in Fedora Linux. It sources configuration files under /etc/pam.d on each login and, if one of its configuration files is corrupt or invalid, logins might fail (or succeed when they shouldn’t).
  * Authconfig is a tool that provides higher-level management of the PAM configuration. It is a script that sets up PAM as directed by the user/sysadmin.
  * Authselect is a replacement for Authconfig. Authselect adds the concept of “profiles” (with optional _features_ that may be enabled or disabled as desired). Authselect should cover most use-cases and it makes manually editing PAM’s low-level configuration files unnecessary.



Authselect [became the default in Fedora Linux 28][9] and later [became mandatory in Fedora Linux 36][10].

### Fedora Linux 40, the sssd profile, and the local profile

Now that the fundamentals of PAM, Authconfig, and Authselect have been covered, it is time to compare and contrast the Authselect profiles — the _sssd_ profile versus the new _local_ profile.

First, let’s see what SSSD is. Here is an excerpted from [SSSD’s website][11]:

SSSD is an acronym for System Security Services Daemon. It is the client component of centralized identity management solutions such as FreeIPA, 389 Directory Server, Microsoft Active Directory, OpenLDAP, and other directory servers. The client serves and caches the information stored in the remote directory server and provides identity, authentication, and authorization services to the host machine.

To simplify, you might think of SSSD as a system for accessing an organization’s server which holds the user data (passphrases, full names, etc.). Normally, you would only be able to login and access the data from user accounts that are present on your local machine (normally stored in the /etc/passwd file). With SSSD, you can access remote user accounts that are stored on a remote server such as Active Directory or [389 Directory Server][12].

But why is the sssd profile relevant?

Up to Fedora Linux 39, the default Authselect profile was _sssd_ :

```

    $ authselect current
    Profile ID: sssd
    Enabled features:
    - with-silent-lastlog
    - with-mdns4
    - with-fingerprint

```

However, as part of [Changes/SSSDRemoveFilesProvider][13] for Fedora Linux 40, the way the _sssd_ profile handles local users has changed:

• New “local” profile to handle local users without SSSD will be introduced. This profile will be based on “minimal”, but it may gain more features.

• “minimal” profile will be removed and replaced by “local”.

• “Local” profile will be now the default profile

• ‘sssd’ profile will lose _with‐files‐domain_ and _with‐files‐access‐provider_ options, and will gain _‐‐with‐tlog_ option.

So, the upgraded _local_ profile replaces the previous _minimal_ profile and _local_ becomes the default Authselect profile for new installs (instead of _sssd_ ).

Below is what Authselect shows on a fresh Fedora Linux 40 installation (or from a Live CD session):

```

    $ authselect current
    Profile ID: local
    Enabled features:
    - with-silent-lastlog
    - with-mdns4

```

### Migration

The new _local_ profile should be sufficient for those whom only need local user accounts. If you’ve upgraded to Fedora Linux 40 from an earlier release, you will not be switched to the new _local_ profile automatically. You might want to manually switch your system to use the _local_ profile if you do not need the remote account abilities that the _sssd_ profile provides.

The list of features available for the _local_ profile is:

```

    $ authselect list-features local
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
    without-nullok
    without-pam-u2f-nouserok

```

A description of the profile and each of its features can be seen with authselect show local.

To migrate between profiles, use the authselect select <profile> [feature] [feature...] command.

To migrate to the _local_ profile with the _with-silent-lastlog_ and _with-mdns4_ features enabled:

```

    # authselect select local with-silent-lastlog with-mdns4

```

If, for example, you want to add support for fingerprint readers, add that feature name to the list on the command line:

```

    # authselect select local with-silent-lastlog with-mdns4 with-fingerprint

```

### Conclusion

Fedora took the safe route of applying this change only to new Fedora Linux installations. Existing users who upgrade their systems do not need to worry that their PAM authentication stacks will be changed. However, end users may benefit from manually switching to the new _local_ profile on their local-only PCs.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/authselect-in-fedora-linux-40-migrating-to-the-new-local-profile/

作者：[Mateus Rodrigues Costa][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mateusrodcosta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/07/authselect.svg
[2]: https://unsplash.com/@bergerteam?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/three-assorted-color-keys-SzG0ncGBOeo?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://github.com/authselect/authselect
[5]: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/pluggable_authentication_modules
[6]: https://fedoramagazine.org/use-fido-u2f-security-keys-with-fedora-linux/
[7]: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/authconfig-install
[8]: https://fedoraproject.org/wiki/Changes/Authselect
[9]: https://fedoraproject.org/wiki/Changes/AuthselectAsDefault
[10]: https://fedoraproject.org/wiki/Changes/Make_Authselect_Mandatory
[11]: https://sssd.io/docs/introduction.html
[12]: https://www.port389.org/
[13]: https://fedoraproject.org/wiki/Changes/SSSDRemoveFilesProvider
