# git stash

Park uncommitted changes so you can switch branches with a clean tree.

```bash
git stash push -m "half-done login form"   # save (tracked files)
git stash push -u -m "with new files"      # -u also saves untracked files
git stash list                             # stash@{0}: On main: half-done login form
git stash pop                              # re-apply newest and drop it
git stash apply stash@{1}                  # re-apply but keep it in the list
git stash drop stash@{1}
```

**Gotcha:** plain `git stash` ignores new (untracked) files. Use `-u`.

**Tip:** `git stash show -p stash@{0}` shows the diff before applying.
