---
title: "How I use vimwiki in neovim"
date: "2023-05-12"
categories: 
  - "uncategorised"
tags: 
  - "vim"
---

Please view the official [Vimwiki Github repository](https://github.com/vimwiki/vimwiki) for up-to-date details of Vimwiki usage and installation. This page just documents my own processes at the time.

## Installation

Add the following to `plugins.lua`

```
use "vimwiki/vimwiki"
```

Run the following two commands separately in the neovim command line:

```
:PackerSync
:PackerInstall
```

Close and open Neovim.

## Initalizing Vimwiki

pressing `<leader>ww` for the first time will ask you if it should create a directory at `~/vimwiki`. Press `y` and `enter`.

You are presented with a blank buffer which is your Vimwiki index.

Please checkout the Github repo linked above for functionality.

## How I am using Vimwiki

I have 2 separate wikis set up in my Neovim.

One for personal and one for private.

I set these up by adding the following in my dotfiles, at the following position: `$NEOVIM_CONFIG_ROOT/after/plugin/vimwiki.lua`

```
vim.cmd([[
  let wiki_1 = {}
  let wiki_1.path = '~/vimwiki/personal/'
  let wiki_1.html_template = '~/vimwiki/personal_html/'
  let wiki_2 = {}
  let wiki_2.path = '~/vimwiki/private/'
  let wiki_2.html_template = '~/vimwiki/private_html/'
  let g:vimwiki_list = [wiki_1, wiki_2]
  call vimwiki#vars#init()
]])
```

The `path` keys tell vimwiki where to plave the root `index.wiki` file for each wiki you configure.

The `html_template` keys tell vimwiki where to place the compiled html files (when running the `:VimwikiAll2HTML` command).

I keep them separate as I am considering having a custom command to deploy my personal (public) wiki to my server at a public URL.

When I want to open my personal wiki I enter `1<leader>ww` and when I want to open my private one I enter `2<leader>ww`.
