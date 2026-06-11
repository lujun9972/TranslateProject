[#]: subject: "What you need to know about the Microsoft Secure Boot certificate expiration: Don’t Panic!"
[#]: via: "https://fedoramagazine.org/expiration-of-microsoft-secure-boot-keys/"
[#]: author: "Marta Lewandowska https://fedoramagazine.org/author/mlewando/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

What you need to know about the Microsoft Secure Boot certificate expiration: Don’t Panic!
======

![][1]

[Illustration][2] by [Boxicons][3] on [Unsplash][4]

UEFI Secure Boot keys, used to sign the first stage boot loader, are expiring in June 2026 (this month!) But that only means that Microsoft can no longer sign with them. Machines, both bare metal and virtual, will continue to boot long after June is over as long as the current public keys are not removed from the firmware database or revoked via the dbx database. In the meantime, Fedora Rawhide (f45) already contains a first stage boot loader that is signed by multiple keys for maximal compatibility. So there is no need to panic, but action is recommended.

### Secure Boot basics

UEFI Secure Boot is a security feature which ensures only trusted (signed) applications run during a computer’s boot up process. This applies to the boot loaders, the operating system kernel, and the kernel modules. Trust is established using asymmetric cryptography. Tested algorithms, like [R][5][S][5][A][5] or [ECDSA][6], are used to create asymmetric key pairs. The private key is used to sign the application. A totally different but complementary public key is used to verify the application. The private key is kept secret while the public key is available to anyone who wants to run the application. UEFI Secure Boot is only available for machines that run UEFI firmware, and for Fedora, the key expiration only applies to the x86_64 architecture (Intel, AMD), and to those who have Secure Boot enabled.

The root of trust for Secure Boot is in the firmware. Hardware manufacturers add trusted Secure Boot public keys to their devices’ Secure Boot firmware database (db). Firmware for virtualization, known as edk2-ovmf, is built with similar trusted public keys. In order to simplify the process, there is a central signing authority which signs the first stage boot loader. This is the “shim” whose public key is enrolled pretty much everywhere, and that is Microsoft. Microsoft first started signing shim with their 2011 UEFI Third Party CA, but by the end of June they will no longer be able to do so. Since October 2025, Microsoft began signing with a new 2023 key as well. Once the 2011 key expires, new shims will only be signed with the 2023 key.

The OS maintains the rest of the Secure Boot chain. Fedora’s shim embeds a Fedora Secure Boot public CA key. Private keys on Fedora’s signing server are used to sign the next stage boot loader (grub2), the kernel, and any other applications that need to run during the boot process (like fwupd for firmware updates or unified kernel images– UKIs)

When the kernel is built, kernel modules are signed using an ephemeral key. Only signed kernel modules can be loaded when Secure Boot is enabled.

### Action Recommended

The fact is that you don’t really have to do anything about any of this right now. Your computer will continue to boot. New installations of both older and new OSes will continue to be possible.

BUT, we recommend updating your Secure Boot database if and when an update is available. The next deliverable shim update can only be signed by the 2023 key and it is best to be prepared. While there are no known exploitable security vulnerabilities in shim at this time, new ones may be found next month or next year. Below are some commands that will help you determine what state your computer is in, and how to make the correct updates.

#### How to tell if you have UEFI or legacy BIOS

The presence of the /sys/firmware/efi directory is the clearest way to check whether you are running UEFI firmware or legacy BIOS. The following command will print “BIOS” if the efi directory does not exist:

```

    $ [[ -d /sys/firmware/efi ]] || echo BIOS

```

#### How to check if Secure Boot is enabled

```

    $ mokutil --sb-state
    SecureBoot enabled

```

The Secure Boot state may be “enabled”, “disabled”, or the machine may be in “Setup Mode”, which means there are no Secure Boot keys enrolled in firmware.

#### How to identify which keys are in the firmware db

```

    $ mokutil --db --short
    580a6f4cc4 Microsoft Windows Production PCA 2011
    45a0fa3260 Windows UEFI CA 2023
    46def63b5c Microsoft Corporation UEFI CA 2011
    b5eeb4a670 Microsoft UEFI CA 2023

```

This output is from a VM, and as you can see, it already contains the 2011 and 2023 public keys. Your laptop or desktop will also show other database keys from the manufacturer.

#### How to update the firmware db

Enable and use fwupd to get your updates from the [Linux Vendor Firmware Service (LVFS)][7]:

```

    $ sudo fwupdmgr update

```

If you have an HP or Fujitsu machine, the update will be available soon, after you have updated your firmware. Use either the above command, or the vendor-recommended command at that time.

#### How to check which key(s) signed the shim

```

    $ sudo dnf install pesign -y
    $ sudo pesign -S -i /boot/efi/EFI/fedora/shimx64.efi
    ----------------------------------------------
    certificate address is 0x7f3fffc11410
    Content was not encrypted.
    Content is detached; signature cannot be verified.
    The signer's common name is Microsoft Windows UEFI Driver Publisher
    No signer email address.
    No signing time included.
    There were certs or crls included.
    ----------------------------------------------
    certificate address is 0x7f3fffc139e0
    Content was not encrypted.
    Content is detached; signature cannot be verified.
    The signer's common name is Microsoft UEFI CA 2023 signer
    No signer email address.
    No signing time included.
    There were certs or crls included.
    -----------------------------------------------

```

The output shown here is from the dual-signed Fedora Rawhide (F45) shim. If Rawhide is not installed, the shim will only be signed with the first key, which is the 2011 key.

You can use the same pesign command to examine grub2 (/boot/efi/EFI/fedora/grubx64.efi) and the kernel (/boot/vmlinuz-…).

### What NOT to do

If a database update is not available for your system, contact your hardware manufacturer. Do not attempt to force an incompatible update. Do not update your database manually unless you know exactly what you are doing!

Do not remove or revoke the 2011 key. The 2011 key is not compromised, it is only expiring, so there is no need to remove it. Additionally, it was used to sign option ROMs, so removing it could render peripherals on your system inoperable. Likewise, adding the 2011 key to the firmware dbx database (the forbidden database) will affect option ROMs. This will stop the dual-signed shim from booting.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/expiration-of-microsoft-secure-boot-keys/

作者：[Marta Lewandowska][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mlewando/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/06/MS_Cert_Expiration-816x345.jpg
[2]: https://unsplash.com/illustrations/an-open-black-padlock-icon-on-a-white-background-MWCbAefWxlc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/@boxicons/illustrations?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://unsplash.com/illustrations?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[5]: https://en.wikipedia.org/wiki/RSA_cryptosystem
[6]: https://en.wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm
[7]: http://fwupd.org
