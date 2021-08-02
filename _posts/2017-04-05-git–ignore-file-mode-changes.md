---
bg_credential:
bg:            ""
layout:        post
title:         ""
crawlertitle:  ""
summary:       ""
date:          2017-04-05
categories:    posts
tags:          []
author:        "mwilczek.net"
references:
  "":
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
