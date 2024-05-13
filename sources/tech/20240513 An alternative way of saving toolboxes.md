[#]: subject: "An alternative way of saving toolboxes"
[#]: via: "https://fedoramagazine.org/alternative-way-of-saving-toolboxes-for-later-use/"
[#]: author: "Liviu Vasut https://fedoramagazine.org/author/viuser/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

An alternative way of saving toolboxes
======

![][1]

Contributed by Liviu Vasut

A [previous article][2] in the Fedora Magazine describes how toolboxes can be saved in a container image repository and restored on the same or a different machine. The method described there works well for complex scenarios where setting up the toolbox takes considerable time or effort. But most of the time, toolboxes are simpler than that, and saving them as container images is… well, wasteful. Let’s see how we can store and use our toolboxes in a cheaper way.

### Problem statement

  1. Define toolboxes in simple text files so that they are easy to transfer or version in a GIT repository.
  2. Have the ability to describe a toolbox in a declarative way.
  3. Have everything set up automatically so that the toolbox is ready to use upon initial entry.
  4. The system should support customizations or extensions to accommodate any corner cases that were not foreseeable from the start.



### Proposed solution

Toolboxes are just instances of a container image. However, they have access to the home directory and use the same configuration as the host shell. On the other hand, each toolbox has a special file, visible only inside the toolbox, that keeps the name of the toolbox. This is _/run/.containerenv_. Combining these two facts presents a possible route to the desired state: simply keep whatever initialization or configuration steps as simple _rc_ files and use a convention to source them only for a specific toolbox. Consider, step by step, how this can be accomplished (using _bash_ as an example because it’s the default shell in Fedora. Other shells should support the same mechanisms).

For the system to work, two things are needed:

  * A few toolbox definitions.
  * Something to take those definitions and turn them into toolboxes.



### Storing toolbox Definitions

The first point is easy. Put the files anywhere. For example, they can reside in*~/.bashrc.d/toolboxes*. (This path is used throughout the rest of the discussion.) Each _rc_ file is named after the toolbox it configures. For example, _~/.bashrc.d/toolboxes/taskwarrior.rc_ for a toolbox named _taskwarrior_ to be used for tasks and time tracking. The contents of this file is described later in this article.

### Converting Definitions into toolboxes

For the second point, to keep things nice and tidy, place the orchestration logic in a separate file in the _~/.bashrc.d_ directory. For example, call it _toolbox.rc_. It should have the following content:

```

    function expose(){
         [ -f "$1" ] || echo -e "#!/bin/sh\nexec /usr/bin/flatpak-spawn --host $(basename $1) \"\$@\"" | sudo tee "$1" 1>/dev/null && sudo chmod +x "$1"
    }

    function install_dependencies(){
         [ -f /.first_run ] || sudo dnf -y install $@
    }

    if [ -f "/run/.toolboxenv" ]
    then
         TOOLBOX_NAME=$( grep -oP "(?<=name=\")[^\";]+" /run/.containerenv )
        if [ -f "$HOME/.bashrc.d/toolboxes/${TOOLBOX_NAME}.rc" ]
      then
                  . "$HOME/.bashrc.d/toolboxes/${TOOLBOX_NAME}.rc"
      fi

      if ! [ -f /.first_run ] ; then
                [[ $(type -t setup) == function ]] && setup
                   sudo touch /.first_run
        fi
    fi

```

With the orchestration logic set up, some toolboxes are needed to orchestrate. Continuing with the _taskwarrior_ toolbox example, a definition is added. Create a file called _~/.bashrc.d/toolboxes/taskwarrior.rc_ and add the following line in it:

```

    install_dependencies task timew

```

This practically says that in this toolbox these two packages are to be installed: _task_ and _timew_.

### Creating toolboxes

Now, create and enter the toolbox:

```

    $ toolbox create taskwarrior
    $ toolbox enter taskwarrior

```

When the newly created toolbox is entered, _dnf_ runs automatically to install the declared dependencies. Exit the toolbox and enter it again and you will get the prompt directly because all the packages are already installed.

It is now possible to stop the container and recreate the toolbox and everything will be installed back automatically.

```

    $ podman stop timewarrior
    $ toolbox rm timewarrior
    $ toolbox create taskwarrior
    $ toolbox enter taskwarrior

```

### Getting More Complicated

Now complicate things a bit. What if some random commands need to run to set up the toolbox? This is done using a special function, called _setup()_ , which is called from _toolbox.rc_ , as shown above. As an example, here is the setup for a toolbox for working with AWS resources. It is named _awscli_ and the associated configuration file is _~/.bashrc.d/toolboxes/awscli.rc_ :

```

    setup() {
          curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
     unzip awscliv2.zip
            sudo ./aws/install
    }

```

Another use case to cover is exposing host commands inside the toolbox. Consider a toolbox for file management that opens pdf files in a browser previously installed as a flatpak on the host. Employ the _expose()_ function, also defined in _toolbox.rc_ , to give access to flatpak inside the toolbox. Below is the _vifm.rc_ file used to create the _vifm_ toolbox:

```

    install_dependencies vifm fuse-zip curlftpfs shared-mime-info ImageMagick poppler-utils
    expose /usr/bin/flatpak

```

With that, from inside the toolbox, start the browser using:

```

    $ flatpak run com.vivaldi.Vivaldi

```

### Extending the toolbox

The last point in the problem statement (wish list) was extensibility. What is shown thus far is just a basis that already works pretty well. However, one can see how this system is adaptable and can evolve to meet other requirements. For example, new functions can be defined, both as implementations in _toolbox.rc_ or as hooks to be called if defined inside the toolbox configuration file. Also, the existing functionality can be mixed and matched depending on current needs. The last example, for instance, demonstrates a combination of dependencies and host command access. Do not forget that the toolbox configurations defined in _~/.bashrc.d/toolboxes_ are ultimately just shell files and you can add everything that the shell supports: aliases, custom functions, environment variables, etc.

### Troubleshooting

**Problem** : nothing is happening when I enter a new toolbox.

The _~/.bashrc_ might not be set up to source files from _~/.bashrc.d_. Check that the following block exists in _~/.bashrc_ :

```

    # User specific aliases and functions
    if [ -d ~/.bashrc.d ]; then
        for rc in ~/.bashrc.d/*; do
            if [ -f "$rc" ]; then
                . "$rc"
            fi
        done
    fi
    unset rc

```

**Problem** : when I enter a toolbox I get a _command not found_ error.

The order in which files are sourced might not be correct. Try renaming _~/.bashrc.d/toolbox.rc_ to _~/.bashrc.d/00-toolbox.rc_ , then delete and recreate the toolbox.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/alternative-way-of-saving-toolboxes-for-later-use/

作者：[Liviu Vasut][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/viuser/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/toolbox-backup-code-1-816x345.jpg
[2]: https://fedoramagazine.org/backup-and-restore-toolboxes-with-podman/
