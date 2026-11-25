# Recovering "lost" work with reflog

Git remembers every position `HEAD` has been at for ~90 days, even after a bad `reset --hard` or a deleted branch.

```bash
git reflog
# a1b2c3d HEAD@{0}: reset: moving to HEAD~3
# 9f8e7d6 HEAD@{1}: commit: add payment retry     <- the work you "lost"

git reset --hard 9f8e7d6          # go back to it
# or keep current state and just restore a branch:
git branch rescue 9f8e7d6
```

**Works for:** bad resets, botched rebases, deleted branches.
**Doesn't work for:** changes that were never committed (use `git stash` habitually).
