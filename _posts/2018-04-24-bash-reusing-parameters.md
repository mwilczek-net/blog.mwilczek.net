---
bg_credential: <a href="https://unsplash.com/@markusspiske?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Markus Spiske</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "markus-spiske-VO5w2Ida70s-unsplash.jpg"
layout:        post
title:         "Bash reusing parameters – BANG (!)"
crawlertitle:  "Bash reusing parameters – BANG (!)"
summary:       "!! &nbsp; !* &nbsp; !^ &nbsp; !$ &nbsp; !:0 &nbsp; !:n-m"
date:          2018-04-24
categories:    posts
tags:          ['bash', 'parameters', 'reuse', '!']
author:        "mwilczek.net"
references:
  "https://stackoverflow.com/questions/3371294/how-can-i-recall-the-argument-of-the-previous-bash-command":
  "https://ss64.com/bash/bang.html":
---

Bash allows us to reuse parameters or even whole command. It seams to be nothing, but in reality it helps a lot. Let’s start with examples.

Suppose, you have command like this:

```bash
apt-get --purge remove nginx
```

Command won’t work. You need admin privileges. Instead of typing sudo and whole command again, you can just type:

```bash
# Short way - use previous command as parameter
sudo !!

# Long - just for comparision
sudo apt-get --purge remove nginx

# Problem with connection? - try again whole last command
!!
```

Which do you prefer?

But it’s not only `sudo` case

```bash
# Create file and reuse its path
touch /home/user_name/documents/very/obscure/path/to/new/document/new_document_with_obscure_path.md
vim !$

# Or do hard work twice
touch /home/user_name/documents/very/obscure/path/to/new/document/new_document_with_obscure_path.md
vim /home/user_name/documents/very/obscure/path/to/new/document/new_document_with_obscure_path.md
```

## Docs

Not every option works with each BASH version. Just check what works in your environment.

```bash
!!    # run / reuse full command
!$    # run as a command / reuse last parameter
!^    # run as a command / reuse first parameter
!*    # run as a command / reuse all parameters
!:0   # run as a command / reuse previous command name
!:n   # run as a command / reuse n'th parameter
!:n-m # run as a command / reuse parameters form n to m
!:^-$ # run as a command / reuse all parameters
```
