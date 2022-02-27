---
bg_credential: <a href="https://unsplash.com/@ripato?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Ricardo Gomez Angel</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Unsplash</a>
bg:            "ricardo-gomez-angel-GsZLXA4JPcM-unsplash.jpg"
layout:        post
title:         "sed &mdash; filter lines and more"
crawlertitle:  "sed &mdash; filter lines and more"
summary:       "Filter shell input"
date:          2017-06-17
categories:    posts
tags:          ['bash', 'grep', 'sed']
author:        "mwilczek.net"
references:
  "https://linux.die.net/man/1/sed":
---

While programming I often look for different objects and names across many projects.
When I find desired files, I’d like to perform some operations on sub group of results.
Lets say open 100 files but skipping first 5.

Lets start with just finding all “*.java” and “*.xml” files with “foo” and “bar” strings.
Generally, my spell looks similar to this:

```bash
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar'
```

Then filtering
```bash
# filter
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar' | sed '5,105!d'

# open files with kwrite
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar' | sed '5,105!d' | xargs kwrite
```

Meaning of sed’s parameters:
- `5` – take lines from 5th line
- `105` – take lines to 105th line
- `!` – take everything except from 5th to 105th line
- `d` – delete what you took and print everything else

Similarly, if you want to keep everything except 100 lines starting form 5th, then just drop ‘!’

```bash
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar' | sed '5,105d'
```
