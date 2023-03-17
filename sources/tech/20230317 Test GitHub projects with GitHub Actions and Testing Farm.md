[#]: subject: "Test GitHub projects with GitHub Actions and Testing Farm"
[#]: via: "https://fedoramagazine.org/test-github-projects-with-github-actions-and-testing-farm/"
[#]: author: "Petr Hracek https://fedoramagazine.org/author/phracek/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Test GitHub projects with GitHub Actions and Testing Farm
======

![][1]

Photo by [İsmail Enes Ayhan][2] on [Unsplash][3]

Every project on GitHub that’s destined for [Red Hat Enterprise Linux][4] (RHEL), Fedora Linux, CentOS 7, CentOS Stream 8, and CentOS Stream 9, should be tested before its changes are synced into a Git distribution repository (dist-git). It’s important to catch problems before delivering software to customers, and help quality assurance teams catch errors. We should implement [Shift Left][5] into our workflows process.

### Introduction

[Testing Farm][6] is an open-source testing system offered as a service. Testing Farm’s idea is similar to [Compile Farms][7], but with a focus on executing automated tests. Its mission is to provide a reliable and scalable service for executing automated tests from various users, such as Fedora CI, Packit, and others. The entry point for our users is an [HTTP-based API][8]. Testing Farm scales across many infrastructures, including private and public clouds. Using the composite [**testing-farm-as-a-github-action**][9], currently available on the GitHub Marketplace, allows you to test your project efficiently.

#### GitHub Marketplace and advantages of publishing actions here

[GitHub Marketplace][10] is a place where developers can find, among other elements, all published GitHub Actions, in one place. Anyone is authorized to publish an action on the GitHub Marketplace.

An action, in order to be published, must reside in its own GitHub repository.

The advantage of publishing an action on the Marketplace, in addition to publishing it in a public GitHub repository, is the visibility of written actions for other users.

#### Testing Farm as GitHub Action

[Testing-farm-as-a-github-action][11], shortly TFaGA, is a composite GitHub action, intended to be used from other GitHub Actions.

Its main purpose is scheduling tests on the Testing Farm infrastructure triggered by an event that occurs in [a GitHub repository][12] and, optionally, displaying the results of executed tests.

NOTE: It is important to have the tested code reviewed by an **authorized person** , like **an owner** or **member** , in order to avoid running malicious code on the Testing Farm infrastructure.

Any kind of test which can be described with a TMT plan, can be executed. The testing environment can be chosen from Fedora Linux, CentOS, including CentOS Stream, or RHEL. We need to test our software as soon as possible.

##### For whom is testing-farm-as-github-action intended

The TFaGA can be used by developers or maintainers, generally, anyone who wants to test a repository located on GitHub. Anyone who would like to add software to the distributions mentioned above should guarantee that it delivers working software. Customers love software that is working and tested.

##### Action inputs

TFaGA input is highly configurable but there only two inputs that are without default values and are required to be inserted by the user. These are:

  * api_key – API key for Testing Farm
  * git_url – URL to a repository with TMT plans



NOTE: You can obtain **api_key** from [tft@redhat.com][13]. For more information [see the onboarding site][14].

The minimal example of using the TFaGA (on an already checkouted repository) will look similar to this:

```

    - name: Schedule tests Testing Farm
      uses: sclorg/testing-farm-as-github-action@v1
      with:
          api_key: ${{ secrets.TF_API_KEY }}
          git_url: <URL to a TMT plan>

```

All other input values are optional and have preassigned default values.

The inputs are divided into logical groups:

  * Testing Farm
    * contains options for configuring the testing farm itself. Configurable items can be the API key, URL to TF’s API, and the scope of the used TF – public, or private
  * TMT metadata
    * contains options for configuring the TMT specification, such as URL for the Git repository with the TMT plan, or regex for selecting the plan.
  * Test environment
    * contains options for configuring the operating system and architecture and where the test would be run. Supported Linux distributions are Fedora Linux, and CentOS, including CentOS Stream, RHEL7, and RHEL8. Moreover, the secrets and environment variables needed for the test execution can be specified with options belonging to this group.
  * Test artifacts
    * contains settings for additional artifacts to install in the test environment. For more information see [Rest API documentation][8].
  * Miscellaneous
    * contains settings for various miscellaneous options, such as, whether the PR should be updated with test results after finishing the job or what should be written in it.



More information about the inputs can be found in [the README.md][11].

##### Action outputs

TFaGA action provides, as output, a **request_id** and a **request_url** of a scheduled testing farm request. Combining **request_url** and **request_id** together, the user obtains a URL address pointing to a log artifactory. Test logs and test results are collected here in text form from the Testing Farm.

Optionally, if the event which triggers the Testing Farm action is related to a Pull Request, the user can enable a Pull Request status update. Enabling this option ensures that test results are summarized in a graphical form directly in the PR. An example of the graphical output is displayed in the picture below.

![Status of tests delivered by Testing Farm as GitHub Action][15]

#### How to use a Testing Farm as GitHub Action in your repository?

As TFaGA is a composite GitHub action, it is supposed to be embedded in other user-specified GitHub actions.

##### Example of action, triggered by commenting on a PR

The following example demonstrates, how the TFaGA can be used in a GitHub project. The whole example can be found in [sclorg repositories][16].

NOTE: It is important to check the contents of the tested PR so that no malicious code will be run on the Testing Farm infrastructure. For this reason, only members and owners of the repository should be able to run the tests, as shown in the example below.

The test in this specific example would be triggered with a created comment on a PR by a member or owner of a specific repository. The comment has to include the string ‘[test]’.

```

    name: upstream tests at Testing Farm
    on:
            issue_comment:
              types:
    Created
    jobs:
            build:
              name: A job run on explicit user request
              run-ons: ubuntu-20.04

      if: |
        github.event.issue.pull_request
        && contains(github.event.comment.body, '[test]')
        && contains(fromJson('["OWNER", "MEMBER"]'),        github.event.comment.author_association)

```

Clone and checkout repository to a proper pull request branch:

```

    - name: Checkout repo
      uses: actions/checkout@v2

```

The following shows scheduled tests on Testing Farm by the GitHub Action. This will pass to a testing-farm-as-a-github-action an api_key, stored in the repository secrets, the URL to a TMT plan, and the environment variables that are required by the triggered tests. The chosen testing OS is CentOS7.

```

    - name: Schedule tests on external Testing Farm
      uses: sclorg/testing-farm-as-github-action@v1
      with:
          api_key: ${{ secrets.TF_API_KEY }}
          git_url: "https://github.com/sclorg/sclorg-testing-farm"
          variables: "REPO_URL=$GITHUB_SERVER_URL/$GITHUB_REPOSITORY;REPO_NAME=$GITHUB_REPOSITORY;PR_NUMBER=${{ github.event.issue.number }};OS=centos7;TEST_NAME=test"
          compose: "CentOS-7"

```

Test results are, by default, displayed as a status directly within a Pull Request [with GitHub statuses API][17].

#### Summary

Why use this GitHub action in your project? It will eliminate caring about testing the infrastructure environment, writing a lot of new GitHub Action workflows, and handling Pull Request statuses.

When using TFaGA, you get the whole testing infrastructure according to your needs simply by providing a TMT test plan and an API key. The pool of available testing environments is composed of many processor architectures and Linux distributions.

Your tests are triggered simply by an action you specify in the configuration file. Logs and results from test execution are collected, reported, and stored in text form and optionally also transparently displayed in the Pull Request status.

Your action is only to get the ‘api_key’ from the Testing Farm team and write a simple GitHub workflow to use our GitHub Action.

So let’s test project changes as soon as possible before the project goes out to the customers!

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/test-github-projects-with-github-actions-and-testing-farm/

作者：[Petr Hracek][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/phracek/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2023/03/test_github_w_actions_n_farm-816x345.jpg
[2]: https://unsplash.com/@ismailenesayhan?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[3]: https://unsplash.com/photos/lVZjvw-u9V8?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
[4]: https://developers.redhat.com/products/rhel/overview
[5]: https://devopedia.org/shift-left
[6]: https://docs.testing-farm.io/general/0.1/index.html
[7]: https://en.wikipedia.org/wiki/Compile_farm
[8]: https://testing-farm.gitlab.io/api/
[9]: https://github.com/marketplace/actions/schedule-tests-on-testing-farm
[10]: https://docs.github.com/en/get-started/customizing-your-github-workflow/exploring-integrations/about-github-marketplace
[11]: https://github.com/sclorg/testing-farm-as-github-action
[12]: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows
[13]: mailto:tft@redhat.com
[14]: https://docs.testing-farm.io/general/0.1/onboarding.html
[15]: https://fedoramagazine.org/wp-content/uploads/2023/03/Screenshot-2023-03-14-at-9.27.51.png
[16]: https://github.com/sclorg/nginx-container/blob/master/.github/workflows/container-tests.yml
[17]: https://docs.github.com/en/rest/reference/repos#statuses
