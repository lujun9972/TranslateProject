[#]: subject: "GitHub Actions: Use Podman to run Fedora Linux"
[#]: via: "https://fedoramagazine.org/github-actions-use-podman-to-run-fedora-linux/"
[#]: author: "Benson Muite https://fedoramagazine.org/author/fed500/"
[#]: collector: "lujun9972"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

GitHub Actions: Use Podman to run Fedora Linux
======

![An image showing boxes on a conveyer belt. After passing a magnifying glass, the box has a check mark. Below the conveyor belt is text "Ensuring a Fedora Software Pipeline".][1]

### Introduction

[GitHub][2] enables distributed and collaborative code development. To ensure software works correctly, many projects use continuous integration to build and test each new contribution before including it. The continuous integration service on GitHub is [GitHub actions][3].

### Background

GitHub offers testing on Ubuntu, macOS and Windows operating systems. However, there is a wide variety of other operating systems and you may want to ensure that an open source project developed on GitHub runs well on another operating system, in particular Fedora Linux.

Podman is a command line tool that can run a different Linux operating system in a container. This provides a convenient way to test software on other operating systems. The article [Getting Started with Podman in Fedora Linux][4] introduces how to run Podman on Fedora.

This article demonstrates how to run Fedora Linux in a container using Podman. The host operating system can be any distro that has Podman installed, even macOS or Windows. In the following demo, the host operating system is Ubuntu. This will allow us to test that projects developed on GitHub will work successfully on Fedora, even if Fedora is not available as a base operating system for GitHub actions.

### Example GitHub Actions Configuration

As an example, we add continuous integration for Fedora Linux to [RedAmber][5], a project enabling the use of dataframes for machine learning and other data science applications in [Ruby][6]. This project relies on [Apache Arrow][7] release 10 or greater, so we need to use Fedora Linux Rawhide (F38) since Fedora Linux 37 currently has Apache Arrow release 9 in the Fedora repositories.

GitHub has great documentation on using [GitHub Actions][3]. In summary, we need to create a [yaml][8] file in the _.github/workflows_ directory of the project, and then enable GitHub Actions if it is not already enabled. A sample yaml file which you can easily modify is below:

```

    name: CI
    on:
      push:
        branches:
          - main
      pull_request:

    jobs:
      test:
        name: fedora
        runs-on: ubuntu-latest

        steps:
          - name: Setup Podman
            run: |
              sudo apt update
              sudo apt-get -y install podman
              podman pull fedora:38
          - name: Get source
            uses: actions/checkout@v3
            with:
              path: 'red_amber'
          - name: Create container and run tests
            run: |
              {
                  echo 'FROM fedora:38'
                  echo '# set TZ to ensure the test using timestamp'
                  echo 'ENV TZ=Asia/Tokyo'
                  echo 'RUN dnf -y update'
                  echo 'RUN dnf -y install gcc-c++ git libarrow-devel libarrow-glib-devel ruby-devel'
                  echo 'RUN dnf clean all'
                  echo 'COPY red_amber red_amber'
                  echo 'WORKDIR /red_amber'
                  echo 'RUN bundle install'
                  echo 'RUN bundle exec rake test'
              } > podmanfile
              podman build --tag fedora38test -f ./podmanfile

```

Adding the above yaml file enables testing on Fedora Linux running as a guest on Ubuntu. Similar workflows should work for other projects developed on GitHub, thereby ensuring a wide variety of software will run well on Fedora Linux.

### Acknowledgements

Benson Muite is grateful to [Hirokazu SUZUKI][9] for creating RedAmber, improving the workflow, and using it to test RedAmber on Fedora Linux.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/github-actions-use-podman-to-run-fedora-linux/

作者：[Benson Muite][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/fed500/
[b]: https://github.com/lujun9972
[1]: https://fedoramag.wpenginepowered.com/wp-content/uploads/2022/12/Podman-GitHub-Actions-Fedora-816x345.jpg
[2]: https://github.com
[3]: https://docs.github.com/en/actions
[4]: https://fedoramagazine.org/getting-started-with-podman-in-fedora/
[5]: https://github.com/heronshoes/red_amber
[6]: https://rubylang.org
[7]: https://arrow.apache.org
[8]: https://yaml.org/
[9]: https://github.com/heronshoes
