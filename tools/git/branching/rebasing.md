# Rebase

"Rebasing replays changes from one line of work onto another in the order they were introduced"

https://git-scm.com/book/en/v2/Git-Branching-Rebasing

## Git rebasing

### Rebase onto master/main

```
git checkout master
git pull
git checkout feature/my-cool-feature
git rebase master
```
- updates your feature branch with the lastest changes from master
- keeps a linear history
- you might need to resolve conflicts during the rebase

### Disabling automatic rebasing when pulling
```
git config pull.rebase false
```
- this ensures `git pull` does a merge instead of a rebase
- useful if you want to preserve merge commits rather than rewriting history