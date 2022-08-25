---
title: Git fork origin
date: "2020-10-28T19:12:03.284Z"
description: "git fork origin"
---

```
## Register upstream
git remote add upstream git://github.com/
## for remove
git remote rm upstream
## Pull fork source repository.
git fetch upstream
## Merge fork source repository master to local branch
git merge upstream/master
```