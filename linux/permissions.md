# File permissions

```text
-rwxr-x---  1 hema dev  run.sh
 │  │  └── others: nothing
 │  └───── group:  read + execute
 └──────── owner:  read + write + execute
```

| Number | Meaning |
|---|---|
| 4 | read |
| 2 | write |
| 1 | execute |

```bash
chmod 755 run.sh        # rwx r-x r-x
chmod 600 ~/.ssh/id_ed25519   # private key: owner only (ssh refuses otherwise)
chmod +x deploy.sh      # add execute
chown hema:dev file     # change owner and group
```

On folders, `x` means "can enter". A folder needs `r` + `x` to list its contents.

**Gotcha:** `chmod -R 777` "fixes" permission errors by letting everyone write everything. Find the right owner instead.
