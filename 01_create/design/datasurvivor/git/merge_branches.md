---
tags:
  - git
  - merge
  - branch
  - push
  - remote
  - local
---
# Merge branches 

Previously
- [[branches_intro|you got familiar with branches]]
- [[create_branch|you created a `some_feature` branch]]
- you finished working on it

so it's time to merge everything with the main branch.
I certainly use `main` branch and `some_feature` branch as examples. You can have as many branches as you want and branches can branch further. In this example `main` is the branch that we forked off from and where we want to return to. 

## Fast forward merge
The easiest of all merges is when `main` in intact and `some_feature` only contain non-conflicting changes with `main`. (Eg. you just add a few extra lines, without the rest of the code being changed.)

1. Check out to the `main` branch.
```bash
git switch main
git pull # Optional but you can update it with origin
```

2. Now you can merge.
```bash
git merge some_feature
```

Basically that's it. 

Now you are ready to [[delete_branch|delete the redundant branch.]] Certainly, this step is not strictly necessary. Sometimes you need to keep the `some_feature` branch for further development or testing purposes.

## Merge with conflicts

Life is tough sometimes and you need to resolve conflicts between `main` and `some_feature`. For instance, when the same line of code contains contradictory information on each branch.

Sometimes it's just enough to say, that whenever you have a conflict, the content of the given line of one of the branches should prevail. 

Eg.

```python
# Main branch line 1:
print("Hello World!)

# Some_feature branch line 1:
print("Good-bye World!")
```

The code depends on which branch we favor. If it's the `main` branch, or _our_ one (the one we are currently on), the command will be:

```bash
git merge -X ours some_feature
```

If it's the _other_ branch (ie. `some_feature`), then the command is:

```bash
git merge -X theirs some_feature
```

I don't think `ours` and `theirs` is the smartest naming convention, but hey. Git is full of these quirks. 

If you wonder what `-X` is, it's just a shorthand for the `--strategy-option` flag. This is used to finetune merging strategies. (In our case, if it should keep info from our or their branch.)

Oh, this only works with conflicting structural parts. If you have changes elsewhere in the file, they will be merged like [[#Fast forward merge|we discussed before]]. 