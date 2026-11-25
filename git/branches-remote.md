# Working with remote branches

```bash
git fetch origin                       # download, change nothing locally
git switch -c feature origin/feature   # local branch tracking a remote one
git push -u origin feature             # first push; -u sets upstream
git branch -vv                         # see what each branch tracks, ahead/behind
git push origin --delete feature       # delete remote branch
git fetch --prune                      # forget remote branches that were deleted
```

**`pull` = `fetch` + `merge`** (or rebase). Make rebase the default to avoid noise merge commits:

```bash
git config --global pull.rebase true
```
