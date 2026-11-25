# Undoing commits

Pick the command by *where* the mistake is.

| Situation | Command |
|---|---|
| Fix the last commit message / add a forgotten file | `git commit --amend` |
| Undo last commit, keep changes staged | `git reset --soft HEAD~1` |
| Undo last commit, keep changes unstaged | `git reset HEAD~1` |
| Throw away last commit and its changes | `git reset --hard HEAD~1` |
| Undo a commit that's already pushed | `git revert <hash>` |

```bash
git revert a1b2c3d        # creates a NEW commit that undoes a1b2c3d
git push                  # safe: history isn't rewritten
```

**Gotcha:** `reset` rewrites history. Only use it on commits you haven't pushed, or you'll need a force push and will break teammates' clones.
