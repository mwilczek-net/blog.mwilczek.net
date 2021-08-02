---
bg_credential: <a href="https://unsplash.com/@ronwhitaker?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Ron Whitaker</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "ron-whitaker-jH_-L1C_o6Q-unsplash.jpg"
layout:        post
title:         "Git – ignore file mode changes"
crawlertitle:  "Git – ignore file mode changes"
summary:       "When jumiping from OS to OS"
date:          2017-04-05
categories:    posts
tags:          ['git', 'file mode', 'file system']
author:        "mwilczek.net"
references:
  "https://stackoverflow.com/questions/1580596/how-do-i-make-git-ignore-file-mode-chmod-changes/1580644#1580644":
  "https://git-scm.com/docs/git-config#Documentation/git-config.txt-corefileMode":
---

Dealing with different operating systems and different file systems, may causes with unwanted file mode changes. For example file mode `766`, which is correct for Unixes (and similar), will be converted to `666` when fetching code to FAT file system.

```bash
git config core.fileMode false # configuration for current repo
git config --global core.fileMode false # global configuration
```

Given commands ignores file mode changes. Of course it may affect you code / application in may ways, but if you need FAT (or other weird file systems)…
