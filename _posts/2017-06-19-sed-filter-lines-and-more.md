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
  "https://www.wyzant.com/resources/answers/646117/bash-tool-to-get-nth-line-from-a-file":
---

## Print `nth` line of an input

Use a pipe to generate multi-line input:

```bash
# print the 4th line of the reflog
git reflog | sed -n -e "4p"
```

`sed` can read a file directly as well:

```bash
# print 5th line of a file
sed -n -e "5p" my_log_beautiful_file.txt
```

## Print or skip range of lines

While programming, I often search for object names across many projects.
When I find the desired files, I often want to perform operations on a subset of the results.
Let's say I want to open 100 files while skipping the first 5.

Let's start by finding all `*.java` and `*.xml` files that contain the strings `foo` and `bar`.
Typically, my spell looks like this:

```bash
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar'
```

Then apply filtering:
```bash
# filter
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar' | sed '5,105!d'

# open files with kwrite
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar' | sed '5,105!d' | xargs kwrite
```

Meaning of the sed expression:
- `5` - start at the 5th line
- `105` - stop at the 105th line
- `!` - negate the address range
- `d` - delete matching lines, print what is left

Similarly, if you want to keep everything except 100 lines starting from the 5th, then just remove `!`.

```bash
find . -iname '*.java' -o -iname '*.xml' | xargs grep -irl 'foo' | xargs grep -irl 'bar' | sed '5,105d'
```
