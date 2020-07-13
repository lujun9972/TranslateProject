[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Some easy choices for encrypting files on Linux)
[#]: via: (https://www.networkworld.com/article/3566374/some-easy-choices-for-encrypting-files-on-linux.html)
[#]: author: (Sandra Henry-Stocker https://www.networkworld.com/author/Sandra-Henry_Stocker/)

Some easy choices for encrypting files on Linux
======

[Gerd Altmann][1] [(CC0)][2]

There are numerous commands for encrypting files on Linux. When you want to limit access to file contents, you can use file permissions but file encryption makes limiting access much more effective. This post compares some of the commands for encrypting files and provides an easy script for trying them out.

Encryption means, of course, that a file that you can look at with Linux commands and tools is altered in ways that make it unusable and unreadable unless you reverse the encryption process. Encryption does not generally reduce the size of files unless compression is used as well. In fact, the encryption process might make some files larger. Some commands compress by default; others do not.

Things to keep in mind when preparing to encrypt a file include how you intend to use it (e.g., secure backups, transfer to another system), how you manage keys so that you can decrypt the file when needed, and whether the original file remains on the original system or is encrypted "in place" -  you are left only with the encrypted version of the file.

NOTE: Some encryption commands can be used with public/private keys or with passwords provided at the time of the encryption. This post only shows commands using passwords/passphrases.

### gpg

One of the standard and most well know tools for encrypting files on Linux is **gpg**. It can provide both digital encryption and signing services although, in this post, we’ll just look at encrypting files with a passphrase. Unlike some of the other tools, **gpg** does apply some file compression before encrypting the file contents.

If you type a command like this one, the contents of the file will be encrypted using a symmetric key. In other words, the same word or phrase will  be used both to encrypt and to decrypt the file. Public/private keys can be used with the **-e** option.

```
$ gpg -c BigFile
```

You will be prompted twice to enter a password and the original file will remain intact as shown in this example:

```
$ ls -l BigFile*
-rw-rw-r-- 1 shs shs 107740386 Jul 10 13:21 BigFile
-rw-rw-r-- 1 shs shs  32359452 Jul 11 11:00 BigFile.gpg
```

Notice the nice reduction in the resultant file size and that original file is still intact.

The **gpg** command only works with one file at a time.

### zip

The **zip** command is generally used to compress files and to collect files into archives for easy storage and transport. The command does, however, also support encryption. You just have the add the --encrypt option.

```
$ zip --encrypt BigFile.zip BigFile
```

Like **gpg**, **zip** does both encryption and compression, so the resultant file size should be considerably smaller than the original.

```
$ ls -l BigFile*
-rw-rw-r-- 1 shs shs 107740386 Jul 10 13:21 BigFile
-rw-rw-r-- 1 shs shs  27587355 Jul 10 14:40 BigFile.zip
```

Since **zip** is a tool intended to create archives, you can add multiple files to your encrypted bundle by adding them on the command line.

```
$ zip --encrypt loops.zip loop1 loop2
Enter password:
Verify password:
  adding: loop1 (deflated 4%)
  adding: loop2 (deflated 10%)
$ ls -l loops*
-rw-rw-r-- 1 shs shs 468 Jul 11 09:04 loops.zip
```

### 7z

The **7z** command works like **zip**, but touts a surprisingly impressive compression ratio. Like **zip**, it can include a number of files in one encrypted archive. To invoke encryption, include the encryption password on the command line following the **-p** option.

```
$ 7z a BigFile.7z BigFile -phard2gue$$

$ ls -l BigFile*
-rw-rw-r-- 1 shs shs 107740386 Jul 10 13:21 BigFile
-rw-rw-r-- 1 shs shs     27674 Jul 11 12:37 BigFile.7z
```

### ccrypt

Another tool for encrypting and decrypting files, **ccrypt** (based on the Rijndael block cipher) is believed to provide very strong security and, like the other commands described, is easily run on the command line.

Notice that **ccrypt** removes the original file (encrypts the file in place), doesn't significantly change the file size and doesn't alter the file's date/time to reflect the time the encryption was performed.

```
$ ccrypt -e BigFile
$ ls -l BigFile*
-rw-rw-r-- 1 shs shs 107740418 Jul  9 10:09 BigFile.cpt
```

The **ccrypt** command can encrypt multiple files with one command, but encrypts them separately.

### mcrypt

The **mcrypt** command prompts for a password twice, leaves the original file intact and changes file permissions to that the encrypted file only provides read and write access permissions to the file owner. It offers a lot of choices with respect to encryption algorithms and also provides options for compressing the files prior to encryption (see-z and -p options. It can work with multiple files, but encrypts them separately.

Using the --list option, **mycrypt** will list the available encryption algorithms.

```
$ mcrypt --list
cast-128 (16): cbc cfb ctr ecb ncfb nofb ofb
gost (32): cbc cfb ctr ecb ncfb nofb ofb
rijndael-128 (32): cbc cfb ctr ecb ncfb nofb ofb
twofish (32): cbc cfb ctr ecb ncfb nofb ofb
arcfour (256): stream
cast-256 (32): cbc cfb ctr ecb ncfb nofb ofb
loki97 (32): cbc cfb ctr ecb ncfb nofb ofb
rijndael-192 (32): cbc cfb ctr ecb ncfb nofb ofb
saferplus (32): cbc cfb ctr ecb ncfb nofb ofb
wake (32): stream
blowfish-compat (56): cbc cfb ctr ecb ncfb nofb ofb
des (8): cbc cfb ctr ecb ncfb nofb ofb
rijndael-256 (32): cbc cfb ctr ecb ncfb nofb ofb
serpent (32): cbc cfb ctr ecb ncfb nofb ofb
xtea (16): cbc cfb ctr ecb ncfb nofb ofb
blowfish (56): cbc cfb ctr ecb ncfb nofb ofb
enigma (13): stream
rc2 (128): cbc cfb ctr ecb ncfb nofb ofb
tripledes (24): cbc cfb ctr ecb ncfb nofb ofb
```

The **mcrypt** command appears to use **rijndael-128** as its default encryption algorithm. However, you can verify which has been used by using the **file** command on the compressed file:

```
$ file BigFile.bz2.nc
BigFile.bz2.nc: mcrypt 2.5 encrypted data, algorithm: rijndael-128, keysize: 32 bytes, mode: cbc,
```

### A script for trying encryption commands

This script should be called "try" and makes it easy for you to experiment with  the tools covered in this post. For example, if you type "try 7z target" (where "target" is the name of the file you want to encrypt), the script will run the command to encrypt your file with **7z** and show you the results. If you try to use a command that is not installed on your system, it will explain that it isn't yet set up to use that command.

```
#!/bin/bash

# verify that 2 arguments have been provided
if [ $# != 2 ]; then
    echo "OOPS: command and file name required"
    exit
fi

# make sure the requested encryption command in available
which $1 > /dev/null
if [ $? != 0 ]; then
    echo "$1 not available"
    exit 1
fi

# make sure the file exists
if [ ! -f $2 ]; then
    echo "No such file: $2"
    exit 2
fi

case $1 in
  gpg)  gpg -c $2
        ;;
  ccrypt) ccrypt -e $2
        ;;
  7z)   echo -n "please provide password: "
        read password
        7z a $2.7z $2 -p$password
        ;;
  zip)  zip --encrypt $2.zip $2
        ;;
  mcrypt) mcrypt -p $2
        ;;
  *)    echo "Sorry, this script is not yet set up for $1"
        exit;;
esac

# show the file(s)
ls -l $2*
```

The **try** script is not set up to encrypt more than one target file at a time as it uses $2 (the second argument provided to the script) to specify the target file and exits if more than one file is provided as an argument. Feel free to modify or add to the script to suit your needs.

Join the Network World communities on [Facebook][3] and [LinkedIn][4] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3566374/some-easy-choices-for-encrypting-files-on-linux.html

作者：[Sandra Henry-Stocker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Sandra-Henry_Stocker/
[b]: https://github.com/lujun9972
[1]: https://pixabay.com/illustrations/data-key-key-close-close-to-lock-571156/
[2]: https://creativecommons.org/publicdomain/zero/1.0/
[3]: https://www.facebook.com/NetworkWorld/
[4]: https://www.linkedin.com/company/network-world
