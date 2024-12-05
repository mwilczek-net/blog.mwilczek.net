---
bg_credential: <a href="https://unsplash.com/@hirmin?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Max Kleinen</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Unsplash</a>
bg:            "max-kleinen-lMiYuow_KZE-unsplash.jpg"
layout:        post
title:         "AWK split input by&hellip;"
crawlertitle:  "AWK split input by char, string or regex"
summary:       "By default AWK split input by white chars"
date:          2021-11-28
categories:    posts
tags:          ['awk', 'regex', 'split', 'report']
author:        "mwilczek.net"
references:
  "https://unix.stackexchange.com/questions/106243/awk-split-parameter-by-char":
  "http://www.gnu.org/software/gawk/manual/html_node/Field-Separators.html":
  "https://linux.die.net/man/1/awk":
---

`awk` is designed to process text for reports. Let's think about different methods of splitting text.

## Default behaviour

Split by white characters and take second part

```bash
echo 'what is first part what IS second part' | awk '{print $2}'
is
```

Awk prints second word `is`

## Split by string - it is regex but lets keep it step by step

To set splitting string use `-F` parameter. Lets split by 'is' (small letters)

```bash
echo 'what is first part what IS second part' | awk -F 'is' '{print $2}'
 first part what IS second part
```

When `field` separator was set to `is` (case sensitive) result was: ` first part what IS second part`

Now let's split by `IS` (big letters).

```bash
echo 'what is first part what IS second part' | awk -F 'IS' '{print $2}'
 second part
```

Right now we only get ` second part` as second field.

## Split by regex

Now let's split by `is` but, case insensitive.

### Command parameter

```bash
echo 'what is first part what IS second part' | awk -F '[Ii][Ss]' '{print $2}'
 first part what
```

Due to used regex, whole line was splitted into 3 fields. Where second field was: ` first part what `.
Both `IS` and `is` was interpreted as field separator

### Syntax

The same but lets use syntax instead of parameter

```bash
echo 'what is first part what IS second part' | awk 'BEGIN  {FS="[Ii][Ss]"}; {print $2}'
 first part what
```

## Split by position of string and format

`awk` allows also ussage of `substr` method and can find possition of string.

```bash
echo 'Lay me down Let the only sound Be the overflow Pockets full of stones' | awk '{p=index($0,"Be");print "First part of line: \"", substr($0,0,p-1) "\",\nSecond part of line: \"", substr($0,p), "\""}'
First part of line: " Lay me down Let the only sound ",
Second part of line: " Be the overflow Pockets full of stones "
```

## Use last element of split string

Variable `$NF` represent last chunk

```bash
echo 'what is first part what IS second part' | awk -F '[Ii][Ss]' '{print $NF}'
  second part
```
