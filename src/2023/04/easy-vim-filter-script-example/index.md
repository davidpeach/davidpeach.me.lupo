---
title: "Easy Vim filter script example"
date: "2023-04-22"
categories: 
  - "programming"
tags: 
  - "bash"
  - "command-line"
  - "linux"
  - "vim"
---

You can run any number of selected lines in Vim through any bash script and whatever you echo from that script will replace those selected lines.

## Comment filter script example

Super easy example to get the point across. I'm using PHP-style single line commenting for simplicity.

You can add an executable file with the following contents into a directory that is in your $PATH.

For me I'd save the file to "~/.local/bin/comment". "~/.local/bin" is a directory in my `$PATH` and I just name it "comment". Also make sure that the file is executable.

```
#!/usr/bin/bash
while read -r line; do
    line="// ${line}"
    echo "$line"
done
```

Then if you open an empty buffer in Vim and write some text in.

Lets say you write the following:

```
This is my text
```

Now with your cursor on that line, in NORMAL mode, press the key sequence "!!" (exclamation point pressed twice). That should add a small sequence to your Vim console that looks like this:

```
:.!
```

I believe this basically says:

1. ":" start command

3. "." on the current line

5. "!" and run this program (which we need to then enter ourselves)

The program is something you need to write after the "!". Any shell command you want to run in the Vim console must be preceeded by "!".

So providing that the comment script you added is indeed in your `$PATH`, you can complete the command to read like this in the Vim console:

```
:.!comment
```

And hit enter.

The script will loop through each of the selected lines (one in this case but works for multiple in VISUAL mode too) and replace the "line" with itself but preceeded by "// ".

This example is super basic (when it comes to bash that is) but whatever you can script in bash can be used in vim. In fact this is part of the UNIX philosophy - have small programs that do one thing and do it well, as well as making them interoperable.

Have fun.

_I've been watching lot's of videos on YouTube on a channel called "rwxrob", and the guy has ignited a love of bash scripting in me. So thanks for this and probably future bash-related posts will go to him._
