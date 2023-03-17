---
bg_credential: <a href="https://unsplash.com/de/@fredasem?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Freddy Kearney</a> on <a href="https://unsplash.com/photos/enkfvvZkKv0?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "freddy-kearney-enkfvvZkKv0-unsplash.jpg"
layout:        post
title:         "Clear shell history"
crawlertitle:  "How to clear history for different shells"
summary:       "BASH: history -c | ZSH: history -p"
date:          2023-03-16
categories:    posts
tags:          ['cmd', 'terminal', 'shell', 'bash', 'zsh']
author:        "mwilczek.net"
references:
  "https://unix.stackexchange.com/a/607556":
  "https://ss64.com/bash/history.html":
  "https://linux.die.net/man/1/zshbuiltins":
  
---

## bash

```shell
history -c
```

## zsh

```shell
history -p
```