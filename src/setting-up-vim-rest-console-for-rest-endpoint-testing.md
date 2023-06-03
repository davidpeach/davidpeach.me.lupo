---
title: Setting up Vim Rest Console for REST endpoint testing
---

Vim Rest Console is a Vim plugin that enables you to send requests to REST endpoints from directly in Vim.

## Installation

Install the [vim-rest-console](https://github.com/diepm/vim-rest-console) package for Vim / Neovim with your chosen Vim package manager.

```
# Using Packer
use ({ 'diepm/vim-rest-console' })
```

Close and Reopen vim.

## Usage

Open an empty vim buffer and set filetype to `rest`:

```
:set ft=rest
```
