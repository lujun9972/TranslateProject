[#]: subject: "Python CI on Fedora with GitHub Actions"
[#]: via: "https://fedoramagazine.org/python-ci-on-fedora-with-github-actions/"
[#]: author: "Monasor J.J Atairu https://fedoramagazine.org/author/mariowritescode/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Python CI on Fedora with GitHub Actions
======

![][1]

Photo by [Brecht Corbeel][2] on [Unsplash][3] (cropped)

As a Python developer you work hard to ensure code works correctly across different Python versions. You have to test against Python 3.11, 3.12, 3.13 and beyond, it can be tedious. But what if your continuous integration (CI) pipeline could handle it automatically? This is where GitHub Actions and tox come in – a powerful combo for seamless CI and multi-version testing.

### Introduction

Imagine you are a developer for a small real estate company, racing against the clock to deliver a groundbreaking fizz-buzz feature on the company’s python app. You make a last minute fix and commit. After testing locally, you merge with confidence, push to GitHub, and ship. Then disaster strikes, the change breaks an existing feature and the new feature you added does not work. Management is furious, and the only excuse you could give is “it worked on my machine”.

If only you had set up GitHub Actions for continuous integration (CI), you could have made sure it worked on different versions of Python.

In this article, you will learn how to set up GitHub Actions to manage continuous integration for your Python projects. You will also learn how to test your code on different versions of Python using tox on Fedora.

#### Prerequisites

  * GitHub Account
  * Fedora, CentOS, or RHEL server. This guide uses Fedora 41 server edition. Fedora, CentOS, and RHEL servers are interchangeable.
  * A user account with sudo privileges on the server.
  * Command line competency.
  * Python 3.13 environment, with poetry, tox, and pytest packages installed.



### What is Continuous Integration?

Continuous Integration (CI) is a practice where you merge your code to the repository several times a day. CI reduces software defects, because every time you push a change to the repository it is verified by automated tests and built. Generally, CI refers to the server part of the build process, where you run unit tests and build your application. However, it can also be done locally. To carry out CI, you define a build pipeline using YAML. The build pipeline runs a set of automated tools for unit tests, security checks, document generation, or code quality checks.

### Why use CI?

Central to CI is code stability. By running unit tests on your code whenever you make a change, you are confident that those changes do not cause software defects in your codebase. This way, you know, your code is stable; commit after commit.

There are two important aspects of CI that ensure code stability:

  1. CI checks that code compiles or builds successfully.
  2. CI checks that all unit tests pass successfully.



### What is Tox?

Tox, is a tool that automates Python unit tests in multiple Python environments. According to tox [documentation][4], you can use tox for:

  * checking your package builds and installs correctly under different environments
  * Running your tests in each of the environments with the test tool of choice
  * As a frontend to continuous integration servers



### What are GitHub Actions?

GitHub Actions is a feature on [Github.com][5] that serves as an automation engine for CI. It allows you to automate tasks directly within your GitHub repository using workflows.

To use GitHub Actions effectively, you need to understand how the system works using a top-down approach.

![][6]

An event is a specified activity that triggers a workflow. An activity may occur when a commit is pushed or a pull request is made. In this tutorial, an event occurs when you push a commit to your GitHub repository.

A workflow is an automated process which runs when an event occurs. It defines how code is tested, built or compiled using actions. A YAML file defines the steps in the workflow and exists in the .github/workflows directory of your repository.

A job runs actions you specify. While there are no limits on the number of actions you can run in a job, there is a maximum execution time of 6 hours. Jobs are executed in runners (containers or virtual machines). You can choose Linux, Windows, or macOS runners to run your CI jobs.

An action is the smallest building block of a workflow. According to GitHub documentation; “an action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task”. You can write custom actions as Node.js scripts or use those in the GitHub marketplace.

### Test a Python project

This python project is for a calculator with functions for adding and multiplying numbers only. You will use pytest and tox to test the code using Python 3.12, and 3.13. You will also push the code to GitHub, and use GitHub Actions for CI.

> HEAD’s UP: Remember, GitHub Actions uses runners for CI jobs, and runners can be Windows, Ubuntu or macOS? Did you notice, Fedora is not on the list?

[Checkout, out this repository][7] on GitHub. It contains working code for the calculator, tests, and a workflow for this tutorial. It uses the [tox-github-action][8] from [Fedora Python][9] to run tests in CI. The tests are run in a Fedora container, which is hosted in an Ubuntu runner.

![][10]

_**This is the file structure you will work with;**_

![][11]

### Step 1: Write the Code

Here is the calculator code at _/ciwithfedora/calculator.py_

```

    def add(a, b):
       """Returns the sum of two numbers."""
       return a + b

    def multiply(a, b):
       """Returns the product of two numbers."""
       return a * b

```

### Step 2: Write unit tests

Here is the unit test code at _/ciwithfedora/test_calculator.py_

```

    import pytest
    from calculator import add, multiply

    # Test cases for add function
    def test_add_positive_numbers():
       assert add(2, 3) == 5

    def test_add_negative_numbers():
       assert add(-1, -1) == -2

    def test_add_zero():
       assert add(0, 5) == 5
       assert add(5, 0) == 5

    def test_add_mixed_signs():
       assert add(-1, 3) == 2
       assert add(3, -1) == 2

    # Test cases for multiply function
    def test_multiply_positive_numbers():
       assert multiply(2, 3) == 6

    def test_multiply_with_zero():
       assert multiply(0, 5) == 0
       assert multiply(5, 0) == 0

    def test_multiply_negative_numbers():
       assert multiply(-2, -3) == 6

    def test_multiply_mixed_signs():
       assert multiply(-2, 3) == -6
       assert multiply(2, -3) == -6

```

### Step 3: Manage Dependencies with Poetry

##### 3.1 Peotry configuration:

Here is the poetry configuration code at . _/pyproject.toml_

```

    [tool.poetry]
    name = "ciwithfedora"
    version = "0.1.0"
    description = "Python CI on Fedora with GitHub Actions. Tutorial article for Fedoramagazine.org."
    authors = [""]
    readme = "README.md"

    [tool.poetry.dependencies]
    python = "^3.11"

    [tool.poetry.group.dev.dependencies]
    tox = "^4.26.0"
    pytest = "^8.3.5"
    [build-system]
    requires = ["poetry-core"]
    build-backend = "poetry.core.masonry.api"

```

##### 3.2 Install the dependencies

```

    $ poetry install

```

### Step 4. Configure tox to run tests in different Python environments

Here is the tox configuration code at . _/tox.ini_

```

    [tox]
    envlist = py313, py312

    [testenv]
    allowlist_externals = poetry
    commands_pre =
       poetry install --no-interaction --no-root
    commands =
       poetry run pytest

```

### Step 5. Run tests

##### 5.1 Run unit tests with pytests

```

    $ poetry run pytest -v

```

![][12]

##### 5.2 Run unit tests with tox in different Python environments

```

    $ poetry run tox

```

![][13]

### Step 6. Automate tests with GitHub Actions

The workflow file is located at .github/workflows/workflow.py/

Here is the code;

```

    name: Python Tests

    on:
      push:
        branches: [ dev ]

    jobs:
      tox_test:
        name: Tox test
        steps:
        - uses: actions/checkout@v4
        - name: Run tox tests
          id: test

          uses: fedora-python/tox-github-action@main
          with:
            tox_env: py313,py312
            dnf_install: poetry

        runs-on: ubuntu-latest

```

### Step 7. Push project to GitHub to trigger CI

```

    $ git push

```

You can click on the actions tab on your GitHub repo to see CI in progress.

![][14]

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/python-ci-on-fedora-with-github-actions/

作者：[Monasor J.J Atairu][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/mariowritescode/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/06/Python_CI_Github_actions-816x345.jpg
[2]: https://unsplash.com/@brechtcorbeel?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-neon-circle-with-a-snake-on-it-qHx3w6Gwz9k?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://tox.wiki/en/4.26.0/
[5]: http://github.com
[6]: https://fedoramagazine.org/wp-content/uploads/2025/05/github-actions-top-down.jpeg
[7]: https://github.com/monasorjja/ciwithfedora
[8]: https://github.com/fedora-python/tox-github-action
[9]: https://github.com/fedora-python
[10]: https://fedoramagazine.org/wp-content/uploads/2025/05/fedora-tox.png
[11]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250529_031930.png
[12]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250529_033533-1024x398.png
[13]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250530_095004-1024x221.png
[14]: https://fedoramagazine.org/wp-content/uploads/2025/05/Screenshot_20250530_135445-1024x303.png
