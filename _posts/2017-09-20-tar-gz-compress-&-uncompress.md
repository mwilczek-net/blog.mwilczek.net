---
bg_credential: <a href="https://unsplash.com/@fotograw?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Dmitriy Demidov</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "dmitriy-demidov-X41i5nIsVw4-unsplash.jpg"
layout:        post
title:         ".tar.gz – compress & uncompress"
crawlertitle:  ".tar.gz – compress & uncompress"
summary:       "Archive and compression"
date:          2017-06-17
categories:    posts
tags:          ['tar', 'gzip', '.tar.gz']
author:        "mwilczek.net"
references:
  "https://osxdaily.com/2012/04/05/create-tar-gzip/":
  "https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file#25348":
---

Quickly create tar.gz archive:

```bash
tar -cvzf tar_file_name.tar.gz ITEMS_TO_BE_COMPRESSED
```

`ITEMS_TO_BE_COMPRESSED` can be single file, single folder, or group of files.

Quick uncompress:

```bash
tar -xvzf tar_file_name.tar.gz
# Uncompressing to different folder.
tar -xvzf tar_file_name.tar.gz -C ./path/for/uncompressed/content
```

`./path/for/uncompressed/content` **should already exists**
