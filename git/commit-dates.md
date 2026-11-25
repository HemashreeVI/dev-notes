# How commit dates work

Every commit stores two timestamps:

```text
author    Name <email> 1641038400 +0530   <- when the change was written
committer Name <email> 1641038400 +0530   <- when it was applied (changes on rebase/cherry-pick)
```

They're Unix timestamps (seconds since 1970-01-01 UTC) plus a timezone. Git takes them from the clock, unless you set them:

```bash
GIT_AUTHOR_DATE="2024-03-15T12:00:00+0530" \
GIT_COMMITTER_DATE="2024-03-15T12:00:00+0530" \
git commit -m "message"
```

```bash
git log --format='%h  author: %ad  committer: %cd'   # see both
git commit --amend --no-edit --date=now              # reset author date on last commit
```

**Why it matters:** GitHub's contribution graph uses the **author date**, so dates are trivially editable and prove nothing on their own. (See my `time-travel` repo for an experiment with this.)
