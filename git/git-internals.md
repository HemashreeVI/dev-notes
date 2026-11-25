# Git internals in 5 minutes

Git is a key-value store of 4 object types, each named by the hash of its content:

| Object | Holds |
|---|---|
| blob | file contents |
| tree | a folder: names -> blobs/trees |
| commit | a tree + parent(s) + author/committer + message |
| tag | a name + message pointing at a commit |

```bash
git cat-file -p HEAD            # the commit
git cat-file -p HEAD^{tree}     # its top-level folder
git cat-file -p <blob-hash>     # a file's contents
```

A **branch** is just a file containing a commit hash (`.git/refs/heads/main`). `HEAD` points at the current branch.

**Consequences:**
- Changing anything in a commit (message, date, parent) changes its hash, which is why rebase "rewrites history".
- Identical files are stored once, no matter how many commits contain them.
