[#]: subject: "Terminal Text Editor: Like VS Code But in Linux Terminal"
[#]: via: "https://itsfoss.com/terminal-text-editor/"
[#]: author: "Sreenath https://itsfoss.com/author/sreenath/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Terminal Text Editor: Like VS Code But in Linux Terminal
======

[![Warp Terminal][1]][2]

I spend a lot of time in the terminal. Whether it is writing scripts, editing configuration files, or managing remote servers, the terminal remains the place where I get most of my work done. But when a project becomes slightly complex, I often find myself reaching for the comfort of a graphical code editor like [Zed][3].

I'll be honest, while I can appreciate [why people love tools like Vim][4] and Neovim, learning a modal editor has always felt like more of a commitment than I was willing to make.

My editing needs are fairly straightforward, and spending hours memorizing keybindings, configuring plugins, and building a workflow from scratch never felt like a worthwhile investment for me.

That's why [TTT][5] caught my attention. The project describes itself as a real alternative to VS Code, Zed, and Sublime Text that runs entirely inside the terminal.

✋

Like most of the new open source software, TTT is also developed with the help of AI assistants.

### Installing TTT

On Linux, to install TTT, you can use the official installer script. That's fashion these days. No package, just an installer script curled right into your system.

```

    curl -sSfL https://raw.githubusercontent.com/eugenioenko/ttt/main/install.sh | sh

```

This will install the binary in `~/.local/bin`. To run it, open your favorite terminal and use the command:

```

    ttt

```

There are also prebuilt binaries available to download so that you can place it in a folder of your choice and use it in portable mode.

### TTT features I liked

Instead of trying to emulate traditional terminal editors, it aims to provide a modern, GUI-like editing experience in the terminal application with virtually no configuration required.

Sure, not all of these features might be unique, but they are good to have in an editor.

#### Syntax Highlighting

TTT uses `textmate-go` for syntax highlighting, a Go implementation of [Microsoft's TextMate engine][6] that powers syntax highlighting in VS Code. It claims to support more than 120 languages out of the box, giving it a surprisingly mature editing experience for a terminal-based application.

![Syntax Highlighting][7]

#### Multi-Cursor Editing

Multi-cursor editing is one of those features I started appreciating after spending some time with [Helix][8]. It's something I now instinctively look for in any editor.

Thankfully, TTT ships with multi-cursor support out of the box, so there's no need to install plugins or configure anything before getting started.

The workflow feels familiar if you've used modern editors before, like Sublime Text.

Pressing `Ctrl+D` selects the next occurrence of the highlighted text, while `Alt+Click` lets you place additional cursors exactly where you need them.

Multi-Cursor Editing

#### Mouse Support

Many terminal editors advertise mouse support, but often that simply means you can click around and scroll. TTT goes much further than that.

The mouse interactions felt surprisingly close to what I'd expect from a graphical editor rather than a typical terminal application.

You can click to position the cursor, drag to select text, and right-click to access context menus.

0:00

/0:30

1×

Mouse Support in TTT

The latter ended up being my favorite part because the menu isn't just a generic list of actions. Depending on where you click, TTT presents relevant options, making the whole experience feel far more polished and GUI-like than most terminal editors I've tried.

#### LSP and Auto Completion

A code editor doesn't feel complete these days without intelligent auto-completion, and TTT checks that box through [Language Server Protocol (LSP)][9] support.

Getting it up and running is fairly straightforward as you only need to install the language server for the programming language you work with.

The project also maintains a [dedicated guide covering language server setup][10] for a wide range of languages, which can save some trial and error during the initial configuration.

Once configured, you get the kind of code completion and language-aware features you'd expect from a modern editor, but without leaving the terminal.

LSP Autocompletion

#### Multi-folder Workspaces

Multi-folder workspaces allow you to group related folders into a single workspace and treat them as one project, much like VS Code's multi-root workspaces.

What makes this even more useful is that the workspace can be saved to a `workspace.ttt` file and reopened later with the exact same setup. So instead of manually opening the same collection of directories every time, you can simply load the workspace and continue where you left off.

For example, I have this `customization.ttt` file that has the content:

```

    {
      "folders": [
        { "path": "/home/itsfoss/Projects/text-script-files/" },
        { "path": "/home/itsfoss/Projects/public-dot-files/" },
        { "path": "/home/itsfoss/Projects/desktop-customization" }
      ]
    }

```

Now, I can always open this workspace by using the command:

```

    ttt --workspace ~/Projects/customization.ttt

```

You don't need to manually create this file since you can add location to a workspace and later save it all via File -> Save Workspace As option.

0:00

/0:41

1×

Multifolder Workspaces

#### Modern Search with Ripgrep

TTT uses [ripgrep][11] under the hood, which is already a favorite among developers thanks to its speed and ability to handle large projects without feeling sluggish.

In practice, this means you get fast, project-wide search capabilities directly inside the editor.

Combined with shortcuts like the `Ctrl+K F` for workspace search and `Ctrl+K R` for search and replace, it feels much closer to the experience you'd expect from a modern GUI editor than a typical terminal-based tool.

Search in TTT

💡

You need to have ripgrep installed on your system.

#### Git Integration

TTT provides a dedicated Changes panel where you can stage, unstage, discard, commit, pull, push, and sync repositories without dropping back to the command line.

The built-in diff viewer is particularly nice to work with because it combines Git diffs with syntax highlighting, making code changes easier to read.

The Git gutter indicators and inline blame information help provide context while editing.

If you're working with multiple repositories in a workspace, TTT automatically groups changes by repository, which keeps things organized when juggling several projects at once.

0:00

/0:33

1×

Git Integration

#### Integrated Terminal

You may find it funny that one of my favorite features in a terminal-based editor is... another terminal. But in practice, I found it incredibly useful.

Whenever I needed to run a command, I didn't have to open a split terminal in my terminal emulator or switch to another tab. Everything stayed inside TTT, which helps maintain focus on the task at hand.

TTT's integrated terminal is a full terminal emulator rather than a basic command prompt. It supports multiple terminal tabs, true-color rendering, scrollback, and can be toggled between panel and fullscreen modes with keyboard shortcuts.

For a project that aims to bring a GUI-like experience into the terminal, this feature fits perfectly, eliminating one more reason to leave the editor while working.

0:00

/0:41

1×

Integrated Terminal

#### Plugins

TTT already comes with many of the features I normally install plugins for in other editors. But the more I explored it, the more I appreciated the approach.

TTT supports Lua-based plugins that can add commands, panels, and keybindings, allowing you to extend the editor without turning it into a configuration project.

Plugins run inside a sandboxed environment and must explicitly request permissions to approve each plugin's capabilities.

To add even more convenience, you can install plugins through a dedicated panel within the TUI.

You may read more about the plugins in their [official documentation][12].

Plugins in TTT

#### Theming

TTT ships with a decent collection of built-in themes, including popular options like Dracula, Monokai, etc., making it easy to find something comfortable without downloading anything extra.

The built-in theme picker offers live previews as you browse themes, and you can customize virtually every aspect of the interface through JSON files, from syntax highlighting and diff colors to the sidebar, status bar, and even terminal colors.

Themes in TTT

### Wrapping Up

After spending some time with TTT, my biggest takeaway isn't that it's a great terminal editor. It's that this thing often doesn't feel like a terminal editor at all. In many ways, it feels like a full-blown GUI application that just happens to live inside a terminal window.

Now, I don't know how many of you will actually approve of that direction. The Linux and terminal communities have long maintained a clear distinction between TUIs and GUIs, and plenty of users prefer terminal applications precisely because they don't try to mimic desktop software. TTT deliberately blurs that line. Whether that's a good thing or not will ultimately depend on what you want from a terminal editor.

I found TTT's approach refreshing. It takes many of the conveniences people expect from modern GUI editors and brings them into the terminal with surprisingly very few compromises. If that idea sounds appealing, TTT is absolutely worth a look.

By the way, TTT is not the only editor of this kind. We have covered [several other terminal editors that are easy to use][13] since they provide terminal user interfaces that can be used with a mouse. If you are not allergic to Microsoft, their [open source Edit editor][14] is also worth a look.

I welcome your comments on TTT and other terminal based text editors you prefer.

If this helped you, consider supporting It's FOSS

It's FOSS has been helping people use Linux for the past 14 years. Help us stay independent from big tech. Become a Plus member, enjoy ad-free reading and get 5 eBooks.

Plus yearly

Ad-free, FREE ebooks

[Join yearly][15]

Best value

Plus lifetime

Pay once, Enjoy forever

[Go lifetime][16]

Buy us a coffee

Any amount, no commitment

[Support on Ko-fi][17]

Skip the AI slop and SEO spam in your Google results

Tell Google you prefer It's FOSS, and it will show our Linux news and tutorials, created by experienced Linux users, more often when you search. It takes just a click.

[Set as preferred source][18]

--------------------------------------------------------------------------------

via: https://itsfoss.com/terminal-text-editor/

作者：[Sreenath][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sreenath/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://itsfoss.com/news/zed-editor/
[4]: https://itsfoss.com/pro-vim-tips/
[5]: https://tttedit.dev/
[6]: https://github.com/microsoft/vscode-textmate
[7]: https://itsfoss.com/content/images/2026/10/syntax-highlight-ttt.png
[8]: https://itsfoss.com/helix-editor/
[9]: https://microsoft.github.io/language-server-protocol/
[10]: https://github.com/eugenioenko/ttt/blob/main/docs-web/src/content/docs/guides/lsp.md
[11]: https://itsfoss.com/ripgrep-all/
[12]: https://github.com/eugenioenko/ttt/blob/main/docs-web/src/content/docs/guides/plugins.md
[13]: https://itsfoss.com/fresh-terminal-text-editor/
[14]: https://itsfoss.com/news/microsoft-edit/
[15]: https://itsfoss.com/#/portal/signup
[16]: https://itsfoss.com/lifetime-membership/
[17]: https://ko-fi.com/itsfoss
[18]: https://www.google.com/preferences/source?q=itsfoss.com
