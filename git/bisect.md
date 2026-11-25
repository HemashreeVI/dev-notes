# Finding the bad commit with git bisect

Binary search through history: 1,000 commits take ~10 steps.

```bash
git bisect start
git bisect bad                 # current commit is broken
git bisect good v1.4.0         # this tag was fine
# Git checks out a middle commit. Test it, then:
git bisect good    # or: git bisect bad
# ...repeat until Git prints "<hash> is the first bad commit"
git bisect reset               # back to where you started
```

**Automate it** with any command that exits 0 for good, non-zero for bad:

```bash
git bisect run ./run_tests.sh
```
