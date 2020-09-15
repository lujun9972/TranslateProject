[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Using bash’s shopt builtin to manage Linux shell behavior)
[#]: via: (https://www.networkworld.com/article/3574960/using-bashs-shopt-builtin-to-manage-linux-shell-behavior.html)
[#]: author: (Sandra Henry-Stocker https://www.networkworld.com/author/Sandra-Henry_Stocker/)

Using bash’s shopt builtin to manage Linux shell behavior
======
The shopt builtin offers 53 settings that can alter how bash behaves. Read this post and then refer to bash's man page to follow up on how these settings might work for you.
Network World / IDG

If you haven’t tried it yet, you might be surprised by the many features of **shopt**. While it works like a Linux command, it’s actually a bash shell builtin that allows you to change many things about that shell’s behavior.

One option, for example, allows the shell to fix minor typos when you type directory names. To demonstrate, in the first **cd** command shown below, the directory name, bin, is typed with an extra letter and the shell complains and gives up:

```
$ cd binn
-bash: cd: binn: No such file or directory
```

This next command enables the **cdspell** option that gets bash to attempt to correct minor typos in directory names.

$ shopt -s cdspell

Once **cdspell** is enabled, if some directory name is misspelled, bash will display the correct spelling and then run the corrected **cd** command. As you can see below, **pwd** confirms that the **cd** command was indeed run.

```
$ cd binn
bin
$ pwd
/home/shs/bin
```

If you're wondering about the name, try suppressing any impulse to call it "shop tea". It will be easier to remember if you, instead, think "**sh**ell **opt**ion" and pronounce it the same as "shopped". That is undoubtedly what the authors had in mind.

The basic syntax for **shopt** is:

**shopt [-pqsu] [-o] [optname …]**

This syntax summary shows that all arguments are optional and that more than one “optname” (the setting being displayed, enabled or disabled) can be manipulated with one command. Keep in mind when reading about **shopt** that both the “optname” list and the **-pqsu** arguments are often both referred to as “options” -- command options and shell options.

Another very useful **bash** setting is **histappend** which allows more than one shell to write to the same history file. Just remember that **bash** adds commands from a session to its history file only when the session is ended.

Once you test a setting and decide you like it, add the required command to your .bashrc file so that it will be enabled whenever you log in. You may only have to remove a comment marker for some:

```
# append to the history file, don't overwrite it
#shopt -s histappend     <==
```

To see a complete list of the settings available for **shopt** and whether they are currently enabled, simply type “shopt”. In the command below, the output is being passed to the **column** command simply to condense the output for this post.

```
$ shopt | column
autocd          off             globstar        off
assoc_expand_once       off     gnu_errfmt      off
cdable_vars     off             histappend      off
cdspell         on              histreedit      off
checkhash       off             histverify      off
checkjobs       off             hostcomplete    off
checkwinsize    on              huponexit       off
cmdhist         on              inherit_errexit off
compat31        off             interactive_comments    on
compat32        off             lastpipe        off
compat40        off             lithist         off
compat41        off             localvar_inherit        off
compat42        off             localvar_unset  off
compat43        off             login_shell     on
compat44        off             mailwarn        off
complete_fullquote      on      no_empty_cmd_completion off
direxpand       off             nocaseglob      off
dirspell        off             nocasematch     off
dotglob         off             nullglob        off
execfail        off             progcomp        on
expand_aliases  on              progcomp_alias  off
extdebug        off             promptvars      on
extglob         on              restricted_shell        off
extquote        on              shift_verbose   off
failglob        off             sourcepath      on
force_fignore   on              xpg_echo        off
globasciiranges on
```

The list above contains 53 settings. If you want to display only those settings that are enabled, use the **shopt -s** command:

```
$ shopt -s | column
cdspell         on              force_fignore   on
checkwinsize    on              globasciiranges on
cmdhist         on              interactive_comments    on
complete_fullquote      on      login_shell     on
expand_aliases  on              progcomp        on
extglob         on              promptvars      on
extquote        on              sourcepath      on
```

To view the status of an individual setting, you can type “shopt” following by the setting name. For example:

```
$ shopt cdspell
cdspell         on
```

The options for the **shopt** built-in include:

  * -s enable (set) the setting
  * -u disable (unset) the setting
  * -q suppress the normal output
  * -o restricts values of **optname** to those defined for the **-o** option with set



The **-q** option might be a little difficult to understand until you try it out. In the second example below, we use this option when trying to determine if the **cdspell** setting is enabled, but don’t see any confirmation because the **-q** suppresses the output. We can, however, still determine whether the setting is enabled by displaying the return code. If the setting had been disabled, the **echo $?** command would have returned a **1**.

```
$ shopt cdspell
cdspell         on
$ shopt -q cdspell
$ echo $?
0
```

To view a list of the **shopt** settings (a.k.a. options) with explanations about how each of them affects how **bash** behaves, look at the **bash** man page and scroll down to the section that begins like this:

```
The list of shopt options is:

              assoc_expand_once
                      If  set, the shell suppresses multiple evaluation of as‐
                      sociative array subscripts during arithmetic  expression
                      evaluation,  while  executing  builtins that can perform
                      variable assignments, and while executing builtins  that
                      perform array dereferencing.
              autocd  If  set,  a command name that is the name of a directory
                      is executed as if it were the argument to  the  cd  com‐
                      mand.  This option is only used by interactive shells.
              cdable_vars
                      If  set,  an  argument to the cd builtin command that is
                      not a directory is assumed to be the name of a  variable
                      whose value is the directory to change to.
              cdspell If set, minor errors in the spelling of a directory com‐
                      ponent in a cd command will be  corrected.   The  errors
                      checked for are transposed characters, a missing charac‐
                      ter, and one character too many.   If  a  correction  is
                      found,  the  corrected filename is printed, and the com‐
                      mand proceeds.  This option is only used by  interactive
                      shells.
```

Since this post mentions the **histappend** setting, here is the man page’s explanation for that one:

```
histappend
        If set, the history list is appended to the  file  named
        by the value of the HISTFILE variable when the shell ex‐
        its, rather than overwriting the file.
```

The **shopt** builtin may not become one of your favorite Linux tricks, but some of the ways that it allows you to tweak the way **bash** behaves might please you.

Join the Network World communities on [Facebook][1] and [LinkedIn][2] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3574960/using-bashs-shopt-builtin-to-manage-linux-shell-behavior.html

作者：[Sandra Henry-Stocker][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Sandra-Henry_Stocker/
[b]: https://github.com/lujun9972
[1]: https://www.facebook.com/NetworkWorld/
[2]: https://www.linkedin.com/company/network-world
