---
bg_credential: <a href="https://unsplash.com/@tvick?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Taylor Vick</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "taylor-vick-M5tzZtFCOfs-unsplash.jpg"
layout:        post
title:         "How to disconnect hanged ssh session?"
crawlertitle:  "How to disconnect hanged ssh session?"
summary:       "Just: enter tilde dot"
date:          2016-12-14
categories:    posts
tags:          ['ssh', 'kill']
author:        "mwilczek.net"
references:
  "https://www.cyberciti.biz/faq/openssh-linux-unix-osx-kill-hung-ssh-session/":
---

Some network issues makes ssh session hangs. Possible solutions are:

- close terminal,
- open new terminal and kill ssh process,
- wait,
- find a good solution.

First three options make us losing data, killing other ssh sessions or loosing our precious time. Simple solution, that helps us avoid possible inconvenience are two characters:

```bash
~ .
```

Tilde and dot is ssh’s command to kill session. But remember, it has to be placed immediately after new line character (press enter before).
