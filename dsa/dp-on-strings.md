# DP on two strings

`dp[i][j]` = answer for the first `i` chars of `a` and first `j` of `b`.

**Longest common subsequence:**

```python
def lcs(a, b):
    m, n = len(a), len(b)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if a[i-1] == b[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    return dp[m][n]
```

**Edit distance:** same table; on mismatch `1 + min(insert dp[i][j-1], delete dp[i-1][j], replace dp[i-1][j-1])`, with base cases `dp[i][0] = i`, `dp[0][j] = j`.

Used in `diff`, spell-checkers, and DNA alignment.
