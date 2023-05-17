---
title: "Using TMUX without prefixes"
date: "2023-04-13"
categories: 
  - "programming"
tags: 
  - "linux"
  - "terminal"
  - "tmux"
coverImage: "tmux.jpg"
---

Every tutorial / setup ive come across for TMUX uses a prefix when binding keys to actions.

The idea is that you hit your prefix combination, followed by another separate key, to perform an action. The default prefix is `Ctrl + b`, but you are free to remap it to whatever you want. I initially opted for `Ctrl + space`.

However, recently I've been looking for ways of improving and streamlining my workflow. To this end I'm trying to move away from using a prefix at all, and just binding actions to `alt+<key>`

So instead of creating a new window with `<prefix> c`, which would mean hitting "Control" and "space" for me, followed by "c", I have remapped this to just `alt+c` - No more prefix.

I know that the `ALT` key is used by other programs: for example in firefox `ALT+<number>` will switch tabs. But when I am in my TMUX session in the terminal, I don't care about firefox bindings, or any other program.

The code example below shows how my "new-window" binding would work, both with a prefix and without a prefix.

Note that the top example is already set in TMUX by default. This is for demonstration purposes only. :)

```
# Here the <prefix> is assumed by TMUX
# This is a TMUX default binding.
bind c new-window

# passing the "-n" flag to the bind command tells TMUX to not expect the <prefix> before.
# "M" here means "Meta" key, which in my case is the ALT key.
bind -n M-c new-window
```

For all the default bindings that I use, I have just created an "`ALT`" mapping for them.
