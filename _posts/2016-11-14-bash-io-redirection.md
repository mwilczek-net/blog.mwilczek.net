---
bg_credential: <a href="https://unsplash.com/@amfiloxia_68?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">George Girnas</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:           "george-girnas-6RTn6HZD-RI-unsplash.jpg"
layout:       post
title:        "Bash I/O redirection"
crawlertitle: "Bash I/O redirection"
summary:      "Redirect input and output in Bash"
date:         2016-11-14 09:35:44 +0100
categories:   posts
tags:         ['Bash']
author:       "mwilczek.net"
---

I/O Redirection allows us to change destination of data. Reasons to use it are countless. Some of them are clean output when looking for files. Commands like:

```
find / -iname '*.java'
grep -irl 'Hello World' /
```

Produces huge amount of errors when we try to look into directory (or files) without proper permission.

```
find: /.DocumentRevisions-V100: Permission denied
find: /.fseventsd: Permission denied
find: /.Spotlight-V100: Permission denied
find: /.Trashes: Permission denied
```

Other reason can be saving different outputs to different log files or advance piping.

Most of uses:
```
# Hide / remove error stream
command 2>/dev/null

# Combine output and error stream as one output stream
command 2>&1
```
