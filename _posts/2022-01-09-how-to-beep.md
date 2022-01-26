---
bg_credential: <a href="https://unsplash.com/@cbarbalis?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Chris Barbalis</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "chris-barbalis-PSYliyPf7yA-unsplash.jpg"
layout:        post
title:         "How to beep"
crawlertitle:  "How to beep in CMD"
summary:       "Ring the bell with CMD / Terminal"
date:          2022-01-09
categories:    posts
tags:          ['cmd', 'terminal', 'beep', 'bell', 'ring', 'notification']
author:        "mwilczek.net"
references:
  "https://discover.hubpages.com/technology/How-to-Make-a-CMD-Beep-Sound-With-Your-Computer":
  "https://superuser.com/questions/969080/how-to-ring-the-system-bell-from-command-line":
---

If there is a need for user of a script to react when task is ready (or failed), there are some options: keep eye on script, check from time to time, get notification or play a sound.

Depending on a system and configuration, notifications and sound may be easier or harder to use, but there is quite unified and easy option to use default system bell.

## bash

```bash
echo -e "\07"
```

Simple. If needed just wrap it into script or function.

## CMD (Windows)

Save it as a script

```cmd
echo •
```

If coping won't work. Instead of `•` press left `ALT` and on numeric keyboard type `7` (ALT Codes).
When using BASH, `-e` switch allows translating `\07` into char that rings a bell, but on Windows ALT Codes does the work.
More about [ALT Codes here]({% post_url 2022-01-26-alt-codes})

If no script is needed and still information on command end is needed, then press `CTRL + G` ring the bell.
