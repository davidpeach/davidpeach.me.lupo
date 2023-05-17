---
title: "Setting up Neovim for clojure development"
date: "2023-01-07"
tags: 
  - "clojure"
  - "neovim"
  - "programming"
  - "workflow"
---

I have decided to start learning a functional style programming language, as I have never done so before. Both as a way to get experience with development styles foreign to my own, and to hopefully compliment my current work.

On top of this am going to try and do something that I wished I'd done when learning PHP -- keep a record and share my learnings as I pick things up.

This is the first entry in that series -- setting up my editor of choice. And of course it has to be the very best editor available: Neovim.

ensure junegunn/fzf installed

Add following to packer.vim

```
use "Olical/conjure"
use "junegunn/fzf"
use {
    "guns/vim-sexp",
    ft = 'clojure',
}
use {
    "liquidz/vim-iced",
    ft = 'clojure',
}
```

Add vim iced bin folder to $PATH

```
export PATH=$HOME/.local/share/nvim/site/pack/packer/opt/vim-iced/bin:$PATH
```

check iced is working with `iced version`.

cd into a "lein" project and then call `iced repl`.

to be continued...
