[#]: subject: "The "current branch" in git"
[#]: via: "https://jvns.ca/blog/2024/03/22/the-current-branch-in-git/"
[#]: author: "Julia Evans https://jvns.ca/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

The "current branch" in git
======

Hello! I know I just wrote [a blog post about HEAD in git][1], but I’ve been thinking more about what the term “current branch” means in git and it’s a little weirder than I thought.

### four possible definitions for “current branch”

  1. It’s what’s in the file **`.git/HEAD`**. This is how the [git glossary][2] defines it.
  2. It’s what **`git status`** says on the first line
  3. It’s what you most recently **checked out** with `git checkout` or `git switch`
  4. It’s what’s in your shell’s **git prompt**. I use [fish_git_prompt][3] so that’s what I’ll be talking about.



I originally thought that these 4 definitions were all more or less the same, but after chatting with some people on Mastodon, I realized that they’re more different from each other than I thought.

So let’s talk about a few git scenarios and how each of these definitions plays out in each of them. I used git version `2.39.2 (Apple Git-143)` for all of these experiments.

### scenario 1: right after `git checkout main`

Here’s the most normal situation: you check out a branch.

  1. `.git/HEAD` contains `ref: refs/heads/main`
  2. `git status` says `On branch main`
  3. The thing I most recently checked out was: `main`
  4. My shell’s git prompt says: `(main)`



In this case the 4 definitions all match up: they’re all `main`. Simple enough.

### scenario 2: right after `git checkout 775b2b399`

Now let’s imagine I check out a specific commit ID (so that we’re in “detached HEAD state”).

  1. `.git/HEAD` contains `775b2b399fb8b13ee3341e819f2aaa024a37fa92`
  2. `git status` says `HEAD detached at 775b2b39`
  3. The thing I most recently checked out was `775b2b399`
  4. My shell’s git prompt says `((775b2b39))`



Again, these all basically match up – some of them have truncated the commit ID and some haven’t, but that’s it. Let’s move on.

### scenario 3: right after `git checkout v1.0.13`

What if we’ve checked out a tag, instead of a branch or commit ID?

  1. `.git/HEAD` contains `ca182053c7710a286d72102f4576cf32e0dafcfb`
  2. `git status` says `HEAD detached at v1.0.13`
  3. The thing I most recently checked out was `v1.0.13`
  4. My shell’s git prompt says `((v1.0.13))`



Now things start to get a bit weirder! `.git/HEAD` disagrees with the other 3 indicators: `git status`, the git prompt, and what I checked out are all the same (`v1.0.13`), but `.git/HEAD` contains a commit ID.

The reason for this is that git is trying to help us out: commit IDs are kind of opaque, so if there’s a tag that corresponds to the current commit, `git status` will show us that instead.

Some notes about this:

  * If we check out the commit by its ID (`git checkout ca182053c7710a286d72`) instead of by its tag, what shows up in `git status` and in my shell prompt are exactly the same – git doesn’t actually “know” that we checked out a tag.
  * it looks like you can find the tags matching `HEAD` by running `git describe HEAD --tags --exact-match` (here’s the [fish git prompt code][4])
  * You can see where `git-prompt.sh` added support for describing a commit by a tag in this way in commit [27c578885 in 2008][5].
  * I don’t know if it makes a difference whether the tag is annotated or not.
  * If there are 2 tags with the same commit ID, it gets a little weird. For example, if I add the tag `v1.0.12` to this commit so that it’s with both `v1.0.12` and `v1.0.13`, you can see here that my git prompt changes, and then the prompt and `git status` disagree about which tag to display:



```

    bork@grapefruit ~/w/int-exposed ((v1.0.12))> git status
    HEAD detached at v1.0.13

```

(my prompt shows `v1.0.12` and `git status` shows `v1.0.13`)

### scenario 4: in the middle of a rebase

Now: what if I check out the `main` branch, do a rebase, but then there was a merge conflict in the middle of the rebase? Here’s the situation:

  1. `.git/HEAD` contains `c694cf8aabe2148b2299a988406f3395c0461742` (the commit ID of the commit that I’m rebasing onto, `origin/main` in this case)
  2. `git status` says `interactive rebase in progress; onto c694cf8`
  3. The thing I most recently checked out was `main`
  4. My shell’s git prompt says `(main|REBASE-i 1/1)`



Some notes about this:

  * I think that in some sense the “current branch” is `main` here – it’s what I most recently checked out, it’s what we’ll go back to after the rebase is done, and it’s where we’d go back to if I run `git rebase --abort`
  * in another sense, we’re in a detached HEAD state at `c694cf8aabe2`. But it doesn’t have the usual implications of being in “detached HEAD state” – if you make a commit, it won’t get orphaned! Instead, assuming you finish the rebase, it’ll get absorbed into the rebase and put somewhere in the middle of your branch.
  * it looks like during the rebase, the old “current branch” (`main`) is stored in `.git/rebase-merge/head-name`. Not totally sure about this though.



### scenario 5: right after `git init`

What about when we create an empty repository with `git init`?

  1. `.git/HEAD` contains `ref: refs/heads/main`
  2. `git status` says `On branch main` (and “No commits yet”)
  3. The thing I most recently checked out was, well, nothing
  4. My shell’s git prompt says: `(main)`



So here everything mostly lines up, except that we’ve never run `git checkout` or `git switch`. Basically Git automatically switches to whatever branch was configured in `init.defaultBranch`.

### scenario 6: a bare git repository

What if we clone a bare repository with `git clone --bare https://github.com/rbspy/rbspy`?

  1. `HEAD` contains `ref: refs/heads/main`
  2. `git status` says `fatal: this operation must be run in a work tree`
  3. The thing I most recently checked out was, well, nothing, `git checkout` doesn’t even work in bare repositories
  4. My shell’s git prompt says: `(BARE:main)`



So #1 and #4 match (they both agree that the current branch is “main”), but `git status` and `git checkout` don’t even work.

Some notes about this one:

  * I think `HEAD` in a bare repository mainly only really affects 1 thing: it’s the branch that gets checked out when you clone the repository. It’s also used when you run `git log`.
  * if you really want to, you can update `HEAD` in a bare repository to a different branch with `git symbolic-ref HEAD refs/heads/whatever`. I’ve never needed to do that though and it seems weird because `git symbolic ref` doesn’t check if the thing you’re pointing `HEAD` at is actually a branch that exists. Not sure if there’s a better way.



### all the results

Here’s a table with all of the results:

--------------------------------------------------------------------------------

via: https://jvns.ca/blog/2024/03/22/the-current-branch-in-git/

作者：[Julia Evans][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://jvns.ca/
[b]: https://github.com/lujun9972
[1]: https://jvns.ca/blog/2024/03/08/how-head-works-in-git/
[2]: https://git-scm.com/docs/gitglossary#def_HEAD
[3]: https://fishshell.com/docs/current/cmds/fish_git_prompt.html
[4]: https://github.com/fish-shell/fish-shell/blob/a5156e9e0e89bff2bd81ac945a019bad34f14346/share/functions/fish_git_prompt.fish#L521-L527
[5]: https://github.com/git/git/commit/27c578885a0b8f56430c5a24f558e2b45cf04a38
