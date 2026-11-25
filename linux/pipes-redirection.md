# Pipes and redirection

```bash
cmd > out.txt          # stdout to file (overwrite)
cmd >> out.txt         # append
cmd 2> err.txt         # stderr to file
cmd > all.txt 2>&1     # both to the same file (order matters!)
cmd &> all.txt         # same, bash shorthand
cmd 2>/dev/null        # discard errors
cmd < input.txt        # file as stdin
cmd1 | cmd2            # stdout of cmd1 -> stdin of cmd2
cmd | tee out.txt      # show AND save
```

**Exit codes:** `$?` is the last command's status (0 = success). In a pipeline it's the *last* command's, so add `set -o pipefail` in scripts to fail if any part fails.

**Gotcha:** `cmd 2>&1 > file` sends stderr to the terminal, not the file. Redirections apply left to right.
