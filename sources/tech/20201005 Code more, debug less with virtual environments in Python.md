[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Code more, debug less with virtual environments in Python)
[#]: via: (https://opensource.com/article/20/10/venv-python)
[#]: author: (Seth Kenlon https://opensource.com/users/seth)

Code more, debug less with virtual environments in Python
======
Protect against unexpected and unwelcome surprises by using venv in
Python.
![woman on laptop sitting at the window][1]

If you've ever shared a neat computer trick, a complex application, or something in between with a friend, then you've probably uttered the phrase, "Well, it works on my computer." No matter how advanced computers become, there seem to be recurrent problems related to the differences in what any two machines have configured or installed. There are ongoing attempts to solve this, and for Python developers, one of the best ways to prevent it is to use virtual environments.

### Virtual environments in Python

A virtual environment is a temporary adjustment to how [Python][2] runs code. A virtual environment is _not_ a [virtual machine][3], nor is it quite a [container][4]. In fact, a virtual environment manipulates the [environment variables][5] of your shell so that you can execute one known version of Python using a local set of modules.

### Life without virtual environments

Without a virtual environment, when you type `python` or `python3` into your terminal, you're launching whatever version of Python is installed on your computer:


```
$ python --version
Python 2.7.17
$ python3 --version
Python 3.7
```

On Monday, this might be version X, but on Tuesday, it could suddenly be Python Y, should you happen to update your computer overnight. Quite often, that's not a problem because Python tends to be good at backward compatibility. However, some computers retain very old versions of Python in the interest of legacy support, and some developers write on the cutting edge in their eagerness to use the newest features of the language. This can cause unexpected problems.

The same problem extends to individual Python modules. You might install version Z of the ExamplePyMod module, develop your code, and post your application online. Should someone who installed version X or Y of ExamplePyMod a year ago try to run your code, unexpected compatibility issues could arise. It's also a common problem for developers to take a module for granted. If you use a module so frequently that you practically think of that module as part of Python, then you're likely to forget to add the module as a requirement for running your application.

In both cases, for you to find the root cause of errors, you'd have to audit and update your system or the user's system so that you're both running the same versions of everything involved.

### Using virtual environments in Python

A virtual environment temporarily redirects calls to Python to a specific version of Python. For instance, using version Python 3.7 to create a virtual environment ensures that `python` points to Python 3.7, not Python 2.7 or Python 3.8 or whatever else you may have lying around on your development machine.

For example, here's a virtual environment created with Python 3.7:


```
# no virtual environment
$ python --version
Python 2.7.17

# virtual environment
$ python3.7 -m venv example37/venv
$ cd example37
$ source ./venv/bin/activate
(venv)$ python
Python 3.7
(venv)$ deactivate

# no virtual environment
$ python --version
Python 2.7.17
```

#### Using modules in a virtual environment

Modules are installed locally within the virtual environment. When you're working in a virtual environment, you can install ExamplePyMod and use it all day long, but it will be gone once you leave the virtual environment.

Here's the module installation process:


```
# no virtual environment
$ python3
&gt;&gt;&gt; import flask
ModuleNotFoundError: No module named 'flask'

# virtual environment
(venv)$ python -m pip install flask
[...]
(venv) bash-4.3$ python -m pip install flask
Collecting flask
  Downloading [...]
Successfully installed [...]
(venv)$ python
&gt;&gt;&gt; from flask import Flask
&gt;&gt;&gt; app = Flask(__name__)
(venv)$ deactivate

# no virtual environment again
$ python3
&gt;&gt;&gt; import flask
ModuleNotFoundError: No module named 'flask'
```

#### Restoring a virtual environment with pip

It might seem like a lot of extra work for you to install and reinstall your required modules every time you sit down to hack on code. Actually, the virtual environment system encourages you to keep track of the modules you're using in a `requirements.txt` file within your project directory. You can process `requirements.txt` with `pip` to handle automated installs of all dependencies:


```
$ cd myproject
$ source ./venv/bin/activate
(venv)$ python -m pip install -r requirements.txt
Installed [...]
$ python
&gt;&gt;&gt; from flask import Flask
&gt;&gt;&gt; import examplepymod
```

Python also caches required modules, so you're up and running in no time.

For a complete overview of `pip` and its abilities, download Moshe Zadka's [pip cheatsheet][6].

### Virtual environment overview

The command to create a virtual environment on Python is:


```
`$ python -m venv /directory/venv`
```

To activate a virtual environment:


```
$ source ./venv/bin/activate
(venv)$
```

To install required modules:


```
`(venv)$ python -m pip install -r requirements.txt`
```

To deactivate a virtual environment:


```
`(venv)$ deactivate`
```

Virtual environments are an important part of the Python development process. Learn to use them to protect yourself and your users from unexpected and unwelcome surprises. In short, use virtual environments so you can spend more time coding and less time debugging!

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/venv-python

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/lenovo-thinkpad-laptop-window-focus.png?itok=g0xPm2kD (young woman working on a laptop)
[2]: https://www.python.org/
[3]: https://opensource.com/article/19/5/getting-started-gnome-boxes-virtualization
[4]: https://opensource.com/article/19/10/namespaces-and-containers-linux
[5]: https://opensource.com/article/19/8/what-are-environment-variables
[6]: https://opensource.com/downloads/pip-cheat-sheet
