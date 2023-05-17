---
title: "My workflow for building an open-source project"
date: "2023-05-12"
categories: 
  - "programming"
tags: 
  - "git"
  - "github"
  - "programming"
  - "terminal"
  - "workflow"
---

Note: This is currently a brain dump.

## Pre-requisites

- The project I am working in is a git repository and exists in my Github account.

- I have installed gh (github cli tool).

## Workflow

1. I have an idea for a feature

3. Open terminal and run `gh issue create`

5. Follow the prompts to enter the issue **title** and optional **description** and any metadata. Hit submit.

7. Checkout a feature branch with `git checkout -b feature/my-feature-idea`

9. **_At least one commit_** needs to be added before a draft PR can be created.

11. Push the branch with `git push`.

13. Run `gh issue list` and make note of the id for the correct issue.

15. Create a new PR with `gh pr create --draft`

17. Follow the prompts to enter the PR **title** and a **description that contains "closes #ID\_OF\_ISSUE"**.  
    So if my issue was the fifth one for this repo, I'd add "closes #5".

19. Submit the draft PR.

21. Continue working on the issue until ready for review.

23. TBC
