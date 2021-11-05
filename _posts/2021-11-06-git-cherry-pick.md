---
bg_credential: <a href="https://unsplash.com/@joannakosinska?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Joanna Kosinska</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
bg:            "joanna-kosinska-_xN7UbcZ33I-unsplash.jpg"
layout:        post
title:         "GIT &mdash; cherry-pick"
crawlertitle:  "GIT &mdash; cherry-pick more powerful than you think!"
summary:       "Moving commits form branch to branch"
date:          2021-11-06
categories:    posts
tags:          ['git', 'cherry-pick', 'commit']
author:        "mwilczek.net"
references:
  "https://git-scm.com/docs/git-cherry-pick":
  "https://stackoverflow.com/questions/1994463/how-to-cherry-pick-a-range-of-commits-and-merge-them-into-another-branch":
---

`git cherry-pick` is a simple method for applying the same changes into multiple branches.
It's enough to do changes once, then copy commit into different places.

## Find commit id

To select only one commit, first find it's id. Depending on tool there are different methods
to do so:
* Check history in gui tool (Source Tree, GIT GUI, GIT Kraken, etc&hellip;)
* Check history in command line: `git log` for example
* Check history in remote tool (GitHub, GitLab, Gerrit, etc&hellip;)

## Pick one commit

Switch to destination branch and pass commit id to `git cherry-pick` command. Commit id can be either short or full.

```bash
# git cherry-pick COMMIT_ID

git cherry-pick e1d3c7
# OR
git cherry-pick e1d3c7d0d51d59de61020517a2b53119ead4b7d6
```

In case of conflicts (it happens), follow the same procedures as during
merge, rebase, or other operations that moves commits between branches.

## Pick multiple commits

It's very common practice to create multiple small commits for each
feature or task. In such situation it is very time consuming to pick
commit by commit.

Fortunately, `git cherry-pick` supports ranges!

Lets suppose that source branch looks like this:

```
 Z
 |
 Y
 |
 X
 |
...
 |
 D
 |
 C
 |
 B
 |
 A
 |
Initial Commit
```

Now we need to pick commits starting from C up to Y. There are 2 ways
of defining range:
* Including all pointed commits: `C^..Y`
* Starting from next commit than given: `B..Y` - take next commit (C)
than given (B)

```bash
# Remember about switching to destination branch

git cherry-pick C^..Y
# OR
git cherry-pick B..Y
```
