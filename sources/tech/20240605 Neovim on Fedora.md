[#]: subject: "Neovim on Fedora"
[#]: via: "https://fedoramagazine.org/configuring-neovim-on-fedora-as-an-ide-and-using-lazyvim/"
[#]: author: "Bryar Topham https://fedoramagazine.org/author/human-d3v/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Neovim on Fedora
======

![][1]

Photo by [Vincenzo Marotta][2] on [Unsplash][3]

### From modal text editor to full-featured IDE on Fedora Workstation

Are you a Fedora user who values open-source software and customization options? Are you a software engineer, developer, data scientist, sysadmin, or a student? In this tutorial, we’ll guide you through the process of installing Neovim on Fedora for efficient and effective coding in languages like Rust, Python, Go, and TypeScript. This is not a ‘How to Use Vim’ tutorial — we’re focusing on the power and flexibility of Neovim for language-specific development. Let’s dive in and supercharge your coding experience!

### Downloading Neovim

To start, download and install Neovim on Fedora using _dnf_ :

```

    sudo dnf install neovim

```

Or build from source

```

    # install dependencies
    sudo dnf -y install ninja-build cmake gcc make unzip gettext curl glibc-gconv-extra

```

```

    # clone repo
    git clone https://github.com/neovim/neovim &&
    cd neovim

```

```

    # build and install package
    make CMAKE_BUILD_TYPE=Release
    sudo make install

```

After installation, Neovim is initiated by typing _nvim_ in the terminal or selecting the application in the applications menu.

![][4]

Note: _If you build from source, the icon won’t appear in the applications menu._

With Neovim installed, it’s time to create your local configuration.

* * *

### The local configuration directory structure

Understanding the directory structure can be a headache for new users. When Neovim launches, it searches first for the _~/.config/nvim_ directory and expects the following files and directories to be present.

Note: _The list of searched-for directories can also be found by typing **:h runtimepath** on the Neovim command line_

```

    ~/.config/nvim/
                ╰- init.lua                 <-- init file
                ╰- after/plugin/            <-- directory for plugin configurations
                ╰- lua/config/
                             ╰-lazy.lua     <-- plugin manager file

```

  * The _/after_ directory contains files to be loaded after the _init.lua_ script has run.
  * The _/lua_ directory contains the plugins configured in Lua.
  * Both _/plugin_ and _/config_ directories are searched for runtime files.



The following script will build the basic directory structure and source the _lazy.lua_ file:

```

    mkdir -p ~/.config/nvim/after/plugin/ ~/.config/nvim/lua/config &&
    touch ~/.config/nvim/lua/config/lazy.lua &&
    touch ~/.config/nvim/init.lua &&
    echo "require('config.lazy')" >> ~/.config/nvim/init.lua

```

### The Lazy plugin manager

Regardless of your desired development language(s), the [Lazy.nvim][5] plugin manager makes it easy to install and manage all of your plugins. Inside of your _~/.config/lua/config/lazy.lua_ file, copy the following starter script:

```

    -- ~/.config/lua/config/lazy.lua

    local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
    if not (vim.uv or vim.loop).fs_stat(lazypath) then
      vim.fn.system({
        "git",
        "clone",
        "--filter=blob:none",
        "https://github.com/folke/lazy.nvim.git",
        "--branch=stable", -- latest stable release
        lazypath,
      })
    end
    vim.opt.rtp:prepend(lazypath)

    vim.g.mapleader = " " -- the leader key is used in many keymaps,

    local plugins = {
        -- plugins go here
    }

    require("lazy").setup(plugins, {})

```

Save the _lazy.lua_ file and restart Neovim. Enter _:Lazy_ on the command line to bring up the Lazy plugin manager interface.

![][6]

### Add plugins:

Lua is an easy-to-read, dynamically-typed programming language typically used for scripting in programs and games. Most plugins for Neovim are written in Lua, so some familiarity with the language is good, but is not a requirement.

The basic workflow for adding a new plugin to Neovim is as follows:

![][7]

Regardless of the programming language, the following plugins are helpful:

  * [plenary.nvim][8] – for additional functions (including asynchronous requests) in Neovim.
  * [nvim-treesitter][9] – provides treesitter support for language parsers, queries, and additional
features like syntax highlighting, indentation, and more.
  * [nvim-telescope][10] – a fuzzy finder for searching projects, repositories, and files.
  * [harpoon][11] — a ui/cl utility for switching between files quickly.
  * [undotree][12] — a visual representation of the changes made to a file, making it easy to switch between undo branches.
  * [vim-fugitive][13] — a git repository management tool.
  * [mason.nvim][14] — a language server (lsp) management utility.
  * [nvim-cmp][15] — for autocompletion support.
  * [LuaSnip][16] — for snippet engine support.
  * A color scheme like [NeoSolarized][17], [tokyonight][18], [papercolor][19], [kanagawa][20], or any of the [myriad of other themes][21] available.



Add these plugins to the plugins table in _~/.config/nvim/lua/config/lazy.lua._

```

    -- partial file

    local plugins = {
        "nvim-lua/plenary.nvim",
        {"nvim-treesitter/nvim-treesitter", build = ":TSUpdate"},
        {"nvim-telescope/telescope.nvim", tag = '0.1.6',
            requires = { {"nvim-lua/plenary.nvim"}}},
        {"ThePrimeagen/harpoon", branch = "harpoon2",
            dependencies = {"nvim-lua/plenary.nvim"}},
        {"mbbill/undotree"},
        {"tpope/vim-fugitive"},
        --lsp configuration
            {"neovim/nvim-lspconfig"}, --lsp configs
            {"hrsh7th/cmp-nvim-lsp"}, -- autocompletion
            {"hrsh7th/nvim-cmp"}, --additional autocompletion
            {"L3MON4D3/LuaSnip", version = "v2.*", build = "make install_jsregexp", dependencies = {'saadparwaiz1/cmp_luasnip','rafamadriz/friendly-snippets'}}, --snippet engine
            {"williamboman/mason.nvim"}, --lsp package manager
            {"williamboman/mason-lspconfig.nvim"}, --lsp package manager configs
        --color scheme
        {'rebelot/kanagawa.nvim'},
    }

    require("lazy").setup(plugins, {})

```

Close and reopen Neovim to make the Lazy plugin manager download all of the above plugins.

![][22]

* * *

### Configure the plugins after they are loaded

After plugins are loaded using Lazy, Neovim looks for files in the _~/.config/nvim/after/plugin/_ directory to configure them. Every _.lua_ file in this directory is sourced for configuration regardless of naming convention. While this means that you could configure all the plugins in a single file called _single_file.lua_ , this file would be disorganized, large, and difficult to navigate.

Instead, organize plugin configurations either by **function** or by **name**.

#### Example of organization by function:

**Function** | **File** | **Plugin(s) configured in file**
---|---|---
Navigating files, git repos,
and fuzzy finding | nav.lua | vim-fugitive, harpoon, telescope
Syntax parsing, LSP,
autocompletion | lsp.lua | treesitter, mason, nvim-cmp,
nvim-lsp, luasnip
Color scheme | colors.lua | kanagawa (or comparable
colorscheme)
Fixing mistakes | undo.lua | undotree

The resulting directory structure looks like this:

```

    ~/.config/nvim/
                ╰- init.lua
                ╰- after/plugin/
                               ╰- nav.lua
                               ╰- colors.lua
                               ╰- lsp.lua
                               ╰- undo.lua
                ╰- lua/config/
                             ╰-lazy.lua

```

#### Example of organzation by plugin name:

**Function** | **FIle** | **Plugin(s) configured in file**
---|---|---
Autocompletion | cmp.lua | nvim-cmp
Color scheme | colors.lua | kanagawa (or comparable colorscheme)
File jumping | harpoon.lua | harpoon
LSP support | lsp.lua | mason, nvim-lsp, luasnip
Fuzzy finding | telescope.lua | telescope
Language parsing | treesitter.lua | treesitter
Fixing mistakes | undotree.lua | undotree

The resulting directory structure looks like this:

```

    ~/.config/nvim/
                ╰- init.lua
                ╰- after/plugin/
                               ╰- cmp.lua
                               ╰- colors.lua
                               ╰- harpoon.lua
                               ╰- lsp.lua
                               ╰- telescope.lua
                               ╰- treesitter.lua
                               ╰- undotree.lua
                ╰- lua/config/
                             ╰-lazy.lua

```

Note: _The following sections are written through an ‘organization by plugin name’ paradigm._

### treesitter.lua

```

    require("nvim-treesitter.configs").setup({
        ensure_installed = {"lua", "python","rust","go", "vimdoc", "c"}, --any language parsers you want installed
        sync_install = false, --if you want to load the parsers synchronously
        auto_install = true,
        highlight = {
            enable = true,
            disable = {}, --include any languages you want to disable highlighting
            disable = function(lang, buf)
                local max_filesize = 100 * 1024 -- 100 KB
                local ok, stats = pcall(vim.loop.fs_stat, vim.api.nvim_buf_get_name(buf))
                if ok and stats and stats.size < max_filesize then
                    return true
                end
            end,
            additional_vim_regex_highlighting = false,
        }
    })

```

### telescope.lua

```

    local builtin = require("telescope.builtin")
    vim.keymap.set('n', '<leader>ff', builtin.find_files, {})
    vim.keymap.set('n', '<leader>fg', builtin.git_files, {})
    vim.keymap.set('n', '<leader>ps', function()
        builtin.grep_string({search = vim.fn.input(":Grep > ")})
    end)

```

This sets the following keymaps for use with telescope as a fuzzy finder:

  * _leader + ff_ : Find files
  * _leader + fg_ : Find git files
  * _leader + ps_ : Grep for string



Your **leader** key is mapped to the **space key** in your _~/.config/nvim/lua/config/lazy.lua_ file.

### harpoon.lua

```

    local harpoon = require("harpoon")

    -- REQUIRED
    harpoon:setup()
    -- REQUIRED

    vim.keymap.set("n", "<leader>a", function() harpoon:list():add() end) --add file to end of ui list
    vim.keymap.set("n", "<C-e>", function() harpoon.ui:toggle_quick_menu(harpoon:list()) end)

    vim.keymap.set("n", "<C-h>", function() harpoon:list():select(1) end)
    vim.keymap.set("n", "<C-t>", function() harpoon:list():select(2) end)
    vim.keymap.set("n", "<C-n>", function() harpoon:list():select(3) end)
    vim.keymap.set("n", "<C-s>", function() harpoon:list():select(4) end)

    -- Toggle previous & next buffers stored within Harpoon list
    vim.keymap.set("n", "<C-S-P>", function() harpoon:list():prev() end)
    vim.keymap.set("n", "<C-S-N>", function() harpoon:list():next() end)

```

### undotree.lua

```

    vim.keymap.set("n", "<leader>u", vim.cmd.UndotreeToggle)

```

This sets _leader + u_ to open the undotree ui.

### colors.lua

This file can be as simple as setting the colorscheme, or as complex as changing individual components. The typical implementation is setting the background color and colorscheme.

#### **Simple configuration using kanagawa**

```

    -- assuming you added {'rebelot/kanagawa.nvim'} to your lazy.lua file for your colorscheme
    -- ~/.config/nvim/after/plugin/colors.lua

    vim.o.background = 'dark'
    vim.cmd.colorscheme('kanagawa')

```

![][23]

**Other Examples:**

NeoSolarized:

![][24]

Everforest:

![][25]

### lsp.lua

```

    require("mason").setup({})
    require("mason-lspconfig").setup({
        handlers = {
            function(server_name)
                local capabilities = require("cmp_nvim_lsp").default_capabilities()
                require("lspconfig")[server_name].setup({
                    capabilities = capabilities
                })
            end,
        },
    })

    vim.api.nvim_create_autocmd("LspAttach", {
        callback = function(args)
            local bufnr = args.buf
            local opts = {buffer = bufnr, remap = false}
                  vim.keymap.set("n","gd",function() vim.lsp.buf.definition() end, opts) --go to definition
             vim.keymap.set('n','K',function() vim.lsp.buf.hover() end, opts) -- hover
             vim.keymap.set('n','<leader>vws', function() vim.lsp.buf.workspace_symbol() end, opts) --view workspace
                 vim.keymap.set('n','<leader>vd', function() vim.diagnostic.open_foat() end, opts) --view diagnostic
             vim.keymap.set('n','[d',function() vim.diagnostic.goto_next() end, opts)
              vim.keymap.set('n',']d',function() vim.diagnostic.goto_prev() end, opts)
              vim.keymap.set('n','<leader>vca', function() vim.lsp.buf.code_action() end, opts) --view code action
                    vim.keymap.set('n','<leader>vrn', function() vim.lsp.buf.rename() end, opts) --rename variables
                 vim.keymap.set('n','<leader>vrr', function() vim.lsp.buf.references() end, opts)
                vim.keymap.set('n','<leader>h', function() vim.lsp.buf.signature_help() end, opts)
        end
    })

```

This configures the LSP servers. This specific implementation offloads all setup and management to mason.

When a file is opened, the parsers provided by treesitter trigger the LSP to attach to the buffer. The above _autocmd_ configures the keymaps for the LSP to the following:

  * _gd_ – Go to definition
  * _K_ – Hover
  * _leader + vws_ – View workspace
  * _leader + vd_ – View diagnostic
  * _[d_ – Next diagnostic
  * _]d_ – Previous diagnostic
  * _leader + vca_ – View code action
  * _leader + vrn_ – Rename variables
  * _leader +_ vrr – View references
  * _leader + h_ – View signature help



### cmp.lua

```

    local cmp = require("cmp")

    require('luasnip.loaders.from_vscode').lazy_load()

    cmp.setup({
        snippet = {
            expand = function(args)
                require('luasnip').lsp_expand(args.body)
            end,
        },
        window = {
            -- uncomment the following if you want bordered completion options
            -- completion = cmp.config.window.bordered(),
            -- documentation = cmp.config.window.bordered(),
        },
        mapping = cmp.mapping.preset.insert({
          ['<C-p>'] = cmp.mapping.select_prev_item({select = true}),
              ['<C-n>'] = cmp.mapping.select_next_item({select = true}),
              ['<C-Space>'] = cmp.mapping.complete(),
         ['<C-y>'] = cmp.mapping.confirm({select = true}),
        }),
        sources = cmp.config.sources({
            {name = 'nvim_lsp'},
            {name = 'luasnip'},
        }, {
            {name = 'buffer'},
        })
    })

```

There are _many ways_ to configure lsp and completion support. From loading each server and configuring individual capabilities to creating custom language servers and linking them to custom filetypes. This is meant only as an easy-to-implement approach.

* * *

### Language-specific plugins and configurations

The power of Neovim lies in its unparalleled customization, allowing you to tailor your coding experience to suit your needs, workflow, and preferences. The sheer range of customization options can be overwhelming at first. The following language-specific plugins and configurations will help you get started.

#### Rust

Install Rust on Fedora with _rustup:_

```

    ## install rustup on Fedora
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- --default-toolchain none -y

```

After installation, source the new environment file by entering _. $HOME/.cargo/env_ or close the terminal and reopen it:

```

    ## install the nightly (or stable) toolchain and component clippy
    rustup toolchain install nightly --allow-downgrade --profile minimal --component clippy

```

After installing the nightly toolchain, install the rust-analyzer:

```

    ## install the rust-analyzer LSP component from rustup
    rustup component add rust-analyzer

```

##### **LSP** Support:

When writing rust in Neovim using the _rustaceanvim_ plugin, it’s important to avoid installing _rust-analyzer_ via Mason, instead, use the _rustup component add rust-analyzer_ command above. This will properly install the LSP to function with _rustaceanvim_. This avoids downloading the _rust-analyzer_ with the wrong toolchain.

##### **Load plugins:**

The two plugins to load with Lazy are:

  * [rustaceanvim][26] — for a host of extra tools, including lsp, man pages, advanced running capabilities and more.
  * [nvim-dap][27] — (Debug Adapter Protocol) for added debugging capabilities.



```

    -- for Rust Programming
    {'mrcjkb/rustaceanvim', version = '^4', lazy = true, ft = {rust}},
    {'mfussenegger/nvim-dap'},

```

To load the plugins, add them to the _plugins_ table of the _~/.config/nvim/lua/config/lazy.lua_ file.

```

    --- partial file
    -- ~/.config/nvim/lua/config/lazy.lua

    local plugins = {
        "nvim-lua/plenary.nvim",
     {"nvim-treesitter/nvim-treesitter", build = ":TSUpdate"},
     {"nvim-telescope/telescope.nvim", tag = "0.1.1",
              requires = { {"nvim-lua/plenary.nvim"}}},
     {"ThePrimeagen/harpoon",branch = "harpoon2",
                  dependencies = {"nvim-lua/plenary.nvim"}},
            {"mbbill/undotree"},
          {"tpope/vim-fugitive"},
       --lsp configuration
                   {"neovim/nvim-lspconfig"},
                    {"hrsh7th/cmp-nvim-lsp"}, --autocompletion
                    {"hrsh7th/nvim-cmp"}, --additional autocompletion
             {"L3MON4D3/LuaSnip", version = "v2.*", build = "make install_jsregexp",
                       dependencies = {'saadparwaiz1/cmp_luasnip',
                                  'rafamadriz/friendly-snippets'}}, --snippet engine
                    {"williamboman/mason.nvim"}, --lsp manager
                    {"williamboman/mason-lspconfig.nvim"}, --lsp configs manager
          --colorscheme
        {'rebelot/kanagawa.nvim'},
        -- for Rust programming
          {'mrcjkb/rustaceanvim', version = '^4', lazy = true, ft = {rust}},
            {'mfussenegger/nvim-dap'},
    }

```

##### **Configure plugins:**

In your _.config/nvim/after/plugin/_ directory, add a _rust.lua_ file for Rust-specific configuration. This example sets up keymaps for the _rust-analyzer_ and _dap_.

```

    -- ~/.config/nvim/after/plugin/rust.lua

    -- find local buffer
    local bufnr = vim.api.nvim_get_current_buf()

    -- FileType specific keymaps
    vim.api.nvim_create_autocmd("FileType", {
      pattern = {"rust", "rs", "Rust"},
      callback = function ()
        vim.schedule(function ()
          vim.keymap.set("n", "<leader>rr", ":RustRun<CR>", {buffer = true})
              --rustaceanvim remaps
               --code actions
                vim.keymap.set("n", "<leader>ca", function ()
                     vim.cmd.RustLsp('codeAction')
               end, {silent = true, buffer = bufnr})
           -- hover actions
                    vim.keymap.set("n", "<leader>K", function ()
                            vim.cmd.RustLsp { 'hover', 'actions' }
            end, {silent = true, buffer = bufnr})
       --explain error
             vim.keymap.set("n", "<leader>e", function ()
                      vim.cmd('explainError')
                 end, {silent = true, buffer = bufnr})
     end)
      end
    })

    -- for debugging

    local dap = require('dap')
    dap.adapters.gdb = {
           type = "executable",
          command = "gdb",
      args = {"-i", "dap"}
    }

    dap.configurations.rust = {
      {
           name = "Launch",
      type = "gdb",
        request = "launch",
           program = function()
                  return vim.fn.input('Path to executable: ', vim.fn.getcwd() .. '/', 'file')
           end,
          cwd = "${workspaceFolder}",
           stopAtBegginingOfMainSubProgram = false,
      }
    }

```

This remaps the following for Rust files using _rustaceanvim_ :

  * _leader + rr_ to the Neovim terminal command “:RustRun” to run the current file.
  * _leader + ca_ to display the code-action using the Rust LSP.
  * _leader + K_ to give the LSP hover capabilities.
  * _leader + e_ to explain errors more verbosely.



There are other capabilities available to customize on the [usage and features][28] section of the _rustaceanvim_ wiki.

For debugging, the above example uses the [gnu project debugger (gpd)][29] in conjunction with the _nvim-dap_ plugin.

![][30]

#### Python

If you’re writing python for data science, AI and machine learning, game development, or general programming, Neovim is a great choice.

##### **Installation**

To install Python3 on Fedora, you can either install via _dnf_ or build from source (not shown here).

```

    ### install the latest version of Python3.12 and pip (python package manager) with dnf
    sudo dnf install python3.12 python3-pip

```

##### **Optional Installation**

Common python libraries that can be installed via

dnf

include:

  * [python3-devel][31] – for development headers and libraries.
  * [python3-virtualenv][32] – for building virtual environments.
  * [python3-pandas][33] -for working with structured data in dataframes.
  * [python3-numpy][34] – for working with numerical data in arrays.



```

    ### Optional installation
    sudo dnf install python3-devel python3-virtualenv python3-pandas python3-numpy

```

##### **LSP Support**

[pyright][35] is great for language server support, static type checking, and code completion. It can be installed using _:MasonInstall pyright_ from the command line in Neovim.

Note: _pyright_ requires _npm_ to be installed prior to running. See the Typescript section for instructions on installing _npm_ on Fedora.

##### **Example of data-science specific configuration:**

In the R-Programming Language you send commands to a terminal to work with data stored in memory. In order to work in a similar manner, the following functions are used to create a python REPL and send selections of code to be evaluated in the REPL. You can add these functions to a _python.lua_ file in the _~/.config/nvim/after/plugin/_ directory.

```

    -- ~/.config/nvim/after/plugin/python.lua

    function OpenTerminalBuffer(termType)
        -- open a terminal buffer
        vim.api.nvim_exec2('belowright split | term', {output = true})
        -- save terminal buffer
        local term_buf = vim.api.nvim_get_current_buf()
        vim.api.nvim_chan_send(vim.api.nvim_get_option_value('channel', {buf = term_buf}), termType .. "\r")
    end

    local function nextLine()
        local current_line = vim.api.nvim_win_get_cursor(0)[1]
            local total_lines = vim.api.nvim_buf_line_count(0)

      for i = current_line+1, total_lines do
                local line_content = vim.api.nvim_buf_get_lines(0, i-1, i, false)[1]
                  if line_content:match('^%S') then
                            vim.api.nvim_win_set_cursor(0, {i, 0})
                        break
                 end
           end
    end

    function SendToTerminal(opt)
       -- 0: send current line to buffer
       -- 1: send visual selection to buffer
       -- 2: send entire file up to and including current line to buffer

       -- extract text from current buffer
       local txt = ''
        if opt == 1 then
            vim.cmd('normal! gv"xy') -- move visual selection to x register
            txt = vim.fn.getreg('x')
            vim.api.nvim_exec2(":'>",{}) -- move cursor to last highlighted line
        elseif opt == 2 then
            local ln, _ = unpack(vim.api.nvim_win_get_cursor(0))
            local line_txts = vim.api.nvim_buf_get_lines(vim.api.nvim_get_current_buf(), 0, ln, false)
            txt = table.concat(line_txts, '\n')
        else
            txt = vim.api.nvim_get_current_line()
       end

        -- move cursor to next non-whitespace line
        nextLine()

        -- locate terminal buffer
       local term_buf = nil
       for _, bufnr in ipairs(vim.api.nvim_list_bufs()) do
            if vim.bo[bufnr].buftype == 'terminal' then
                term_buf = bufnr
                break
            end
        end
        if term_buf == nil then
            print('No terminal buffer found')
            return
        end

        vim.api.nvim_chan_send(vim.api.nvim_get_option_value('channel', {buf = term_buf}), txt .. "\r")
    end

    vim.api.nvim_create_autocmd('FileType', {
        pattern = {'python'},
        callback = function()
            vim.schedule(function()
                vim.keymap.set('n', '<leader><leader>py', [[:lua OpenTerminalBuffer("python3")<CR>]])
                vim.keymap.set({'v','x'}, '<BSlash>d', [[:lua SendToTerminal(1)<CR>]])
                vim.keymap.set('n', '<BSlash>d', [[:lua SendToTerminal(0)<CR>]])
                vim.keymap.set('n', '<BSlash>aa', [[:lua SendToTerminal(2)<CR>]])
            end)
        end,
    })

```

This creates two global functions _OpenTerminalBuffer()_ and _SendToTerminal()_ ,
then remaps keybindings to the following:

  * _leader + leader +py_ – Open a python REPL in a terminal buffer.
  * _\d_ – Send a visual selection or visual block to the REPL.
  * _\d_ – Send the current line to the REPL.
  * _\aa_ – Send the entire file up to and including the current line to the
REPL.



![][36]

#### TypeScript

##### Installation

To install TypeScript support on Fedora, you will need Node.js and npm (node package manager). (Or comparable runtime like [Bun][37])

```

    ### if you want to install nodejs and npm directly from the fedora repos
    sudo dnf install nodejs npm

```

Next, install TypeScript either to your project or globally:

```

    ## locally
    npm install typescript --save-dev

    ## globally
    npm install -g typescript

```

##### LSP Support

The following LSP’s are helpful in writing TypeScript. They are installed with
mason:

  * _:MasonInstall tsserver_ – TypeScript Language Server for LSP support.
  * _:MasonInstall eslint_d_ – eslint for linting.



![][38]

While there are plugins available specifically for typescript like [typescript-tools.nvim][39], LSP support is enough for a basic implementation to work in TypeScript.

#### Go

##### Installation

Install _Go_ on Fedora using _dnf_ :

```

    sudo dnf install go

```

After installation, build the _~/go_ directory and add _Go_ to your _PATH_ :

```

    # make go directory
    mkdir -p ~/go

```

```

    # add go to path and source .bashrc
    echo 'export GOPATH=$HOME/go' >> ~/.bashrc &&
    source ~/.bashrc

```

For more specific information on installation, see the [Fedora Developer Portal][40] entry on _Go_.

##### LSP support

Install lsp support, formatting, and linting using _mason_.

  * _:MasonInstall gopls_ – the official _Go_ LSP [(gopls][41]).
  * _:MasonInstall gofumpt_ – a strict formatter ([gofumpt][42]).
  * _:MasonInstall goimports_ – formatter that removes unused imports and adds referenced imports ([goimports][43]).
  * _:MasonInstall gomodifytags_ – a _go_ tool used to modify field tags and structs ([gomodifytags][44]).
  * _:MasonInstall golangci-lint_ – linter ([golangci-lint][45]).
  * _:MasonInstall gotests_ – a _go_ tool for generating table-driven tests ([gotests][46]).



##### Load plugins

The only plugin to load is [go.nvim][47].

```

    {
      "ray-x/go.nvim",
      dependencies = {"ray-x/guihua.lua"},
      config = function()
        require("go").setup()
      end,
      event = {"CmdlineEnter"},
      ft = {"go", 'gomod'},
      lazy = false,
    }

```

Add this to your _~/.config/nvim/lua/config/lazy.lua_ plugin table:

```

    --- partial file
    -- ~/.config/nvim/lua/config/lazy.lua

    local plugins = {
        "nvim-lua/plenary.nvim",
     {"nvim-treesitter/nvim-treesitter", build = ":TSUpdate"},
     {"nvim-telescope/telescope.nvim", tag = "0.1.1",
              requires = { {"nvim-lua/plenary.nvim"}}},
     {"ThePrimeagen/harpoon",branch = "harpoon2",
                  dependencies = {"nvim-lua/plenary.nvim"}},
            {"mbbill/undotree"},
          {"tpope/vim-fugitive"},
       --lsp configuration
                   {"neovim/nvim-lspconfig"},
                    {"hrsh7th/cmp-nvim-lsp"}, --autocompletion
                    {"hrsh7th/nvim-cmp"}, --additional autocompletion
             {"L3MON4D3/LuaSnip", version = "v2.*", build = "make install_jsregexp",
                       dependencies = {'saadparwaiz1/cmp_luasnip',
                                  'rafamadriz/friendly-snippets'}}, --snippet engine
                    {"williamboman/mason.nvim"}, --lsp manager
                    {"williamboman/mason-lspconfig.nvim"}, --lsp configs manager
          --colorscheme
        {'rebelot/kanagawa.nvim'},
        -- for Go programming
        {
           "ray-x/go.nvim",
           dependencies = {"ray-x/guihua.lua"},
           config = function()
             require("go").setup()
           end,
           event = {"CmdlineEnter"},
           ft = {"go", 'gomod'},
           lazy = false,
        }
    }

```

##### Plugin usage

Since _setup()_ is run when the plugin in loaded, _go.nvim_ doesn’t require a configuration file in the _~/.config/nvim/after/plugin/_ directory unless you want to implement custom changes to the configuration. It implements a huge list of commands available from the Neovim command line, simply type _:Go_ and press _< tab>_ to display the possibilites.

![][48]

* * *

### General settings

Some general settings to implement include setting relative line numbers, a color column, filetype triggering, and terminal-buffer escaping. These are only a few of the [options][49] available to customize. Do this by adding to a _settings.lua_ file in the _~/.config/nvim/lua/config/_ directory:

```

    -- ~/.config/nvim/lua/config/settings.lua

    -- line numbering
    vim.opt.nu = true
    vim.opt.relativenumber = true

    -- set tab spaces to 4
    vim.opt.tabstop = 4
    vim.opt.softtabstop = 4
    vim.opt.shiftwidth = 4
    vim.expandtab = true

    -- hand off undoing to undotree plugin and don't keep a swapfile
    vim.opt.swapfile = false
    vim.opt.backup = false
    vim.undodir = os.getenv("HOME") .. "/.vim.undodir"
    vim.opt.undofile = true

    -- set incremental search. This helps immensly with tricky searches
    vim.opt.hlsearch = false
    vim.opt.incsearch = true

    -- fast update time
    vim.opt.updatetime = 50

    -- color column to 80 characters
    vim.opt.colorcolumn = "80"

    -- filetype trigger
    vim.opt.filetype='on'

    -- set escape to enter normal mode in terminal buffer
    vim.keymap.set("t", "<esc>", [[<C-\><C-n>]], {silent = true, noremap = true})
    vim.api.nvim_set_keymap("n", "<leader><leader>term", ':belowright split | terminal<CR>',
        {noremap = true, silent=true})

```

After creating the _settings.lua_ file, add it to the _~/.config/nvim/init.lua_ file to source it:

```

    -- ~/.config/nvim/lua/config/settings.lua
    require('config.lazy')
    require('config.settings')

```

* * *

### Final directory structure:

If you followed this tutorial to this point, your final directory structure looks like this:

```

    ~/.config/nvim/
                ╰- init.lua
                ╰- after/plugin/
                               ╰- cmp.lua
                               ╰- colors.lua
                               ╰- harpoon.lua
                               ╰- lsp.lua
                               ╰- python.lua
                               ╰- rust.lua
                               ╰- telescope.lua
                               ╰- treesitter.lua
                               ╰- undotree.lua
                ╰- lua/config/
                             ╰-lazy.lua
                             ╰-settings.lua

```

And _~/.config/nvim/lua/config/lazy.lua_ looks like this:

```

    -- ~/.config/lua/config/lazy.lua

    local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
    if not (vim.uv or vim.loop).fs_stat(lazypath) then
      vim.fn.system({
        "git",
        "clone",
        "--filter=blob:none",
        "https://github.com/folke/lazy.nvim.git",
        "--branch=stable", -- latest stable release
        lazypath,
      })
    end
    vim.opt.rtp:prepend(lazypath)

    vim.g.mapleader = " " -- the leader key is used in many keymaps

    local plugins = {
        "nvim-lua/plenary.nvim",
        {"nvim-treesitter/nvim-treesitter", build = ":TSUpdate"},
        {"nvim-telescope/telescope.nvim", tag = '0.1.6',
            requires = { {"nvim-lua/plenary.nvim"}}},
        {"ThePrimeagen/harpoon", branch = "harpoon2",
            dependencies = {"nvim-lua/plenary.nvim"}},
        {"mbbill/undotree"},
        {"tpope/vim-fugitive"},
        --lsp configuration
            {"neovim/nvim-lspconfig"}, --lsp configs
            {"hrsh7th/cmp-nvim-lsp"}, -- autocompletion
            {"hrsh7th/nvim-cmp"}, --additional autocompletion
            {"L3MON4D3/LuaSnip", version = "v2.*", build = "make install_jsregexp", dependencies = {'saadparwaiz1/cmp_luasnip','rafamadriz/friendly-snippets'}}, --snippet engine
            {"williamboman/mason.nvim"}, --lsp package manager
            {"williamboman/mason-lspconfig.nvim"}, --lsp package manager configs
        --color scheme
        {'rebelot/kanagawa.nvim'},
        -- Rust programming
            {'mrcjkb/rustaceanvim', version = '^4', lazy = true, ft = {rust}},
            {'mfussenegger/nvim-dap'},
        -- Go programming
           {"ray-x/go.nvim", dependencies = {"ray-x/guihua.lua"},
               config = function()
                 require("go").setup()
               end,
               event = {"CmdlineEnter"}, ft = {"go", 'gomod'},
               lazy = false},
    }

    require("lazy").setup(plugins, {})

```

* * *

### Out-of-the-box alternative using LazyVim

“All of this configuration is too much work!” – you, probably.

We get it. You want to start writing code now without learning what a Lua table is or how to configure treesitter parsers. You still want a lightweight, fully-integrated development enviroment on Fedora Workstation and you love Vim motions. LazyVim is a great alternative.

LazyVim requires the installation of Neovim using the instructions above.

#### Stash your current configuration (optional)

If you have already configured Neovim but want to use LazyVim, stash your current confiration with the following commands:

```

    mv ~/.config/nvim{,.bak}
    mv ~/.local/state/nvim{,.bak}
    mv ~/.local/share/nvim{,.bak}
    mv ~/.cache/nvim{,.bak}

```

#### Load the starter

```

    ### clone starter repository locally to the ~/.config/nvim directory
    git clone https://github.com/LazyVim/starter ~/.config/nvim

```

Open Neovim using the _nvim_ command to see the new interface:

![][50]

The icons above will only be available if you install a nerd font like JetBrains-Mono.

```

    ### install jetbrainsmono and fontawesome
    sudo dnf install jetbrains-mono-fonts fontawesome-fonts

```

#### Language-specific setup

LazyVim makes it extremely easy to optimize for specific language development. Simply type _:LazyExtras_ to bring up the Extras configuration options.

![][51]

Scroll down the list or search the list with the _/_ (forward-slash) key to find your preferred language. (e.g. _lang.go_ , _lang.rust_ , _lang.python_ , _lang.typescript_ , _lang.haskell_ , etc.) and with the cursor over the line, press the _x_ key to enable that configuration.

### Conclusion

Whether you build a bespoke configuration to match your workflow or grab LazyVim for easy development, Fedora offers a reliable, leading-edge platform for software development, data analysis, research, and learning. Happy coding!

_:q!_

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/configuring-neovim-on-fedora-as-an-ide-and-using-lazyvim/

作者：[Bryar Topham][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/human-d3v/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/05/Neovim_on_Fedora-816x345.jpg
[2]: https://unsplash.com/@lookatviki?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-computer-keyboard-with-a-monitor-afG2ZF8h1OQ?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://fedoramagazine.org/wp-content/uploads/2024/05/app-menu.icon_-1024x713.png
[5]: https://github.com/folke/lazy.nvim
[6]: https://fedoramagazine.org/wp-content/uploads/2024/05/01-lazy-loaded-1024x731.png
[7]: https://fedoramagazine.org/wp-content/uploads/2024/05/workflow-1024x174.png
[8]: https://github.com/nvim-lua/plenary.nvim
[9]: https://github.com/nvim-treesitter/nvim-treesitter
[10]: https://github.com/nvim-telescope/telescope.nvim
[11]: https://github.com/ThePrimeagen/harpoon/tree/harpoon2
[12]: https://github.com/mbbill/undotree
[13]: https://github.com/tpope/vim-fugitive
[14]: https://github.com/williamboman/mason.nvim
[15]: https://github.com/hrsh7th/nvim-cmp
[16]: https://github.com/L3MON4D3/LuaSnip
[17]: https://github.com/Tsuzat/NeoSolarized.nvim
[18]: https://github.com/folke/tokyonight.nvim
[19]: https://github.com/NLKNguyen/papercolor-theme
[20]: https://github.com/rebelot/kanagawa.nvim
[21]: https://vimcolorschemes.com/
[22]: https://fedoramagazine.org/wp-content/uploads/2024/05/01-plugins-loaded-1024x734.png
[23]: https://fedoramagazine.org/wp-content/uploads/2024/05/kanagawa-1024x649.png
[24]: https://fedoramagazine.org/wp-content/uploads/2024/05/neosolar-1024x653.png
[25]: https://fedoramagazine.org/wp-content/uploads/2024/05/2024-05-22_07-48-39-1024x804.png
[26]: https://github.com/mrcjkb/rustaceanvim
[27]: https://github.com/mfussenegger/nvim-dap
[28]: https://github.com/mrcjkb/rustaceanvim?tab=readme-ov-file#books-usage--features
[29]: https://www.sourceware.org/gdb/
[30]: https://fedoramagazine.org/wp-content/uploads/2024/05/03-rust-code-action-1024x642.png
[31]: https://packages.fedoraproject.org/pkgs/python3.12/python3-devel/
[32]: https://packages.fedoraproject.org/pkgs/python-virtualenv/python3-virtualenv/
[33]: https://packages.fedoraproject.org/pkgs/python-pandas/python3-pandas/
[34]: https://packages.fedoraproject.org/pkgs/python3-numpy/
[35]: https://github.com/microsoft/pyright
[36]: https://fedoramagazine.org/wp-content/uploads/2024/05/python-repl.gif
[37]: https://bun.sh/
[38]: https://fedoramagazine.org/wp-content/uploads/2024/05/typescript.gif
[39]: https://github.com/pmizio/typescript-tools.nvim
[40]: https://developer.fedoraproject.org/tech/languages/go/go-installation.html
[41]: https://github.com/golang/tools/tree/master/gopls
[42]: https://github.com/mvdan/gofumpt
[43]: https://pkg.go.dev/golang.org/x/tools/cmd/goimports
[44]: https://github.com/fatih/gomodifytags
[45]: https://github.com/golangci/golangci-lint
[46]: https://github.com/cweill/gotests
[47]: https://github.com/ray-x/go.nvim
[48]: https://fedoramagazine.org/wp-content/uploads/2024/05/2024-05-21_09-55-50-1024x816.png
[49]: https://neovim.io/doc/user/options.html
[50]: https://fedoramagazine.org/wp-content/uploads/2024/05/2024-05-22_10-10-49-1024x885.png
[51]: https://fedoramagazine.org/wp-content/uploads/2024/05/2024-05-22_10-18-39-1024x911.png
