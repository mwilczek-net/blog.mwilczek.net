---
bg_credential: Photo by <a href="https://unsplash.com/@carolinachadwick?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash" target="_blank">Carolina Pimenta</a> on <a href="https://unsplash.com/photos/long-exposure-photography-of-white-smoke-hBsOq3RcndM?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash" target="_blank">Unsplash</a>
bg:            "carolina-pimenta-hBsOq3RcndM-unsplash.jpg"
layout:        post
title:         "GIT inspect ignore rules"
crawlertitle:  "Inspect ignore rules in GIT"
summary:       "Check which rule ignores files and list them all"
date:          2025-03-26
categories:    posts
tags:          ['git', '.gitignore', 'check-ignore']
author:        "mwilczek.net"
references:
  "https://stackoverflow.com/a/467053":
  "https://git-scm.com/docs/git-status":
    title: "GIT status documentation"
  "https://git-scm.com/docs/git-check-ignore":
    title: "GIT check-ignore documentation"
---

For complex project structure, may happen that multiple '.gitignore' files or complex rules introduces unexpected ignore behaviour.
Fortunately GIT provides methods to detect which rule affects file and can list all currently ignored files (or directories).

## List all currently ignored files and folders

```bash
git status --ignored
```

## Check which rule affects file

```bash
# Check single file
git check-ignore -v -- path/to/my/file

# or inspect all files in given directory
git check-ignore -v -- *
```