[#]: subject: "Use systemd-cryptenroll with FIDO U2F or TPM2 to decrypt your disk"
[#]: via: "https://fedoramagazine.org/use-systemd-cryptenroll-with-fido-u2f-or-tpm2-to-decrypt-your-disk/"
[#]: author: "Alexander Wellbrock https://fedoramagazine.org/author/w4tsn/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Use systemd-cryptenroll with FIDO U2F or TPM2 to decrypt your disk
======

![][1]

Photo by [Bruno Brito][2] on [Unsplash][3]

Fedora Workstation includes [systemd-cryptenroll][4] by default which makes adding alternative methods for unlocking [LUKS][5] partitions fairly straight forward. This article shows how to use either a [TPM2][6] chip or a FIDO U2F security key as an alternative factor to the passphrase when unlocking your LUKS partitions.

### Previous articles

A TPM2 chip is a little piece of storage with secure APIs where you can store secrets protected by Secure Boot. Secure Boot establishes a chain of trust by computing hashes based on, for example, hardware or software components. This way you can store a LUKS decryption key which is only accessible if the system is in a non-tampered state (in theory). Unfortunately, this means you’ll want to measure things like your initramfs and kernel into this state which means invalidating this factor every time you do a system upgrade. FIDO U2F keys do not suffer from this problem as they are not tied to the hardware platform.

Check out my previous article about using an integrated TPM2 secure storage device to learn more in-depth specifics about how TPM2-based unlocking works and its security implications.

The previous article, however, uses clevis which adds additional dependencies and has a more complex interface than using the already present systemd-cryptenroll.

> [Automatically decrypt your disk using TPM2][7]

A FIDO2 or FIDO U2F compliant key is an external storage device with secure APIs for storing and retrieving secrets. These keys can be used as a second- or sole-factor in authentication flows. Secrets never leave the device and verification is done on the client. So attack scenarios like fishing are mitigated by design as compared to other MFA (multi-factor authentication) technologies like TOTP (time-based one time passwords).

A previous post about FIDO U2F / FIDO2 keys here on Fedora Magazine showed how to set up those keys for Linux PAM authentication – primarily _sudo_ and GNOME login.

> [Use FIDO U2F security keys with Fedora Linux][8]

### Find your encrypted LUKS disks

For the following sections you need the filesystem path(s) to your LUKS encrypted partition(s). Use _lsblk_ to find them.

```

    $> lsblk
    NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
    sda                     8:0    1     0B  0 disk
    sdb                     8:16   1     0B  0 disk
    zram0                 252:0    0     8G  0 disk  [SWAP]
    nvme0n1               259:0    0 476.9G  0 disk
    ├─nvme0n1p1           259:1    0   600M  0 part  /boot/efi
    ├─nvme0n1p2           259:2    0     1G  0 part  /boot
    └─nvme0n1p3           259:3    0 475.4G  0 part
      └─luks-fdb98c38-... 253:0    0 475.3G  0 crypt /home
                                                     /

```

Find the partition number(s) hosting the _luks-_ partition of type _crypt_. In this case that’d be _/dev/nvme0n1p3_. Use this path as target for the following sections.

### (Maybe) Get rid of clevis

Assuming you followed the previous post on using TPM2 you might want to unbind and remove clevis before proceeding with systemd-cryptenroll. Otherwise just skip this section.

First, remove any TPM2 binding from the LUKS secrets slots. Beware: do not remove slot 0 as it contains the passphrase binding!

```

    $ sudo clevis luks list -d /dev/nvme0n1p3
    ... Slot 1 (or whichever is your TPM2 binding) ...
    $ sudo clevis luks unbind -d /dev/nvme0n1p3 -s 1

```

Now remove the clevis packages.

```

    sudo dnf remove -y clevis clevis-luks clevis-dracut clevis-udisks2 clevis-systemd

```

### Choose TPM2 or FIDO as an alternative decryption method

The following steps are required for both methods. Choose one to your liking.

  * Add the corresponding dracut module so support is available in the initramfs at boot
  * Enroll / bind a LUKS secret slot tied to either the TPM2 or the FIDO key
  * Update /etc/crypttab with the new configuration
  * Rebuild the initramfs to apply the changes



It is important to run dracut last to not only include new dependencies but also your updated _crypttab_ in the _initramfs_.

### Use systemd-cryptenroll with a FIDO U2F key

Add the _fido2_ dracut module to your dracut configuration.

```

    $ echo "add_dracutmodules+=\" fido2 \"" | sudo tee /etc/dracut.conf.d/fido2.conf
    add_dracutmodules+=" fido2 "

```

Now enroll the FIDO key with your LUKS partition as an alternative decryption factor. See [systemd-cryptenroll(1)][9] for options to control features like touch or pin prompt. By default presence and pin are requested for enrollment and use.

```

    sudo systemd-cryptenroll --fido2-device auto /dev/nvmen1p3

```

Update _/etc/crypttab_ and append _fido2-device=auto_ to the appropriate line’s options. A line in _crypttab_ consists of four fields with the last one being a comma separated list.

Finally, rebuild your initramfs using dracut. The following command will rebuild your currently-booted initramfs slot.

```

    sudo dracut -f

```

Don’t worry about the FIDO key not working or about losing it since the passphrase is still available as a fallback.

You’ll now be prompted at boot to enter the PIN of your FIDO key. Be aware that the PIN entry prompt looks exactly the same as the passphrase prompt. You will notice a difference only when using the terminal (which you can view by hitting the **ESC** key). After entering the correct PIN the hardware token will prompt you to touch it which (also) is not indicated on the prompt. If it does not prompt for a touch, then _systemd-cryptenroll_ was not able to find a hardware token corresponding to the entered PIN.

**Note** : _systemd-cryptenroll does not currently work with multiple connected hardware tokens._

### Use systemd-cryptenroll with a TPM2 chip

Add the _tpm2-tss_ module to your dracut configuration.

```

    $ echo "add_dracutmodules+=\" tpm2-tss \"" | sudo tee /etc/dracut.conf.d/tpm2.conf
    add_dracutmodules+=" tpm2-tss "

```

Enroll the TPM2 chip as alternative decryption factor for your LUKS partition(s). The _‐‐wipe-slot tpm2_ option ensures that after successful enrollment any previous bindings are removed. Use this command every time you need to update the binding.

```

    sudo systemd-cryptenroll --wipe-slot tpm2 --tpm2-device auto --tpm2-pcrs "0+1+2+3+4+5+7+9" /dev/nvme0n1p3

```

Update /etc/crypttab and append _tpm2-device=auto,tpm2-pcrs=0+1+2+3+4+5+7+9_ to the appropriate line’s options, depending on the PCRs used. A line in crypttab consists of four fields with the last one being a plus separated list.

Last but not least, rebuild your _initramfs_ using _dracut_. The following command will rebuild your currently booted _initramfs_ slot.

```

    sudo dracut -f

```

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/use-systemd-cryptenroll-with-fido-u2f-or-tpm2-to-decrypt-your-disk/

作者：[Alexander Wellbrock][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/w4tsn/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/05/systemd_cryptenroll_and_fido_u2f-816x345.jpg
[2]: https://unsplash.com/ko/@bhdebrito?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/s/photos/security-key?orientation=landscape&utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://www.freedesktop.org/software/systemd/man/systemd-cryptenroll.html
[5]: https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup
[6]: https://en.wikipedia.org/wiki/Trusted_Platform_Module
[7]: https://fedoramagazine.org/automatically-decrypt-your-disk-using-tpm2/
[8]: https://fedoramagazine.org/use-fido-u2f-security-keys-with-fedora-linux/
[9]: https://man7.org/linux/man-pages/man1/systemd-cryptenroll.1.html
