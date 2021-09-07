---
bg_credential: <a href="https://unsplash.com/@amir_v_ali?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">amirali mirhashemian</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "amirali-mirhashemian-kiH-RBm08NQ-unsplash.jpg"
layout:        post
title:         "BASH & multithreading"
crawlertitle:  "Multithreading with BASH"
summary:       "If you need to perform two or more time consuming jobs, and these jobs can be run independently, you can still use Bash"
date:          2018-04-01
categories:    posts
tags:          ['bash', 'multithread', 'subprocess']
author:        "mwilczek.net"
references:
  "https://stackoverflow.com/questions/4549489/can-i-change-the-name-of-nohup-out":
    "More about nohup variations"
---

If you need to perform two or more time consuming jobs, and these jobs can be run independently,
you can still use BASH.

## Just bash

Bash allows running scripts, programs and functions as background tasks. Also, Bash provides joining mechanism. First running tasks in background.

```bash
function task_x {
    // time consuming task x
}

function task_y {
    // time consuming task y
}

task_x &
task_y &
```

Adding a lone `&` sign will run command as background task. Such command will end immediately
after starting task in background, and allows running next command. **Background task will be
terminated if session is closed.**

If there is need for synchronized work, use `wait` method.

```bash
function task_x {
    // time consuming task x
}

function task_y {
    // time consuming task y
}

task_x &
pid_x=$!

task_y &
pid_y=$!

wait $pid_x
wait $pid_y
```

`$!` returns pid of last background task, which was stared by current thread.
Knowing pid opens wide range of options

`wait` command waits until end of task with given pid. If thread ended before wait command,
current thread won't wait, but will obtain data.

Important thing: `wait` returns exit code, returned by thread.

## Command (or sometimes built-in function) – nohup

Presented multithreading has one downside (or not, depending on your needs). If terminal get closed or killed, then all subprocesses will die too. If screen-like behaviour is needed, nohup command enters stage.

```bash
nohup time_consuming_task
```

And, by default, result will be saved to `nohup.out` text file. Now you can close terminal.

`nohup` command saves output to `nohup.out` file. If you need other, you can change name using:

```bash
nohup time_consuming_task > output_file &
```

When closing bash session you may get warn, that background task is running. Don’t worry it will finish everything as expected and print output to given file.

Unfortunately, syntax with different output file may not work in some environments.

## screen

For tasks, that should work even when terminal window is closed, please consider using `screen`.
