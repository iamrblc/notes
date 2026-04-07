---
tags:
  - branch
  - git
---
# What are branches?

You can certainly work on a codebase in one chunk. You start somewhere and eventually reach an endpoint. You can even distribute the work among many of you so that everyone is responsible for one chunk. However, you’ll soon see that this approach may pose many obstacles, headaches, and the use of profane language.

The situation gets especially heated when you need to make changes (e.g. introducing a new feature) without breaking the whole code. (Also called: impossible mission.)

Now imagine you could keep a more or less working version up and running while secretly working on a new version behind the scenes—and you only incorporate the new work once it runs smoothly.

That’s where branches come in. Let’s say you have a `main` branch, but you want to introduce a new feature. You just [[create_branch|create]] a `some_feature` branch, which is a duplicate of the current state of `main`. You can fool around on the `some_feature` branch as much as you want. It won’t affect the functionality of the `main` branch. Once you’re done developing the feature, you can [[merge_branches|merge]] the changes back into `main`.