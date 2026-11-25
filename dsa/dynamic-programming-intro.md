# Dynamic programming: how to start

DP = recursion + remembering answers to overlapping subproblems.

**Four questions**
1. **State:** what does `dp[i]` mean? ("min coins to make amount i")
2. **Transition:** how is it built from smaller states?
3. **Base case:** `dp[0] = 0`.
4. **Answer:** which state? (`dp[amount]`)

```python
def coin_change(coins, amount):
    INF = float("inf")
    dp = [0] + [INF] * amount
    for a in range(1, amount + 1):
        for c in coins:
            if c <= a:
                dp[a] = min(dp[a], dp[a - c] + 1)
    return dp[amount] if dp[amount] != INF else -1
```

**Top-down** (`@functools.cache` on a recursive function) is often easier to write first; convert to a bottom-up table if recursion depth is a problem.
