---
title: Git Worktrees from the trenches
date: 6th June 2023
---

Ever since I saw The Primeagen's video on Git Worktrees I wanted to switch over.

However, when you are working day to day in the same codebase for your day job, it can be tricky to switch everything over to another way of working with git.

But I have took the plunge.

I re-cloned mt work's repository down, using the `--bare` flag:

```
git clone --bare https://git.whereever/company/repo-name.git
```

Then I "checkout" the master branch as a worktree:

```
git worktree add master
```

## Usage with docker and docker compose

We use docker compose for setting up the codebase locally, which I anticipated making it difficult to work with worktrees.

... tbc...
