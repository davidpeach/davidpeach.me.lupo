---
title: "How I organize my Neovim configuration"
date: "2023-01-15"
categories: 
  - "programming"
tags: 
  - "neovim"
  - "web-development"
coverImage: "2023-01-25-130915_2168x817_scrot.png"
---

The entry point for [my Neovim Configuration](https://github.com/davidpeach/.dotfiles/tree/main/nvim/.config/nvim) is the `init.lua` file.

## Init.lua

My entrypoint file simply requires three other files:

```
require 'user.plugins'
require 'user.options'
require 'user.keymaps'
```

The `**user.plugins**` file is where I'm using [Packer](https://github.com/wbthomason/packer.nvim) to require plugins for my configuration. I will be writing other posts around some of the plugins I use soon.

The `**user.options**` file is where I set all of the Neovim settings. Things such as mapping my leader key and setting number of spaces per tab:

```
vim.g.mapleader = " "
vim.g.maplocalleader = " "

vim.opt.expandtab = true
vim.opt.shiftwidth = 4
vim.opt.tabstop = 4
vim.opt.softtabstop = 4

...etc...
```

Finally, the `**user.keymaps**` file is where I set any general keymaps that aren't associated with any specific plugins. For example, here I am remapping the arrow keys to specific buffer-related actions:

```
-- Easier buffer navigation.
vim.keymap.set("n", "<Left>", ":bp<cr>", { noremap = true, silent = true })
vim.keymap.set("n", "<Right>", ":bn<cr>", { noremap = true, silent = true })
vim.keymap.set("n", "<Down>", ":bd<cr>", { noremap = true, silent = true })
vim.keymap.set("n", "<Up>", ":%bd<cr>", { noremap = true, silent = true })
```

In that example, the **left** and **right** keys navigate to previous and next buffers. The **down** key closes the current buffer and the **up** key is the nuclear button that closes all open buffers.

## Plugin-specific setup and mappings

For any plugin-specific setup and mappings, I am using Neovim's "after" directory.

Basically, for every plugin you install, you can add a lua file within a directory at `./after/plugin/` from the root of your Neovim configuration.

So for example, to add settings / mappings for the "vim-test" plugin, I have added a file at: `./after/plugin/vim-test.lua` with the following contents:

```
vim.cmd([[
  let test#php#phpunit#executable = 'docker-compose exec -T laravel.test php artisan test'
  let test#php#phpunit#options = '--colors=always'
  let g:test#strategy = 'neovim'
  let test#neovim#term_position = "vert botright 85"
  let g:test#neovim#start_normal = 1
]])

vim.keymap.set('n', '<Leader>tn', ':TestNearest<CR>', { silent = false })
vim.keymap.set('n', '<Leader>tf', ':TestFile<CR>', { silent = false })
vim.keymap.set('n', '<Leader>ts', ':TestSuite<CR>', { silent = false })
vim.keymap.set('n', '<Leader>tl', ':TestLast<CR>', { silent = false })
vim.keymap.set('n', '<Leader>tv', ':TestVisit<CR>', { silent = false })
```

This means that these settings and bindings will only be registered after the vim-test plugin has been loaded.

I used to just have extra required files in my main init.lua file, but this feels so much more cleaner in my opinion.

Update: 9th February 2023 -- when setting up Neovim on a fresh system, I notice that I get a bunch of errors from the after files as they are executing on boot, before I've actually installed the plugins. I will add protected calls to the plugins soon to mitigate these errors.
