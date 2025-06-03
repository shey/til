# Cleaning Up Old Git Branches

## Prune Branches

Removes references to branches that no longer exist on origin.

```bash
$ git remote prune origin
```

## Delete Merged Local Branches

Cleans up local branches that have already been merged.

```bash
$ git branch --merged | grep -Ev "(^\*|^\+|master|staging|main)" | xargs --no-run-if-empty git branch -d
```
