---
bg_credential: <a href="https://unsplash.com/@steve_j?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Steve Johnson</a> on <a href="https://unsplash.com/s/photos/bin?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "steve-johnson-Kr8Tc8Rugdk-unsplash.jpg"
layout:        post
title:         "Find what application uses your resources (*nix)"
crawlertitle:  "Find what application uses your resources (*nix) - lsof"
summary:       "lsof command"
date:          2016-11-14
categories:    posts
tags:          ['bash', 'kill', 'lsof', 'ports']
author:        "mwilczek.net"
references:
  "http://stackoverflow.com/a/3855359":
  "https://www.macobserver.com/tmo/article/terminal-using-lsof-when-files-wont-delete":
---

It happens sometimes, that some applications block certain port even though it shouldn’t doing so. There are many reasons like bugs, locks, poor optimization. In such cases desired action is to kill guilty process, but first it has to be found.

The same story applies to case when it’s impossible to delete file or remove device.

```bash
# Find process that uses certain port.
lsof -i tcp:3000

# Find process that uses file / disk / device / etc.
lsof [file]
```

Those commands give command name, pid, and other infos, but those two first are crucial. The easiest way from this point is to kill all processes.

```bash
lsof -i tcp:8000 | awk '{print $2;}' | tail -n +2 | xargs kill -kill

#sometimes sudo may be needed
lsof -i tcp:8000 | awk '{print $2;}' | tail -n +2 | xargs sudo kill -kill
```

Command tail help us skipping header.
