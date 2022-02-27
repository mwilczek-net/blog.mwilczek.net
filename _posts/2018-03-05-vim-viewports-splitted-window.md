---
bg_credential: <a href="https://unsplash.com/@hngstrm?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Henry & Co.</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Unsplash</a>
bg:            "henry-co-K4GqdInyBQI-unsplash.jpg"
layout:        post
title:         "VIM viewports &mdash; splitted window"
crawlertitle:  "VIM viewports &mdash; splitted window"
summary:       "Turning VIM into IDE"
date:          2018-03-05
categories:    posts
tags:          ['vim']
author:        "mwilczek.net"
references:
  "https://www.linux.com/training-tutorials/vim-tips-using-viewports/":
  "https://benaiah41.wordpress.com/2009/02/21/resizing-vertical-viewports-in-vim/":
---

Vim seams to be simple and without many features. But it’s just false first impression. One of “hidden” feature is splitted window.

By default new viewport shows file visible in current viewport.

Splitting:
- **`:sp`**, **`:split`** &mdash; splits window horizontaly
- **`:sp filename`**, **`:split filename`** &mdash; splits window horizontaly and opens `filename`
- **`:12 sp`**, **`:12 split`** &mdash; splits window horizontaly with heigth = `12 lines`
- **`:vsp`**, **`:vsplit`** &mdash; splits verticaly
- **`:vsp filename`**, **`:vsplit filename`** &mdash; splits verticaly and opens `filename`
- **`:12 vsp`**, **`:12 vsplit`** &mdash; splits verticaly with width = `12 chars`

Working with splitted view:
- **`Ctrl-w Ctrl-w`** &mdash; moves between Vim viewports.
- **`Ctrl-w j`** &mdash; moves focus one viewport down.
- **`Ctrl-w k`** &mdash; moves focus one viewport up.
- **`Ctrl-w h`** &mdash; moves focus one viewport to the left.
- **`Ctrl-w l`** &mdash; moves focus one viewport to the right.
- **`Ctrl-w =`** &mdash; tells Vim to resize viewports to be of equal size.
- **`Ctrl-w –`** &mdash; shorten current viewport by one line.
- **`Ctrl-w +`** &mdash; enlarge current viewport by one line.
- **`Ctrl-w >`** &mdash; widen current viewport by one char.
- **`Ctrl-w <`** &mdash; decrease width of current viewport by one char.
- **`Ctrl-w q`** &mdash; will close the active viewport.
- **`Ctrl-w r`** &mdash; will rotate all viewports to the right / down.
- **`Ctrl-w R`** &mdash; will rotate all viewports to the left / up.
