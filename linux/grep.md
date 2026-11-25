# grep essentials

```bash
grep -rn "TODO" src/            # recursive, with line numbers
grep -ri "error" app.log        # case-insensitive
grep -v "DEBUG" app.log         # lines NOT matching
grep -c "500" access.log        # count matching lines
grep -E "timeout|refused" log   # extended regex: alternation
grep -o "user_id=[0-9]*" log    # print only the matched part
grep -A3 -B1 "Traceback" log    # 3 lines after, 1 before
grep -l "kafka" -r config/      # just the file names
```

**Faster alternative:** `rg` (ripgrep) respects `.gitignore` and is recursive by default: `rg "TODO" src/`.

**Gotcha:** quote patterns, or the shell expands `*` and `?` before grep sees them.
