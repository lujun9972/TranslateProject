[#]: subject: "Enhancing Your Python Workflow with UV on Fedora"
[#]: via: "https://fedoramagazine.org/enhancing-your-python-workflow-with-uv-on-fedora/"
[#]: author: "Jose Nunez https://fedoramagazine.org/author/josevnz/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Enhancing Your Python Workflow with UV on Fedora
======

![][1]

Photo by [Brecht Corbeel][2] on [Unsplash][3] (cropped)

This article is a tutorial on using UV to enhance or improve your Python work flow.

If you work with Python you most likely have used one or all of the following tools:

  * [Pip][4] to install packages or [pipx][5] to install them on virtual environments.
  * [Anaconda][6] to install packages, custom Python versions and manage dependencies
  * [Poetry][7] (and pipx), to manage your Python project and packaging.



Why do you need another tool to manage your Python packaging or install your favorite Python tools? For me, using [uv][8] was a decision based on the following features:

  1. _Simplicity_ : uv can handle all the tasks for packaging or installing tools with a very easy-to-use CLI.
  2. _Improved dependency management_ : When there are conflicts, the tool does a great job explaining what went wrong.
  3. _Speed_ : If you ever used Anaconda to install multiple dependencies like PyTorch, Ansible, Pandas, etc. you will appreciate how fast uv can do this.
  4. _Easy to install_ : No third-party dependencies to install, comes with batteries included (this is demonstrated in the next section).
  5. _Documentation_ : Yes, the online documentation is easy to follow and clear. No need to have a master degree in the occult to learn how to use the tool.



Now let’s be clear from the beginning, there is no one-size-fits-all tool that fixes all the issues with Python workflows. Here, I will try to show you why it may make sense for you to try uv and switch.

You will need a few things to follow this tutorial:

  * A Linux installation: I use [Fedora][9] but any other distribution will work pretty much the same.
  * An Internet connection, to download [uv][8] from their website.
  * Be familiar with [pip][10] and [virtual environments][11]: This is optional but it helps if you have installed a Python package before.
  * Python programming experience: We will not code much here, but knowing about Python [modules][12] and how to [package][13] a project using [pyproject.toml][14] with frameworks like [setuptools][15] will make it easier to follow.
  * Optionally, elevated privileges ([SUDO][16]), if you want to install binaries system-wide (like RPMS).



Let’s start by installing uv, if you haven’t done so already.

### Installing UV

If you have a Linux installation you can install uv like this:

```

    # The installer has options and an unattended installation mode, won't cover that here
    curl -LsSf https://astral.sh/uv/install.sh | sh

```

Using an RPM? [Fedora lists][17] several packages since version 40. So there you can do something like this:

```

    # Fedora RPM is slightly behind the latest version but it does the job
    sudo dnf install -y uv

```

Or make yourself an [RPM][18] using the statically compiled binaries from Astral and a little help from [Podman][19] and [fpm][20]:

```

    josevnz@dmaf5 docs]$ podman run --mount type=bind,src=$HOME/tmp,target=/mnt/result --rm --privileged --interactive --tty fedora:37 bash
    [root@a9e9dc561788 /]# gem install --user-install fpm
    ...
    [root@a9e9dc561788 /]# curl --location --fail --remote-name https://github.com/astral-sh/uv/releases/download/0.6.9/uv-x86_64-unknown-linux-gnu.tar.gz
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
      0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
    100 15.8M  100 15.8M    0     0  8871k      0  0:00:01  0:00:01 --:--:-- 11.1M
    [root@a9e9dc561788 /]# fpm -t rpm -s tar --name uv --rpm-autoreq --rpm-os linux --rpm-summary 'An extremely fast Python package and project manager, written in Rust.' --license 'Apache 2.0' --version v0.6.9 --depends bash --maintainer 'Jose Vicente Nunez <kodegeek.com@protonmail.com>' --url https://github.com/astral-sh/uv  uv-x86_64-unknown-linux-gnu.tar.gz
    Created package {:path=>"uv-v0.6.9-1.x86_64.rpm"}
    mv uv-v0.6.9-1.x86_64.rpm /mnt/result/
    # exit the container
    exit

```

You can then install it on /usr/local, using --prefix:

```

    sudo -i
    [root@a9e9dc561788 /]# rpm --force --prefix /usr/local -ihv /mnt/result/uv-v0.6.9-1.x86_64.rpm
    Verifying...                          ################################# [100%]
    Preparing...                          ################################# [100%]
    Updating / installing...
       1:uv-v0.6.9-1                      ################################# [100%]
    [root@a9e9dc561788 /]# rpm -qil uv-v0.6.9-1
    Name        : uv
    Version     : v0.6.9
    Release     : 1
    Architecture: x86_64
    Install Date: Sat Mar 22 23:32:49 2025
    Group       : default
    Size        : 40524181
    License     : Apache 2.0
    Signature   : (none)
    Source RPM  : uv-v0.6.9-1.src.rpm
    Build Date  : Sat Mar 22 23:28:48 2025
    Build Host  : a9e9dc561788
    Relocations : /
    Packager    : Jose Vicente Nunez <kodegeek.com@protonmail.com>
    Vendor      : none
    URL         : https://github.com/astral-sh/uv
    Summary     : An extremely fast Python package and project manager, written in Rust.
    Description :
    no description given
    /usr/local/usr/lib/.build-id
    /usr/local/usr/lib/.build-id/a1
    /usr/local/usr/lib/.build-id/a1/8ee308344b9bd07a1e3bb79a26cbb47ca1b8e0
    /usr/local/usr/lib/.build-id/e9
    /usr/local/usr/lib/.build-id/e9/4f273a318a0946893ee81326603b746f4ffee1
    /usr/local/uv-x86_64-unknown-linux-gnu/uv
    /usr/local/uv-x86_64-unknown-linux-gnu/uvx

```

Again, you have several choices.

Now it is time to move to the next section and see what uv can do to make Python workflows faster.

### Using UV to run everyday tools like Ansible, Glances, Autopep8

One of the best things about uv is that you can download and install tools on your account with less typing.

One of my favorite monitoring tools, [glances][21], can be installed with pip on the user account:

```

    pip install --user glances
    glances

```

But that will pollute my Python user installation with glances dependencies. So the best next thing is to isolate it on a virtual environment:

```

    python -m venv ~/venv/glances
    . ~/venv/glances/bin/activate
    pip install glances
    glances

```

You can see now where this is going. Instead, I could do the following with uv:

```

    uv tool run glances

```

That is a single line to _run and install glances_. This creates a temporary environment which can be discarded once we’re done with the tool.

Let me show you the equivalent command, it is called uvx:

```

    uvx --from glances glances

```

If the command and the distribution match then we can skip explicitly where it comes ‘–from’:

```

    uvx glances

```

_Less typing_ , uv created a virtual environment for me and downloaded glances there. Now say that I want to use a different Python, _version_ _3.12_ , to run it:

```

    uvx --from glances --python 3.12 glances

```

If you call this command again, uvx will re-use the virtual environment it created, using the Python interpreter of your choice.

You just saw how uv allows you to install custom Python interpreters. This topic is covered in a bit more detail in the following section.

#### Is it a good idea to install custom Python interpreters?

Letting Developers and DevOps [install custom Python interpreters][22] can be a time-saver, given that no elevated privileges are required and the hassle of making an RPM to distribute a new Python is gone.

Consider, now, that you wish to use Python 3.13:

```

    [josevnz@dmaf5 ~]$ uv python install 3.13
    Installed Python 3.13.1 in 3.21s
     + cpython-3.13.1-linux-x86_64-gnu

```

Where was it installed? Let’s search for it and run it:

```

    # It is not the system python3
    [josevnz@dmaf5 ~]$ which python3
    /usr/bin/python3

    # And not in the default PATH
    [josevnz@dmaf5 ~]$ which python3.13
    /usr/bin/which: no python3.13 in (/home/josevnz/.cargo/bin:/home/josevnz/.local/bin:/home/josevnz/bin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/home/josevnz/.local/share/JetBrains/Toolbox/scripts)

    # Let's find it (Pun intended)
    [josevnz@dmaf5 ~]$ find ~/.local -name python3.13
    /home/josevnz/.local/share/uv/python/cpython-3.13.1-linux-x86_64-gnu/bin/python3.13
    /home/josevnz/.local/share/uv/python/cpython-3.13.1-linux-x86_64-gnu/include/python3.13
    /home/josevnz/.local/share/uv/python/cpython-3.13.1-linux-x86_64-gnu/lib/python3.13

    # Ah it is inside /home/josevnz/.local/share/uv/python, Let's run it:
    [josevnz@dmaf5 ~]$ /home/josevnz/.local/share/uv/python/cpython-3.13.1-linux-x86_64-gnu/bin/python3.13
    Python 3.13.1 (main, Jan 14 2025, 22:47:38) [Clang 19.1.6 ] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

```

Interesting, a _custom_ location that is not in the [PATH][23], that allows you to mix and match Python versions.

Let’s see if uv can re-use installations now. Imagine, now, that I want to install the tool [autopep8][24] (used to correct style issues on Python code) using Python 3.13:

```

    [josevnz@dmaf5 ~]$ uv tool install autopep8 --python 3.13.1
    Resolved 2 packages in 158ms
    Prepared 2 packages in 72ms
    Installed 2 packages in 8ms
     + autopep8==2.3.2
     + pycodestyle==2.12.1
    Installed 1 executable: autopep8

```

Did the new autopep8 installation re-use the Python3.13 we installed before?

```

    [josevnz@dmaf5 ~]$ which autopep8
    ~/.local/bin/autopep8
    [josevnz@dmaf5 ~]$ head -n 1 ~/.local/bin/autopep8
    #!/home/josevnz/.local/share/uv/tools/autopep8/bin/python
    [josevnz@dmaf5 ~]$ ls -l /home/josevnz/.local/share/uv/tools/autopep8/bin/python
    lrwxrwxrwx. 1 josevnz josevnz 83 Mar 22 16:50 /home/josevnz/.local/share/uv/tools/autopep8/bin/python -> /home/josevnz/.local/share/uv/python/cpython-3.13.1-linux-x86_64-gnu/bin/python3.13

```

Yes it did, very good, we are not wasting space with duplicate Python interpreter installations.

But what if we want to re-use the existing _system_ python3? If we force the installation, will we have a duplicate (newly downloaded and existing system-wide installation)?

My system has Python 3.11, let’s force the autopep8 install and see what happens:

```

    josevnz@dmaf5 ~]$ uv tool install autopep8 --force --python 3.11
    Resolved 2 packages in 3ms
    Uninstalled 1 package in 1ms
    Installed 1 package in 3ms
     ~ autopep8==2.3.2
    Installed 1 executable: autopep8

    # Where ia autopep8
    [josevnz@dmaf5 ~]$ which autopep8
    ~/.local/bin/autopep8

    # What python is used to run autopep8? Check the Shebang on the script
    [josevnz@dmaf5 ~]$ head -n 1 ~/.local/bin/autopep8
    #!/home/josevnz/.local/share/uv/tools/autopep8/bin/python3

    # Where does that Python point to?
    [josevnz@dmaf5 ~]$ ls -l /home/josevnz/.local/share/uv/tools/autopep8/bin/python3
    lrwxrwxrwx. 1 josevnz josevnz 6 Mar 22 16:56 /home/josevnz/.local/share/uv/tools/autopep8/bin/python3 -> python
    [josevnz@dmaf5 ~]$ ls -l /home/josevnz/.local/share/uv/tools/autopep8/bin/python
    lrwxrwxrwx. 1 josevnz josevnz 19 Mar 22 16:56 /home/josevnz/.local/share/uv/tools/autopep8/bin/python -> /usr/bin/python3.11

```

uv is smart enough to use the system Python.

Now say that you want to make this Python3 version the default for your user. There is a way to do that using the experimental flags --preview (add to the PATH location) and --default (make a link to python3):

```

    [josevnz@dmaf5 ~]$ uv python install 3.13 --default --preview
    Installed Python 3.13.1 in 23ms
     + cpython-3.13.1-linux-x86_64-gnu (python, python3, python3.13)

    # Which one is now python3
    [josevnz@dmaf5 ~]$ which python3
    ~/.local/bin/python3

    # Is python3.13 our default python3?
    [josevnz@dmaf5 ~]$ which python3.13
    ~/.local/bin/python3.13

```

If you want to enforce a more strict control on what interpreters can be installed, you can create a $XDG_CONFIG_DIRS/uv/uv.toml or ~/.config/uv/uv.toml file and you can put the following [settings][25] there:

```

    # Location: ~/.config/uv/uv.toml or /etc/uv/uv.toml
    # https://docs.astral.sh/uv/reference/settings/#python-preference: only-managed, *managed*, system, only-system
    python-preference = "only-system"
    # https://docs.astral.sh/uv/reference/settings/#python-downloads: *automatic*, manual or never
    python-downloads = "manual"

```

The Fedora managers had an interesting conversation about [how set a more restrictive policy system-wide to prevent accidental interpreter installations][26]. This is definitely worth reading as you may have a similar conversation within your company. The [Fedora system uv.toml][27] has those settings, system-wide.

To wrap up this section, let me show you how to remove an installed Python using uv:

```

    [josevnz@dmaf5 docs]$ uv python uninstall 3.9
    Searching for Python versions matching: Python 3.9
    Uninstalled Python 3.9.21 in 212ms
     - cpython-3.9.21-linux-x86_64-gnu

```

Now it is time to go back to other time-saving features. Is there a way to type less when installing applications? Let’s find out in the next section.

#### Bash to the rescue

There is nothing ye old Bourne Shell (or your favorite shell) cannot fix. Put this on your ~/.profile or [environment initialization configuration file][28]:

```

    #  Use a function instead of an alias (aliases were deprecated but still supported)
    function glances {
       uvx --from glances --python 3.12 glances $*
    }

```

Another cool trick you can teach bash is to [autocomplete][29] your uv commands. Just set it up like this:

```

    josevnz@dmaf5 docs]$ uv --generate-shell-completion bash > ~/.uv_autocomplete
    [josevnz@dmaf5 docs]$ cat<<UVCONF>>~/.bash_profile
    > if [[ -f ~/.uv_autocomplete ]]; then
    >     . ~/.uv_autocomplete
    > fi
    > UVCONF
    [josevnz@dmaf5 docs]$ . ~/.uv_autocomplete

```

Before you start writing functions for all your Python tools, I’ll show you an even better way to install them in our environment.

#### Consider installing your tool instead of running it with a transient deployment.

You probably use [Ansible][30] all the time to manage your infrastructure as code. And you don’t want to use uv or uvx to call it. It is time to _install it_ :

```

    uv tool install --force ansible
    Resolved 10 packages in 17ms
    Installed 10 packages in 724ms
     + ansible==11.3.0
     + ansible-core==2.18.3
     + jinja2==3.1.6
    ...

```

Now we can call it without using uv or uvx, as long as long as you add ~/.local/bin in your PATH environment variable. You can confirm if that is the case by using which:

```

    which ansible-playbook
    ~/.local/bin/ansible-playbook

```

Another advantage of using ‘ _tool install_ ‘ is that if the installation is big (like Ansible), or you have a slow network connection, you only need to install once, since it is cached locally and ready for use the next time.

The last trick for this section, is if you installed several Python tools using uv, you can upgrade them all in one shot with the --upgrade flag:

```

    [josevnz@dmaf5 ~]$ uv tool upgrade --all
    Updated glances v4.3.0.8 -> v4.3.1
     - glances==4.3.0.8
     + glances==4.3.1
    Installed 1 executable: glances

```

This is pretty convenient!

We have seen, so far, how to manage someone else’s packages, what about our own? The next section explores that.

### Managing your Python projects with UV

Eventually, you will find yourself packaging a [Python project][31] that has multiple modules, scripts and data files. Python offers a rich ecosystem to manage this scenario and uv takes away some of the complexity.

Our small demo project will create an application that will use the ‘[Grocery Stores][32]‘ data from the _Connecticut Data portal_. The data file is updated every week and is in JSON format. The application takes that data and displays it in a terminal as a table.

‘ _Uv init_ ‘ allows me to initialize a basic project structure, which we will improve on shortly. I always like to start a project with a description and a name:

```

    [josevnz@dmaf5]$ uv init --description 'Grocery Stores in Connecticut' grocery_stores
    Initialized project `grocery_stores` at `/home/josevnz/tutorials/docs/Enhancing_Your_Python_Workflow_with_UV_on_Fedora/grocery_stores`

```

uv created a few files here:

```

    [josevnz@dmaf5 Enhancing_Your_Python_Workflow_with_UV_on_Fedora]$ ls -a grocery_stores/
    .  ..  hello.py  pyproject.toml  .python-version  README.md

```

The most important part, for now, is _pyproject.toml_. It has a full description of your project among other things:

```

    [project]
    name = "pretty-csv"
    version = "0.1.0"
    description = "Grocery Stores in Connecticut"
    readme = "README.md"
    requires-python = ">=3.13"
    dependencies = []

```

Also created is _[.python-version][33]_ which has the version of Python supported by this project. This is how uv enforces the Python version used in this project.

Another file is hello.py. _You can get rid of it_ , it has a hello world in Python. We will also later fill the _README.md_ with proper content.

Back to our script, we will use a [TUI][34] framework called [Textual][35] that will allow us to take the JSON file and show the contents as a table. Because we know that dependency, let’s use uv to add it to our project:

```

    [josevnz@dmaf5 grocery_stores]$ uv add 'textual==2.1.2'
    Using CPython 3.13.1
    Creating virtual environment at: .venv
    Resolved 11 packages in 219ms
    Prepared 2 packages in 143ms
    Installed 10 packages in 47ms
     + linkify-it-py==2.0.3
     + markdown-it-py==3.0.0
     + mdit-py-plugins==0.4.2
     + mdurl==0.1.2
     + platformdirs==4.3.7
     + pygments==2.19.1
     + rich==13.9.4
     + textual==2.1.2
     + typing-extensions==4.12.2
     + uc-micro-py==1.0.3

```

Three things happened:

  1. We downloaded textual and their transitive dependencies
  2. pyproject.toml was updated and now the dependencies section has values (go ahead and open the file) and see:



```

    [project]
    name = "pretty-csv"
    version = "0.1.0"
    description = "Simple program that shows contents of a CSV file as a table on the terminal"
    readme = "README.md"
    requires-python = ">=3.13"
    dependencies = [
        "textual==2.1.2",
    ]

```

  3. uv created a [uv.lock][36] file next to the pyproject.toml. This file has the exact version of all the packages used in your project, which ensures consistency.



```

    version = 1
    requires-python = ">=3.13"

    [[package]]
    name = "linkify-it-py"
    version = "2.0.3"
    source = { registry = "https://pypi.org/simple" }
    dependencies = [
        { name = "uc-micro-py" },
    ]
    sdist = { url = "https://files.pythonhosted.org/packages/2a/ae/bb56c6828e4797ba5a4821eec7c43b8bf40f69cda4d4f5f8c8a2810ec96a/linkify-it-py-2.0.3.tar.gz", hash = "sha256:68cda27e162e9215c17d786649d1da0021a451bdc436ef9e0fa0ba5234b9b048", size = 27946 }
    wheels = [
        { url = "https://files.pythonhosted.org/packages/04/1e/b832de447dee8b582cac175871d2f6c3d5077cc56d5575cadba1fd1cccfa/linkify_it_py-2.0.3-py3-none-any.whl", hash = "sha256:6bcbc417b0ac14323382aef5c5192c0075bf8a9d6b41820a2b66371eac6b6d79", size = 19820 },
    ]
    ...

```

You can see _uv.lock_ is very explicit, as its purpose is to be as specific and unambiguous as possible. This file is meant to be added to your repository on git, same as ‘ _.python-version’_ . It will allow developers across your team to have a consistent tool set installed.

Let’s also add the ‘[httpx][37]‘ library, so we can download the grocery data asynchronously:

```

    [josevnz@dmaf5 pretty_csv]$ uv add 'httpx==0.28.1'
    Resolved 18 packages in 229ms
    Prepared 6 packages in 108ms
    Installed 7 packages in 8ms
     + anyio==4.9.0
     + certifi==2025.1.31
     + h11==0.14.0
     + httpcore==1.0.7
     + httpx==0.28.1
     + idna==3.10
     + sniffio==1.3.1

```

These are runtime dependencies, but what if we want to use tools to do things like linting, or profiling? We will explore that in the next section.

#### Development dependencies

You may want to use some tools while developing your application, like [pytest][38] to run unit tests or [pylint][39] to check the correctness of the code. But you don’t want to deploy those tools in your final version of the application.

This is a development dependency, and you can add them to a special ‘– _dev_ ‘ section of your project like this :

```

    [josevnz@dmaf5 grocery_stores]$ uv add --dev pylint==3.3.6 pytest==8.3.5
    Resolved 29 packages in 15ms
    Installed 10 packages in 19ms
     + astroid==3.3.9
     + dill==0.3.9
     + iniconfig==2.1.0
     + isort==6.0.1
     + mccabe==0.7.0
     + packaging==24.2
     + pluggy==1.5.0
     + pylint==3.3.6
     + pytest==8.3.5
     + tomlkit==0.13.2

```

This produces the following section on my pyproject.toml file:

```

    [dependency-groups]
    dev = [
        "pylint==3.3.6",
        "pytest==8.3.5",
    ]

```

#### Writing a JSON-to-Table display Python application

The first step is to have the code that loads the data, then renders the Grocery store raw data as a table. I will let you [read the Textual tutorial][40] on how to do this and instead will share the bulk of the code I wrote in a file called ‘[groceries.py][41]‘:

```

    """
    Displays the latest Grocery Store data from
    the Connecticut Data portal.
    Author: Jose Vicente Nunez <kodegeek.com@protonmail.com>
    Press ctrl+q to exit the application.
    """

    import httpx
    from httpx import HTTPStatusError
    from textual.app import App, ComposeResult
    from textual.widgets import DataTable, Header, Footer
    from textual import work, on
    from orjson import loads

    GROCERY_API_URL = "https://data.ct.gov/resource/fv3p-tf5m.json"


    class GroceryStoreApp(App):
        def compose(self) -> ComposeResult:
            header = Header(show_clock=True)
            yield header
            table = DataTable(id="grocery_store_table")
            yield table
            yield Footer()

        @work(exclusive=True)
        async def update_grocery_data(self) -> None:
            """
            Update the Grocery data table and provide some feedback to the user
            :return:
            """
            table = self.query_one("#grocery_store_table", DataTable)

            async with httpx.AsyncClient() as client:
                response = await client.get(GROCERY_API_URL)
                try:
                    response.raise_for_status()
                    groceries_data = loads(response.text)
                    table.add_columns(*[key.title() for key in groceries_data[0].keys()])
                    cnt = 0
                    for row in groceries_data[1:]:
                        table.add_row(*(row.values()))
                        cnt += 1
                    table.loading = False
                    self.notify(
                        message=f"Loaded {cnt} Grocery Stores",
                        title="Data loading complete",
                        severity="information"
                    )
                except HTTPStatusError:
                    self.notify(
                        message=f"HTTP code={response.status_code}, message={response.text}",
                        title="Could not download grocery data",
                        severity="error"
                    )

        def on_mount(self) -> None:
            """
            Render the initial component status, show an initial loading message
            :return:
            """
            table = self.query_one("#grocery_store_table", DataTable)
            table.zebra_stripes = True
            table.cursor_type = "row"
            table.loading = True
            self.notify(
                message=f"Retrieving information from CT Data portal",
                title="Loading data",
                severity="information",
                timeout=5
            )
            self.update_grocery_data()

        @on(DataTable.HeaderSelected)
        def on_header_clicked(self, event: DataTable.HeaderSelected):
            """
            Sort rows by column header
            """
            table = event.data_table
            table.sort(event.column_key)


    if __name__ == "__main__":
        app = GroceryStoreApp()
        app.title = "Grocery Stores"
        app.sub_title = "in Connecticut"
        app.run()

```

Now that we have some code, let’s test it. First using an editable mode (in a way similar to using pip):

```

    [josevnz@dmaf5 grocery_stores]$ uv pip install --editable .
    Resolved 18 packages in 105ms
       Built grocery-stores @ file:///home/josevnz/tutorials/docs/Enhancing_Your_Python_Workflow_with_UV_on_Fedora/grocery_stores
    Prepared 18 packages in 1.07s
    Uninstalled 18 packages in 87ms
    Installed 18 packages in 53ms
     ~ anyio==4.9.0
     ~ certifi==2025.1.31
     ~ grocery-stores==0.1.0 (from file:///home/josevnz/tutorials/docs/Enhancing_Your_Python_Workflow_with_UV_on_Fedora/grocery_stores)
     ~ h11==0.14.0
     ~ httpcore==1.0.7
     ~ httpx==0.28.1
     ~ idna==3.10
     ~ linkify-it-py==2.0.3
     ~ markdown-it-py==3.0.0
     ~ mdit-py-plugins==0.4.2
     ~ mdurl==0.1.2
     ~ platformdirs==4.3.7
     ~ pygments==2.19.1
     ~ rich==13.9.4
     ~ sniffio==1.3.1
     ~ textual==2.1.2
     ~ typing-extensions==4.12.2
     ~ uc-micro-py==1.0.3

```

Now run our groceries store application using uv. Uv will pick up our local installation and use it:

```

    uv run groceries.py

```

The application looks more or less like this:

![][42]

The grocery store application was written with [Textual][35]. Not bad for a few lines of code.

Time to see next how we can lint and unit test our new grocery store application

#### Linting code with pylint:

We use [pylint][39] as follows (I like to pin the version to avoid unwanted warnings due to API changes):

```

    [josevnz@dmaf5 grocery_stores]$ uv run --with 'pylint==3.3.6' pylint groceries.py
    ************* Module groceries
    groceries.py:15:0: C0115: Missing class docstring (missing-class-docstring)
    groceries.py:25:8: W0612: Unused variable 'table' (unused-variable)
    groceries.py:27:12: W0612: Unused variable 'response' (unused-variable)
    groceries.py:29:4: C0116: Missing function or method docstring (missing-function-docstring)
    groceries.py:10:0: W0611: Unused work imported from textual (unused-import)

    ------------------------------------------------------------------
    Your code has been rated at 7.73/10 (previous run: 7.73/10, +0.00)

    Fix the issues, run the tests again:

    [josevnz@dmaf5 grocery_stores]$ uv run --with 'pylint==3.3.6' pylint groceries.py

    -------------------------------------------------------------------
    Your code has been rated at 10.00/10 (previous run: 9.04/10, +0.96)

```

#### Running unit tests with pytest

My _textual_ app uses async so it requires a little bit of support from [pytest][43]. Not a problem:

```

    [josevnz@dmaf5 grocery_stores]$ uv add --dev pytest_asyncio
    [josevnz@dmaf5 grocery_stores]$ uv run --dev pytest test_groceries.py
    ======================================================================================================================= test session starts ========================================================================================================================
    platform linux -- Python 3.13.1, pytest-8.3.5, pluggy-1.5.0
    rootdir: /home/josevnz/tutorials/docs/Enhancing_Your_Python_Workflow_with_UV_on_Fedora/grocery_stores
    configfile: pyproject.toml
    plugins: anyio-4.9.0, asyncio-0.25.3
    asyncio: mode=Mode.STRICT, asyncio_default_fixture_loop_scope=None
    collected 1 item

    test_groceries.py .                                                                                                                                                                                                                                          [100%]

    ======================================================================================================================== 1 passed in 0.43s =========================================================================================================================

```

My test code just simulates starting the application and pressing _ctrl-q_ to exit it. Not very useful but this next test gives you an idea what you can to do to test your application simulating keystrokes:

```

    """
    Unit tests for Groceries application
    https://textual.textualize.io/guide/testing/
    """
    import pytest

    from grocery_stores_ct.groceries import GroceryStoreApp


    @pytest.mark.asyncio
    async def test_groceries_app():
        groceries_app = GroceryStoreApp()
        async with groceries_app.run_test() as pilot:
            await pilot.press("ctrl+q")  # Quit

```

Now run the tests:

```

    [josevnz@dmaf5 grocery_stores]$ uv run --dev pytest test_groceries.py

    ================================================ test session starts =================================================
    platform linux -- Python 3.13.1, pytest-8.3.5, pluggy-1.5.0
    rootdir: /home/josevnz/tutorials/docs/Enhancing_Your_Python_Workflow_with_UV_on_Fedora/grocery_stores
    configfile: pyproject.toml
    plugins: asyncio-0.25.3, anyio-4.9.0
    asyncio: mode=Mode.STRICT, asyncio_default_fixture_loop_scope=None
    collected 1 item

    test/test_groceries.py .                                                                                       [100%]

    ================================================= 1 passed in 1.17s ==================================================

```

#### Packaging and uploading to your Artifact repository

It is time to package our new application. Let’s try to build it:

```

    [josevnz@dmaf5 grocery_stores]$ uv build
    Building source distribution...
    error: Multiple top-level modules discovered in a flat-layout: ['groceries', 'test_groceries'].

    To avoid accidental inclusion of unwanted files or directories,
    setuptools will not proceed with this build.
    ...

```

_Not so fast_. uv is getting confused as we have 2 main modules, instead of one. The right thing to do is to setup a [src-layout][44] for our project, so we move some files around.

After moving groceries.py to a module called _‘src/grocery_stores_ct’_ and _tests_groceries_ to _test_ :

```

    [josevnz@dmaf5 grocery_stores]$ tree
    .
    ├── pyproject.toml
    ├── README.md
    ├── src
    │   ├── grocery_stores_ct
    │   │   ├── groceries.py
    │   │   └── __init__.py
    │   └── grocery_stores.egg-info
    │       ├── dependency_links.txt
    │       ├── PKG-INFO
    │       ├── requires.txt
    │       ├── SOURCES.txt
    │       └── top_level.txt
    ├── test
    │   └── test_groceries.py
    └── uv.lock

```

Re-test it, lint-it:

```

    uv pip install --editable .[dev]
    uv run --dev pytest test/test_groceries.py
    uv run --with 'pylint==3.3.6' pylint src/grocery_stores_ct/groceries.py

```

And now build it again:

```

    [josevnz@dmaf5 grocery_stores]$ uv build
    Building source distribution...
    running egg_info
    writing src/grocery_stores.egg-info/PKG-INFO
    writing dependency_links to src/grocery_stores.egg-info/dependency_links.txt
    removing build/bdist.linux-x86_64/wheel
    Successfully built dist/grocery_stores-0.1.0.tar.gz
    Successfully built dist/grocery_stores-0.1.0-py3-none-any.whl

```

Now comes the time when you want to share your application with others.

#### Uploading to a custom index

I don’t want to pollute the real [pypi.org][45] with a test application, so instead I will set my index to be something [else, like test.pypi.org][46]. In your case this can be a Nexus 3 repository, an Artifactory repository, or whatever artifact repository you have set up in your company.

For pypi, add the following to your pyproject.toml file:

```

    # URL match your desired location
    [[tool.uv.index]]
    name = "testpypi"
    url = "https://test.pypi.org/simple/"
    publish-url = "https://test.pypi.org/legacy/"
    explicit = true

```

You will also need to generate an application token ( _this varies by provider_ and won’t be covered here). Once you get your token, call uv publish --index testpypi $token:

```

    [josevnz@dmaf5 grocery_stores]$ uv publish --index testpypi --token pypi-AgENdGVzdC5weXBpLm9yZwIkYzFkODg5ODMtODUxZS00ODc2LWFhYzMtZjhhNWFmNjZhODJmAAIqWzMsIjZmZGNjMzc1LTYxNmEtNDA5Zi1hNTJkLWJhMDZmNWQ3N2NlZSJdAAAGIG3wrTZdgmOBlahBlahBlah
    warning: `uv publish` is experimental and may change without warning
    Publishing 2 files https://test.pypi.org/legacy/
    Uploading grocery_stores-0.1.0-py3-none-any.whl (2.7KiB)
    Uploading grocery_stores-0.1.0.tar.gz (2.5KiB)

```

#### Other things that you should have on your pyproject.toml

UV does a lot of things but doesn’t do everything. There is a lot of extra Metadata that you should have on your [pyproject.toml][14] file. I’ll share some of the essentials here:

```

    [project]
    authors = [
        {name = "Jose Vicente Nunez", email = "kodegeek.com@protonmail.com"}
    ]
    maintainers = [
        {name = "Jose Vicente Nunez", email = "kodegeek.com@protonmail.com"}
    ]
    license = "MIT AND (Apache-2.0 OR BSD-2-Clause)"
    keywords = ["ct", "tui", "grocery stores", "store"]
    classifiers = [
        "Development Status :: 4 - Beta",
        "Intended Audience :: End Users/Desktop",
        "Topic :: Desktop Environment",
        "Programming Language :: Python :: 3.13",
    ]
    [project.urls]
    Homepage = "https://github.com/josevnz/tutorials"
    Repository = "https://github.com/josevnz/tutorials.git"

```

A few things before wrapping this section:

  * You can see the full list of classifiers [here][47].
  * If you do not want a project to be uploaded to Pypi by accident, add the following classifier: ‘Private :: Do Not Upload‘.
  * You will need to bump the version, rebuild and upload again after making any changes, like adding _keywords_ (useful to tell the world where to find your app).



### Inline script metadata, self contained scripts

Python has a feature, [PEP-0723][48], that allows it to [incorporate metatada embedded in the script][49], like this:

```

    # /// script
    # requires-python = ">=3.13"
    # dependencies = [
    # "httpx==0.28.1",
    # "orjson==3.10.15",
    # "textual==2.1.2",
    # ]
    # ///

    # ... Omitted rest of the code

```

These 8 lines at the begining of the script indicates that this is the embedded metadata.

If you remember our pyproject.toml file, these are the instructions used by package managers like _setuptools_ and _uv_ to handle the project dependencies, like python versions and required libraries to run. This is powerful, since tools capable of reading this inline metadata (between the ` _///_ ` sections) do not need to check an extra file.

Now, uv ([has a flag][50]) called ` _–script_ ` which allows it to interpret the inline metadata on the script. For example, this will update the dependencies for the `example` script, by reading them from the script directly:

```

    uv add --script example.py 'requests<3' 'rich'
    uv run example.py

```

This is convenient. If we combine both inline dependencies and uv we can have a self executable script that can also download its own dependencies:

```

    #!/usr/bin/env -S uv run --script
    # /// script
    # requires-python = ">=3.13"
    # dependencies = [
    #   "httpx==0.28.1",
    #   "orjson==3.10.15",
    #   "textual==2.1.2",
    # ]
    # ///
    """
    Displays the latest Grocery Store data from
    the Connecticut Data portal.
    Author: Jose Vicente Nunez <kodegeek.com@protonmail.com>
    This version of the script uses inline script metadata:
      https://packaging.python.org/en/latest/specifications/inline-script-metadata/
    Press ctrl+q to exit the application.
    """

    import httpx
    from httpx import HTTPStatusError
    from textual.app import App, ComposeResult
    from textual.widgets import DataTable, Header, Footer
    from textual import work, on
    # pylint: disable=no-name-in-module
    from orjson import loads

    GROCERY_API_URL = "https://data.ct.gov/resource/fv3p-tf5m.json"


    class GroceryStoreApp(App):
        """
        TUI application that shows grocery stores in CT
        """
        current_sorts: set = set()

        def compose(self) -> ComposeResult:
            header = Header(show_clock=True)
            yield header
            table = DataTable(id="grocery_store_table")
            yield table
            yield Footer()

        @work(exclusive=True)
        async def update_grocery_data(self) -> None:
            """
            Update the Grocery data table and provide some feedback to the user
            :return:
            """
            table = self.query_one("#grocery_store_table", DataTable)

            async with httpx.AsyncClient() as client:
                response = await client.get(GROCERY_API_URL)
                try:
                    response.raise_for_status()
                    groceries_data = loads(response.text)
                    table.add_columns(*[key.title() for key in groceries_data[0].keys()])
                    cnt = 0
                    for row in groceries_data[1:]:
                        table.add_row(*(row.values()))
                        cnt += 1
                    table.loading = False
                    self.notify(
                        message=f"Loaded {cnt} Grocery Stores",
                        title="Data loading complete",
                        severity="information"
                    )
                except HTTPStatusError:
                    self.notify(
                        message=f"HTTP code={response.status_code}, message={response.text}",
                        title="Could not download grocery data",
                        severity="error"
                    )

        def on_mount(self) -> None:
            """
            Render the initial component status
            :return:
            """
            table = self.query_one("#grocery_store_table", DataTable)
            table.zebra_stripes = True
            table.cursor_type = "row"
            table.loading = True
            self.notify(
                message="Retrieving information from CT Data portal",
                title="Loading data",
                severity="information",
                timeout=5
            )
            self.update_grocery_data()

        def sort_reverse(self, sort_type: str):
            """
            Determine if `sort_type` is ascending or descending.
            """
            reverse = sort_type in self.current_sorts
            if reverse:
                self.current_sorts.remove(sort_type)
            else:
                self.current_sorts.add(sort_type)
            return reverse

        @on(DataTable.HeaderSelected)
        def on_header_clicked(self, event: DataTable.HeaderSelected):
            """
            Sort rows by column header
            """
            table = event.data_table
            table.sort(
                event.column_key,
                reverse=self.sort_reverse(event.column_key.value)
            )


    if __name__ == "__main__":
        app = GroceryStoreApp()
        app.title = "Grocery Stores"
        app.sub_title = "in Connecticut"
        app.run()

```

This is the same script we wrote before, except that we use the last big of magic here:

```

    !/usr/bin/env -S uv run --script

```

We call env (part of [coreutils][51]) to split arguments (-S) to call uv with the --script flag. Then uv reads the inline metadata and downloads the required python with all the dependencies automatically:

```

    [josevnz@dmaf5 Enhancing_Your_Python_Workflow_with_UV_on_Fedora]$ chmod a+xr inline_script_metadata/groceries.py
    [josevnz@dmaf5 Enhancing_Your_Python_Workflow_with_UV_on_Fedora]$ ./inline_script_metadata/groceries.py
    Installed 18 packages in 29ms
    # And here the script starts running!!!

```

It doesn’t get simpler than this. This is great, for example, to run installer scripts.

### Learning more

A lot of material is covered here but there is still more to learn. As with everything, you will need to try to see what better fits your style and available resources.

Below is a list of links I found useful and may also help you:

  * The official [uv][8] documentation is very complete, and you will most likely spend your time going back and forth reading it.
  * Users of older Fedora distributions may take a look at the [UV Source RPM][52]. Lots of good stuff, including Bash auto-completion for UV.
  * Anaconda and [miniconda][53] also have counter parties written in rust ([mamba and micromamba][54]), in case you decide jumping to uv is too soon. These are backward compatible and much faster.
  * Did you remember the file [uv.lock][55] we discussed before? Now Python has agreed to a way to manage dependencies ([PEP 751][56]) in a much more powerful way than the pip requirements.txt file. Keep an eye on [packaging.python.org][13] for more details.
  * I showed you how to use _pylint_ to check for code smells. I would strongly recommend you try [ruff][57]. It is written in rust and it is _pretty fast_ :



```

    [josevnz@dmaf5 grocery_stores]$ uv tool install ruff@latest
    Resolved 1 package in 255ms
    Prepared 1 package in 1.34s
    Installed 1 package in 4ms
    ruff==0.11.2
    Installed 1 executable: ruff
    # The lets check the code
    [josevnz@dmaf5 grocery_stores]$ ruff check src/grocery_stores_ct
    All checks passed!

```

Remember: _“perfect is the enemy of good”_ , so try uv and other tools and see what is best for your Python workflow needs.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/enhancing-your-python-workflow-with-uv-on-fedora/

作者：[Jose Nunez][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/josevnz/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2025/03/python_uv_fedora-816x345.jpg
[2]: https://unsplash.com/@brechtcorbeel?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-purple-and-black-background-with-a-purple-and-black-logo-QUwM2LDVs3A?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://pypi.org/project/pip/
[5]: https://github.com/pypa/pipx
[6]: https://www.anaconda.com/docs/tools/main
[7]: https://python-poetry.org/docs/
[8]: https://docs.astral.sh/uv/
[9]: https://fedoraproject.org/
[10]: https://docs.python.org/3/installing/index.html
[11]: https://docs.python.org/3/library/venv.html
[12]: https://docs.python.org/3/tutorial/modules.html
[13]: https://packaging.python.org/en/latest/
[14]: https://packaging.python.org/en/latest/guides/writing-pyproject-toml/
[15]: https://setuptools.pypa.io/en/latest/setuptools.html
[16]: https://www.sudo.ws/
[17]: https://src.fedoraproject.org/rpms/uv
[18]: https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/8/html/packaging_and_distributing_software/introduction-to-rpm_packaging-and-distributing-software
[19]: https://www.redhat.com/en/topics/containers/what-is-podman
[20]: https://www.freecodecamp.org/news/getting-started-with-fpm/
[21]: https://github.com/nicolargo/glances
[22]: https://docs.astral.sh/uv/concepts/python-versions/#installing-a-python-version
[23]: https://en.wikipedia.org/wiki/PATH_(variable)
[24]: https://github.com/hhatto/autopep8
[25]: https://docs.astral.sh/uv/reference/settings/
[26]: https://src.fedoraproject.org/rpms/uv/pull-request/18
[27]: https://src.fedoraproject.org/rpms/uv/blob/rawhide/f/uv.toml
[28]: https://fedoramagazine.org/customizing-bash/
[29]: https://github.com/scop/bash-completion
[30]: https://docs.ansible.com/ansible/latest/index.html
[31]: https://docs.astral.sh/uv/concepts/projects/
[32]: https://data.ct.gov/Business/Grocery-Stores/fv3p-tf5m/about_data
[33]: http://grocery_stores/.python-version
[34]: https://en.wikipedia.org/wiki/Text-based_user_interface
[35]: https://textual.textualize.io/
[36]: http://grocery_stores/uv.lock
[37]: https://www.python-httpx.org/
[38]: https://docs.pytest.org/en/stable/index.html
[39]: https://www.pylint.org/
[40]: https://textual.textualize.io/tutorial/
[41]: http://grocery_stores/src/grocery_stores_ct/groceries.py
[42]: https://fedoramagazine.org/wp-content/uploads/2025/03/image-2-1024x315.png
[43]: https://docs.pytest.org/en/stable/
[44]: https://packaging.python.org/en/latest/discussions/src-layout-vs-flat-layout/
[45]: https://pypi.org/
[46]: https://test.pypi.org/
[47]: https://pypi.org/classifiers/
[48]: https://peps.python.org/pep-0723/
[49]: https://packaging.python.org/en/latest/specifications/inline-script-metadata/
[50]: https://docs.astral.sh/uv/guides/scripts/#creating-a-python-script
[51]: https://packages.fedoraproject.org/pkgs/coreutils/coreutils/
[52]: https://src.fedoraproject.org/rpms/uv/blob/rawhide/f/uv.spec
[53]: https://www.anaconda.com/docs/getting-started/miniconda/main
[54]: https://mamba.readthedocs.io/en/latest/index.html
[55]: https://docs.astral.sh/uv/concepts/projects/sync/
[56]: https://discuss.python.org/t/pep-751-one-last-time/77293/150
[57]: https://docs.astral.sh/ruff/
