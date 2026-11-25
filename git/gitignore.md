# .gitignore patterns

```gitignore
# files anywhere
*.log
.env

# a folder anywhere
node_modules/
__pycache__/

# only at repo root
/build

# everything in a folder except one file
config/*
!config/example.yaml
```

**Already committed a file you now want ignored?** Ignoring doesn't untrack it:

```bash
git rm --cached .env
git commit -m "Stop tracking .env"
```

**Check why a file is ignored:** `git check-ignore -v path/to/file`

**Gotcha:** if `.env` with secrets was ever pushed, removing it isn't enough. Rotate the secrets.
