---
title: Create a new branch
tags:
  - git
  - branch
  - push
  - remote
---
Assuming you are already familiar with [[branches_intro|how branches work]]  in git, it's time to create a new branch. 
# Create new branch locally and pushing it to remote

While `git checkout -b newbranchname` works, this will also do the job:
```bash
git switch -c newbranchname
```
Now start working on it. Then...

```bash
git add whateveryouwanttoadd
git commit -m "Commit message"
git push -u origin newbranchname
```

The `-u` flag is needed only for the first push. From now on you can simply push as

```bash
git add whateveryouwanttoadd
git commit -m "Some other commit message"
git push
```

## Git MOC
[[0_git_moc]]


