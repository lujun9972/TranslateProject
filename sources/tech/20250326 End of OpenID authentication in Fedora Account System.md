[#]: subject: "End of OpenID authentication in Fedora Account System"
[#]: via: "https://fedoramagazine.org/end-of-openid-authentication-in-fedora-account-system/"
[#]: author: "Michal Konečný https://fedoramagazine.org/author/zlopez/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

End of OpenID authentication in Fedora Account System
======

![][1]

Photo by [Rui Silva sj][2] on [Unsplash][3] (cropped)

The Fedora Infrastructure Team is announcing the end of OpenID in Fedora Account System (FAS). This will occur on **20th May 2025**.

### Why the change?

[OpenID][4] is being replaced by [OpenIDConnect][5] (OIDC) in most of the modern web and most of the Fedora infrastructure is already using OIDC as the default authentication method. OIDC offers better security by handling both authentication and authorization. It also allows us to have more control over services that are using Fedora Account System (FAS) for authentication.

### What will change for you?

With the End Of Life of OpenID we will switch to OIDC for everything and no longer support authentication with OpenID.

If **your web or service is already using OIDC** for authentication **nothing will change for you**. If **you are still using OpenID** open a ticket on [Fedora Infrastructure issue tracker][6] and **we will help you with migration to OIDC**.

**For users** using FAS as authentication option **there should be no change at all**.

### How to check if a service you maintain is using OpenID?

You may quickly check if your service is using OpenID for FAS authentication by looking at where you are redirected when logging in with FAS.

If you are redirected to <https://id.fedoraproject.org/openidc/Authorization> you are already using OIDC and you can just ignore this announcement.

If you are being redirected to <https://id.fedoraproject.org/openid> you are still using the **OpenID authentication method**. You should open a ticket on [Fedora Infrastructure issue tracker][6] so we can help you with migration.

### What will happen now?

We will be reaching out directly to services we identify as using OpenID. But since we don’t have control over OpenID authentication, we can’t identify everyone.

If you are interested in following this work feel free to watch this [ticket][7].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/end-of-openid-authentication-in-fedora-account-system/

作者：[Michal Konečný][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/zlopez/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/03/end_OPENID_in_FAS-816x345.jpg
[2]: https://unsplash.com/@ruisilvasj?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/silhouette-of-mountain-during-sunset-JxXc54HYYaI?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://en.wikipedia.org/wiki/OpenID
[5]: https://openid.net/developers/how-connect-works/
[6]: https://pagure.io/fedora-infrastructure/issues
[7]: https://pagure.io/fedora-infrastructure/issue/10241
