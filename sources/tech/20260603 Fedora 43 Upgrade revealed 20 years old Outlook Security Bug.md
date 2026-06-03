[#]: subject: "Fedora 43 Upgrade revealed 20 years old Outlook Security Bug"
[#]: via: "https://fedoramagazine.org/fedora-43-upgrade-revealed-20-years-old-outlook-security-bug/"
[#]: author: "Marius Schwarz https://fedoramagazine.org/author/mschwarz/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Fedora 43 Upgrade revealed 20 years old Outlook Security Bug
======

![][1]

[Illustration][2] by [Boxicons][3] on [Unsplash][4]

Yes, the Fedora 43 upgrade brought an interesting revelation for all Outlook users—one that Microsoft is unlikely to be thrilled about. Outlook was not encrypting email connections, even though SSL/TLS was clearly enabled in the account settings. It looks like, that bug dates back to at least Outlook 2007, which is the oldest Outlook version I was informed about.

### Let us start with the beginning

Every six months, Fedora Servers require and upgrade to the next release version, as you all know 😉 This May we had to upgrade from 42 to 43 and in this upgrade, Dovecot POP/IMAP server switched to version 2.4.3. Dovecot did us all an unexpected favor, because it required a full rewrite of the used service config, because it’s not backwards compatible. This change introduced a new paradigm: PLAIN TEXT passwords are no longer allowed over unencrypted connections.

This is a major break with the oldest RFCs (i.e. RFC 1081) regarding POP3 behavior, but a good one IMHO. No one should still use unencrypted connections to any form of service on the internet when we have easy to use encryption protocols like STARTTLS (STLS) at hand in any major client.

### The Day After

After the upgrade, “we” (admins & customers) did not even know about the now broken auth-mechanism. This came a day later when customers started to call the support line about rquesters popping up for them to enter their passwords again. This is a normal behavior if auth fails… and it failed hard 😉

As all admins know, such upgrades will result in higher amounts of support calls. To my surprise it was all Outlook clients that called. The oldest version so far was Outlook 2007. We even had an old MACOS Outlook :-). They all had in common, that the mailbox prefs had “SSL/TLS” enabled, but used Port 110, which is the old cleartext port for POP3, where port 995 is the correct SSL port. A normal mailclient would change the port number to 995 as soon as you enable SSL/TLS encryption. This is because you can’t “speak” SSL on a non-ssl port, except if you choose STARTTLS. This starts as a cleartext connection, but upgrades itself to ssl-encrypted later.

### “Look, there is something out there!”

Outlook did the worst move you can take as a security enhanced app. It silently ignored the choosen SSL option and used the unencrypted port 110 without any notice to the user. After our server upgrade, the following message popped up:

![German version of the error message][5]

“-ERR [AUTH] Cleartext authentication disallowed on non -secure ( SSL/TLS ) connections.“ popped up if you tried to open your inbox. The server logs revealed it clearly: the user used a non-secure connection and got this message correctly. This never got noticed since the EU GDRP only states, that corporations and organisations need to protect their data via a transport encryption like TLS. Normal persons don’t need to do so.

Even some of the notable folks of Fedora did not use encryption, which I personally advise to change immediately. Having this in mind, who are we to judge if you encrypt your connection or not? 😉

### **Really folks: use TLS encryption for your mailboxes!**

You can easily check if TLS encryption is working. Send yourself an mail and open the mail headers, you will find lines like this:

_Received: from bastion01.fedoraproject.org ([38.145.32.11] helo=bastion.fedoraproject.org)
by s113.resellerdesktop.de with esmtps **(TLS1.3) tls TLS_AES_256_GCM_SHA384**
(Exim 4.99.2)
(envelope-from <[updates@fedoraproject.org][6]>)
…_
Any good MTA ( Exim, Postfix, etc. ) will note if the connection was encrypted or not.

If you don’t see an encryption notice, you can use this command:

```

    tcpdump -A -n -n port 110 or port 143

```

in a root terminal and see if the unencrypted port is used for transport. If so, if it’s cleartext or if it’s using STLS.

So… THANKS Fedora 43 and Dovecot 2.4 … you revealed a 20 year old security bug in Outlook \o/

**Disclaimer** : It is possible that MS patched the Outlook UI in the past in a way that only old accounts are affected by this major fail. As Fedora users we had no Outlook available to test this 😉

Source: <https://marius.bloggt-in-braunschweig.de/2026/06/03/outlook-hat-emailverbindung-nicht-verschluesselt/>

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/fedora-43-upgrade-revealed-20-years-old-outlook-security-bug/

作者：[Marius Schwarz][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mschwarz/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2026/06/20_year_old_Outlook_bug-816x345.jpg
[2]: https://unsplash.com/illustrations/an-open-black-padlock-icon-on-a-white-background-MWCbAefWxlc?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/@boxicons/illustrations?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://unsplash.com/illustrations?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[5]: https://fedoramagazine.org/wp-content/uploads/2026/06/Outlookpop3Fehler.jpg
[6]: mailto:updates@fedoraproject.org
