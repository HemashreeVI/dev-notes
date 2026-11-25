# find and xargs

```bash
find . -name "*.py"                       # by name
find . -type f -size +100M                # files over 100 MB
find /var/log -mtime -1                   # modified in the last day
find . -name "*.pyc" -delete              # delete matches
find . -type d -name node_modules -prune  # match folder but don't descend

find . -name "*.log" -print0 | xargs -0 gzip     # safe with spaces in names
find . -name "*.js" -exec wc -l {} +             # run once with many files
ls *.png | xargs -P 4 -I{} convert {} {}.webp    # 4 in parallel
```

**Gotcha:** without `-print0` / `-0`, file names with spaces break xargs.
