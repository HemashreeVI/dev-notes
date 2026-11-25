# sed for quick edits

```bash
sed 's/foo/bar/' file           # replace first match per line (prints result)
sed 's/foo/bar/g' file          # all matches
sed -i 's/8080/9090/g' app.conf # edit in place (GNU/Linux)
sed -i '' 's/a/b/g' file        # in place on macOS (BSD sed needs '')
sed -n '10,20p' file            # print lines 10-20
sed '/^#/d' file                # delete comment lines
sed '/^$/d' file                # delete empty lines
sed 's|/usr/local|/opt|g' file  # any delimiter, handy for paths
```

**Gotcha:** `-i` differs between GNU and BSD sed. For scripts that must run on both, write to a temp file and `mv` it.
