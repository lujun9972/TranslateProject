[#]: subject: "Automatically decrypt your disk using TPM2"
[#]: via: "https://fedoramagazine.org/automatically-decrypt-your-disk-using-tpm2/"
[#]: author: "Alexander Wellbrock https://fedoramagazine.org/author/w4tsn/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Automatically decrypt your disk using TPM2
======

![][1]

Photo by [bassem Kira][2] on [Unsplash][3] (cropped)

This article demonstrates how to configure clevis and systemd-cryptenroll using a Trusted Platform Module 2 chip to automatically decrypt your LUKS-encrypted partitions at boot.

If you just want to get automatic decryption going you may skip directly to the Prerequisites section.

### Motivation

Disk encryption protects your data (private keys and critical documents) through direct access of your hardware. Think of selling your notebook / smartphone or it being stolen by an opportunistic evil actor. Any data, even if “deleted”, is recoverable and hence may fall into the hands of an unknown third party.

Disk encryption **does not** protect your data from access on the running system. For example, disk encryption does not protect your data from access by malware running as your user or in kernel space. It’s already decrypted at that point.

Entering the passphrase to decrypt the disk at boot can become quite tedious. On modern systems a secure hardware chip called “TPM” (Trusted Platform Module) can store a secret and automatically decrypt your disk. This is an **alternative** factor, not a **second** factor. Keep that in mind. Done right, this is an alternative with a level of security similar to a passphrase.

### Background

A TPM2 chip is a little hardware module inside your device which basically provides APIs for either WRITE-only or READ-only information. This way you might write a secret onto it, but you can never read it out later (but the TPM may use it later internally). Or you write info at one point that you only read out later. The TPM2 provides something called PCRs (Platform Configuration Registers). These registers take SHA1 or SHA256 hashes and contain _measurements_ used to assert integrity of, for example, the UEFI configuration.

Enable or disable Secure Boot in the system’s UEFI. Among other things, Secure Boot computes hashes of every component in the boot chain (UEFI and its configuration, bootloader, etc.) and chains them together such that a change in one of those components changes the computed and stored hashes in all following PCRs. This way you can build up trust about the environment you are in. Having a measure of the trustworthiness of your environment is useful, for example, when decrypting your disk. The [UEFI Secure Boot specification][4] defines PCRs 0 – 7. Everything beyond that is free for the OS and applications to use.

#### A summary of what is measured into which PCRs according to the spec

  * **PCR 0**: the EFI Firmware info like its version
  * **PCR 1**: additional config and info related to the EFI Firmware
  * **PCR 2**: EFI drives from hardware components (like RAID controller)
  * **PCR 3**: additional config and info to drivers stored in 2
  * **PCR 4**: pre-OS diagnostics and the EFI OS Loader
  * **PCR 5**: config of the EFI OS Loader and GPT table
  * **PCR 6**: is reserved for host platform manufacturer variables and is not used by EFI
  * **PCR 7**: stores secure boot policy configuration



#### Some examples on what is measured into which PCR

  * Changes to the initramfs measure into PCRs 9 and 10. So if you regenerate the initramfs using _dracut -f_ you have to rebind. This will happen on every update to the kernel.
  * Changes to the Grub configuration, like adding kernel arguments, kernels, etc. measure into PCRs 8, 9 and 10.
  * Storage devices measure into PCRs 8 and 10. However, Hubs and YubiKeys do not seem to measure in any PCR.
  * Additional operating systems measure into PCR 1. This occurs, for example, when attaching a USB stick before boot with a Fedora Linux live image.
  * Booting into a live image changes PCRs 1, 4, 5, 8, 9 and 10.



A tool called _clevis_ generates a new decryption secret for the LUKS encrypted disk, stores it in the TPM2 chip and configures the TPM2 to only return the secret if the PCR state matches the one at configuration time. Clevis will attempt to retrieve the secret and automatically decrypt the disk at boot time only if the state is as expected.

### Security implications

As you establish an alternative unlock method using only the on-board hardware of your platform, you have to trust your platform manufacturer to do their job right. This is a delicate topic. There is trust in a secure hardware and firmware design. Then there is trust that the UEFI, bootloader, kernel, initramfs, etc. are all unmodified. Combined you expect a trustworthy environment where it is OK to automatically decrypt the disk.

That being said you have to trust (or better, _verify_) that the manufacturer did not mess anything up in the overall platform design for this to be considered a fairly safe decryption alternative. There are a range of cases where things did not work out as planned. For example, when [security researches showed that BitLocker on a Lenovo notebook would use unencrypted SPI communication][5] with the TPM2 leaking the LUKS passphrase in plain text without even altering the system, or that BitLocker used the native encryption features of SSD drives that you can [by-pass through factory reset][6].

These examples are all about BitLocker but it should make it clear that if the overall design is broken, then the secret is accessible and this alternative method less secure than a passphrase only present in your head (and somewhere safe like a password manager). On the other hand, keep in mind that in most cases elaborate research and attacks to access a drive’s data are not worth the effort for an opportunistic bad actor. Additionally, not having to enter a passphrase on every boot should help adoption of this technology as it is transparent but adds additional hurdles to unwanted access.

### Prerequisites

First check that:

  * Secure Boot is enabled and working
  * A TPM2 chip is available
  * The _clevis_ package is installed



Clevis is where the magic happens. It’s a tool you use in the running OS to bind the TPM2 as an **alternative** decryption method and use it inside the _initramfs_ to read the decryption secret from the TPM2.

Check that secure boot is enabled. The output of _dmesg_ should look like this:

```

    $ dmesg | grep Secure
    [    0.000000] secureboot: Secure boot enabled
    [    0.000000] Kernel is locked down from EFI Secure Boot mode; see man kernel_lockdown.7
    [    0.005537] secureboot: Secure boot enabled
    [    1.582598] integrity: Loaded X.509 cert 'Fedora Secure Boot CA: fde32599c2d61db1bf5807335d7b20e4cd963b42'
    [   35.382910] Bluetooth: hci0: Secure boot is enabled

```

Check _dmesg_ for the presence of a TPM2 chip:

```

    $ dmesg | grep TPM
    [    0.005598] ACPI: TPM2 0x000000005D757000 00004C (v04 DELL   Dell Inc 00000002      01000013)

```

Install the _clevis_ dependencies and regenerate your initramfs using _dracut_.

```

    sudo dnf install clevis clevis-luks clevis-dracut clevis-udisks2 clevis-systemd
    sudo dracut -fv --regenerate-all
    sudo systemctl reboot

```

The **reboot** is **important** to get the correct PCR ****measurements based on the new initramfs image used for the next step.

### Configure clevis

To bind the LUKS-encrypted partition with the TPM2 chip. Point clevis to your (root) LUKS partition and specify the PCRs it should use.

Enter your current LUKS passphrase when asked. The process uses this to generate a new independent secret that will tie your LUKS partition to the TPM2 for use as an **alternative** decryption method. So if it does not work you will still have the option to enter your decryption passphrase directly.

```

    sudo clevis luks bind -d /dev/nvme... tpm2 '{"pcr_ids":"1,4,5,7,9"}'

```

As mentioned previously, PCRs 1, 4 and 5 change when booting into another system such as a live disk. PCR 7 tracks the current UEFI Secure Boot policy and PCR 9 changes if the initramfs loaded via EFI changes.

Note: If you just want to protect the LUKS passphrase from live images but don’t care about more “elaborate” attacks such as altering the unsigned initramfs on the unencrypted boot partition, then you might omit PCR 9 and save yourself the trouble of rebinding on updates.

### Automatically decrypt additional partitions

In case of secondary encrypted partitions use _/etc/crypttab_.

Use _systemd-cryptenroll_ to register the disk for _systemd_ to unlock:

```

    sudo systemd-cryptenroll /dev/nvme0n1... --tpm2-device=auto --tpm2-pcrs=1,4,5,7,9

```

Then reflect that config in your _/etc/crypttab_ by appending the options _tpm2-device=auto,tpm2-pcrs=1,4,5,7,9_.

### Unbind, rebind and edit

**List all current bindings of a device**:

```

    $ sudo clevis luks list -d /dev/nvme0n1... tpm2
    1: tpm2 '{"hash":"sha256","key":"ecc","pcr_bank":"sha256","pcr_ids":"0,1,2,3,4,5,7,9"}'

```

**Unbind a device**:

```

    sudo clevis luks unbind -d /dev/nvme0n1... -s 1 tpm2

```

The **-s** parameter specifies the slot of the alternative secret for this disk stored in the TPM. It should be 1 if you always unbind before binding again.

**Regenerate binding, in case the PCRs have changed**:

```

    sudo clevis luks regen -d /dev/nvme0n1... -s 1 tpm2

```

**Edit the configuration of a device**:

```

    sudo clevis luks edit -d /dev/nvme0n1... -s 1 -c '{"pcr_ids":"0,1,2,3,4,5,7,9"}'

```

### Troubleshooting

**Disk decryption passphrase prompt shows at boot, but goes away after a while**:

Add a sleep command to the _systemd-ask-password-playmouth.service_ file using _systemctl edit_ to avoid requests to the TPM before its kernel module is loaded:

```

    [Service]
    ExecStartPre=/bin/sleep 10

```

Add the following to the config file _/etc/dracut.conf.d/systemd-ask-password-plymouth.conf_:

```

    install_items+=" /etc/systemd/system/systemd-ask-password-plymouth.service.d/override.conf "

```

Then regenerate _dracut_ via _sudo dracut -fv –regenerate-all_.

Reboot and then regenerate the binding:

```

    sudo systemctl reboot
    ...
    sudo clevis luks regen -d /dev/nvme0n1... -s 1

```

### Resources

  * [Automatic LUKS volume unlocking using a TPM2 chip][7]
  * [Automatically decrypt with TPM2 on Silverblue (Discussion)][8]
  * [Right way to use the tpm for full disk encryption (Security StackExchange)][9]
  * [How does the TPM perform integrity measurements on a system (Security StackExchange)][10]
  * [Configuring SecureBoot + TPM2][11]
  * [Switch PCR banks on TPM2 devices][12]
  * [tpm2-luks project on Github][13]
  * [Understanding TPM PCRs, PCR banks and their relations][14]
  * [From a stolen laptop to inside the company network][5]
  * [TPM library specification][15]
  * [TCG EFI Platform specification][4]



--------------------------------------------------------------------------------

via: https://fedoramagazine.org/automatically-decrypt-your-disk-using-tpm2/

作者：[Alexander Wellbrock][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/w4tsn/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/01/automatically-decrypt-816x345.jpg
[2]: https://unsplash.com/@kiradev?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/REDXOfzXKy4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://trustedcomputinggroup.org/resource/tcg-efi-platform-specification/
[5]: https://dolosgroup.io/blog/2021/7/9/from-stolen-laptop-to-inside-the-company-network
[6]: https://blog.elcomsoft.com/2019/01/life-after-trim-using-factory-access-mode-for-imaging-ssd-drives/
[7]: https://blog.dowhile0.org/2017/10/18/automatic-luks-volumes-unlocking-using-a-tpm2-chip/
[8]: https://discussion.fedoraproject.org/t/automatic-decrypt-with-tpm2-on-silverblue/8424/18
[9]: https://security.stackexchange.com/questions/124338/right-way-to-use-the-tpm-for-full-disk-encryption
[10]: https://security.stackexchange.com/questions/39329/how-does-the-tpm-perform-integrity-measurements-on-a-system/44350#44350
[11]: https://www.tevora.com/threat-blog/configuring-secure-boot-tpm-2/
[12]: https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/switch-pcr-banks-on-tpm-2-0-devices
[13]: https://github.com/vchatterji/tpm2-luks
[14]: https://security.stackexchange.com/questions/252391/understanding-tpm-pcrs-pcr-banks-indexes-and-their-relations
[15]: https://trustedcomputinggroup.org/resource/tpm-library-specification/
