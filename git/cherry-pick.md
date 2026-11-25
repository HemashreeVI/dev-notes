# git cherry-pick

Copy one specific commit onto the current branch.

```bash
git switch release-1.2
git cherry-pick 4f2a9c1            # copy a hotfix from main
git cherry-pick a1b2..c3d4         # a range (excludes a1b2)
git cherry-pick -x 4f2a9c1         # adds "(cherry picked from ...)" to the message
```

On conflict: fix files, `git add`, then `git cherry-pick --continue` (or `--abort`).

**When to use:** backporting a fix to a release branch.
**When not to:** moving whole features around. Merge or rebase instead, or you'll get duplicate commits.
