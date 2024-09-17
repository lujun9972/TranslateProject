[#]: subject: "Ubuntu Adds a New Authentication Feature"
[#]: via: "https://news.itsfoss.com/ubuntu-authd/"
[#]: author: "Sourav Rudra https://news.itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Ubuntu Adds a New Authentication Feature
======
Better security for Ubuntu users. A good step.
[![][1]][2]

Being adept in the field of cybersecurity is an important skill to have, more so if you are an enterprise with a workforce spanning the globe. If you were to slip up, it would open up the door for a range of cyberattacks, resulting in monetary and reputational losses.

Some of the most common ways to secure an IT infrastructure are to manage who/what gets access to which resources through the use of open protocols like [OAuth][3]. Another increasingly popular way to manage identity [authentication][4] is by using [OpenID Connect][5] (OIDC), which is based on OAuth and is a standardized way for authorizing users to access apps and services.

Moving on to the topic at hand, Canonical has introduced **support for OIDC authentication on Ubuntu** by implementing a new open-source tool called “ **Authd** ”.

Let's see what it has to offer. 😃

### Ubuntu Authd: What To Expect?

![Source: Canonical][6]

Primarily written in the [Go][7] programming language, Authd is an authentication service for [Ubuntu 24.04 LTS][8] that has been introduced to simplify the needs of organizations and individuals looking to use identity management services.

At launch, Authd supports OIDC, with Microsoft's [Entra ID][9] being the first supported [identity provider][10]. As demonstrated by the screenshot above, Ubuntu was showing an authentication prompt to log in to a service equipped with Entra ID.

Authd can be used to log in through the GNOME Display Manager ([GDM][11]), or via Secure Shell ([SSH][12]). It has a modular design that makes it effortless to integrate with cloud services.

Canonical also intends **to introduce more identity providers** in the near future, with plans to also have a white-label OIDC provider ( _allows wider customization)_ in the mix.

Though, they have not mentioned which ones, if I had to guess, they are probably going to integrate well-known options like [Okta][13], [Google Identity Platform][14], and [Auth0][15].

You can take a look at **Authd's architecture** below. 👇

![][16]

We won't go into the technical aspects of it, but keep in mind that the identity brokers shown above are provided as [snaps][17]. In the end, Authd is something that arose out of the need for a reliable solution for supporting identity providers on Linux desktops and servers.

You can go through the [announcement blog][18] to dive into the technical bits of Authd.

#### Want To Check It Out?

Currently, Authd is available for all users of Ubuntu 24.04 [Desktop][19] and [Server][20]. If you are looking to deploy this at an enterprise level, then the official [Project Wiki][21] is worth a visit.

And, if you want to take a look at the source code or contribute to the project, then you should visit Authd's [GitHub][22] repo.

[Authd (GitHub)][22]

**Suggested Read** 📖

![][23]

* * *

--------------------------------------------------------------------------------

via: https://news.itsfoss.com/ubuntu-authd/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://news.itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://news.itsfoss.com/assets/images/pikapods-banner-v3.webp
[2]: https://www.pikapods.com/?utm_campaign=banner-2024-05&utm_source=itsfoss
[3]: https://en.wikipedia.org/wiki/OAuth
[4]: https://en.wikipedia.org/wiki/Authentication
[5]: https://openid.net/developers/how-connect-works/
[6]: https://news.itsfoss.com/content/images/2024/09/Ubuntu_Authd.jpg
[7]: https://go.dev/
[8]: https://news.itsfoss.com/ubuntu-24-04-lts/
[9]: https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id
[10]: https://en.wikipedia.org/wiki/Identity_provider
[11]: https://en.wikipedia.org/wiki/GNOME_Display_Manager
[12]: https://linuxhandbook.com/ssh-hardening-tips/
[13]: https://www.okta.com/
[14]: https://cloud.google.com/security/products/identity-platform
[15]: https://auth0.com/
[16]: https://news.itsfoss.com/content/images/2024/09/Ubuntu_Authd_Architecture.jpg
[17]: https://ubuntu.com/core/services/guide/snaps-intro
[18]: https://ubuntu.com//blog/authd-oidc-authentication-for-ubuntu-desktop-server
[19]: https://ubuntu.com/download/desktop
[20]: https://ubuntu.com/download/server
[21]: https://github.com/ubuntu/authd/wiki/01---Get-started-with-authd
[22]: https://github.com/ubuntu/authd
[23]: https://linuxhandbook.com/content/images/size/w256h256/2021/08/Linux-Handbook-New-Logo.png
