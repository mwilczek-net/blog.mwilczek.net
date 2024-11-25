---
bg_credential: <a href="https://unsplash.com/@priscilladupreez?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Priscilla Du Preez 🇨🇦</a> on <a href="https://unsplash.com/photos/a-person-holding-a-book-in-their-hands-t_OgJSGXSYc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
bg:            "priscilla-du-preez-t_OgJSGXSYc-unsplash.jpg"
layout:        post
title:         "GIT change commit author"
crawlertitle:  "GIT - Change commit author"
summary:       "Change author of different commits"
date:          2024-11-25
categories:    posts
tags:          ['git', 'history', 'commit', 'author']
author:        "mwilczek.net"
references:
  "https://stackoverflow.com/a/43231587":
    title: "More variants"
---

Sometimes, if we forget to correctly cofnigure GIT, default (or misconfigured) author credentials
are saved into one or more commits.

Sometimes it is not an issue, but for some projects, external repository may disallow pushing.

Below there are few methods of how to repari commit author.

## Changing author of the last commit

```bash
# Just reset to current default
git commit --amend --reset-author --no-edit

# Reset to current default, but let me edit commit message
git commit --amend --reset-author

# Just set to given value
git commit --amend --author "Foo Bar <foo.bar@net.com>" --no-edit

# Set to given value, but let me edit commit message
git commit --amend --author "Foo Bar <foo.bar@net.com>"
```

## Changing author of multiple commits
```bash
# Reset last 10 commits to default author
git rebase -i HEAD~10 --exec "git commit --amend --reset-author --no-edit"

# Reset last 10 commits to given value
git rebase -i HEAD~10 --exec "git commit --amend --author 'Foo Bar <foo.bar@net.com>' --no-edit"
```
