[#]: subject: "Integrating a uTrust FIDO2 Security Key for Full Disk Encryption, Login, and Sudo Access on Fedora 42"
[#]: via: "https://fedoramagazine.org/integrating-utrust-fido2-security-key-for-disk-encryption-login-and-sudo-access-for-fedora-42/"
[#]: author: "Joe Murphy https://fedoramagazine.org/author/ihs-2025/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Integrating a uTrust FIDO2 Security Key for Full Disk Encryption, Login, and Sudo Access on Fedora 42
======

![][1]

Photo by [Lysander Yuen][2] on [Unsplash][3] (cropped)

This guide provides a step-by-step walk-through for integrating a uTrust FIDO2 security key (Identiv uTrust) with Fedora 42 to secure:

  * LUKS2 full disk encryption (FDE)
  * Graphical login (LightDM + Cinnamon)
  * Sudo elevation



### Audience for this article

The guide is intended for instructional cybersecurity labs and intermediate Fedora users. It prioritizes **PIN + Touch** verification for strong security.

NOTE: Since misconfiguration can result in system lockout, readers should work only on non-production systems, maintain a fallback password, and back up all critical data before making changes.

### Background

The following technology is used in this walk-through:

**FIDO2** (Fast Identity Online 2) is a standard for passwordless or multi-factor authentication using hardware tokens. It relies on public key cryptography and supports PIN or biometric verification. In this setup, FIDO2 provides secure, hardware-backed authentication using a PIN and a required physical touch on the key.

**LUKS2** (Linux Unified Key Setup 2) is the full-disk encryption format used in modern Linux systems.

**PAM** (Pluggable Authentication Modules) and **Polkit** (PolicyKit) control authentication for logins and privilege escalation across both GUI and CLI actions.

This guide combines these technologies to deliver end-to-end security — from full-disk decryption at boot, to graphical login, to administrative elevation with sudo.

### System Overview

The following hardware/software is used in this implementation:

**Hardware and Software:**

  * **Architecture:** x86_64
  * **CPU:** Intel Core i7
  * **Kernel:** 6.14.9-300.fc42.x86_64
  * **Fedora Version:** Fedora 42 (Adams)
  * **Desktop Environment:** Cinnamon with LightDM



**FIDO2 Key:** Identiv uTrust FIDO2

  * Vendor/Product: 0x04e6:0x5a11
  * Protocol: CTAP2 / FIDO_2_0
  * PIN: Required
  * User Presence: Touch required
  * User Verification: PIN only (no biometrics)
  * Device Path: /dev/hidraw0



**Disk Setup**

  * Btrfs on LUKS2 FDE ( /dev/sda3 )
  * LUKS UUID: 8b2f0322-f508-4bed-8b1e-8f05cc784d60 _(this will differ on each machine)_
  * Keyslots:
  * 0: Passphrase (argon2id)
  * 1: FIDO2 credential _(note: in testing, only one FIDO2 key could be used at a time)_



* * *

### Process Flow Overview

The following phases occur during implementation:

  1. **System preparation** — Install Fedora 42 with LUKS2 full-disk encryption and update packages.
  2. **Package installation** — Add the development, PAM, and FIDO2 tools required for integration.
  3. **FIDO2 key enrollment** — Register the key with LUKS2 for disk unlock.
  4. **PAM configuration** — Enable FIDO2 authentication for login and sudo.
  5. **Polkit configuration (optional)** — Extend FIDO2 support to graphical privilege prompts.
  6. **Testing and verification** — Confirm PIN + Touch authentication at boot, login, and sudo elevation.



### Implementation Guide

#### Phase 1: System Preparation

  1. Create a clean install of Fedora 42 with Cinnamon + LightDM
  2. During installation/partitioning configure the following:
    * LUKS2 Full Disk Encryption (Btrfs or ext4)
    * No separate /home
    * No auto-login
    * Create an admin user
  3. Update the system:
sudo dnf upgrade --refresh -y



#### Phase 2: Required Package Installation

Install required development and security packages:

sudo dnf install -y
gcc make cmake git autoconf automake libtool
pam-devel systemd-devel glibc-devel openssl-devel
libfido2 libfido2-devel fido2-tools u2f-host pam-u2f
pcsc-lite pcsc-lite-ccid pcsc-tools ccid opensc
authselect cryptsetup pam_passwdqc fprintd-pam gnome-keyring-pam

Enable and start the PC/SC daemon for smartcard support:

sudo systemctl enable --now pcscd

#### Phase 3: FIDO2 Key Setup

  1. Insert the FIDO2 key and verify it is detected:
lsusb
fido2-token -L
fido2-token -I /dev/hidraw0
Expected output is:
Identiv uTrust FIDO2 (0x04e6:0x5a11) with options rk, clientPin.
  2. Troubleshooting considerations if the key isn’t recognized:
    * Ensure /dev/hidraw0 exists
    * Run the following to load kernel modules:
sudo modprobe hid
sudo modprobe hid_generic
    * Replug the key
  3. If FIDO_ERR_INTERNAL (-9) occurs:
    * Create the plugdev group:
sudo groupadd plugdev
sudo usermod -aG plugdev $USER
    * Apply a udev rule:
echo 'KERNEL=="hidraw*", ATTRS{idVendor}=="04e6", ATTRS{idProduct}=="5a11", TAG+="uaccess", GROUP="plugdev"' | sudo tee /etc/udev/rules.d/70-u2f.rules sudo udevadm control --reload-rules && sudo udevadm trigger
    * Reboot:
sudo reboot
  4. Enroll the FIDO key for LUKS2:
sudo systemd-cryptenroll --fido2-device=/dev/hidraw0 --fido2-with-client-pin=yes /dev/sda3
  5. Validate enrollment:
sudo cryptsetup luksDump /dev/sda3
  6. Update /etc/crypttab:
sudo nano /etc/crypttab
Add or modify:
luks-... UUID UUID=... none fido2-device=auto fido2-with-client-pin=yes discard



#### Phase 4: PAM Configuration

  1. Fedora’s pam-u2f package lacks pamu2fcfg. Build pamu2fcfg from source:

    * git clone <https://github.com/Yubico/pam-u2f>
    * cd pam-u2f
    * mkdir build && cd build
    * cmake -DBUILD_MANPAGES=OFF ..
    * make
    * sudo cp ./pamu2fcfg/pamu2fcfg /usr/local/bin/
    * sudo chmod +x /usr/local/bin/pamu2fcfg
  2. Generate U2F mapping:
pamu2fcfg -n -u $(whoami) -o pam://fedora | sudo tee /etc/u2f_mappings
Verify output includes +presence+pin (e.g., yourusername:3aaOH5…Base64…,M9hAf2…==,es256,+presence+pin)

  3. Set permissions:
sudo chmod 600 /etc/u2f_mappings
sudo chown root:root /etc/u2f_mappings

  4. Backup PAM files:
mkdir -p ~/fido2-audit/pam
sudo cp /etc/pam.d/{sudo,lightdm,cinnamon-screensaver,system-auth,password-auth,polkit-1} ~/fido2-audit/pam/

  5. Update PAM files to include FIDO2 authentication. On this system, the working configuration is:

    * /etc/pam.d/sudo
      * auth sufficient pam_u2f.so authfile=/etc/u2f_mappings cue pinverification=always origin=pam://fedora appid=pam://fedora
      * auth required pam_unix.so
      * account include system-auth
      * password include system-auth
      * session optional pam_keyinit.so revoke
      * session required pam_limits.so
      * session include system-auth
    * /etc/pam.d/lightdm
      * auth sufficient pam_u2f.so authfile=/etc/u2f_mappings cue pinverification=always origin=pam://fedora appid=pam://fedora
      * auth [success=done ignore=ignore default=bad] pam_selinux_permit.so
      * auth required pam_env.so
      * auth substack system-auth
      * auth include postlogin
      * account required pam_nologin.so
      * account include system-auth
      * password include system-auth
      * session required pam_selinux.so close
      * session required pam_loginuid.so
      * session required pam_selinux.so open
      * session optional pam_keyinit.so force revoke
      * session required pam_namespace.so
      * session include system-auth
      * session optional pam_lastlog.so silent
      * session include postlogin
    * /etc/pam.d/cinnamon-screensaver
      * auth sufficient pam_u2f.so authfile=/etc/u2f_mappings cue pinverification=always origin=pam://fedora appid=pam://fedora
      * auth include system-auth
      * account include system-auth
      * password include system-auth
      * session include system-auth


```

```

#### Phase 5: Polkit Configuration (Optional)

Polkit GUI prompts were **not enabled** on my test system (no /etc/pam.d/polkit-1 and no running user agent). If you want FIDO2 for Polkit dialogs, ensure a compatible agent is running (for Cinnamon: polkit-gnome-authentication-agent-1). In testing, GUI prompts were not enabled by default and required additional configuration.”

**Screensaver unlock:** When the screen is locked, Fedora may default to the password prompt. Click the small **two-person icon** to switch to the FIDO2 method. Keep a fall-back password available. In various tests some desktop prompts did not always default to FIDO2.

#### Phase 6: Testing

##### Reboot the system

![Boot screen asking for LUKS2 token PIN.][4]

##### Confirm functionality

The following sequence of images shows the following:

  * FDE (LUKS Unlock): PIN + Touch prompt appears at boot
  * GUI Login (LightDM): PIN + Touch required
  * Sudo: sudo echo test should prompt for PIN + Touch
  * Cinnamon lock screen: PIN + Touch (switch input method)
  * Polkit: GUI software install or pkexec prompts for PIN + Touch



![FDE \(LUKS Unlock\): PIN + Touch prompt appears at boot FIDO2 key lit up, waiting for touch to complete full-disk unlock.][5]

![GUI login PIN Fedora LightDM login screen prompting for FIDO2 key PIN.][6]

![GUI login key touch Login process with FIDO2 key lit up, requiring touch to proceed.][7]

![GUI login completion Login screen showing successful authentication, ready to “Log In.”][8]

![Sudo escalation \(terminal\) Example of sudo test requiring PIN + touch in terminal.][9]

![Locked screen where the user may need to click the person icon to switch back to FIDO2 login.][10]

##### Confirm the fallback password login remains functional

![Locked screen PIN entry Re-login screen asking for FIDO2 key PIN to unlock session.][11]

### Recovery and Backup

**Backup:**

```

    mkdir -p ~/fido2-audit/pam_restore
    for file in sudo lightdm cinnamon-screensaver system-auth password-auth polkit-1;
    do
      sudo cp ~/fido2-audit/pam/$file ~/fido2-audit/pam_restore/$file
    done

```

**Restore if needed** using TTY or Live USB.

**Emergency Login:**

  * Use a high-entropy admin password
  * Store the password securely off-line or in encrypted container



### Troubleshooting

**Multiple FIDO2 Keys:**

```

    lsusb
    sudo usbreset /dev/bus/usb/001/003

```

### Warnings

  * Never test on production systems
  * Back up /etc/crypttab and /etc/pam.d/*
  * Avoid running dracut --force unless ready



### Security Notes

**Strengths:**

  * Hardware-backed auth
  * PIN + Touch = Strong 2FA



**Risks:**

  * Loss of key
  * System updates may break compatibility



**Recommendations:**

  * Always keep a fall-back passphrase
  * Register a backup FIDO2 key
  * Back up /etc/u2f_mappings and test after upgrades



### Performance Considerations

Component | Delay Added
---|---
Boot (FDE) | ~5–10 seconds
GUI Login | ~2–3 seconds
Sudo/Polkit | ~1–2 seconds

### Conclusion

This guide demonstrates the successful integration of a uTrust FIDO2 security key with Fedora 42 for secure authentication across **LUKS2 full-disk encryption, LightDM login,** and **sudo elevation**. The setup is stable, reproducible, and well-suited for labs or intermediate Fedora users.

Polkit integration is optional and may vary by desktop environment. In testing, GUI prompts were not enabled by default and required additional configuration.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/integrating-utrust-fido2-security-key-for-disk-encryption-login-and-sudo-access-for-fedora-42/

作者：[Joe Murphy][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/ihs-2025/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/07/FIDO_LUKS_sudo-816x345.jpg
[2]: https://unsplash.com/@lysanderyuen?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/low-angle-photography-of-building-BY66BwIa9Bg?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/wp-content/uploads/2025/09/one-970x1024.jpeg
[5]: https://fedoramagazine.org/wp-content/uploads/2025/09/two-1024x768.jpeg
[6]: https://fedoramagazine.org/wp-content/uploads/2025/09/three-1024x768.jpeg
[7]: https://fedoramagazine.org/wp-content/uploads/2025/09/four-1024x768.jpeg
[8]: https://fedoramagazine.org/wp-content/uploads/2025/09/five-1024x768.jpeg
[9]: https://fedoramagazine.org/wp-content/uploads/2025/09/six-1024x768.jpeg
[10]: https://fedoramagazine.org/wp-content/uploads/2025/09/seven-1024x768.jpeg
[11]: https://fedoramagazine.org/wp-content/uploads/2025/09/eight-1024x768.jpeg
