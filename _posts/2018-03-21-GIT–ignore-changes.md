---
bg_credential:
bg:            ""
layout:        post
title:         "Bash I/O redirection"
crawlertitle:  "Bash I/O redirection"
summary:       "git &mdash; ignore changes"
date:          2018-03-21
categories:    posts
tags:          ['git', '.gitignore', 'git update-index']
author:        "mwilczek.net"
references:
  "https://stackoverflow.com/questions/1753070/how-do-i-configure-git-to-ignore-some-files-locally":
  "https://stackoverflow.com/a/13631525":
  "https://fallengamer.livejournal.com/93321.html":
  "https://git-scm.com/docs/git-update-index":
---

If there are changes that you need to ignore, but you can’t or doesn’t want to edit neither
`.gitignore_global` nor `.gitignore` files, there is still hope for you. In repository there is file:

```bash
.git/info/exclude
```

That file has the same structure and function as `.gitignore`, but version from one repository,
doesn’t affect other repositories.

But if file is already tracked, there is another ways of ignoring changes:

```bash
git update-index --skip-worktree <files>
git update-index --assume-unchanged <files>
```

Difference is that `--skip-worktree` means for git: "don’t touch, because developer should change this
file for his needs". While `--assume-unchanged` means for git: "you don’t have to check files,
because it shouldn’t be changed by developer".

And undo:

```bash
git update-index --no-skip-worktree <files>
git update-index --no-assume-unchanged <files>
```

This will help you finding what files are marked with `git update-index --skip-worktree` and
`git update-index --assume-unchanged` respectively:

```bash
git ls-files -v | grep '^S'
git ls-files -v | grep '^h'
```
