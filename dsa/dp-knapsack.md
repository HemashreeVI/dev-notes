# 0/1 knapsack and its family

Each item is used at most once; maximise value within capacity W.

```python
def knapsack(weights, values, W):
    dp = [0] * (W + 1)
    for w, v in zip(weights, values):
        for cap in range(W, w - 1, -1):     # go BACKWARDS so each item is used once
            dp[cap] = max(dp[cap], dp[cap - w] + v)
    return dp[W]
```

**Same shape, different question:**
- Partition equal subset sum → can we reach `sum/2`? (boolean dp)
- Target sum with +/- → count ways to reach a sum.

**Unbounded knapsack** (items reusable, e.g. coin change): loop capacity **forwards**.
