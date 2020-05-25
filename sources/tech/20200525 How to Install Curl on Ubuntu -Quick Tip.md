[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How to Install Curl on Ubuntu [Quick Tip])
[#]: via: (https://itsfoss.com/install-curl-ubuntu/)
[#]: author: (Sergiu https://itsfoss.com/author/sergiu/)

How to Install Curl on Ubuntu [Quick Tip]
======

Summary

To install curl on Ubuntu or Ubuntu-based Linux distributions, you can use the apt command in the terminal like this:

**sudo apt install curl**

[Curl][1] is one of the underrated and yet crucial command line tool for transferring data using various network protocol.

As a Linux user, you’ll often come across curl being used for downloading software from web repositories. Curl is much more powerful than that. Curl allows more complex operations than simply downloading files: any sort of HTTP requests, SSL connections, FTP uploads, authentication, managing proxies, setting timeouts and many more.

Another major advantage is the fact that it is designed to work without user interaction and can very easily be used in scripts. This is why curl is used in numerous software projects across the globe.

We are not going to discuss [various ways curl command can be used][2]. The full range of options can be easily referenced in the man page, accessible using the **man curl** command or by following **[this link][3]**.

The scope of this quick tutorial is to show how to install curl on Ubuntu.

### Installing curl on Ubuntu

Since curl is a popular open source software that has been used for more than twenty years now, Ubuntu includes it in the main repository.

Which means installing curl on Ubuntu is just a matter of a single command. But before you install curl, I suggest updating the local package cache first.

Open a terminal (use Ctrl+Alt+T shortcut on Ubuntu) and use the following [command to update Ubuntu][4] package cache:

```
sudo apt update
```

Now that you updated the cache, you can install curl using apt command like this:

```
sudo apt install curl
```

It cannot be more simple than this, can it? Once the installation is finished, you can check everything went fine using:

```
curl --version
```

This will also give you the current installed version. At the time of writing this article, this is what my output is (yours should be similar):

```
curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3
Release-Date: 2018-01-24
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp smb smbs smtp smtps telnet tftp
Features: AsynchDNS IDN IPv6 Largefile GSS-API Kerberos SPNEGO NTLM NTLM_WB SSL libz TLS-SRP HTTP2 UnixSockets HTTPS-proxy PSL
```

Trivia

Curl was originally named urlget. It was later renamed to httpget and ultimately renamed to curl. By the way, curl stands for ‘Client URL’.

Questions? Feel free to leave a comment below.

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-curl-ubuntu/

作者：[Sergiu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sergiu/
[b]: https://github.com/lujun9972
[1]: https://curl.haxx.se/
[2]: https://linuxhandbook.com/curl-command-examples/
[3]: https://curl.haxx.se/docs/manpage.html
[4]: https://itsfoss.com/update-ubuntu/
