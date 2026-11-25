# Binary search (the version that doesn't loop forever)

Search for the **first position where a condition becomes true**.

```python
def first_true(lo, hi, ok):
    # ok(x) is False...False True...True on [lo, hi]
    while lo < hi:
        mid = (lo + hi) // 2
        if ok(mid):
            hi = mid          # mid might be the answer
        else:
            lo = mid + 1      # answer is after mid
    return lo

# lower_bound: first index with nums[i] >= target
i = first_true(0, len(nums), lambda i: i == len(nums) or nums[i] >= target)
```

**Binary search on the answer:** "minimum capacity to ship in D days", "smallest speed to eat bananas" → `ok(x)` = "is x enough?".

Python has it built in: `bisect.bisect_left(nums, target)`.
