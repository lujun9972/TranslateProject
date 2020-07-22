[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (State-of-the-art crypto goes post-quantum)
[#]: via: (https://opensource.com/article/20/7/tinyssh)
[#]: author: (Charles Fisher https://opensource.com/users/chasil)

State-of-the-art crypto goes post-quantum
======
The TinySSH server aims to eliminate post-quantum cryptography
weaknesses.
![Parts, modules, containers for software][1]

Secrecy is one of the most important functions of computer science. Should electronic secrecy suddenly collapse into total transparency, we could not engage in electronic commerce, we would be unable to communicate privately, our past communications would be globally visible, and we would be critically impacted in myriad ways that would fundamentally change our ability to work and live. Consider the time we spend every day maintaining our secrecy with passwords, lock patterns, wireless fobs, and biometrics that restrict access to protect us and the ramifications of their failure.

Public-key cryptosystems form a critical aspect of our secrecy. The ability to establish private communications over a public medium is exercised billions of times per day. Should technology arise that unmasks this private discourse, the consequences could be incalculable.

In quantum computing, such a technology is rising. Potential hardware that can execute [Shor's algorithm][2] to directly threaten commonly used public-key schemes (RSA, conventional Diffie-Hellman, and elliptic curve) may be far nearer to realization than we would expect. D-Wave corporation has [promised to deliver][3] an adiabatic quantum computer this year with 5,000 qubits; this machine is not capable of directly running Shor's algorithm, but if it were, TLS and SSH would be severely compromised. There is some urgency to correct our cryptosystems.

Unlike the ubiquitous [CMOS][4] technology that permeates our electronics, [quantum logic][5] is a vastly different design that accommodates uncertainty and indeterminism, starting with the form of the "qubit," a binary value that counterintuitively can be both positive and negative at the same time. The threat of these new computing devices is very real, to the extent that the U.S. National Institute of Standards [launched a competition][6] for a quantum-resistant public-key cryptosystem.

Into this controversy, [TinySSH][7], a minimal SSH server with an embedded focus, has implemented a hybrid key exchange involving [NTRU Prime][8] (a [round 2 finalist][9] in the NIST competition) combined with conventional ed25519 elliptic curve keys. The approach allows ed25519 keys to generally stay in use, but transparently adds the appearance of "[quantum-forward secrecy][10]." The approach was adopted in OpenSSH v8.0:


```
commit dfd591618cdf2c96727ac0eb65f89cf54af0d97e
Author: [djm@openbsd.org][11]
Date:   Mon Jan 21 10:20:12 2019 +0000

    upstream: Add support for a PQC KEX/KEM:
   
    [sntrup4591761x25519-sha512@tinyssh.org][12] using the Streamlined NTRU Prime
    4591^761 implementation from SUPERCOP coupled with X25519 as a stop-loss. Not
    enabled by default.
```

The TinySSH server adheres closely to cryptographic technology associated with [Daniel J. Bernstein][13], relying on chacha20-poly1305 for the bulk of the SSH session traffic; no other cipher is allowed. It likewise does not allow password logins but requires user ed25519 keys to be in place for a successful connection. These constraints may seem rigid, but they are also best practices.

The TinySSH server can supplement or replace a Linux OpenSSH daemon, and instructions are present to do this with `inetd` or systemd socket activation. The minimalist stance of TinySSH also fits well with Linux container design, but there are a few twists required to achieve this.

In any case, NTRU key exchange has been deployed in OpenSSH for long enough that general use is a reasonable goal. It is also [vastly preferable to ssh-rsa][14] keys, the default SSH2 user and host key type for many years, which is now critically weakened by reliance upon SHA-1. While the author of TinySSH, Jan Mojžíš, hints NTRU key exchange has not yet reached the point where it is "ready for production use—including post-quantum crypto"—enabling it certainly appears safer than continuing to rely upon ssh-rsa.

### Design a container

Containers, in general, share a common kernel but separate userspace, which distinguishes them from virtual machines. The most straightforward Linux container likely starts with [BusyBox][15]. For this exercise, I obtained the [1.31.0][16] release that is compiled with musl libc (as opposed to uclibc). Choose your appropriate architecture; I have proceeded with a standard x86_64 PC.

As the root user with your copy of BusyBox in the local directory, enter the commands below to organize and launch `/home/pqc` as your Post-Quantum Container:


```
# mkdir -p /home/pqc/bin
# cp busybox-x86_64 /home/pqc/bin
# mkdir /home/pqc/root
# mkdir /home/pqc/ssh
# mkdir -p /home/pqc/var/log
# cd /home/pqc/bin
# chmod 755 busybox-x86_64
# ./busybox-x86_64 --list | awk '{print "ln -s busybox-x86_64 " $0}' | sh
# cd /home/pqc
# tar cf - /usr/share/zoneinfo | tar xvpf -
# ln -s bin sbin
# mkdir /home/pqc/etc
# echo 'NAME="Post-Quantum Container"' &gt; /home/pqc/etc/os-release
# echo 'root::0:0:root:/root:/bin/sh' &gt; /home/pqc/etc/passwd
# echo root❌0: &gt; /etc/group
# echo 'console::respawn:/bin/getty 38400 /dev/console' &gt; /home/pqc/etc/inittab
# echo '::sysinit:/bin/syslogd' &gt;&gt; /home/pqc/etc/inittab
# echo '::sysinit:/bin/inetd' &gt;&gt; /home/pqc/etc/inittab
# echo 'tssh 2222/tcp' &gt; /home/pqc/etc/services
# echo "tssh stream tcp nowait root /ssh/tinysshd tinysshd -lpsv \
   -x sftp=/ssh/sftp-server /etc/tinyssh/sshkeydir" &gt; /home/pqc/etc/inetd.conf
# systemd-nspawn -bD /home/pqc
```

After executing the final nspawn command above, a new userspace will launch that allows you to log in as root in an environment that mimics a basic Unix System V:


```
Spawning container pqc on /home/pqc.
Press ^] three times within 1s to kill container.
Jun 23 14:44:04 pqc syslog.info syslogd started: BusyBox v1.31.0
Jun 23 19:44:04 pqc daemon.info : starting pid 4, tty '': '/bin/inetd'
Jun 23 19:44:04 pqc daemon.err inetd[5]: tssh/tcp: unknown service
Jun 23 19:44:04 pqc daemon.info : starting pid 6, tty '/dev/console': '/bin/getty 38400 /dev/console'

pqc login: root
Jun 23 19:44:06 pqc auth.info login[6]: root login on 'console'
# ps
PID   USER     TIME  COMMAND
    1 root      0:00 init
    3 root      0:00 /bin/syslogd
    5 root      0:00 /bin/inetd
    6 root      0:00 -sh
    7 root      0:00 ps
#
```

The inetd daemon above is configured to launch TinySSH, which is not yet present in your container image. You can build TinySSH and return to the container for installation.

If you have never seen an nspawn container, take some time to explore it before proceeding. If you would like to shut it down, halt it:


```
# halt
The system is going down NOW!
Sent SIGTERM to all processes
Jun 27 21:51:42 pqc daemon.info : The system is going down NOW!
Jun 27 16:51:42 pqc syslog.info syslogd exiting
Sent SIGKILL to all processes
Requesting system halt
Container pqc has been shut down.
```

Be careful not to accidentally halt the host.

If you add a password to the root account in the configuration above, it will be stored using an ancient DES hash within the `/etc/passwd` file. Only the nspawn console will allow a password login; TinySSH ignores passwords. If you would prefer a shadow password, run the following commands within the container:


```
# echo root:::::::: &gt; /etc/shadow
# chmod 600 /etc/shadow
# passwd -a sha512 root
```

Eventually, you will want to disable the console getty and allow logins only via TinySSH. That is done by commenting the first line of `/home/pqc/etc/inittab` and placing the following service file for systemd:


```
# echo '[Unit]
Description=pqc container

[Service]
ExecStart=/usr/bin/systemd-nspawn -bD /home/pqc
' &gt; /etc/systemd/system/pqc.service
```

You are not ready to do this yet.

### Build musl

It is possible to use glibc and existing host code inside a container through a variety of mechanisms. However, this can be difficult, as there are a great many dependencies in most programs that can be tedious to replicate. Consider the `sshd` server on Red Hat/CentOS 7; placing all fourty-nine of these shared objects correctly within a container is not a trivial procedure:


```
$ ldd /usr/sbin/sshd
linux-vdso.so.1 =&gt;  (0x00007ffeec564000)
libfipscheck.so.1 =&gt; /lib64/libfipscheck.so.1 (0x00007fafbfa3b000)
libwrap.so.0 =&gt; /lib64/libwrap.so.0 (0x00007fafbf830000)
libaudit.so.1 =&gt; /lib64/libaudit.so.1 (0x00007fafbf607000)
[...]
libkeyutils.so.1 =&gt; /lib64/libkeyutils.so.1 (0x00007fafb978e000)
libattr.so.1 =&gt; /lib64/libattr.so.1 (0x00007fafb9589000)
libelf.so.1 =&gt; /lib64/libelf.so.1 (0x00007fafb9371000)
libbz2.so.1 =&gt; /lib64/libbz2.so.1 (0x00007fafb9161000)
```

The [musl C library][17] allows either a dramatic reduction or complete elimination of runtime linker dependencies in compiled objects. You can use it, at a minimum, to build a functional TinySSH.

In order to build musl, you must have the GNU C Compiler and associated tools present. If they have not been loaded, then obtain them by running the following command as root (on a Red Hat/CentOS platform):


```
`# yum group install 'Development Tools'`
```

Download musl, then unpack and compile it, preferably as a non-root user:


```
$ tar xvzf musl-1.2.0.tar.gz
$ cd musl-1.2.0/
$ ./configure
$ make
```

…then, as root:


```
`# make install`
```

Most of the installation will take place in `/usr/local/musl`, with the exception of `/lib/ld-musl-x86_64.so.1` (which would be more congruous in `/lib64`, but the odd placement is irrelevant when compiling static binaries).

Of particular interest is `/usr/local/musl/bin/musl-gcc`, which is a short shell script that utilizes the system C compiler with an alternate libc linkage.

### Build TinySSH

The flexibility of TinySSH in containers or a base OS installation requires slight variations in the build procedure, primarily to shift focus from glibc to musl, which is not difficult.

Legacy systems in various stages of sunsetting support can also use TinySSH to implement modern best-practice ciphers. Red Hat/CentOS 5 runs TinySSH quite well, although an elderly HP-UX 10.20 system could not compile it due to a lack of c99 support. Note that Red Hat/CentOS 8 includes NTRU-capable OpenSSH clients and servers; if your host OS is running OpenSSH v8 or above, TinySSH is really only appropriate for container usage (enabling NTRU keys on Red Hat/CentOS 8 requires changes to the `/usr/share/crypto-policies/DEFAULT/opensshserver.txt` file).

[Download][18] the `20190101.tar.gz` file, and unpack it:


```
$ tar xvzf 20190101.tar.gz
$ cd tinyssh-20190101
```

There is no `configure` step to perform a build, just a `make`:


```
$ make
sh -e make-tinyssh.sh
=== Sat Jun 27 18:00:33 CDT 2020 === obtaining compiler
=== Sat Jun 27 18:00:34 CDT 2020 ===   cc ok
=== Sat Jun 27 18:00:34 CDT 2020 === finishing
=== Sat Jun 27 18:00:34 CDT 2020 === checking compiler options
=== Sat Jun 27 18:00:34 CDT 2020 ===   -pedantic ok
[...]
=== Sat Jun 27 18:00:53 CDT 2020 ===   _tinyssh 6627
=== Sat Jun 27 18:00:53 CDT 2020 ===   74069 words of code
=== Sat Jun 27 18:00:53 CDT 2020 === finishing
=== Sat Jun 27 18:00:53 CDT 2020 === counting words of code
=== Sat Jun 27 18:00:53 CDT 2020 ===   sysdep 936
=== Sat Jun 27 18:00:53 CDT 2020 ===   tinyssh 38680
=== Sat Jun 27 18:00:53 CDT 2020 ===   crypto 21330
=== Sat Jun 27 18:00:53 CDT 2020 ===   60932 words of code
=== Sat Jun 27 18:00:53 CDT 2020 === finishing
```

This compiled a glibc-linked TinySSH, and you can display the dependent objects:


```
$ ldd build/bin/tinysshd
        linux-vdso.so.1 =&gt;  (0x00007ffce33e1000)
        libutil.so.1 =&gt; /lib64/libutil.so.1 (0x00007f53ade04000)
        libc.so.6 =&gt; /lib64/libc.so.6 (0x00007f53ada36000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f53ae007000)
```

This binary will work quite well for the host operating system's SSH server, but attempts to place it within an nspawn environment with its obvious dependencies will fail with calls to `getpwnam()`. Rather than debug what appears to be a glibc Name Service Switch problem, rebuild the code with musl:


```
make clean
CC='/usr/local/musl/bin/musl-gcc -static' make
ldd build/bin/tinysshd
```

The final output from the commands above should be "`not a dynamic executable`."

The musl library also supports using dynamic shared objects, just as glibc does. If you are preparing a great deal of compiled C using the musl environment in an nspawn, consider using shared libraries in your container applications to reduce memory consumption and perhaps even rebuilding BusyBox to use shared objects.

In any case, move the static TinySSH binaries into the container as the root user:


```
mv build/bin/tinysshd /home/pqc/ssh/
mv build/bin/tinysshd-makekey /home/pqc/ssh/
mv build/bin/tinysshd-printkey /home/pqc/ssh/
```

The only things lacking now are container host and user keys.

### Install keys and test login

If you previously halted your `pqc` container, restart it. Ensure you are logged in as root, and run the following commands:


```
mkdir /etc/tinyssh
/ssh/tinysshd-makekey /etc/tinyssh/sshkeydir
```

This will generate a new ed25519 host key. You might prefer to use an existing key from OpenSSH; this will be discussed below.

Additionally, an `authorized_keys` file must be installed into the specific user account that will host the login. If you have not yet generated such a key, do so. For this test case, it is preferable that the key not have a passphrase:


```
$ ssh-keygen -t ed25519 -f testkey
Generating public/private ed25519 key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in testkey.
Your public key has been saved in testkey.pub.
The key fingerprint is:
SHA256:tahsHrY5b0PqNMuxxDew35xS7FoLWNJ6VNOslUNCFao [cfisher@yourhost.com][19]
The key's randomart image is:
+--[ED25519 256]--+
|         .o.+.   |
|           * .   |
|          = *    |
|       . = = .   |
|      o E.o      |
|     o X. o      |
|      /o=o.      |
|     Bo%+*.o     |
|     .O+++=      |
+----[SHA256]-----+
```

Install the public key into the target account. This example uses root. If you prefer a non-root target, create the user and test it from the nspawn console. Install the key into the appropriate container directory:


```
# mkdir /home/pqc/root/.ssh
# cat testkey.pub &gt;&gt; /home/pqc/root/.ssh/authorized_keys
```

Test your login:


```
# ssh -p 2222 -i testkey root@localhost
The authenticity of host '[localhost]:2222 ([127.0.0.1]:2222)' can't be established.
ED25519 key fingerprint is SHA256:1nnku5/Q8leUwnbB9mDcfPobvsQapj2JJA6FVVQjTJg.
ED25519 key fingerprint is MD5:bc:dc:b6:52:31:8a:59:1d:dc:c7:61:7c:2b:7c:37:01.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[localhost]:2222' (ED25519) to the list of known hosts.
Enter passphrase for key 'testkey':
~ #
```

The container should now be ready for best-practice SSH logins, optionally protected by the NTRU (likely) quantum-secure key exchange.

### Post-quantum login and sftp

One problem with NTRU keys is that there are currently only two servers and one client that implement them. If you are lucky enough that your operating system includes OpenSSH v8 or above, you can directly test the NTRU exchange:


```
`$ ssh -p 2222 -i testkey -o KexAlgorithms=sntrup4591761x25519-sha512@tinyssh.org root@localhost`
```

If you are one of many Linux users not running such a recent OpenSSH release, you can use musl to make one. I will demonstrate other components of OpenSSH (sftp-server, scp, etc.) below, so even users of recent OpenSSH versions will have reasons to have a musl version. Download the latest release of OpenSSH, then perform a musl build with:


```
$ tar xvzf openssh-8.3p1.tar.gz
$ cd openssh-8.3p1
$ CC='/usr/local/musl/bin/musl-gcc -static' ./configure --without-openssl --without-zlib
$ make
```

Building without OpenSSL has been experimental for quite a long time:


```
$ ./configure --help | grep without-openssl | head -1
  --without-openssl       Disable use of OpenSSL; use only limited internal crypto **EXPERIMENTAL**
```

Immediately after the build completes, test an NTRU login:


```
`$ ./ssh -p 2222 -i ~/testkey -o KexAlgorithms=sntrup4591761x25519-sha512@tinyssh.org root@localhost`
```

If you use a key that has a password, you might see the following error from musl's build of ssh:


```
`Load key "/home/cfisher/testkey": key encrypted using unsupported cipher`
```

If this is the case, use the native `ssh-agent` with the musl `ssh` client, and remove the later `-i` reference to the key on the `ssh` command line:


```
$ eval $(ssh-agent)
Agent pid 21067
$ ssh-add ~/testkey
Enter passphrase for /home/cfisher/testkey:
Identity added: /home/cfisher/testkey ([cfisher@yourhost.com][19])
$ ./ssh -p 2222 \
-o KexAlgorithms=[sntrup4591761x25519-sha512@tinyssh.org][12] \
root@localhost
```

You might have noticed a reference to `sftp-server` in the `inetd` reference to TinySSH. If you want to allow sftp or scp, then copy the musl builds into the container, and test the login with a running agent (notice that I have called the glibc `sftp`):


```
# cp sftp-server /home/pqc/ssh
# cp scp /home/pqc/bin

$ echo 'put ssh-agent' | sftp -S ./ssh -o Port=2222 \
-o KexAlgorithms=[sntrup4591761x25519-sha512@tinyssh.org][12] \
root@localhost:/root
```

The output of the sftp session should be:


```
Connected to localhost.
Changing to: /root
sftp&gt; put ssh-agent
Uploading ssh-agent to /root/ssh-agent
ssh-agent                                     100% 1054KB  14.6MB/s   00:00
```

The use of scp is now [discouraged][20], but it is functional. This example assumes a running agent:


```
$ ./scp -S ./ssh -P 2222 -o KexAlgorithms=[sntrup4591761x25519-sha512@tinyssh.org][12] ssh root@localhost:/root
ssh                                           100% 2492KB  59.3MB/s   00:00
```

It might be helpful to set a shell alias for the NTRU option:


```
$ alias pqssh="/your/path/to/ssh \
-o KexAlgorithms=[sntrup4591761x25519-sha512@tinyssh.org][12]"
$ pqssh -i testkey -p 2222 root@localhost
```

If non-localhost logins to the container should be allowed, you must open any firewall restrictions on the port. One way to do this is:


```
`iptables -w -I INPUT -p tcp --dport 2222 --syn -j ACCEPT`
```

Welcome to post-quantum key exchange.

### Migrate the host key

If you ever intend to move host keys between OpenSSH and TinySSH servers, then the TinySSH key format might be a problem, as it is not in the form expected by OpenSSH:


```
# ls -al /home/pqc/etc/tinyssh/sshkeydir
total 8
drwxr-xr-x    1 root     0               42 Jun 27 18:36 .
drwxr-xr-x    1 root     0               18 Jun 27 18:36 ..
-rw-------    1 root     0               64 Jun 27 18:36 .ed25519.sk
-rw-r--r--    1 root     0               32 Jun 27 18:36 ed25519.pk
```

The `tinysshd-printkey` utility is only able to print the public key. Moving the private key to the OpenSSH format might require custom code that does not appear to exist. For this reason, the `tinysshd-makekey` utility is concerning for production host keys.

It is likely best to maintain an OpenSSH-compatible copy of your host keys and use a converter to generate the TinySSH variant. The [current converter][21] requires Python 3 (avoid the [older, C-based][22] key converter). I loaded the Python converter on Red Hat/CentOS 8:


```
# python3 -m pip install tinyssh-keyconvert-0.3.2.zip
WARNING: Running pip install with root privileges is generally not a good idea. Try `__main__.py install --user` instead.
Processing ./tinyssh-keyconvert-0.3.2.zip
Installing collected packages: tinyssh-keyconvert
  Running setup.py install for tinyssh-keyconvert ... done
Successfully installed tinyssh-keyconvert-0.3.2
```

An OpenSSH ed25519 host key is usually stored in `/etc/ssh/ssh_host_ed25519_key` and should be created without a password. Convert such a key to the TinySSH format with:


```
$ tinyssh-keyconvert ssh_host_ed25519_key --dir .

$ ll ed25519.pk .ed25519.sk
-rw-r--r--. 1 fishecj itg 32 Jun 25 11:57 ed25519.pk
-rw-------. 1 fishecj itg 64 Jun 25 11:57 .ed25519.sk
```

Copy all relevant keys to the hosts or containers that will use them. The `ssh_host_ed25519_key.pub` public key is not strictly necessary, as it can be regenerated with `ssh-keygen -y`. Be sure to delete any temporary copies after installation is complete, as losing these keys will compromise a host's communication security:


```
`$ rm -i .ed25519.sk ed25519.pk ssh_host_ed25519_key`
```

### Conclusion

There are a number of arguments against the methods outlined above. Obvious objections include: NTRU Prime has not been officially endorsed; a standard OpenSSH `sshd` is not difficult to prepare with musl; TinySSH does not use "privilege separation" and/or `chroot();` TinySSH lacks important features (port forwarding, sftp/scp, X11, VPN, etc.); and a larger musl SSH build should be performed that does not use experimental features.

With regard to an official NTRU endorsement, OpenSSH intends to disable ssh-rsa in the near term. This will be a traumatic change for legacy systems, many of which will be left with orphaned SSH implementations. With this level of change on the horizon, pressure should be exerted to select the best available cryptosystem, and a case can be made for the inclusion of TinySSH NTRU Prime. No administrator wants to do this twice.

The TinySSH server is vastly less difficult to configure than a full implementation of OpenSSH `sshd`. The server's author claims that "[TinySSH can't be misconfigured][23]"; the same cannot be said for `sshd`. Ease of administration is a factor, especially in a rollout to many servers.

TinySSH's security record appears to be quite clean, and its design avoids known problems with C. Best practices for users are enforced by this server, which may be both a security benefit and a training liability. Perhaps the loss of privilege separation is, in the end, a reasonable trade.

Users can easily learn bad habits and reliance on exotic or deprecated functionality with OpenSSH. These features should be extended parsimoniously to experienced users with demonstrated need.

Finally, if only the `scp` and/or the `sftp-server` server components are used with TinySSH, the experimental build is likely not relevant. OpenSSL also does not include any NTRU implementation, so that aspect likely suffers no degradation

To address larger questions, SSH faces great turmoil with immediate RSA key deprecation and conversion (making TinySSH's decision to omit RSA sagely wise). To ignore the post-quantum question, which was asked by NIST in 2016 and is still unanswered, would foolishly waste the opportunity for broader operational experience with NTRU Prime that would be valuable for both SSH and TLS. NIST opened the post-quantum cryptography competition in 2016, and final drafts are scheduled for 2022-24. AES was [decided in four years][24], but the current competition is greatly delayed.

This ship needs to sail.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/tinyssh

作者：[Charles Fisher][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/chasil
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/containers_modules_networking_hardware_parts.png?itok=rPpVj92- (Parts, modules, containers for software)
[2]: https://en.wikipedia.org/wiki/Shor%27s_algorithm
[3]: https://www.dwavesys.com/press-releases/d-wave-previews-next-generation-quantum-computing-platform
[4]: https://en.wikipedia.org/wiki/CMOS
[5]: https://en.wikipedia.org/wiki/Quantum_logic_gate
[6]: https://quantumcomputingreport.com/whats-happening-with-post-quantum-cryptography-at-nist/
[7]: https://tinyssh.org
[8]: https://ntruprime.cr.yp.to/
[9]: https://csrc.nist.gov/projects/post-quantum-cryptography/round-2-submissions
[10]: https://github.com/janmojzis/tinyssh/issues/42
[11]: mailto:djm@openbsd.org
[12]: mailto:sntrup4591761x25519-sha512@tinyssh.org
[13]: https://www.metzdowd.com/pipermail/cryptography/2016-March/028824.html
[14]: https://www.openssh.com/txt/release-8.3
[15]: https://busybox.net
[16]: https://busybox.net/downloads/binaries/1.31.0-defconfig-multiarch-musl/
[17]: https://www.musl-libc.org/
[18]: https://tinyssh.org/install.html
[19]: mailto:cfisher@yourhost.com
[20]: https://www.openssh.com/txt/release-8.0
[21]: https://raw.githubusercontent.com/ansemjo/tinyssh-keyconvert/master/tinyssh-keyconvert
[22]: https://github.com/ansemjo/tinyssh-convert
[23]: https://tinyssh.org/
[24]: https://en.wikipedia.org/wiki/Advanced_Encryption_Standard_process
