# DFS and backtracking

Backtracking = DFS over choices: choose, explore, un-choose.

```python
def subsets(nums):
    res, path = [], []
    def dfs(i):
        if i == len(nums):
            res.append(path[:])          # copy!
            return
        path.append(nums[i]); dfs(i + 1)  # choose nums[i]
        path.pop();           dfs(i + 1)  # skip nums[i]
    dfs(0)
    return res
```

**Same template solves:** permutations, combinations, combination sum, N-Queens, word search, sudoku.

**Speed-ups:** sort first and skip duplicates (`if i > start and nums[i] == nums[i-1]: continue`), and prune branches that can't succeed.

**Gotcha:** append a *copy* of `path`, or every result ends up as the same list.
