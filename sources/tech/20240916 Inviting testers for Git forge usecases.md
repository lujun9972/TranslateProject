[#]: subject: "Inviting testers for Git forge usecases"
[#]: via: "https://fedoramagazine.org/inviting-testers-for-git-forge-usecases/"
[#]: author: "Michal Konečný https://fedoramagazine.org/author/zlopez/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Inviting testers for Git forge usecases
======

![][1]

Photo by [Yancy Min][2] on [Unsplash][3] Cropped

Following [@t0xic0der][4] and [@humaton][5]’s talk on the Git forge ARC ([Advance Reconaissance Crew][6]) investigation during Fedora Linux Release Party 40 and more recently, [@humaton][5]’s talk on the topic during Flock To Fedora 2024 – we have opened up our ARC investigation to all contributors within the Fedora Project. Please refer to the [ARC initiative page][7] to create or retrieve the use case requirements for the Git forge replacement. As part of that we created community deployments for [GitLab][8] and [Forgejo][9].

### Testing GitLab instance

The [GitLab][8] instance has limited access and needs manual approval of the account. To get an account on this instance please follow the instructions below:

  1. Create an account on the [GitLab][8] instance
  2. Open a ticket on [Fedora Infrastructure issue][10]
    1. Use **Approve my user on GitLab test instance** as summary
    2. In **Types** choose **gitlab_testing_request** template
    3. Fill in the template
  3. Wait for us to approve your account



Our test GitLab instance doesn’t allow SSH pushes. You need to use HTTPS to push changes to the repository.

### Testing Forgejo instance

[Forgejo][9] test instance is much more straightforward when creating an account as it is connected to our staging Fedora Account System. To get an account follow the instructions below:

  1. Create an account in [staging Fedora Account System][11] (you can skip this step if you already have the staging Fedora account)
  2. Login to [Forgejo][9] test instance with your staging Fedora account using **Sign In with Fedora Accounts button**



Our test [Forgejo][9] instance is hosted in the same environment as the GitLab test instance so it doesn’t allow SSH pushes either. You need to use https to push changes to the repository.

Since the [Forgejo][9] test instance is using a staging Fedora account you can use the same username for HTTPS push, but for the password you need to generate a token in **Settings- >Application->Access Tokens**.

### Sharing feedback with us

To share your testing results use this [discussion thread][12] and let us know if either Forgejo or GitLab is suitable for tested use cases.

### How to contact us

You can reach us with any question either in this [discussion thread][12] or in our [Matrix ARC investigation room][13].

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/inviting-testers-for-git-forge-usecases/

作者：[Michal Konečný][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/zlopez/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/Git_Forge_testers-816x345.jpg
[2]: https://unsplash.com/@yancymin?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-close-up-of-a-text-description-on-a-computer-screen-842ofHC6MaI?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://discussion.fedoraproject.org/u/t0xic0der
[5]: https://discussion.fedoraproject.org/u/humaton
[6]: https://fedora-arc.readthedocs.io/en/latest/index.html
[7]: https://pagure.io/fedora-infra/arc/issue/164
[8]: https://gitlab-gitlab-system.apps.fedora.cj14.p1.openshiftapps.com/users/sign_in
[9]: https://forgejoroute-communishift-forgejo.apps.fedora.cj14.p1.openshiftapps.com/
[10]: https://pagure.io/fedora-infrastructure/
[11]: https://accounts.stg.fedoraproject.org/
[12]: https://discussion.fedoraproject.org/t/inviting-testers-for-git-forge-usecases
[13]: https://matrix.to/#/#arc:fedoraproject.org
