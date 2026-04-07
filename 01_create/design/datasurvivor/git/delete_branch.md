---
tags:
  - branch
  - git
  - delete
---
# Delete branches

Sometimes a branch becomes redundant. For example when you [[merge_branches|merged]] the newly developed features to the `main` branch, so `some_feature` is just sitting there on your disk all lonely, feeling worthless and entering an existential crisis. 

### Delete branches locally

Bluntly, you can just...

```bash
git branch -d some_feature
```

However, when `some_feature` is not fully merged, this may end up with an error message. Of course full merge would be ideal but we don't live in an ideal world. Sometimes it's not possible. In this case you can still force deletion with a brave capital move. I mean capitalize the `-D` flag.

```bash
git branch -D some_feature
```

### Delete branches on remote 

You could certainly log on to github and delete the branches manually, but it's much easier to just push the deletion.

```bash
git push origin --delete some_feature
```