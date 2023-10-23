---
bg_credential: <a href="https://unsplash.com/@jentheodore?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Jen Theodore</a> on <a href="https://unsplash.com/photos/corn-cob-lot-4ZUo1sS8FyA?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
bg:            "jen-theodore-4ZUo1sS8FyA-unsplash.jpg"
layout:        post
title:         "Remove kerenels"
crawlertitle:  "Remove kerenels for Linux Debian"
summary:       "Remove kerenels for Linux Debian"
date:          2023-10-23
categories:    posts
tags:          ['linux', 'debian', 'kernel']
author:        "mwilczek.net"
references:
  "https://tweenpath.net/the-safest-way-to-clean-up-boot-partition-in-debian-or-ubuntu/":
  "https://www.tecmint.com/remove-old-kernel-in-debian-and-ubuntu/":
  
---

Every time Debian installs new kernel, old ones are not removed. These days we have large capacity hard drives.
So it may fell like not important issue. Unfortunately, hard drive is divided into partitions with limited space.
One of them is `/boot` partition which, among the others, store configs and other files that allows booting
different kernels. The more kernels we have, the more space is required for `/boot` partition.

To deal with very limited space of `/boot`, we can remove unused kernels.

Before start prepare backup!

First let’s check used and installed kernels:
```sh
# currently used kernel version
uname -r
# currently used kernel name and version
uname -sr

# all available kernels
dpkg --list 'linux-image*'
```

Example list of kernels:
```
    Name                               Version      Architecture Description
+++-==================================-============-============-===================================
rc  linux-image-6.4.0-3-amd64          6.4.11-1     amd64        Linux 6.4 for 64-bit PCs (signed)
un  linux-image-6.4.0-3-amd64-unsigned <none>       <none>       (no description available)
rc  linux-image-6.4.0-4-amd64          6.4.13-1     amd64        Linux 6.4 for 64-bit PCs (signed)
un  linux-image-6.4.0-4-amd64-unsigned <none>       <none>       (no description available)
ii  linux-image-6.5.0-1-amd64          6.5.3-1      amd64        Linux 6.5 for 64-bit PCs (signed)
un  linux-image-6.5.0-1-amd64-unsigned <none>       <none>       (no description available)
ii  linux-image-6.5.0-2-amd64          6.5.6-1      amd64        Linux 6.5 for 64-bit PCs (signed)
un  linux-image-6.5.0-2-amd64-unsigned <none>       <none>       (no description available)
ii  linux-image-amd64                  6.5.6-1      amd64        Linux for 64-bit PCs (meta-package)
un  linux-image-generic                <none>       <none>       (no description available)
```

Removing unwanted kernels. ***Run as admin!***
```sh
apt remove --purge linux-image-6.4.0-3-amd64
apt remove --purge linux-image-6.4.0-4-amd64
apt remove --purge linux-image-6.5.0-1-amd64

# clean leftovers
apt autoremove

# push config to grub - if using grub
update-grub
```

Now reboot system and pray.
