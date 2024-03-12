---
bg_credential: <a href="https://unsplash.com/@vinikhill?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">NIKHIL</a> on <a href="https://unsplash.com/photos/a-red-and-black-background-with-a-circular-design-pThIEv416pE?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
bg:            "nikhil-pThIEv416pE-unsplash.jpg"
layout:        post
title:         "BASH Loops"
crawlertitle:  "Looping in Bash"
summary:       "While | For"
date:          2024-02-22
categories:    posts
tags:          ['bash', 'loop', 'for', 'while']
author:        "mwilczek.net"
references:
  "https://www.cyberciti.biz/faq/bash-while-loop/":
  "https://www.cyberciti.biz/faq/bash-for-loop/":
  "https://linuxhint.com/for-loops-zsh-script/"
    title: "How to Do a for loop in ZSH"

---

Bash supports both `while` and `for` loop. Each has some variants to help us do our work better!

## Control statements

Besides loop condition, both `while` and `for` loop, undesrtands common control commands:

- `break` - finish loop execution immediately
- `continue` - jump to next iteration **now**

## While loop

### While loop with condition

```bash
foo=1
while [ $x -le 10 ]
do
  echo "Iteration ${foo}"
  foo=$(( $foo + 1 ))
done
```

### Dead while loop

Loop without condition is a dead loop

```bash
while :
do
	echo "I' the DEAD LOOP!"
done

echo "Unreachable code"
```

Unless there is a break in it


```bash
while :
do
	break
    echo "Unreachable code"
done

echo "I'm free!"
```

## For loop

### With explicit list of items

```bash
for i in 1 2 3 4 5 6 7 8 9 10
do
   echo "Iteration ${i}"
done
```

### For loop with range

```bash
for i in {1..10}
do
    echo "Iteration ${i}"
done
```

every third element

```bash
for i in {1..10..3}
do
    echo "Iteration ${i}"
done
```

### C style! 💃

```bash
for (( i=1; i<=10; i++ ))
do
   echo "Iteration ${i}"
done
```

### Dead loop again!

```bash
for (( ; ; ))
do
	echo "I' the DEAD LOOP!"
done

echo "Unreachable code"
```

But we can use `break` just like in `while` loop