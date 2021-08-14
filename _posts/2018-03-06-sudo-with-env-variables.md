---
bg_credential: <a href="https://unsplash.com/@markusspiske?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Markus Spiske</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "markus-spiske-uPXs5Vx5bIg-unsplash.jpg"
layout:        post
title:         "Sudo with env variables"
crawlertitle:  "Sudo with env variables"
summary:       "Set variables in nev context"
date:          2018-03-06
categories:    posts
tags:          ['bash', 'sudo', 'env']
author:        "mwilczek.net"
---

Sudo command allows us running command as other user. Some commands or programs relay on environment
variables. There is no problem if those variables are set properly. Situation complicates when required
variables are not set or have other values than required.

In such cases, it is possible to create wrapping script that will setup environment and ten execute
desired command. Let’s be hones, no one want’s to write wrapper to run simple command once.
In some systems, it may be hard to create such script. Fortunately, sudo allows us to setup env variables
and assign them proper values. Just keep in mind, that expressions will be evaluated in current user’s scope
before executing command.

```bash
sudo VARIABLE_1=$value_for_variable_1 VARIABLE_2=$value_for_variable_2 command
```

It can also forward variables for new bash session.

```bash
sudo VARIABLE_1=$value_for_variable_1 VARIABLE_2=$value_for_variable_2 bash
# now you have root privileges and can use $VARIABLE_1 and $VARIABLE_2
```

If you need to pass parameters to command as it's parameters you can use alias:

```bash
alias sudo_spell="sudo command $var1 $var2 $var3"
sudo_spell
```

Above code uses variables and it's values in current scope (scope of a user that invokes sudo command).
Why? Because, `alias sudo_spel` is created in current context, and while creating alias, bash replace
variables with current values. So, when you execute sudo_spell, you execute command which has no variables,
but values that was unwrapped at a time when alias was created.
