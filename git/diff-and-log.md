# Useful diff and log commands

```bash
git diff                     # unstaged changes
git diff --staged            # what will be committed
git diff main...feature      # what feature added since it branched
git diff --stat              # files changed, +/- counts

git log --oneline --graph --all          # branch picture
git log -p path/to/file                  # every change to one file
git log -S "functionName"                # commits that added/removed a string
git log --author="Hema" --since="2 weeks ago"
git blame -L 40,60 app.py                # who last touched lines 40-60
git show HEAD~2:app.py                   # file as it was 2 commits ago
```

**Tip:** `git log -S` ("pickaxe") is the fastest way to find when a function or config key appeared or disappeared.
