---
bg_credential: <a href="https://unsplash.com/@pedrotheartist?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Pedro Forester Da Silva</a> on <a href="https://unsplash.com/photos/a-bunch-of-pipes-are-lined-up-in-a-row-tkfJqN9Lu9Q?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
bg:            "pedro-forester-da-silva-tkfJqN9Lu9Q-unsplash.jpg"
layout:        post
title:         "Pipes in shell"
crawlertitle:  "Joining programs with pipies in shell"
summary:       "Joining programs with pipes"
date:          2018-08-07
categories:    posts
tags:          ['bash', 'zsh', 'shell', 'pipelines']
author:        "mwilczek.net"
references:
  "https://unix.stackexchange.com/questions/14270/get-exit-status-of-process-thats-piped-to-another":c
---

Shells allows easy forwarding of output form one program to input of another program. It is also available in other languages. General term for such phenomena is `piping` or `pipelining`.

## Simple pipes:

```shell
# Print all "a" from random generator
cat /dev/random | grep 'a'

# Delete all local branches from git, except current:
git branch | grep -v '*' | xargs git branch -D
# Or print instead of deleting
git branch | grep -v '*' | xargs echo git branch -D
```

## Error detection

### Simply result of last command

By default error code stored in `$?` variable is result of last command used in pipie. If previous command fails, we need to use more sophisticated method.

```shell
not-existing-command
# result is different than 0
echo "$?"

not-existing-command | cat "test" | grep "t"
# result is 0, which is false positive
echo "$?"
```

### `PIPESTATUS` variable

For complex cases shells have dedicated variable:
- `PIPESTATUS` - bash, indexed form `0`
- `pipestatus` - zsh, indexed form `1`

**BASH**
```shell
not-existing-command | cat "test" | grep "t"
echo "${PIPESTATUS[0]} ${PIPESTATUS[1]}"
# result: "127 0 0"
```

**ZSH**
```shell
not-existing-command | cat "test" | grep "t"
echo "${pipestatus[1]} ${pipestatus[2]}"
# result: "127 0 0"
```
