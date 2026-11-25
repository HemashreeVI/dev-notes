# Rebase vs merge

Both bring changes from one branch into another. They differ in the history they leave.

| | `git merge main` | `git rebase main` |
|---|---|---|
| History | keeps both lines, adds a merge commit | replays your commits on top of `main`, straight line |
| Rewrites commits | no | yes (new hashes) |
| Safe on shared branches | yes | no |

```bash
# on feature branch
git fetch origin
git rebase origin/main        # linear history
# or
git merge origin/main         # merge commit, history untouched
```

**Rule of thumb:** rebase your *own* local branch to tidy it; merge anything other people already pulled.

**Gotcha:** after a rebase you must `git push --force-with-lease`, never plain `--force`. It refuses if someone else pushed in the meantime.
